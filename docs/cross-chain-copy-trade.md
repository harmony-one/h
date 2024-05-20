# Dev Notes | Telegram Wallet: copy-trade from Arbitrum 


## Overview

See https://www.x.country/harmony-2024-defi-a3e0e851036c45c8ace41bd2aadd6f56

Discuss at: https://github.com/polymorpher/sms-wallet/issues/24

## Key Unknowns

1. How much impact the price differences between Arbitrum and (bridged assets on) Harmony would have on the profitability of the trades? 
2. How much liquidity do we need on Harmony to minimize the impact of price slippage on DEX, so the copied-trades remain profitable? 
3. How sensitive are the trades to timing and price-arbitrage on Arbitrum? Would seconds of delay matter? Are most copyable profitable trades high frequency arbitrage trades?
4. Can the trades be meaningfully copied and executed on DEX? Do we need to trade on CEX as well using user deposited funds (which could lead to very complex legal issues), or at least act on behalf of the user using CEX API keys they assign to the system?

## Proposed System Components

For initial implementation, we could skip the "Trading Wallet Identification" component, and copy trades from user-assigned wallets only. 


### Trading Wallet Identification

Create Dune analytics queries and use heuristics and APIs to identify wallets (ranked by trading volume) that are in fact (1) trading, as in interacting with known DEX and CEX; (2) generating profit, by calculating net changes in native asset, well-known ERC-20 tokens and wrapped tokens, for every fixed time interval (e.g. a day)


### Trade Monitoring and Extraction

Parse transactions from a given Trading wallet address on Arbitrum, extract trades and index them in real time in a near-instant KV store (Redis) for immediate lookup, and a document database (ElasticSearch) for search and analytics later

### Express (Custodial) Trading Wallet

Upon receiving instructions from a user (Telegram chat command or button-press in Telegram-bot UI), create a unique hot wallet for each user where the server maintains the private key (stored in a separate PostgreSQL database with finer access control). This wallet allows the user to deposit or withdraw ONE through Telegram Wallet

### Copy-trade Search and Display

Upon receiving instructions from a user, retrieve the most recent X trades from top Y trading wallets (identified through Trading Wallet Identification system). Fix X=20 and Y=10 in the initial implementation, but allow parameters in later iterations, as well as time range and wallet address specification

### Auto-trade Execution

Upon receiving instructions from a user (that specifies a particular wallet to copy-trade), begin or stop auto-trading. When auto-trading is activated, the deposited ONE asset from the user will be converted to the target wallet's asset allocation in proportion (using bridged assets, assumed to exist and have sufficient pool on swap.country), placed into an "Execution Wallet". The system will then subscribe this wallet to trades from the target wallet (as observable through Redis and a pub-sub system), and automatically executes these trades using assets in Execution Wallet provided that the exchange rate does not deviate from the counterpart in Arbitrum for too much. If any trade cannot be completed (due to misaligned rate), auto-trading immediately stops and the user is notified via Telegram message.


## Data acquisition and latency

Not all parts of the system are latency-sensitive. Some parts of the system need not to be computed in real-time. For example, top wallets (by trading volume or similar metrics) can be updated daily or hourly, in which case it is harmless to have some latency in terms of the data which the top-list is computed upon. This allows us to consider a broader range of APIs and tools: Etherscan, Nansen, DefiLlama, dAppRadar, Dune Analytics, The Graph, and of course, constructing custom indexer using transaction data captured from self-hosted RPC nodes. 

We evaluated these tools and found pros and cons for each. In practice, we will need to use some of them simutaneously to achieve the best result.

### Dune Analytics

Dune Analytics provides the most flexible framework and most complete data for our purpose of computing top trading wallets. However, there is no out-of-the-box solutions (pre-built dashboard or queries) that give the information we need. Multiple steps of post-processing will be required following the query result from Dune Analytics, such as removing well-known CEX wallets, bots, contract addresses.  

Here is a simple example query of obtaining 10 wallets with the highest outgoing ETH volumes at a particular date:

