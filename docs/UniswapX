### UniswapX on Harmony

UniswapX is a permissionless, open-source protocol developed by Uniswap Labs for trading cryptocurrencies across automated market makers (AMMs) and other liquidity sources.

It enhances onchain trading by offering gas-free swaps, better pricing, and protection against maximal extractable value (MEV).

The protocol aggregates liquidity from various onchain and offchain sources, using an auction-based system to optimize trade execution.

[Official docs](https://docs.uniswap.org/contracts/uniswapx/overview)

[Github repository](https://github.com/Uniswap/UniswapX)

Core Components:
- **Signed Orders**: Swappers create offchain orders specifying trade intents (e.g., token amounts and limits), signed via Permit2 for secure token transfers.
- **Fillers**: Competitive agents who execute orders by sourcing liquidity, paying gas on behalf of swappers, and batching transactions for efficiency.
- **Order Reactors**: Smart contracts that validate, resolve, and settle orders, coordinating with fillers’ strategies for onchain execution.
- **Dutch Auction Mechanism**: Orders decay over time (e.g., via Exclusive Dutch Orders), incentivizing fillers to compete for the best execution prices.

### Deployment Steps

Deployment for the MVP can be divided by 3 steps:
1) Creating Dutch Order: [source code](https://github.com/ArtemKolodko/uniswapx-demo/blob/main/backend/src/index.ts)
2) Deploying [Dutch Order Reactor](https://github.com/Uniswap/UniswapX/blob/main/src/reactors/V2DutchOrderReactor.sol) contract
3) Creating a [Filler](https://docs.uniswap.org/contracts/uniswapx/guides/createfiller) and [integration](https://hackernoon.com/technical-overview-of-the-uniswapx-protocol-architecture-integration-methods-and-order-execution) with Uniswap V3 (swap.country)
