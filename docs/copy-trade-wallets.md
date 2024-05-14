# Table of Contents

- [Arbitrum Uniswap - Transaction Analysis of the Past 100 Days](#arbitrum-uniswap---transaction-analysis-of-the-past-100-days)
- [Arbitrum GMX - Transaction Analysis of the Past 100 Days](#arbitrum-gmx---transaction-analysis-of-the-past-100-days)
- [Arbitrum Vertex - Transaction Analysis of the Past 100 Days](#arbitrum-vertex---transaction-analysis-of-the-past-100-days)

## Arbitrum Uniswap - Transaction Analysis of the Past 100 Days

### Overview

- In the last 100 days, the most active wallet completed 53,000 transactions.
- Around 20 million transactions occurred during this period.
- Dune Analytics charts are available for the top 10 wallets by volume and transaction count [here](https://dune.com/aishlia/arbitrum-uniswap).

### Key Findings

1. **Top Wallets by Transactions:**
    - The wallet with the highest transaction volume completed 53,000 transactions.
    - The graph limits subgraph requests to 100 transactions returned, making it impractical to pull non-specific total information.

2. **Top Wallets by Volume:**
    - The wallet with the highest volume transacted 1 billion USD equivalent.
    - This volume may be skewed by overvalued tokens, similar to earlier third-party tokens in swaps.

3. **Wallet Characteristics:**
    - Top wallets in both transaction count and volume categories are either part of the Uniswap router or market-making bots.
    - Filtering out wallets that interacted with at least two unique `txn_to` addresses shows similar results.

### Analytical Challenges

- **Incomplete Data:**
    - Neither Dune Analytics nor the graph store provides complete USD equivalent values at the time of trade.
    - The subgraph reports transaction numbers but lacks equivalent gas prices and often misreports USD equivalents.
    - Dune Analytics lacks a column for incoming token USD equivalents.

### Profit Calculation

- By utilizing a tax calculator, it's possible to calculate total profits for specific wallets, excluding any Centralized Exchange (CEX) activity.

## Arbitrum GMX - Transaction Analysis of the Past 100 Days

## Arbitrum Vertex - Transaction Analysis of the Past 100 Days
