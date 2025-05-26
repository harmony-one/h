## BTC/S-USDC LP strategy

### Overview
Pool: BTC/USDC
Goal: optimize position ranges and rebalancing to earn trading fees

Pools examples

[Shadow CL WBTC/USDC](https://www.shadow.so/liquidity/0x8bc2f9e725cbb07c338df4e77c82190119ddd823)

### Position range optimization
Use perpetual futures funding rates to check market dynamics. Positive funding rates suggest bullish outcome; liquidity ranges will go above current price. Negative funding rates indicate bearish outcome, ranges will go below current price.

Example:
Binance BTCUSDC Perpetual funding rates history:

https://www.binance.com/en/futures/funding-history/perpetual/funding-fee-history

Recent trends indicate bullish sentiment on Bitcoin (as of 25 May 2025).

[SCREENSHOT BINANCE RATES]

### Position allocation
- investment size: 50% BTC, 50% USDC
- price range: += 8%

Recommended price range based on recent BTC price movements; can be adjusted at the time of investment.

### Rebalancing Strategy
- Rebalance triggers when price moves outside the current position or when funding rates shift significantly (>0.1% or <-0.1% per 8h).
- Only rebalance if fee income exceeds network fee (to offset price of rebalancing) OR the position was outside of current range for significant period of time (>=1h)
- Emergency exit script in case of high volatility

### Reducing Impermanent Loss
- Increase position range to += 15-20% during high volatility (>50% annualized)
- Allocate 10% of monthly profits to a stablecoin pool (USDC/USDT, 5% APR)

### Risk management
- Diversify by reinvesting profits into stablecoin pools
- Daily manual check of position performance and gas fees

### Metrics and monitoring
- Annualized returns VS. tokens amount deployed
- Measure impermanent loss against HODL strategy for BTC and USDC
- Range efficiency: percentage of time position stays inside LP range
- Alert (Telegram channel, SMS) on > 0.5% funding rates in 8h, indicating potential market shift
