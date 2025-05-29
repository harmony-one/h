## BTC/S-USDC LP strategy

### Objective
Outperform Bitcoin's yearly return by 15% or more while avoiding big price changes.

### Implementation

• Supply liquidity to the WBTC / USDC pool on Uniswap V3 (Ethereum) with a 10% price range.

• Short BTC perpetual on Hyperliquid equal to 50% of LP position notional value to hedge initial BTC exposure.

• Monitor 8-hour funding rates on BTC/USD perpetual; adjust position size when funding exceeds 0.1% per 8h period.

• Rebalance perpetual hedge when LP pair shifts >5% from 50/50 allocation due to price movement.

• Scale short position dynamically: increase short exposure as price approaches upper range, decrease as price approaches lower range.

### Risk Controls
• Maintain perpetual margin usage below 75%; liquidation buffer at 85%.

• Exit LP position if price moves outside range for >24 hours to avoid single-asset concentration.

• Close hedge positions if cumulative funding payments exceed 20% of weekly LP fees for 3 consecutive day.

• Monitor Ethereum gas costs; pause rebalancing if Ethereum gas fees exceed $20 per transaction.

### Key Performance Indicators (KPIs)
• Weekly fee yield ≥ 0.30 % of LP notional.
• Net BTC delta maintained between -5% and +5% of position value.
• Time-in-range ≥ 85% to maximize fee generation
