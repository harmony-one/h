## Jupiter DEX

UI: https://jup.ag

Forum: https://www.jupresear.ch

Intro Doc: https://station.jup.ag/guides

API Doc: https://station.jup.ag/docs/

### Key Designs

- Rust based, made for Solana[^0]
- Good UI/UX - replicating CEX experience
    - Three key features: Perpetual (up to x100 leverage), Limit Order, DCA
- [Liquidity pool](https://station.jup.ag/guides/perpetual-exchange/jlp-pool) based, backed by JPL token. No orderbook
    - Limit orders are queued and executed by monitor server through liquidity pool
    - Total AUM is capped. Asset portfolio allocation pre-configured. Pool relies on market mechanisms to enforce AUM cap and portfolio allocation.
- Comprehensive docs, APIs
    - Prices, oracles, data
    - Web3 JS libraries for order placement
- Advanced stack
    - [Pyth](https://pyth.network) for oracle[^1]
    - [Birdeye](https://bds.birdeye.so) for onchain trading data
    - [TradingView](https://www.tradingview.com) for charts

### Notes

The design seems simple and effective. It appears there is no explanation on the rationale of the design and how some parameters are chosen. Audits appear to be focusing on security and minor technical vulnerabilities. There is no audit or review of the overall design and parameters in place. 

The number of transactions per day is roughly 1.8M, based on latest 30-day statistics from https://station.jup.ag/stats/month. This means roughly 21 transactions per second, which is workable on Harmony shard0, and should have no load issues if they are processed on shard1 or other shards.

The major technical hurdle of creating a DEX based on Jupiter appears to be converting existing Rust codebase (for Solana) into Solidity, and accommodate for a longer delay before transaction can be confirmed (but finalized much faster).

Since the DEX is liquidity pool based, it may have a much harder cold-start problem and lower capital efficiency compared to one that is orderbook based. We should evaluate for orderbook-based alternatives first before looking into the code in more details.


[^0]: can potentially generalize to other chains
[^1]: Does not support Harmony. See [EVM networks](https://docs.pyth.network/price-feeds/contract-addresses/evm)