```
SELECT
  "from",
  SUM(value/1e18) AS total_volume
FROM arbitrum.transactions
WHERE block_time > date('2024-05-10') and block_time <= date('2024-05-11')
GROUP BY
  1
ORDER BY
  total_volume
DESC
limit 10

```

We can extend this query to aggregate both incoming and outgoing volumes, top ERC-20 token transfers, and others. 

Dune Analytics have a detailed explanation on data freshness: https://docs.dune.com/data-catalog/data-freshness. For Arbitrum, the raw data delay is merely 23 seconds, and 53 seconds for decoded data (i.e. from smart contract events). 

- For the purpose of tracking top traders, this may be more than sufficient. 
- For the purpose of follow trades in real-time, this is insufficient.


### Nansan

Nansen provides pre-computed data for "[DEX Trader P&L](https://docs.nansen.ai/data/data-catalog/dex-trades/dex-trader-p-and-l)" and enables both profitable traders and tokens to be [queried](https://docs.nansen.ai/data/data-catalog/dex-trades/dex-trader-use-cases) using their tools. Their [API](https://docs.nansen.ai/api/api-overview) allows these data to be retrieved via custom queries their flexible query language. This could potentially save us a lot of work from computing these data ourselves. 

However, their methodology is undocumented and it would be difficult to verify the quality of their result, unless we build one with similar functionalities ourselves using other tools.

Another potential issue with Nansen is they only vaguely state the data delay average is "around five minutes" and for some endpoints the result "may be cached". See https://docs.nansen.ai/other/general-faqs. There is no specific explanation, so in practice we may experience surprises in the results. The delay in the data also only makes Nansen only suitable for computing top traders, instead of capturing their trades in real-time.


### Defilama and dAppRadar

There is no information regarding data delay. The APIs seem to be more focused on macro data. 


### Etherscan

Etherscan does not provide any macro-level data, and does not have a query framework that enables us to compute top trading wallets. But in my experience, Etherscan captures transactions submitted on-chain usually without any noticeable delay, including "internal transactions" - those that are not initiated from a wallet address itself but some assets "pass through" or end up at the wallet address anyway. This makes Etherscan potentially handy for capturing trades in near real-time.

However, the query rate limit is capped at 30 per second at the highest level of paid plan, and 10-20 at lower tiers of paid plans. See https://etherscan.io/apis. 

This may limit the number of wallet addresses and contracts we can monitor, especially when there is a burst of trading activities

### The Graph

The Graph (and Subgraphs constructed from that) is designed only for indexing and transforming given smart-contract addresses and events. This limitation makes it unsuitable for monitoring EOA addresses (such as trading activities occurred at exchanges or over-the-counter), or for computing macro-level data, such as determining top trading wallets. 

Assuming these limitations can be overcome using other tools (such as Etherscan or querying RPC nodes), we may use The Graph and focus only on pre-processing trades related to DEX and ERC20 tokens. Based on [the experience](https://www.reddit.com/r/thegraph/comments/zst5wi/how_delayed_are_the_graph_indexes_compared_to/) shared by other users, the data-indexing latency for self-hosted Subgraph instances is negligible


### RPC Nodes

Arbitrum offers both official RPC node and a long list of third-party RPC providers. See https://docs.arbitrum.io/build-decentralized-apps/reference/node-providers. The cost and complexity for setting up a self-hosted Arbitrum node is low: the minimum requirement appears to be 1TB NVMe SSD hard drive, 4-core CPU, and 16GB RAM, based on https://docs.arbitrum.io/run-arbitrum-node/run-full-node. This makes implementing a custom indexer using a self-hosted node a much superior option than Etherscan from a long-term cost perspective. 


### Proprietary API

Birdeye.so seems to have already analyzed trades and traders and can provide a sorted list of traders given a token or trading-pair. See documentation at: https://docs.birdeye.so/reference/get_defi-txs-pair. This is only available for some chains (including Arbitrum)