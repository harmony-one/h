# DeFi Yield Strategy Analysis (Corrected)
## Wallet: 0x881e625e5c30973b47cee3a0f3ef456012f13f7d

## Executive Summary
This report analyzes a three-step DeFi yield optimization strategy that combines Aave, Pendle, and Magpie protocols on Sonic network. The strategy transforms a single position through multiple protocols to maximize yield. This analysis corrects previous calculations to avoid double-counting yield components.

## Yield Optimization Path Explained

### Step 0: Initial Deposit (Prerequisite)
- **Action**: Deposit 10,000,000 USDC.e into Aave
- **Result**: Received 9,996,580 aUSDC (interest-bearing USDC)
- **Yield**: ~4.92% APY from Aave lending protocol
- **Transaction**: 0x7bac75c7b1305785ec98fdb8771045c44ab820c6bcdecc035c622d26c99e0a0f
- **Date**: March 17, 2025, 07:14:18 PM UTC

### Step 1: Tokenize Yield with Pendle
- **Action**: Convert aUSDC into PT (Principal Tokens) and YT (Yield Tokens)
- **Result**: Received 10,000,022 PT tokens and 10,000,022 YT tokens
- **Yield Structure**:
  * Original yield: ~4.92% APY (Aave yield now captured by YT tokens)
  * Additional yield: ~6.82% APY (from Pendle's tokenization premium for PT tokens)
- **Transaction**: 0xa20bb4b22b87a36eec87643d0f93a421de11a2317a9d352055a992643878cf96
- **Date**: March 17, 2025, 09:48:07 PM UTC

### Step 2: Liquidity Provision on Pendle
- **Action**: Provide PT tokens + USDC to Pendle liquidity pool
- **Result**: Received LP tokens representing pool share
- **Yield Components** (as displayed in Pendle interface):
  * Trading Fees: ~2.47% (estimated from LP yield components)
  * LP Incentives: ~1.65% (estimated from LP yield components)
- **Transaction**: 0x3a9aada37c469f19ff553901dd5c711b1b769dfa32377d56c02de9c62bee4888
- **Date**: March 17, 2025, 09:55:38 PM UTC
- **Details**: 
  * Deposited approximately 4,891,978 PT tokens (about half of the 10M from Step 1)
  * Used `depositMarket` function to provide liquidity to Pendle pool
  * The wallet's position represents a significant portion of the pool's $13.21M total liquidity

### Step 3: Staking on Magpie (Pending Analysis)
- **Action**: Stake LP tokens on Magpie
- **Result**: Earn additional Magpie rewards while maintaining liquidity position
- **Expected Additional Yield**:
  * Additional yield: [TBD] from Magpie rewards
- **Transaction**: [To be identified]

## Corrected Understanding of Yield Distribution

The key insight in this corrected analysis is recognizing how yield is properly distributed across the different tokens without double-counting:

1. **Original Aave Yield (4.92%)**:
   - This yield is entirely captured by the YT tokens
   - This represents the pure yield component from the original aUSDC position

2. **Pendle Tokenization Premium (~6.82%)**:
   - This yield component applies to PT tokens
   - Represents additional yield generated through Pendle's tokenization mechanism
   - This is NOT double-counting the Aave yield, as it's a separate yield component

3. **Liquidity Provision Yield (~4.12%)**:
   - This yield applies only to the PT tokens placed in the liquidity pool
   - Consists of trading fees and LP incentives
   - This is additional yield on top of the PT tokenization premium

## Corrected Yield Calculation

In this corrected calculation, we break down how each portion of the initial capital generates yield:

### Total Initial Capital: 10,000,000 USDC.e (~$10M)

1. **YT Tokens (10,000,022 tokens)**:
   - Capital Value: ~$10M
   - Yield Rate: 4.92% APY (Aave yield)
   - Annual Yield: ~$492,000

2. **PT Tokens in LP (4,891,978 tokens, ~48.9% of total PT)**:
   - Capital Value: ~$4.89M
   - Base Yield Rate: 6.82% APY (Pendle tokenization premium)
   - Additional LP Yield: 4.12% APY (trading fees + LP incentives)
   - Total PT in LP Yield: 10.94% APY
   - Annual Yield: ~$534,982

3. **Remaining PT Tokens (~5,108,044 tokens, ~51.1% of total PT)**:
   - Capital Value: ~$5.11M
   - Yield Rate: 6.82% APY (Pendle tokenization premium)
   - Annual Yield: ~$348,369

### Overall Corrected Yield

| Token Type | Value ($) | Yield Rate | Annual Yield ($) |
|------------|-----------|------------|------------------|
| YT Tokens | $10M | 4.92% | $492,000 |
| PT in LP | $4.89M | 10.94% | $534,982 |
| PT Held | $5.11M | 6.82% | $348,369 |
| **Total** | **$10M** | **13.75%** | **$1,375,351** |

**Note**: The total effective yield of 13.75% is calculated based on the $1,375,351 annual yield on the initial $10M investment. This represents the properly calculated, non-duplicative yield of the strategy.

## Updated Yield Analysis Based on Pendle V2 API Data (March 20, 2025)
Our initial yield analysis has been refined using direct data from the Pendle V2 API, providing more accurate yield figures for the DeFi strategy. The API endpoints for market data and historical performance reveal several important insights that affect our estimated yield calculations:

### Key API Findings:

1. **Address Clarification**:
   - The address 0x3f5ea53d1160177445b1898afbb16da111182418 is specifically a Pendle LP token representing the PTaUSDC/USDC pool, not just a "Market" address
   - This same address is referenced throughout all steps of the strategy, confirming it as the central liquidity position being optimized

2. **Revised Yield Components**:
   - **Aave Underlying Yield**: 8.717% (vs. our initial 4.92% estimate)
     * Consists of 0.717% base interest + 8.0% rewards
   - **Pendle Tokenization (PT) Yield**: 10.124% implied APY (vs. our initial 6.82% estimate)
   - **LP Position Yield**: 5.13% combined from:
     * 0.21% trading fees (swapFeeApy)
     * 4.92% LP rewards (lpRewardApy)
   - **Maximum Boosted APY**: Up to 22.43% possible according to the API

3. **Total Strategy Yield Recalculation**:

| Token Type | Value ($) | Revised Yield Rate (Annual) | Yield Until Expiry (Aug 14, 2025) |
|------------|-----------|-----------------|------------------|
| YT Tokens | $10M | 8.717% | $436,780 (5 months) |
| PT in LP | $4.89M | 15.25% (10.124% + 5.13%) | $310,719 (5 months) |
| PT Held | $5.11M | 10.124% | $215,557 (5 months) |
| Magpie Staking | $4.89M (same LP tokens) | TBD | TBD |
| **Total** | **$10M** | **21.35%+** | **$963,056+ (5 months)** |

This represents a significant increase from our initial conservative estimate of 13.75%, primarily due to higher-than-estimated yields from both the Aave component and the Pendle tokenization premium. 

### Asset Details

The key asset in this strategy has the following specifications according to the Pendle V2 API:
```
{
      "name": "LP aUSDC",
      "decimals": 18,
      "address": "0x3f5ea53d1160177445b1898afbb16da111182418",
      "symbol": "PENDLE-LPT",
      "tags": [
        "PENDLE_LP"
      ],
      "expiry": "2025-08-14T00:00:00.000Z"
}
```

**Important Note on Expiration**: As shown above, the Pendle position has an expiration date of August 14, 2025, which is approximately 5 months from the position creation date. This means the yield calculations should account for this limited timeframe rather than a full year. The revised table above adjusts yield figures to reflect only the 5-month period until expiration.

### ### Pending Analysis:

The Magpie staking rewards (Step 3) remain unquantified and would further increase the total yield beyond the current projection. It's important to note that the Magpie staking involves the same $4.89M in LP tokens that are already generating the 15.25% APY - this is not double-counting the same capital, but rather adding an additional yield layer on top of the existing LP position. These additional rewards would be earned without disrupting the underlying positions.

### Conclusion:

The direct API data confirms this strategy is even more profitable than initially estimated, with a projected yield of $963,056+ for the 5-month period until the position expires (equivalent to a minimum annualized rate of 21.35% before accounting for additional Magpie rewards). This multi-layered approach effectively extracts multiple yield components from the same capital base, demonstrating sophisticated yield optimization within the limited timeframe dictated by the product's expiration date.

## Appendix: Key Contract Addresses
- Pendle Market: 0x3f5ea53d1160177445b1898afbb16da111182418
- YT Token Contract: 0x18D2D54f42ba720851bAE861b98A0F4B079e6027
- Pendle Router: 0x888888888889758F76e7103c6CbF23ABbF58F946
- aUSDC: 0x578Ee1ca3a8E1b54554Da1Bf7C583506C4CD11c6
