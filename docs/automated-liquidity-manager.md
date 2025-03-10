### Automated Liquidity Manager (Draft)

#### Context
- **Goal**: Automated Liquidity Manager aims to dynamically adjust liquidity positions to optimize fee capture while mitigating impermanent loss, likely by repositioning ranges based on price trends or volatility.
- **Shadow Exchange**: a concentrated liquidity market maker (CLMM) like Uniswap V3, with fees proportional to trading volume within active ranges.
- **Data Structure**: The ClMint and ClBurn interfaces represent liquidity provision (mint) and removal (burn) events in a concentrated liquidity pool, similar to Uniswap V3.

```shell
interface ClMint {
    id: string
    pool: ClPool
    token0: Token
    token1: Token
    owner: string
    origin: string
    amount0: string
    amount1: string
    tickLower: string
    tickUpper: string
}

interface ClBurn {
    id: string
    pool: ClPool
    token0: Token
    token1: Token
    owner: string
    origin: string
    amount0: string
    amount1: string
    tickLower: string
    tickUpper: string
}

interface ClSwap {
  id: string
  pool: ClPool
  token0: Token
  token1: Token
  sender: string
  recipient: string
  amount0: string
  amount1: string
  sqrtPriceX96: string
  tick: string
}

interface ClPool {
  id: string
  symbol: string
  ...
}

interface Token {
  id: string
  symbol: string
  name: string
  ...
}
```

[Shadow Subgraph](https://sonic.kingdomsubgraph.com/subgraphs/name/exp/graphql?query=%7B%0A++clMints%28%0A++++skip%3A0%2C%0A++++first%3A1%2C%0A++++orderDirection%3Aasc%2C%0A++++orderBy%3Atransaction__blockNumber%2C%0A++++where%3A%7B%0A++++++pool_%3A%7B%0A++++++++symbol%3A+%22wS%2FUSDC.e%22%0A++++++%7D%2C%0A++++%7D%0A++%29%7B%0A++++id%0A++++transaction+%7B%0A++++++id%0A++++%09blockNumber%0A++++++timestamp%0A++%7D%0A++++owner%0A++++sender%0A++++origin%0A++++amount0%0A++++amount1%0A++++amountUSD%0A++++tickLower%0A++++tickUpper%0A++++logIndex%0A++++token0+%7B%0A++++++id%0A++++++name%0A++++++symbol%0A++++%7D%0A++++token1+%7B%0A++++++id%0A++++++name%0A++++%7D%0A++++pool+%7B%0A++++++id%0A++++++symbol%0A++++++createdAtTimestamp%0A++++++totalValueLockedUSD%0A++++%7D%0A++%7D%0A%7D#) interface

####  Strategy for Auto Balance on 1-Tick Concentrated Positions
**Core Idea**: Continuously reposition the 1-tick range to "follow" the current price (spot price tick) while anticipating short-term price movements to stay in range longer. 

##### Implementation:
- **Monitor Price**: Track the pool’s current tick in real-time using the latest swap events. Use Harmony 2-seconds block time to execute rebalancing transactions rapidly.
- **Repositioning**: When the price moves out of the current 1-tick range (i.e., crosses tickLower or tickUpper), burn the old position and mint a new 1-tick position centered on or slightly ahead of the current price.
- **Rebalance Frequency**: Adjust positions every few blocks or when a threshold price movement (e.g., 0.05%) occurs, balancing gas costs with responsiveness.
- Prioritize pools with high trading volume (e.g., S/USDC.e) and adjust the fee tier to higher settings (e.g., 0.3% or 1%) for volatile pairs.
- Automate via a smart contract or bot that interacts with Exchange’s CLMM (Concentrated Liquidity Market Maker) interface.

##### Robustness Against Impermanent Loss
Impermanent loss refers to a situation where the compensation you receive from allocating a token in a liquidity pool is less than what you would have received just holding the asset.
This happens when a token’s price changes in the market, causing your allocated assets in the liquidity pool to become worth less than their present value in the market. The larger this price change, the more your assets are exposed to impermanent loss.

[More](https://www.coinbase.com/en-pt/learn/crypto-glossary/what-is-impermanent-loss) about IL.

Robustness of the Strategy
- **Frequent Rebalancing**: By tracking the spot price and repositioning the 1-tick range, the autobalancer minimizes time spent out-of-range, reducing IL exposure. For example, if wS/WETH price shifts 0.1%, rebalancing within 2-3 seconds keeps the position active.
- **Volatility Hedging**: Pair selection matters—stable pairs (e.g., USDC.e/stablecoin) reduce IL risk compared to volatile pairs (e.g., wS/WETH). The autobalancer could prioritize stable pools.
- **Drawback**: Gas costs for frequent rebalancing could reduce profits unless Harmony’s low fees mitigate this.

