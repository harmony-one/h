2025-09-03 Wed: Coordinated with Yuriy to establish access different aerodrome's data source he is working on. Implemented dedicated backtesting performance class to replicate production bot's logging and performance calculation pipeline. Refactored [backtesting architecture](https://github.com/harmony-one/portfolio-manager/pull/36) to utilize the new performance class and corrected APR calculation methodology to use initial capital without compounding, ensuring alignment with production bot metrics. Cleaned up position class by removing deprecated performance measurement methods including unused APR, PnL, and other legacy calculation functions.

2025-09-02 Tue: Following discussion with Aaron, conducted deep analysis on flash loan impact within Aerodrome pool fee generation by monitoring both Swap and Flash events alongside feeGrowthGlobal0X128 accumulator values. Analysis of 292 recent swap transactions revealed zero flash loan activity, confirming that all fee revenue originates exclusively from swap operations in this pool. Identified bottleneck in obtaining synchronized feeGrowthGlobal0X128, token pricing, and market data at production bot intervals due to excessive on-chain RPC calls and indexer API limits. Continued integration of [performance service](https://github.com/harmony-one/portfolio-manager/pull/36) into backtesting framework to mirror production bot's APR calculations and position tracking methodology, transitioning output from database storage to TSV format for improved compatibility.

2025-09-01 Mon: Continued analyzing LP fee mechanics, focusing on flash loan contributions to pool revenue. Generated a [comprehensive report](https://github.com/harmony-one/h/blob/main/docs/defi/aerodrome-position-fess-calculation.md) examining the relationship between flash loan operations and swap fee accumulation in AMM pools. Fixed timestamp handling inconsistencies and optimized CoinGecko integration by implementing historical price caching, significantly reducing API overhead during backtesting runs. Refactored funding rate calculations to minimize divergence between production bot logic and backtesting simulation, ensuring more accurate performance modeling.

---
2025-08-29 Fri: Continued investigating fee calculation discrepancies between the subgraph and Aaron's database. A discussion with Aaron confirmed the need to review the subgraph's source code to verify its fee calculation logic. A deep-dive into LP fee generation revealed that revenue comes from two sources: swap transactions and flash loan operations. These fees accumulate in the feeGrowthGlobal0X128 variable, which uses Q128 mathematics for precise capture. The most reliable method for position fee calculation appears to be the direct use of these accumulator variables, as this mirrors the smart contract's internal calculations and ensures complete fee capture.

2025-08-28 Thu: Added more data points to the database/subgraph analysis, revealing a persistent data coverage gap with variable fee accuracy across different time periods. The database consistently captures 7-11% of total transactions compared to the subgraph, yet achieves 43-83% fee accuracy depending on the hourly transaction mix. These findings will be communicated to Aaron. Further analysis identified the core issue as the fundamental difference in monitoring frequency: the bot checks positions every 10 minutes while backtesting processes hourly data. This 6x frequency difference requires more conservative backtesting parameters to avoid excessive rebalancing. A new HourlyStrategyConfig was created to extrapolate the RiskyStrategyConfig parameters for hourly granularity, using wider ranges (0.10 vs 0.05), higher rebalance thresholds (1.0 vs 0.5), and adjusted time windows for volatility and momentum calculations. 

2025-08-27 Wed: Analysis of Aaron’s database against subgraph hourly data revealed a significant transaction coverage gap, capturing only 7% of transactions (116 vs 1,692) yet showing a minimal 17% fee discrepancy ($654 vs $788). This confirms the database successfully captures high-value swap events, while the subgraph aggregates a wider range of transactions, including micro-transactions. Continued investigating the rebalancing discrepancies between the production bot and backtesting script. Corrected the liquidityValue calculation to use actual pool TVL from dataPoint.tvlUSD instead of individual position value, updated buildMarketState to properly accept pool TVL parameters, and resolved timestamp inconsistencies between milliseconds and seconds by aligning all data sources.

2025-08-26 Tue: Continued investigating rebalancing discrepancy between production bot and backtesting script for Aerodrome LP strategy. Analysis revealed main trigger is outOfRange=true rather than volatility deviations, indicating price movements exceed ultra-narrow position ranges. Corrected data source inconsistencies by implementing CoinGecko integration for both daily price history and hourly current prices, replacing mixed subgraph/CoinGecko approach. Tested Yuiry changes to the Aerodrome Analytics events endpoint changes, and got high request processing time, asked Yuriy to check it.

2025-08-25 Mon: Refined the calculateTokensAndLiquidity() method to ensure a balanced 50/50 token allocation, mirroring the production bot's swapTokensInWallet() logic. Despite this, the backtesting script's rebalancing frequency remains unexpectedly high at 48 events. Currently cross-referencing the backtesting script's rebalancing trigger logic with the production bot's to identify the root cause. Also spoke with Yuriy about optimizing the calculation of Aero Rewards for staked positions by filtering out ClaimRewards events to reduce the immense data handling overhead.

---
2025-08-24 Sun: (2.0h) Investigated excessive rebalancing in Aerodrome LP backtesting script potentially triggered by using Defilab's mathematically optimized token allocation (48.8% BTC / 51.2% USDC) instead of production bot's enforced 50/50 USD value split.

2025-08-22 Fri: Built [queries](https://github.com/harmony-one/h/blob/main/docs/defi/aerodrome-queries.md) to track ownership lifecycle for position management patterns. Aligned Aerodrome LP backtesting with production bot for realistic projections by synchronizing constants (LP APR: 20%, gas: $0.5), added [slippage cost calculation](https://github.com/harmony-one/portfolio-manager/pull/36) using CPMM formula.

2025-08-21 Thu: Researched SQL queries to analyze Aerodrome liquidity provider strategies from Aaron's database export, and discovered positions owned by Gauge contracts indicate staked positions. Debugged APR calculations in backtesting system - issue was JavaScript precision handling of massive BigInt values from feeGrowthGlobal0X128, not mathematical implementation. Fixed by improving BigInt arithmetic and maintaining precision throughout calculation pipeline.

2025-08-20 Wed: Resolved critical bug in Aerodrome LP backtesting where strategy-calculated asymmetric ranges were corrupted during rebalancing. Root issue: rebalanceFromStrategy() incorrectly converted precise strategy bounds into percentage representations, then recalculated ranges through getPositionTickRange(), causing precision losses and constraint violations. Problem manifested when narrow ranges (0.4%) fell below pool's minimum tick spacing (1.005% for tickSpacing=100), creating identical bounds and "Lower bound must be less than upper bound" errors. Fixed by implementing direct strategy bounds preservation, bypassing flawed percentage-conversion roundtrip. Added proper inverted pair handling and minimum range validation. Solution now preserves asymmetric ranges while maintaining compatibility, achieving realistic APRs (112.9%) but need to check rebalancing logic because went from zero to 40 rebalances.

2025-08-19 Tue: Continued analyzing Aaron's backtesting implementation, focusing on database data (LP snapshots, swap events). Discovered multiple users maintaining multiple LP positions for the same pool with different tick ranges, creating LP-level hedging rather than cross-protocol hedging like our approach. Continued testing backtesting script to fix rebalancing discrepancies with production bot. Was using $5 gas fees, but when lowering amount encountered "Lower bound must be less than upper bound" error - working on fixing this issue.

2025-08-18 Mon: Researched Aaron's cross-protocol backtesting infrastructure. He reverse-engineered Aerodrome's dynamic fee algorithm from 60K+ transactions, providing identical accuracy to our streamlined subgraph feeGrowthGlobal0X128 approach but with much richer researchable data. His system coordinates LP positions with Hyperliquid perpetuals and Deribit options for comprehensive hedged strategies. To completely replicate his system, a paid API key is needed - will discuss best approach (read access to his database could be optimal for local backtesting). Finished main branch merging to run our backtesting logic with updated strategy, finding inconsistencies in rebalance count between backtesting script and production data, working on fixing the issue.

---
2025-08-15 Fri: Created local configuration for Aaron's backtesting service for local testing. Continued testing staked position script and discussed with Yuriy updating events endpoint to filter by event type, avoiding ClaimRewards events to reduce rows per request. Resolving git merge issues on main branch to run backtesting script for unstaked positions with the updated strategy.

2025-08-14 Thu: Identified and resolved critical inconsistencies in Analytics API requests for backtesting system. Root cause was timestamp-based event filtering creating boundary condition errors between runs. Fixed by switching to block-number-only filtering. Optimized performance with larger pagination limits (25K-50K), retry logic, and event caching to handle 300K+ events for 14 days without socket timeouts. Performance improved from 50+ API calls to under 20 calls per backtest. Backtesting APR for staked positions improved from erratic values (30%, 120%, 8%) to consistent 8-10% range. Still tweaking gauge events handling. Exploring Aaron backtesting repo to local deploy for research.

2025-08-13 Wed: Integrated CoinGecko to staked Aerodrome backtesting logic and updated analytics client to work with different API instances based on working pool. Completed staking backtesting logic but found inconsistencies with APR calculation due to analytics API data handling. Running tests to fix the issue.

2025-08-12 Tue: Added staked logic to the [backtest script](https://github.com/harmony-one/portfolio-manager/pull/36). Added reverse baseline calculation for staked liquidity using current on-chain stakedLiquidity() minus net deposit/withdrawal events from backtest start to present. Removed logging from backtest script for code cleanup.

2025-08-11 Mon: Researched Aerodrome's staked position logic for production implementation, implementing position earned reward logic. Discovered gauge's withdraw method automatically claims all AERO rewards, collects trading fees, and returns NFT to wallet - existing closing multicall method just needs withdraw call added for staked positions. Continued working on AERO rewards backtesting logic, adding retrieval of staked liquidity prior to backtesting start date and calculating staked liquidity throughout execution while computing earned AERO rewards per period. Discussed Analytics API with Yuriy - he will update starting block number to include events since gauge contract creation. Daily Bot update (v0.0.2): 15h runtime, APR 25.5%, cumulative profit -$0.173, no rebalancing needed (tick 1600).

---
2025-08-08 Fri: Continue working with aero rewards backtesting using Aerodrome Analytics API. Reviewed Aerodrome Analytics repo to check discrepancies with the output data. Will discuss with Yuriy about API usability for backtesting. Daily Bot update (v0.0.2): 12h runtime, APR 24.4%, cumulative profit $0.214, no rebalancing needed (tick 1600).

2025-08-07 Thu: Completed Panoptic deep dive analyzing smart contracts, automation infrastructure, and web interface. Confirmed rebalancing uses off-chain systems calling burnOptions→mintOptions plus LP adjustments, requiring multiple transactions per cycle and increasing gas costs significantly. Unable to create a position on the Panoptic website due to high collateral requirements. Started testing our strategy bot - after 6 hours delivered +$0.10 profit on $65 position, achieving 38% annualized APR. Performance breakdown: $0.039 LP fees and +$0.061 from short BTC hedge with zero rebalancing events. Implementing a workaround for staked liquidity calculation on the backtesting script using a monthly cache where the first backtest run generates complete historical snapshots, then subsequent runs use cached data plus gap events.

2025-08-06 Wed: Analyzed Panoptic approach compared with our strategy. Panoptic uses frequent delta-neutral micro-adjustments triggered by delta drift thresholds, incurring higher rebalancing costs. Our strategy employs event-driven rebalancing (price outside range) with less frequent but comprehensive position resets. Key difference: Panoptic's constant costly adjustments versus our controlled threshold-based rebalancing, allowing better cost management and IL optimization. Had issues configuring the LP Boot to run it locally, will address this in tomorrow's daily meeting. Finally, continued working on backtesting aerodrome rewards.

---
2025-07-30 to 2025-08-05: Paid time off

2025-07-29 Tue: Fixed events and position overlapping for total staked liquidity calculation. [Refactored Aerodrome position class](https://github.com/harmony-one/portfolio-manager/pull/36) to handle staked and unstaked positions. Working on orchestrating AERO rewards handling in the backtesting script.

2025-07-28 Mon: Implemented analytics client [integrating aerodrome-analytics API](https://github.com/harmony-one/portfolio-manager/pull/36) for gauge events (Deposit/Withdraw) and position tracking to calculate totalStakedLiquidity required for Gauge contract's AERO rewards calculation. Discovered critical issue: Events API and Positions API return different tokenId ranges with zero overlap, preventing proper backtesting calculations. Analytics client logic functions correctly but requires synchronized data from both endpoints. Tomorrow I will coordinate with Yuriy on API synchronization.

---
2025-07-26 Sat (5.0h): Current Aerodrome's Analytics service doesn't track stakedLiquidity, rewardGrowthGlobalX128 and lastUpdated values, also lacks date filters. Discussed with Yuriy and he will add these features next week, enabling use of analytics service for backtesting. In the meantime, working on alternative  solution to reconstruct historical totalStakedLiquidity values needed for AERO rewards formula using gauge Deposit/Withdraw events to track on-range staked NFT positions.

2025-07-25 Fri: Talked to Yuriy about his Aerodrome's Analytics service, conducting deep dive on implementation and endpoint services. Researched AERO reward logic and Gauge contracts, concluding best approach is replicating the earn Gauges contract method which calculates AERO rewards based on rewardRate (gauge contract) and totalStakedLiquidity (pool contract). Implemented method to retrieve historical rewardRate data, discovering weekly rates ranging from 0.084-0.145 AERO/sec.

2025-07-24 Thu: Added [price range changes](https://github.com/harmony-one/portfolio-manager/pull/33) to backtesting output showing new ranges after rebalancing. Added hedge_pnl_usd and waste_pct columns to backtesting log output (initially set to 0). Worked on AERO rewards tracking for Aerodrome backtesting script, testing both subgraph queries and direct contract event scanning. Implemented ethers-based event tracking capturing real ClaimRewards events. However, events show user-initiated claims rather than consistent reward distributions needed for backtesting. The blocker is accessing systematic AERO emission data rather than sporadic user claim events. Will discuss with Yuriy tomorrow.

2025-07-23 Wed: Fixed Strategy class's calculateTokensForPosition method by implementing protocol-specific token swapping logic, resolving incorrect token allocations and IL calculations. Achieved realistic IL values (-0.001% to -0.184%) and perfect value calculations. [Fixed dynamic positionType logic](https://github.com/harmony-one/portfolio-manager/pull/33) (10%, 20%, price range) during rebalancing, allowing strategy configuration parameters to modify rebalancing behaviors. Successfully implemented strategy achieving 24% net APR with dynamic position ranges (started 10%, progressed to 11%, finished at 16%) and 99.8% time-in-range efficiency. Reviewed Aaron's live multi-protocol strategy reports and will propose adding hedge_pnl_usd (perpetual trading profits/losses) and waste_pct (overtrading frequency) metrics to team meeting.

2025-07-22 Tue: Added Binance funding rates logic to backtesting script. Fixed price history issue that was incrementing the backtesting range and distorting output (yesterday's 38% APR was incorrect). Continued testing strategy-backtesting-script against basic rebalancing logic (out-of-range only). Strategy approach shows lower APR (28% vs 31%) but higher PnL (1402 vs 1052) compared to basic approach. Debugging unrealistic IL calculation amounts that are affecting performance metrics.
 
2025-07-21 Mon: Integrated [LP strategy class](https://github.com/harmony-one/portfolio-manager/pull/33) with existing Aerodrome backtesting system. Separated concerns where the strategy class handles decision-making (rebalancing triggers, volatility analysis, momentum/funding signals) and calculations (IL, position values, hold comparisons). In contrast, the position class focuses on execution and tracking (fee accumulation, APR calculations). The backtesting script orchestrates both components, utilizing strategy decisions for rebalancing and strategy calculations for metrics. Added new methods (getPositionData(), rebalanceFromStrategy()) to the Position class , and calculateHoldStrategyValue to the Strategy class for clean integration. A strategy-driven approach improved the APR from 30% to 38-40%, although IL calculations require debugging.

---
2025-07-18 Fri: Continued implementing [utility methods](https://github.com/harmony-one/portfolio-manager/pull/32) for LP Strategy, including token-agnostic approach (base token can be located on token0 or token1). Added Defilab methods to calculate token amounts from position parameters and implemented position value calculations with proper token ordering support.

2025-07-17 Thu: [Implemented utility methods](https://github.com/harmony-one/portfolio-manager/pull/32) for LP Strategy class. Key methods include calculateAsymmetricRange using volatility, skew, and range width factors for asymmetric position bounds, calculateExpectedFees with supporting liquidity value and hold time calculations, isOutOfRange for position validation, performCostBenefitAnalysis for rebalancing decisions, calculateGeometricCenter for range centers, and exact impermanent loss calculations using calculateTokensForPosition based on Defilab's tokensForStrategy logic. Initial testing showed calculateExpectedFees returning $12.6M for a $60k position due to multiplying annual APR by days instead of converting to daily rate, requiring discussion with Artem about whether to divide APR by 365 in the fee calculation.

2025-07-16 Wed: Completed protocol agnostic implementation for Position class, basing logic on token0/token1 instead of BTC/stablecoin, fixing token order issues. With this change, both Uniswap and Aerodrome backtesting are completed for basic rebalance logic with compounding fees. Exported [Uniswap backtesting results](https://github.com/fegloff/portfolio-manager/tree/uniswap-defilabs/exports/Uniswap). Found bug in Net gain vs hold calculation - calculateHoldStrategyValue() method was using currentBtcPrice instead of initialBtcPrice. Added dynamic price range logic allowing new positions to change price ranges after rebalancing.

2025-07-15 Tue: Reviewed and discussed Artem's LP rebalance strategy. Received feedback from Theo and Philipp on backtesting TSV export file - Philipp noted that the Net gain vs hold values appear incorrect, need to investigate discrepancies. Worked on refactoring position class to be protocol agnostic by standardizing on token0/token1 calculations regardless of protocol. The Defilabs liquidity unit implementation is based on token0 values (tick values, highs, lows), so eliminated protocol-specific logic in favor of consistent token0/token1 handling across all AMM protocols.

2025-07-14 Mon: Resolved tick calculation inconsistencies between Uniswap and Aerodrome protocols. Discovered core issue: DEXs store BTC prices in different token order (Uniswap: token1Price, Aerodrome: token0Price) which affects the position tick calculations. After testing 4 approaches, determined Uniswap requires "price inversion + sign flip" while Aerodrome needs "price inversion only" to match subgraph tick values. Current solution works functionally but investigating underlying mathematical reasoning behind protocol-specific transformations.

---
2025-07-12 Sat: (2.0h) Fixed APR calculation issues occurring after position rebalancing in Aerodrome backtesting script. [Exported](https://github.com/fegloff/portfolio-manager/tree/uniswap-defilabs/exports/aerodrome) new TSV reports for Aerodrome position. 

2025-07-11 Fri (ongoing): Working on adding liquidity unit logic to the Uniswap backtesting script, following Aerodrome implementation. Updated tsv export logic, adding btc price data, and data type info to each export column.

2025-07-10 Thu: Finished implementing the [unified TSV/console export utils](https://github.com/harmony-one/portfolio-manager/pull/26) for the different protocols on the strategy. The export utilities adhere to the [Uniform Output Table format](https://github.com/harmony-one/portfolio-manager/blob/main/src/docs/BacktestingOutputExample.md). The implementation is working flawlessly on the Aerodrome backtesting script. Exported [daily and hourly](https://github.com/fegloff/portfolio-manager/tree/aerodrome-defilabs/exports/aerodrome) backtesting data for the selected Aerodrome pool from May 1st to July 10th and added the APR indicator to the unified backtesting output. The Aerodrome service was also updated to handle both staked and [unstaked positions](https://github.com/harmony-one/portfolio-manager/pull/27).

2025-07-09 Wed: Implemented unified backtesting output format for Aerodrome LP positions. Created UnifiedOutputStatus interface with 18 standardized fields including portfolio value, PnL, returns, fees, drawdown metrics, and rebalancing tracking. Updated AerodromeSwapDecimalsPosition.currentStatus() method and export service with centralized calculation logic. Analyzed Aaron's lp-hedger repository for performance tracking capabilities, reviewing database persistence for trades, fees, and positions. Asked Aaron for current script data to see real performance of hedging strategies and evaluate TSV format adequacy for comparing options vs perpetuals, addressing Stephen's request for quantitative comparison data.

2025-07-08 Tue: Completed [Aerodrome backtesting script](https://github.com/harmony-one/portfolio-manager/pull/25) by fixing APR calculation issues and adding unified getAPR() method with compounding control. Fixed rebalancing detection logic and closing logic issues that incorrectly counted final bookkeeping as rebalances. Added TSV export functionality with AerodromeExportService creating timestamped files in exports/aerodrome/ folder. Implemented selective console output showing every 100th hour to reduce log noise while preserving complete data export.

2025-07-07 Mon: Refactored Aerodrome Position class and backtesting script to handle both daily and hourly pool data. Implemented granularity type as configurable parameter for position class and backtesting script. Encountered issues with APR calculations during refactoring - working to resolve calculation discrepancies.

---
2025-07-04 Fri: 2025-07-04 Fri: Refactored and tested [rebalancing logic](https://github.com/harmony-one/portfolio-manager/pull/22) of Aerodrome's Defilabs Position class. Started the migration from Pool's daily data to hourly data.

2025-07-03 Thu: Completed [Aerodrome LP backtesting fixes](https://github.com/harmony-one/portfolio-manager/pull/22), achieving proper concentration effects. Resolved liquidity calculation inconsistency showing 1000x difference between versions due to incorrect decimal assignments in liquidityForStrategy method. Fixed full-range liquidity calculation that was artificially inflated using TVL proportion method instead of mathematical approach. Achieved realistic concentration ratio of 36.4x higher liquidity for concentrated positions vs full-range, enabling accurate fee distribution modeling with mathematically consistent implementation.

2025-07-02 Wed: Added TVL and position exposure to backtesting daily logs, fixed tick range comparison issue for in-range position determination, and refactored backtesting script to improve testing input handling. Discovered decimal discrepancies altering APR calculations and identified need for full code review of token balance handling inconsistencies. Stared script debug. 

2025-07-01 Tue: Completed [full-range and custom price range implementation](https://github.com/harmony-one/portfolio-manager/pull/22) (tested with 5% and 10% positions) for Aerodrome backtesting. Fixed critical LP share calculation (was using USD percentage instead of liquidity units percentage - 12x correction factor), resolved tick calculation by correcting token decimal assignments, implemented Defilab's algorithms. Rebalancing logic pending for tomorrow. 

2025-06-30 Mon: Found a [Defilabs backtesting implementation](https://github.com/DefiLab-xyz/uniswap-v3-backtest/blob/main/backtest.mjs) for Uniswap V3 pools that uses [uniswap-v3-backtest package](https://www.npmjs.com/package/@0xelod/uniswap-v3-backtest). The key values feeGrowthGlobal0X128 and feeGrowthGlobal1X128 enable precise fee calculations without hardcoded concentration multipliers. Started researching and implementing Aerodrome backtesting using this methodology. The Aerodrome subgraph poolDayDatas query returns feeGrowthGlobal0X128 and feeGrowthGlobal1X128 values, allowing us to apply the same fee growth delta calculations directly to Aerodrome pools. This eliminates the need for empirical concentration multipliers and enables mathematically accurate backtesting using real blockchain fee accumulation data.

---

2025 Q2 Review (38 hours)

Development of [Beefy protocol](https://github.com/harmony-one/shadow-scraper/pull/6) portfolio tracker scripts

In Q2 2025, I developed DeFi analytics infrastructure for multi-protocol yield tracking and APR calculations across the Sonic ecosystem. I built and deployed the Pendle/Sonic subgraph with RedeemRewards event tracking and entity handlers for PT/YT reward discrimination. Tracking scripts were created for Aave, Beefy, Equilibria, Silo, and Magpie protocols, establishing APR calculation methodologies that matched UI displays. I implemented Balancer v2/v3 yield calculations for Beets tracker, integrating ERC4626RateProvider contracts to handle BEETS rewards and yield-bearing token appreciation.

I completed Uniswap V3 LP backtesting showing 36.18% APR over 1-year historical periods and refactored the Uniswap LP service to use contract calls, eliminating subgraph dependencies to enable mainnet to Sepolia support for backtesting scripts. Full price range backtesting was completed for Aerodrome protocol, achieving APR values close to the User Interface amounts. Cross-protocol backtesting capabilities were advanced by building integrated systems combining Aerodrome LP positions with Hyperliquid perpetual hedging strategies. I fixed funding calculation logic for SHORT positions, resolving negative APR issues where positive funding rates generate income for shorts in bullish markets, and implemented Aaron's BTC LP strategy with dynamic hedge sizing based on token ratio deviations.

Implemented Aaron's strategy on the [cross-protocol backtesting script](https://github.com/harmony-one/portfolio-manager/pull/15), adding token ratio monitoring that detects when LP deviates >5% from a 50/50 balance and signals hedge adjustments. HyperliquidPosition adjusts hedge size using deviation-based factors with 75% max hedge-to-LP ratio limits. Added weekly funding cost monitoring that logs when funding exceeds 20% of LP fees. After completing Aerodrome-to-Defilab refactoring for proper position fees distribution, will integrate the token ratio logic.

I maintained and enhanced 1Bot infrastructure by integrating Claude Opus 4 and Sonnet 4 models, updating OpenAI models with o3 and GPT-4.1 variants, and resolving deployment issues on fly.io servers. Database backup and cloning procedures were implemented to address server instability, adding retry cycles for DB and Telegram connections to prevent continuous restarts. Technical support was provided for user-reported issues including Luma command failures and Harmony Bot deployment troubleshooting.

---

2025-06-29 Sun: (6.0h) Researched and compared different concentration multiplier approaches for Uniswap V3 backtesting, concluding the best approach is to replaced theoretical concentration multiplier approach with [empirically-calibrated system](https://github.com/harmony-one/portfolio-manager/pull/20) for Uniswap V3 backtesting. Eliminated problematic square root formula and competition penalty factor in favor of direct calibrated multipliers. Fixed rebalancing logic, PnL calculcations, and LP Share percentage updates.

2025-06-27 Fri: Fixed Uniswap V3 backtesting issues with price range calculations and time-in-range logic. Previously, tick math created unit mismatch with subgraph BTC/USD prices, invalidating time-in-range calculations. Updated to calculate price ranges as percentage bands around actual daily BTC/USD prices, ensuring consistent units. Added time-in-range factor based on daily high/low prices so positions only earn fees for the fraction of the day they are in range. Implemented hardcoded concentration multipliers to avoid unrealistic APRs from theoretical models.

2025-06-26 Thu: Validated concentration multiplier approach with Artem for Uniswap backtesting position fee distribution. Added price range positioning and rebalancing logic to [Uniswap LP backtesting script](https://github.com/harmony-one/portfolio-manager/pull/18), including compounding APR calculations since rebalancing strategy closes positions, collects fees, and creates new ones. Backtesting now shows Net and weighted APR metrics. Started refactoring Aerodrome backtesting script using validated Uniswap logic.

2025-06-25 Wed: Integrated 10% price range positions into Uniswap LP backtesting script. Encountered blockers with liquidity unit conversions for realistic backtesting accuracy. Determined best approach uses concentration multiplier based on position type percentages rather than complex liquidity unit calculations - scheduled validation with Artem for following day.

2025-06-24 Tue: Implementing 10% price range position to Aerodrome back testing script targeting user interface's 62% APR. Successfully implemented position range calculations and time-in-range tracking. Currently debugging fee calculation discrepancy showing 0.14% APR vs expected 62% - identified issue with comparing USD investment amounts to protocol liquidity units.

2025-06-23 Mon: Paid time off

---
2025-06-20 Fri: [Fixed critical funding calculation logic](https://github.com/harmony-one/portfolio-manager/pull/15) for SHORT positions - positive funding rates generate income for shorts in bullish markets, resolving negative APR issues. Continued integrating Aaron's BTC LP strategy implementation with dynamic hedge sizing based on token ratio deviations (>5% from 50/50 triggers rebalancing). Added weekly funding cost monitoring with automatic position reduction when funding exceeds 20% of LP fees, following Aaron's risk management framework.

2025-06-19 Thu: Built cross-protocol backtesting script combining Aerodrome LP positions with Hyperliquid perpetual hedging. Created position classes (AerodromePosition.ts, HyperliquidPosition.ts) with clean state management and real data integration from subgraphs and protocol services. Encountered issues with negative APR calculations that required debugging funding rate logic for SHORT positions.

2025-06-18 Wed: Completed [Aerodrome backtest script](https://github.com/harmony-one/portfolio-manager/pull/14) for full price range position, achieving APR close to UI's 0.09% (0.17%). Started working on Aerodrome + Hyperliquid backtesting integration for cross-protocol strategy development.

2025-06-17 Tue: Pivoted to active tick approach after reviewing Aerodrome documentation, which states APR is calculated using liquidity within current price range (active tick) and surrounding ticks (+/-1 from current). Fixed APR calculation double-counting issue in calculatePositionFees function by eliminating multiplication of both LP share percentage and position category share. The fix was validated against a pure math test that calculated position share as (full-range liquidity / total active liquidity) * total pool fees, which correctly produced ~0.06% APR matching the UI. Final implementation uses only the position category share calculation to match this validated pure math approach.

2025-06-16 Mon: Realized fee distribution mechanics in Aerodrome concentrated liquidity pools - feesUSD are shared among overlapping position ranges rather than being independent per position, correcting Sunday's assumption about cumulative fees. Initially attempted complex competition model where each range type competed with overlapping ranges (full-range vs all, 30% vs 20%/10%, etc.), reducing APR calculations from 309% (treating as traditional AMM) to 0.248%, though still higher than UI's 0.06%.

---
2025-06-15 Sun: (2.0h) Continued investigating unrealistic APRs in backtesting script and discovered subgraph feesUSD represents cumulative fees rather than daily fees, explaining the 248% overestimation.

2025-06-13 Fri: Added [getPosition and getPositionByOwner methods](https://github.com/harmony-one/portfolio-manager/pull/13) to Aerodrome service with integration tests. Investigated unrealistic backtesting APRs (248%) and identified critical issues with price range dynamics. Understood that price ranges (±10% to full range) determine active liquidity exposure - if cbBTC moves outside range, position becomes 100% single-asset requiring rebalancing while affecting fee competition dynamics.

2025-06-12 Thu: Created [USDC/cbBTC position](https://aerodrome.finance/deposit?token0=0x833589fcd6edb6e08f4c7c32d4f71b54bda02913&token1=0xcbb7c0000ab88b473b1f5afd9ef808440eed33bf&type=2000&chain0=8453&chain1=8453&factory=0x5e7BB104d84c7CB9B682AaC2F3d509f5F406809A&position=16281809) on Aerodrome and resolved Artem's [PR comments](https://github.com/harmony-one/portfolio-manager/pull/10). Started integrating Aerodrome services into Portfolio Manager.

2025-06-11 Wed: Completed Aerodrome backtesting with contract validation comparing subgraph responses against actual contract data. Identified that subgraphs return feesUSD amounts (trading fees)  while contracts return AERO token amounts, where AERO rewards represents 39% of subgraph fee value . High APRs attributed to pool's young age (under 3 months) experiencing significant BTC price volatility. Fixed and improved [Uniswap LP get position method](https://github.com/harmony-one/portfolio-manager/pull/12).

2025-06-10 Tue: Built modularized Aerodrome LP backtesting system with subgraph client for GraphQL queries, contract client for on-chain data, and comprehensive test framework. Completed [backtest of cbBTC/USDC LP](https://github.com/harmony-one/portfolio-manager/pull/10) showing 319% annualized APR from fees alone. Worked on onchain position retrieval script to compare subgraph output with onchain data.

2025-06-09 Mon: Continued Aerodrome backtesting script development, reviewing pool and gauge contracts. Tested HyperSync data engine but found it overly complex for backtesting needs - requires processing individual transaction events and manual daily aggregation. Found Base Aerodrome subgraph on The Graph and switched to this approach, which provides pre-calculated daily metrics (volume, fees, TVL) through simple queries, avoiding the need to process thousands of raw blockchain events.

---
2025-06-06 Fri: Added Claude Opus 4 (/opus /o /otool, o.) and Sonnet 4 models (/sonnet /claude /s, s.) to 1Bot. Reviewed WBTC/USDC LP portfolio backtesting strategy showing 36.18% APR with 100% time-in-range over 1-year historical period, meeting all defined KPI targets. Backtest validates strategy logic and risk management framework for potential live implementation. Started Aerodrome cbBTC/USDC LP backtesting implementation, investigating data infrastructure options including Envio indexer. Key difference identified: Aerodrome uses AERO token emissions vs Uniswap's underlying token fees.

2025-06-05 Thu: Unified Uniswap V3 LP service to use direct contract calls for all networks, eliminating subgraph dependency to ensure integration tests match production logic exactly. Since Uniswap lacks Sepolia subgraph support, migrated all price and pool position retrieval to contract-based approach across Ethereum and other chains. [Implemented universal fetchPoolInfoDirect](https://github.com/harmony-one/portfolio-manager/pull/7/) function with consistent price calculations, resolved decimal precision issues for any token pairs. Established network-agnostic configuration management with all integration tests now executing identical production code paths.

2025-06-04 Wed: Developed test environment for uniswap-lp service methods targeting [USDC/ETH pool](https://app.uniswap.org/explore/pools/ethereum_sepolia/0x224Cc4e5b50036108C1d862442365054600c260C) on Sepolia testnet. Implemented direct contract calls for pool information and pricing due to lack of Sepolia subgraph availability, bypassing existing subgraph infrastructure. Resolved ConfigService dependency injection issues in test environment by migrating from NestJS ConfigService.get methods to direct configuration() function calls.

2025-06-03 Tue: [Corrected the pool price calculation logic](https://github.com/harmony-one/portfolio-manager/pull/4/) by fixing the token price interpretation from subgraph data, ensuring that exchange rates properly display "1 USDC = 0.00000940 WBTC" to match the Uniswap UI. Due to Uniswap V3's architecture using NFTs to represent each position, the pool price calculation requires the proper ratio between token0 and token1. Also created utility modules and subgraph client APIs for modularized architecture. Researched Sepolia testnet migration to eliminate ~$5 mainnet gas costs per test cycle.

2025-06-02 Mon: Improved integration test performance by resolving constant timeouts in writing transactions (token approvals, add liquidity, collect fees, remove liquidity). Fixed performance issues including parallel execution logic and decimal handling bugs (WBTC=8, USDC=6 decimals), making the service compatible with any pool address. Switched RPC from free Infura tier to [PublicNode](ethereum-rpc.publicnode.com) for better reliability (Next: migrate to testnet to avoid ~$5 gas costs per test cycle). Also, implemented position earned fees functionality for querying uncollected LP fees and developed a pool price method with subgraph integration, including comprehensive integration test logic.

---
2025-06-01 Sun: (4.5h) Implemented complete end-to-end integration tests for UniswapLpService with automated token approval logic, successfully demonstrating full LP lifecycle (add liquidity → remove liquidity → collect fees and tokens) using real Ethereum mainnet transactions. When successful, tests prove all core LP methods work correctly with live Uniswap contracts. Experiencing performance issues with addLiquidity tests timing out in most executions due to network congestion and transaction complexity (2 approvals + 1 mint). Implemented token approval optimization to pre-approve WBTC and USDC tokens to improve performance. Other optimizations tested included adaptive gas pricing at 120% of network rates and 3-minute timeouts, but reliability remains inconsistent across different network conditions.

2025-05-30 Fri: Fixed Uniswap V3 subgraph integration issues, delivering comprehensive [daily metrics](https://github.com/harmony-one/portfolio-manager/pull/1) including position value, impermanent loss, PnL, and APR calculations. Implemented Jest-based execution framework with custom logging for clean backtesting analysis. Built integration tests for UniswapLpService methods (addLiquidity, removeLiquidity, collectFees, getPosition), resolving STF errors by adding token approval logic. Tests validate correct contract interactions despite insufficient funds preventing full addLiquidity completion, confirming methods work with real blockchain calls.

2025-05-29 Thu: Completed Hyperliquid position tracker using REST API calls, supporting all SPOT positions with expected perpetual positions compatibility (not tested). Built Uniswap V3 LP backtesting script to simulate liquidity provision over configurable time periods, implementing subgraph queries for historical pool data and real market conditions.

2025-05-28 Wed: Worked on a [Hyperliquid position tracker script](https://github.com/fegloff/hyperliquid-tracker/blob/main/src/hyperliquidTracker.ts) for trade positions. The script needs to retrieve the position value at a given timestamp for backtesting purposes. Reviewed the Hyperliquid documentation and implemented the solution using their public API in TypeScript. Developed the core functionality, including fill processing, historical price retrieval, and position calculation. Created a test spot position in Hyperliquid for validation.
 
2025-05-27 Tue: Completed [swap fee APR calculation](https://github.com/harmony-one/shadow-scraper/pull/20) for Balancer v2 positions on Beets, implementing dual reward tracking where staked positions earn both BEETS tokens (primary) and swap fees (secondary). Updated [BTC/USD pool database](https://github.com/harmony-one/h/blob/main/docs/defi/btc-usd-pools.tsv) expanding coverage across multiple chains. Analyzed impermanent loss (IL) dynamics with BTC price movements, considering 80/20 vs 50/50 pool allocations for bull markets and AMM advantages during bear markets for accumulation strategies. Explored Hyperliquid's orderbook technology as IL-free alternative to traditional AMM rebalancing mechanisms. 
  
2025-05-26 Mon: Researched BTC/USD liquidity pools across different protocols on Sonic chain, compiling findings into [TSV format](https://github.com/harmony-one/h/blob/main/docs/defi/btc-usd-pools.tsv). Investigated Beets swap fee calculation methods, initially attempting onchain event queries but pivoted to subgraph exploration due to performance bottlenecks from excessive event filtering.

---
2025-05-23 Fri: Created position in [Beets scETH/scBTC/scUSD/stS Sonic Quartet Audition pool](https://beets.fi/pools/sonic/v2/0xbd4a2ecdcd7acb0d2b20744ac4cc1368dd8fdc410001000000000000000000a8) and [updated tracking script](https://github.com/harmony-one/shadow-scraper/pull/19) to handle new token integrations. Started exploring swap fee rewards on Beets for Balancer v2 positions, as current v3 positions only handle rewards through underlying yield-bearing tokens.

2025-05-22 Thu: Implemented [Balancer v3 yield calculation](https://github.com/harmony-one/shadow-scraper/pull/18/) for Beets tracker script by creating new subgraph queries for v3 schema and building normalized data structures for unified processing with existing v2 logic. Integrated ERC4626RateProvider contract calls to fetch current exchange rates showing yield-bearing token appreciation over time (e.g., rate of 1.0000003 indicating accumulated yield). Successfully tracking both positions: scBTC/LBTC Weighted Pool generating 2.74% APR via BEETS rewards, and Avalon Bitcoin Treble achieving 39.58% APR through yield-bearing token appreciation (high APR due to short time period - 0.29 days annualized).

2025-05-21 Wed: Fixed Balancer pool deposit value calculation discrepancies by identifying proportional splits follow pool composition ratios (scBTC 88.46% and LBTC 11.54%). Added [APR calculation for staked position](https://github.com/harmony-one/shadow-scraper/pull/16), adding onchain calls to the incentive gauge contract. The APR of Beets rewards for scBTC-LBTC position was 2.70% vs 2.53% according to the UI.

2025-05-20 Tue: Debugged unstake APR calculation showing inflated 585.754% vs UI's 2.73% for scBTC-LBTC position. The issue originated from BTC price volatility affecting BPT pricing (totalLiquidity/totalShares ratio), generating $1+ in reward on a $5.05 deposit after 4 days due to actual position gains exceeding $6 upon closure. Validated APR calculation logic was correct but discovered the UI displays pool-wide APR rather than individual position APR by examining frontend code. [Completed APR calculation](https://github.com/harmony-one/shadow-scraper/pull/16) implementation for unstaked positions.

2025-05-19 Mon: Exploredproper APR calculation methodology for Balancer liquidity positions on Sonic network. Reviewed Balancer contract structures and identified VaultExplorer.getBptRate() for BPT price retrieval, but found this contract unused in production. Discovered position valuation mechanics: while theoretical BPT price equals totalLiquidity/totalShares, actual position value derives from summing current USD values of underlying tokens (not BPT price × shares). Validated approach using scBTC/LBTC position data, calculating 2,533% APR over ~3.14 days, with results matching UI-displayed position value of $6.04. Now working on update the tracker script to include this logic

---
2025-05-18 Sun: (4.0) Implemented Balancer subgraph queries to retrieve Beets deposit and position data, uncovering key protocol mechanics: while LP token shares remain constant, underlying token balances in pools change over time as swap fees accumulate. Initial APR calculations comparing the amount variation of one of the deposit tokens showed significant deviation from Beets UI values. Will try calculating the APR using the BPT (Balancer Pool Token) price.

2025-05-16 Fri: Continued development of Beets Protocol integration, working with Balancer and Gauge subgraphs to retrieve pool configuration and stake position data.  Planning to continue integration progress on the weekend.

2025-05-15 Thu: Diagnosed Spectra Protocol RPC issues by comparing their website behavior with our tracking script — while the Spectra interface experienced RPC errors for wBTC positions, our script successfully retrieved APR data for USDC positions without connection problems. Advanced Beets Protocol integration research, focusing on their composable liquidity pool architecture.

2025-05-14 Wed: Completed support for [wbtc/shadow pools](https://github.com/harmony-one/shadow-scraper/pull/13) on Beefy protocol with improved value and amount handling for deposits and rewards across both Beefy and Equilibria implementations. Established wtbc-scbtc test position on Beefy to validate tracking functionality. Initiated integration of Beets protocol into the tracking system.

2025-05-13 Tue: Verified Silo scripts for PT-aUSDC (14 Aug) scUSD market. Depending on the deposit underlying token, the pool offers different APRs: for PT-aUSDC the APR is 0% (script doesn't work) and for scUSD the APR is 4.9% (tracking script works correctly). Reviewed [Rika's updated PR](https://github.com/harmony-one/shadow-scraper/pull/8) for Pendle LP and PT tracking. Created a position on [Beefy wbtc-usdc.e vault](https://app.beefy.com/vault/shadow-cow-sonic-wbtc-usdc.e-vault) and currently working on the tracking script to retrieve necessary information for APR calculations.

2025-05-12 Mon: Created and analyzed positions across Magpie, Silo, PendlePT, and PendleLP pools to validate script's APR tracking accuracy. Tested Rika's script for Pendle LP and PT position monitoring. Extended script coverage by implementing [multiple market support](https://github.com/harmony-one/shadow-scraper/pull/10) for both Equilibria and Beefy protocols. Resolved issue with Beefy API integration that was affecting data retrieval.

----
2025-05-09 Fri: Implemented [multiple vaults support](https://github.com/harmony-one/shadow-scraper/pull/9/) for Euler APR scripts. Refactored Euler subgraph to interact with Vault factory rather than individual vault addresses after identifying resource contract limitations. Enhanced getEulerInfo logic to handle multiple vault addresses efficiently.

2025-05-08 Thu: Continued vePendle research, creating scripts to fetch user vePendle balance, lock duration, and expiry information. Established new positions on Swapx and Euler protocols (Swapx's ICHI position showing 1.94% APR after few hours vs 1.64% displayed in UI). [Created PR](https://github.com/harmony-one/shadow-scraper/pull/7) to fix negative earnings and rewards value initialization in Euler protocol script.

2025-05-07 Wed: Supported Rika on Pendle reward tracking. Also, started researching vePendle boost effects through on-chain data analysis. Working on scripts to retrieve vePendle info from Pendle's contracts and examine cross-chain boost mechanisms (Pendles and vePendle are generated/locked in Ethereum mainnet, while LP are on Sonic chain). This approach should provide direct insight into actual boost effects through contract interactions.

2025-05-06 Tue: Still with limited capacity due to illness. Completed subgraph integration with Beefy tracker. Added dedicated Beefy subgraph module to centralize tracker subgraphs logic across protocols (Euler, Silo, Shadow). Submitted [PR](https://github.com/harmony-one/shadow-scraper/pull/6) for review and requested code review from Artem.

2025-05-05 Mon: Identified performance bottleneck in Beefy user deposit information retrieval process. Started implementing subgraph integration to significantly improve query speed and efficiency. Also, added USD price conversion for underlying tokens. Note: Working with limited capacity this week due to illness, but making progress on core functionality.

---
2025-05-03 Sat: (3.5h) Integrated [Price Per Full Share (PPFS) retrieval](https://github.com/harmony-one/shadow-scraper/pull/6) for deposit value calculation in Beefy script, along with both APR and APY calculations. The User Interface currently displays APY as the primary KPI (Key Performance Indicator). Will discuss with team on Monday whether to standardize on APR or APY for reporting purposes. Current implementation calculates all values in underlying tokens rather than USD - will implement price conversion functionality on Monday.

2025-05-02 Fri: Resolved PPFS retrieval issue after researching Beefy's repo - identified an alternative API endpoint for historical Price Per Full Share data. This enables comparison of mooToken prices at deposit time vs current price, essential for tracking actual user APR and APY. Currently implementing API logic in Beefy module within shadow-scraper repo. Will complete implementation over the weekend.

2025-05-01 Thu: Developed scripts to retrieve deposit info from Beefy pool and vault data from Beefy API. Encountering issues with historical Price Per Full Share (PPFS) retrieval at deposit time, which is critical for accurate APR calculations. The challenge stems from Beefy's autocompounding mechanics: users receive mooTokens that maintain constant quantity while their value increases (represented by PPFS). To calculate actual position APR, we need both deposit-time PPFS and current PPFS (we have this value) to determine value growth over time. Looking for different approaches to get the PPFS info on deposit time.

2025-04-30 Wed: Removed Database monitor connection from bot [starting script](https://github.com/harmony-one/HarmonyOneBot/pull/377) to reduce server overhead (keeping TypeORM managing the connection). Deployed updated starting script to 1Bot with latest changes (gpt-4.1 and o3 models, GPT prices and context updates). Created a position in Beefy protocol and initiated development of APR calculation script in the shadow-scrapper repo. 

2025-04-29 Tue: Discovered DB server instability while troubleshooting Harmony Bot deployment issues - one instance wasn't starting, causing database connection failures. Implemented DB backup, cloned the primary instance, and replaced the malfunctioning one. Fixed Harmony Bot depoyment script by adding retry cycles for DB and Telegram connections, preventing continuous server restarts. Monitoring deployment on dev environment before Wednesday's production release. Closed positions after one-month trial: borrow strategy (Vicuna/Stability) severely impacted by protocol exploit (from 23% APR to -12%), while collateral strategy (Euler) maintained positive but compressed profitability (supply APY: 33.64% → 8.34%, borrow APY: 18% → 8%). Discussed Beefy Protocol research with Artem, scheduled to begin Wednesday.

2025-04-28 Mon: Fixed [Equilibria protocol's retrieve deposit amount logic](https://github.com/harmony-one/shadow-scraper/pull/5) by identifying a constant conversion factor between eqbPENDLE-LPT tokens and UI display values. Multiple contract transfers during deposits were causing inconsistencies, with transaction logs showing minimal eqbPENDLE-LPT amounts instead of actual deposit values. After examining SmartConvertor.sol state-changing methods and analyzing several deposits, implemented a solution using the discovered conversion constant rather than relying on volatile Pendle price. Addressed PR feedback from Artem and continued troubleshooting Harmony Bot deployment issues on fly.io dev server.

----
2025-04-27 Sun: (3.0h) Submitted [PR implementing Equilibria's APR calculations scripts](https://github.com/harmony-one/shadow-scraper/pull/5) to shadow-scraper repo. The primary script calculates user wallet APR on Equilibria protocol. Encountered challenge retrieving accurate user deposit information requiring hardcoding of deposit amount due to transaction complexities: when users deposit into Equilibria, multiple token transfers occur across different contracts, creating discrepancies between on-chain transaction values and what's displayed in both Equilibria and Pendle trades UIs. Current APR for the Equilibria position is 2.70% based on 0.00090264 PENDLE tokens ($0.002960 at $3.28) earned over 4 days from a $10 deposit.

2025-04-25 Fri: Calculated daily [APR](https://github.com/harmony-one/h/blob/main/docs/defi/exports/2025-04-26T04-25-08_equilibria_apr_0x3F5EA5_0x707096.tsv) on Equilibria for PENDLE: 3.35% based on 0.000507 PENDLE tokens ($0.00183 at $3.62) earned over 2 days from a $10 deposit. Created [scripts to research on-chain reward mechanisms](https://github.com/harmony-one/pendle-sonic-rewards/pull/9) trying to discriminate between SY and Pendle rewards, but the exercise confirms that Pendle is the only reward token. The first script identifies reward pool addresses for a given market address and checks reward tokens (confirming that our market distributes only Pendle). The second script calculates user-earned rewards and APR, while the third retrieves user deposit transactions to Equilibria. Analysis of deposit transactions through the PendleBooster contract revealed that each LP token deposit triggers eight token transfers involving PENDLE and eqbPENDLE tokens. LP tokens move from user to Pendle Proxy while eqbPENDLE-LPT tokens are created and sent to Reward Pool. This confirms Equilibria documentation regarding their wrapping of LP tokens into eqb tokens for position tracking and vePENDLE usage for boosted rewards.

2025-04-24 Thu: Examining rewards on Equilibria - received first reward of 0.0003 Pendle ($0.001011 at $3.37 USD/Pendle) on 10 USD deposit, yielding 3.69% APR (matching UI's 3.7% display). Searching for on-chain information to differentiate between Pendle and SY rewards by locating BaseRewardPoolV2 contract address which contains methods for retrieving user/token reward data. For harmony1Bot, resolved [llama_index/chromadb](https://github.com/harmony-one/harmony-llm-api/pull/31) configuration errors resulting from package version updates triggered by OpenAI and Anthropic changes. These components handle PDF embeddings and URL processing capabilities for Harmony1Bot. Also, updated [OpenAI models](https://github.com/harmony-one/HarmonyOneBot/pull/376) version and prices, adding o3 (o3-2025-04-16) and 4.1 (gpt-4.1-2025-04-14) models. These changes have not been deployed on 1Bot, due to some deployment issues on 0Bot to test them first.

2025-04-23 Wed: Examined Equilibria's integration with Pendle's SY rewards. The [reward contract](https://sonicscan.org/address/0x2FA11DBcbF955467E6B6f81816B21250F8f3Ac30), from the aUSDC Pool, exclusively holds PENDLE tokens without underlying SY token transactions like aUSDC. Analyzed EPendleSY.sol contract that leverages BaseRewardPoolV2.sol for reward functions (like getReward() method). The _harvest() function in EPendleSY obtains rewards and converts them to PENDLE. While BaseRewardPoolV2 supports multiple reward tokens, on-chain data confirms this specific pool distributes exclusively in PENDLE, consistent with EPendleSY's implementation and other Pendle-staking options in the Equilibria app. Equilibria implements a 7-day streaming distribution mechanism to avoid users depositing before rewards distribution, claiming, and immediately withdrawing without providing sustained liquidity. This explains the APY gap between projected (13.74%) and current (3.6%), as new pools gradually ramp up distribution rates over 7 days until reaching the target APY. Opened a position on Equilibria from LP aUSDC on Pendle. On the Merkl protocol analysis, opened a new position with a new wallet, waiting for rewards over the seven-day period.


2025-04-22 Tue: Investigating Aave/Merit/Merkl rewards distribution on Sonic. Found significant discrepancy between advertised APR (7.23%) and actual returns. After analyzing two claims (0.586 aSonWS on April 16 and 0.249 aSonWS on April 22), calculated effective APR of 223% based on $0.428 USDC rewards from $10 aUSDC investment over 7 days. This gap results from DUTCH_AUCTION distribution mechanism - when participation is low, rewards distribute among fewer users, creating higher individual allocations. All rewards belong to opportunity ID [6966266823213568963](https://api.merkl.xyz/v4/opportunities/6966266823213568963) (with 0 APR and 0 TVL), spanning 11 campaigns total. Merit uses 7-day epochs for rewards calculation, with each campaign representing a 4-hour distribution window for position evaluation. Also, started research of SY rewards on Equilibria, checked documentation and [contracts](https://github.com/eqbtech/equilibria-contracts/tree/main) but encountered issues with entering the boost protocol when attempting to make a deposit.

2025-04-21 Mon: Continuing research on Aave Merit within the Sonic chain, retrieved and confirmed the Merkl [Distribution contract](https://github.com/AngleProtocol/merkl-contracts/blob/main/contracts/Distributor.sol) at Sonic: [0x3ef3d8ba38ebe18db133cec108f4d14ce00dd9ae](https://sonicscan.org//address/0x3Ef3D8bA38EBe18DB133cEc108f4D14CE00Dd9Ae#code). Users must actively claim rewards via the Merkl website since they aren't automatically distributed; the contract manages the Merkle root hash, claim records, and destination address without storing unclaimed user info. Developed a script to check daily user claims; however, while the dashboard indicates $0.12 is available for immediate claim, the API is not returning this data accurately, suggesting a potential synchronization issue. Ongoing efforts are focused on finding a workaround to resolve this discrepancy.

---
2025-04-18 Fri: Day off for Good Friday. (3.0h) Investigated Luma error reported by user - identified issue in client.generations.list() method which is used to calculate user's queue position and estimates waiting time. [Implemented workaround](https://github.com/harmony-one/harmony-llm-api/pull/31) by catching the error and returning randomized queue position between 1-3 to maintain functionality. Posted [issue on Luma GitHub repository](https://github.com/lumalabs/lumaai-python/issues/153) for upstream resolution.

2025-04-17 Thu: Day off for Holy Thursday. (1.0h) Responded to user-reported Luma command failure in 1BOT. After initial troubleshooting, temporarily disabled Luma command functionality while developing permanent solution for harmony-llm-api.

2025-04-16 Wed: 2025-04-16 Wed: Investigated Aave Merit program on Sonic revealing non-continuous reward distribution model - program creates short-lived 4-hour distribution windows that represent claiming periods rather than continuous reward accrual. Attempted to match displayed APY with real rewards ($0.27 for 10 USDC deposit), but encountered "PAST" status on all [reward opportunities](https://github.com/harmony-one/pendle-sonic-rewards/pull/8) with APR and TVL zeroed out. For Pendle LP Yield analysis, worked on calculating yield using market state storage but encountered challenges accessing accurate rate values via Gauge Controller contract. Successfully retrieved TVL information for Pendle/Sonic markets using [Python CLI solution](https://github.com/harmony-one/defi-protocol-tvl-tracker).

2025-04-15 Tue: Implemented script to retrieve [Pendle PT rewards](https://github.com/harmony-one/pendle-sonic-rewards/pull/7) calculation by extracting proportionate PT yield for liquidity providers. Solution leverages market's readState method to obtain current pool composition (totalPt and totalSy token amounts) after each contract interaction. Applied PT ratio (PT exposure in LP token) to direct PT yield to calculate exact PT yield component for LP positions, successfully matching UI's displayed values (~0.9%). Founded test wallet supply operation [transaction (tx)](https://sonicscan.org/tx/0xc74a28ff8b115696f6335e402c85f1db9dfd9dfd654bcd98433e4efa496b39a3), and enhanced Aave script with [TSV export functionality](https://github.com/harmony-one/pendle-sonic-rewards/pull/6). Tested Aave APR script with test wallet and [exported result](https://github.com/harmony-one/h/blob/main/docs/defi/exports/2025-04-16T00-38-53_aave_apr_0x5362dB_0x881E62.tsv) getting 0.18470 APR after 25 days.

2025-04-14 Mon: Researched Aave contract mechanics for accurate APR retrieval, focusing on their liquidity index implementation which dynamically adjusts interest rates based supply and demand in the protocol. Discovered Aave's clever balanceOf override that automatically updates user balances with accrued interest without gas expenditure - aTokens (like aSonUSDC) intrinsically represent principal plus accumulated yield. Developed [script to extract Aave APR](https://github.com/harmony-one/pendle-sonic-rewards/pull/6) for specific user wallets and market addresses. Began investigating Pendle PT yield calculation methodology for liquidity provision operations to complete our yield tracking system.

---
2025-04-13 Sun: (6.0h) Implementing APY component extraction tool for Pendle markets on Sonic chain that breaks down returns into PT Yield, Underlying Yield, and LP Yield. Script queries market contracts, Gauge Controller, and token data to produce TSV exports. Currently investigating discrepancies between calculated values and Pendle UI. Added [user LP balance tracking](https://github.com/harmony-one/pendle-sonic-rewards/pull/5) (actual LP tokens held) and active balance monitoring (effective balance for reward calculation including vePENDLE boost) with comprehensive data insights including boost factor analysis. Added UserLPPosition entity to subgraph with Transfer event handling for LP token movements.

2025-04-11 Fri: Expanded Pendle/Sonic subgraph with comprehensive YieldToken contract event tracking, [implementing handlers](https://github.com/harmony-one/pendle-sonic-rewards/pull/5) for YTSwap, YTRedemption, YTYieldClaim, and UserYTBalance events. Developed querying script to analyze and visualize YT reward distribution patterns across protocol participants.

2025-04-10 Thu: Continued PT wstkscUSD yield analysis by examining Pendle contract mechanics, identifying [lastLnImpliedRate as the key parameter driving PT price calculations](https://github.com/harmony-one/pendle-sonic-rewards/pull/4). Verified this rate updates dynamically with each swap/mint/burn transaction in the market. Applied zero-coupon bond pricing approach to understand PT token valuation, where PT price approximates 1/(1 + rate × timeToMaturity/365). Confirmed [market-derived rates (~8.5% APY) align with Pendle UI figures](https://github.com/harmony-one/h/blob/main/docs/defi/exports/2025-04-11T15-06-54_pt_rewards_0x6e4e95.tsv). Analyzed PT pricing behavior showing current values of 0.98-0.99 with 48 days remaining until May 25th maturity, consistent with expected convergence pattern.

2025-04-09 Wed: Met with Artem to analyze APR calculation for [PT wstkscUSD vault positions on Pendle](https://app.pendle.finance/trade/markets/0x6e4e95fab7db1f0524b4b0a05f0b9c96380b7dfa/swap?view=pt&chain=sonic&py=output). Created [script](https://github.com/fegloff/pendle-sonic-rewards/pull/2) distinguishing to fetch pending rewards using contract calls but requires manual deposit info input since subgraph lacks transaction history. Enhanced existing user wallet redeem rewards script with pagination to handle large datasets, TSV export functionality, and command-line parameter support.

2025-04-08 Tue: Implemented subgraph's pagination system for comprehensive data retrieval beyond 1000-row limit with TSV file export functionality via local storage. Integrated Coingecko API for real-time Pendle token price fetching to enable accurate APR calculations. Began SY rewards integration to expand yield analysis capabilities with Standard Yield information for complete protocol reward tracking.

2025-04-07 Mon: Expanded Pendle/Sonic subgraph capabilities with [GaugeController contract events tracking](https://github.com/harmony-one/pendle-sonic-rewards/pull/3), implementing MarketClaimReward and UpdateMarketReward event handlers. Enhanced market metadata retrieval logic for PT, YT and ST contract address resolution. Developed script for querying and displaying market claimed rewards.

___
2025-04-05 Sat: (5.0h) Refactoring entity naming conventions in Pendle/Sonic subgraph to resolve indexing issues. Fixing schema inconsistencies causing entity name conflicts that prevented proper event capture.

2025-04-04 Fri: Fixed Pendle rewards subgraph by refining entity schema design and removing fields causing initialization errors. [Implemented RedeemRewards event handling](https://github.com/harmony-one/pendle-sonic-rewards/pull/2) using index positions as identifiers for client-side resolution. Created get rewards by user address script to test rewards calculation. Successfully deployed subgraph to thegraph services. Resolved harmony1bot Anthropic service balance issue by creating new account, and new API key.

2025-04-03 Thu: Troubleshooting Pendle rewards subgraph indexing issues with PT/YT reward discrimination. Adjusted startBlock initially to accelerate indexing, then reverted to 7830430 (matching DefiLlama). Fixed entity handlers for RedeemRewards events but facing persistent capture challenges. Resolved schema discrepancies causing entity naming confusion in GraphQL API. Verified contract addresses and improved processing logic for PT/YT reward type distinction. Investigating why subgraph only indexes setOverriddenFees events despite proper configuration.

2025-04-02 Wed: Published pendle-sonic-rewards [subgraph](https://thegraph.com/studio/subgraph/pendle-sonic-rewards/playground) implementing [RedeemRewards event tracking functionality](https://github.com/harmony-one/pendle-sonic-rewards/pull/2). Deployed subgraph to production environment and initiated testing to validate data output structure and accuracy.

2025-04-01 Tue: Discussed protocols taks with Artem for Sonic ecosystem, deciding to maintain separate codebases while sharing ideas to enable cross-verification of results for improved accuracy. Met with Li to discuss new task - verifying reward calculations for [Aave aUSDC pool](https://www.pendle.magpiexyz.io/stake/0x3F5EA53d1160177445B1898afbB16da111182418) on Magpie. Began development of Sonic Pendle Rewards [subgraph](https://github.com/harmony-one/pendle-sonic-rewards).

---

2025 Q1 Review (24 hours)

In Q1 2025, I focused on working on DeFi analytics on Portfolio Rebalancing, 1Tick automatic rebalancing, and yield analysis; by developing a Python-based command-line DeFi-protocol-TVL-Tracker with a modular provider-protocol architecture, implementing integrations for Euler, SwapX, Shadow, Curve, Aave, and Beets protocols. I built the Sonic Yield Calculator app to analyze how 1tick automatic rebalancer works, implementing vfat.io functionality using the vfat.tools repository which implements a deposit logic on the Sonic chain. Additionally, I created a Portfolio Management prototype with rebalancing algorithms, using a patched Uniswap SDK and direct contract calls. I provided technical support for Ledger hardware wallet integration, identifying M1/Arm64 architecture compatibility issues.

I enhanced our AI infrastructure by integrating multiple models into Harmony1Bot, including Claude 3.7 Sonnet, DeepSeek, and OpenAI's o1. For the harmony-llm-api, I developed a payment system with ONE balance management and a deposit website built within Flask (not yet live). I configured a Harmony Agent using Eliza's framework with GitBook integration, Telegram client deployment, and created both a Harmony character and Harmonious character with a fun, optimistic tone. I conducted detailed yield analysis for multi-protocol strategies combining Aave, Pendle, and Magpie on the Soniclabs chain.

---

2025-03-31 Mon: Completed Pendle reward handling analysis with detailed technical [documentation](https://github.com/harmony-one/h/blob/main/docs/defi/pendle_contract_analysis.md). Examining Pendle's DefiLlama adapters logic, discovering their reliance on MarketFactory events for market information retrieval and TVL calculation mechanisms. Analyzed Pendle event structures for subgraph custom implementation to efficiently index and retrieve rewards information.​​​​​​​​​​​​​​​​

---
2025-03-28 Fri: Exploring Vicuna, Euler and Pendle protocols for comprehensive Borrow/Collateral yield analysis. Discovered DefiLlama lacks support for Sonic chain implementations of Pendle and Euler protocols, requiring alternative data sources. Advanced Pendle protocol reward logic documentation. Initiated subgraph development research for Pendle Protocol on Sonic chain.

2025-03-27 Thu: Analyzing Pendle protocol's reward system through protocol documentation, contract code, and on-chain transactions. Confirmed reward information is stored on-chain via PendleGauge contracts linked to specific markets. Executed and documented test transactions for [borrow](https://github.com/harmony-one/h/blob/main/docs/defi/Borrow%20Collateral%20Yield%20Analysis%20-%20Strategy%201%20(Borrow).tsv) (Vicuna Protocol) and [collateral](https://github.com/harmony-one/h/blob/main/docs/defi/Borrow%20Collateral%20Yield%20Analysis%20-%20Strategy%202%20(Collateral).tsv) yield strategy (Pendle/Euler), capturing performance metrics and transaction flows. Continuing investigation to definitively determine if reward calculation system is fully on-chain.

2025-03-26 Wed: Analyzing Pendle reward system architecture. Identified on-chain reward mechanism through RewardManager and PendleGauge contracts. Found rewards likely use index-based distribution system allocating rewards proportionally based on stake percentage. Need PendleGauge.sol contract address for target market to analyze live transactions and validate findings. Planning 10 USDC.e test position to observe actual reward calculations before confirming complete on-chain implementation. 

2025-03-25 Tue: Analyzing Pendle's smart contract architecture through PendleRouterV4 proxy pattern. Examined Sonic chain transaction and reviewed addLiquidityDualTokenAndPt implementation code to understand token conversion flows. Investigating whether Pendle rewards utilize on-chain or off-chain calculation mechanisms. Analyzed DeFi test requirements for recursive borrowing and Pendle-Euler leverage strategies. Identified specific APYs, leverage ratios, and token details for crafting detailed inquiry addressing testing parameters, budget requirements, and discrepancies between expected rates and actual market conditions on Sonic network. Fixed issue in dalle command for 1Bot to restore image generation functionality.

2025-03-24 Mon: Executed and analyzed complete Aave+Pendle+Magpie yield strategy using my wallet. Performed each step: deposited 17 USDC.e to Aave (0.24%/8.416% yield), minted PT+YT tokens (10.19% yield), created Pendle LP position with additional 64.48 USDC.e liquidity (9.992% yield), and staked LP tokens on Magpie (14.38% yield). Verified APR calculation methodology in Sonic Yield calculator app. Drafted Q1 2025 review summarizing achievements across DeFi analytics, portfolio rebalancing, and AI infrastructure projects.

---
2025-03-23 Sun: (3.0h) Integrated GraphExplorer provider for SwapX protocol. Examined available [subgraph](https://thegraph.com/explorer/subgraphs/Gw1DrPbd1pBNorCWEfyb9i8txJ962qYqqPtuyX6iEH8u) but found it lacks essential TVL query endpoints. Subgraph contains basic vault data and transaction history but missing direct TVL metrics or complete token information required for accurate calculations. 

2025-03-22 Sat: (1.0h) Implemented [Euler protocol integration](https://github.com/harmony-one/defi-protocol-tvl-tracker/pull/2) to the DeFi-protocol-TVL-Tracker. 

2025-03-21 Fri: Sick day-off

2025-03-20 Thu: Got the flu today, limiting work time. Researched Pendle v2 API and analyzed PTaUSDC/USDC pool assets, extracting underlyingApy, impliedApy, and swapFeeApy metrics for more accurate yield estimation. Discovered pool expiration date (August 14, 2025), adjusting investment timeline to 5 months. Updated [report](https://github.com/harmony-one/h/blob/main/docs/sonic_aave_pendle_analysis.md) and created a standalone yield [summary table](https://github.com/harmony-one/h/blob/main/docs/fegloff-attachments.md) showing complete breakdown of all steps (YT tokens, PT in LP, PT held, Magpie staking) with revised rates totaling 21.35%+ APY and projected $963,056+ return over the 5-month period.

2025-03-19 Wed: Completed [detailed yield analysis](https://github.com/harmony-one/h/blob/main/docs/sonic_aave_pendle_analysis.md) for wallet 0x881e625e5c30973b47cee3a0f3ef456012f13f7d using Aave subgraph and Sonic explorer, tracking multi-protocol strategy combining Aave, Pendle, and Magpie. Calculated corrected total APY of 13.75% on $10M investment ($1.38M annually). Strategy breakdown: YT tokens earning 4.92% on $10M, PT tokens in LP earning 10.94% on $4.89M (via trading fees + incentives), and remaining PT tokens earning 6.82% on $5.11M. Magpie staking rewards analysis still pending completion.

2025-03-18 Tue: Synced with Theo and Rika on current initiatives and coordinated with Artem regarding protocol subgraph requirements. Expanded CLI app with Pendle protocol integration using DefiLlama API and implemented Shadow protocol with [Kingdom Subgraph provider](https://github.com/harmony-one/defi-protocol-tvl-tracker/pull/2). Refactored formatter to handle data output factoring to each provider, due to different data availability and added sorting functionality on TVL data.

2025-03-17 Mon: Discovered and implemented [DefiLlama pool endpoint](https://github.com/harmony-one/defi-protocol-tvl-tracker/pull/1) for retrieving granular TVL data. Refactored DefiLlama provider with local storage caching to optimize API consumption. Expanded protocol coverage by adding Curve, Aave and Beets implementations. Enhanced CLI functionality for improved data querying capabilities. Added [Readme](https://github.com/harmony-one/defi-protocol-tvl-tracker/blob/main/README.md) file

---
2025-03-16 Sun: (5.0h) Evaluated DefiLlama API for DeFi TVL tracker and determined it primarily provides chain/protocol-level data without the required pool-specific metrics needed for our use case. Established modular [project architecture with provider-protocol pattern](https://github.com/harmony-one/defi-protocol-tvl-tracker/pull/1), implemented CLI interface, and initialized Silo protocol integration. Exploring alternative approaches using subgraphs and web scraping to extract granular pool market data

2025-03-14 Fri: Extended CL pool deposit logic with wallet integration and token support (S and USDC.e). Resolved [price retrieval issues](https://github.com/harmony-one/sonic-yield-calculator/pull/1) for current, minimum, and maximum values. Continuing to debug mint transaction completion errors.

2025-03-13 Thu: Testing depositApi implementation while resolving implementation errors, troubleshooting excessive gas estimation issue in mint transaction. Enhanced error handling throughout depositApi module.
 
2025-03-12 Wed: Complete [deposit logic implementation](https://github.com/harmony-one/sonic-yield-calculator/pull/1) with new depositApi module that interfaces with NFT Manager Shadow contract (to create a liquidity position with a specific price range, represented as an NFT) and NFT Farm Strategy (to stake the position, enabling auto-rebalancing and configuring reward preferences using the SHADOW token).

2025-03-11 Tue: Developing deposit feature for Sonic Yield Calculator app. Improving pool retrieval logic to enhance CL (Concentrated Liquidity) data extraction ([here](https://github.com/harmony-one/h/blob/main/docs/fegloff-attachments.md#2025-03-11) current app look and feel).

2025-03-10 Mon: Deployed 1Bot with Claude 3.7 Sonnet model integration and implemented both free and paid versions of DeepEeek. After examining FarmStrategy and Automation contracts in vfat.tools repo, gained crucial insights into their pool handling methods, enabling [dynamic CL pool retrieval with detailed display](https://github.com/harmony-one/h/blob/main/docs/fegloff-attachments.md#2025-03-10) similar to vfat.io. Next steps include resolving loading latency issues and implementing position purchasing to analyze 1Tick rebalancing failures.

---
2025-03-09 Sun: (2.0h) Analyzing vfat.tools codebase to understand implementation patterns for automatic rebalancing functionality. Searching for contract interactions with Automation.sol and FarmStrategy contracts due to restricted access to vfat.io private repository.

2025-03-08 Sat: (5.0h) Extended analysis of VFAT's auto-rebalancing system by investigating [Automation.sol](https://github.com/vfat-io/sickle-public/blob/main/contracts/Automation.sol) contract's relationship with FarmStrategy.sol. Discovered Automation.sol functions as orchestration layer with security boundaries for "automator" addresses. Contracts interact through IAutomation interface allowing flexible architecture - Automation.sol handles batch processing with multicall patterns for gas efficiency while FarmStrategy.sol contains actual rebalancing logic. Updated 1Bot with Claude 3.7 Sonnet integration and resolved dependency conflicts.

2025-03-07 Fri: Conducted detailed analysis of [vfat auto-rebalancing mechanism](https://github.com/harmony-one/h/blob/main/docs/fegloff-attachments.md#2025-03-07) for concentrated liquidity positions, specifically examining failure cases in 1-tick ranges (CL50). Examined [FarmStrategy.sol](https://github.com/vfat-io/sickle-public/blob/main/contracts/strategies/FarmStrategy.sol) contract to understand rebalancing implementation in Sonic ecosystem. Identified that rebalancing executes through _compound function with sequential operations: claiming rewards, charging fees, swapping tokens to adjust ratios, depositing into updated price boundary positions, and returning remaining tokens. For CL50 positions (single-tick liquidity concentration for maximum capital efficiency), failure likely stems from high rebalancing frequency requirements during market volatility, causing prohibitive gas costs due to multiple sequential contract interactions required for each rebalance operation.


2025-03-06 Thu: Updated [sonic-yield-calculator](https://github.com/harmony-one/h/blob/main/docs/sonic-yield-calculator.md) app adding an API/Hooks solution for fetching pool data from Sonic pools providers (Equalizer and Shadow). Implemented workaround for contract discovery using known pool/gauge address pairs instead of dynamic discovery. Delivered clean grid-styled interface displaying standardized pool data with TVL, APR calculations and token information.

2025-03-05 Wed: Replicating Uniswap interface logic on the portfolio management prototype. Modified providers definition and Uniswap route handling but still encountering undefined address error. Created vfat project with [basic grid layout](https://github.com/harmony-one/h/blob/main/docs/sonic-yield-calculator.md) and implemented vfat contract calls.

2025-03-04 Tue: Cleansed portfolio management app code and [created PR](https://github.com/harmony-one/portfolio-management-prototype/pull/2) with three swap implementation approaches: Uniswap SDK integration, direct Uniswap contract calls, and SushiSwap contract implementation. Researched vfat.tools implementation following boss's request, planning to build minimal [spreadsheet-like](https://claude.ai/chat/849bac17-af96-43cf-8340-3aa24e10ff76) interface for Sonic blockchain yield farming data displaying pool names, TVL, APR and weekly rewards from Equalizer and Shadow protocols. Users will calculate potential earnings by inputting token amounts against current rates, leveraging existing contract calls from vfat.tools. Future enhancement could include wallet connection for executing staking transactions and claiming rewards directly.

2025-03-03 Mon: Expanded swap implementation approaches while continuing SDK integration efforts. Built direct swap component using hardcoded parameters to bypass complex routing. Implemented SushiSwap integration with custom calldata construction for token exchanges. Addressing MetaMask gas estimation failures and JSON-RPC errors encountered during transaction execution. Cleansing code after testing multiple alternatives to request Aaron's assistance with troubleshooting errors.

---
2025-03-02 Sun: (4.0h) Worked on troubleshooting Uniswap SDK integration on Harmony network. Developed simplified route generation approach with enhanced debugging to isolate specific failure points. Continuing to address persistent invalid address errors despite comprehensive patch application.

2025-03-01 Sat: (4.0h) Performed detailed patch analysis between [harmony-portfolio](https://github.com/harmony-one/harmony-portfolio) repo and current implementation. Identified and applied missing Harmony network configuration patches. Despite comprehensive patching, continuing to encounter invalid address errors during factory contract resolution.

2025-02-28 Fri: Refactored implementation to utilize Uniswap SDK with Token and NativeCurrency classes. Experimented with various AlphaRouter configurations and explicit Protocol V3 parameters. Identified critical issue with invalid factory address errors—SDK attempting to resolve incorrect factory contract on Harmony chain.

2025-02-27 Thu: Attempted direct contract interaction with Universal Router (0xdAa5Bf7004e33789ce13A2bBE620953B55608B8b) using [ABI](https://github.com/harmony-one/harmony-portfolio/blob/main/src/abi/router.json). Encountered gas estimation failures with "transaction would have cost extra fees" errors. Debugging router execution path to identify parameters causing the transaction rejection.

2025-02-26 Wed: Troubleshooting integration issues with Harmony's universal router contract for swap execution. Encountering difficulties handling native ONE token transactions during swap operations. Attempted implementation of Uniswap SDK with patches from swap/interface fork repository without success. Developing custom patches to resolve compatibility issues.

2025-02-25 Tue: Implemented swap execution logic for Portfolio Management prototype. Simplified routing approach by leveraging existing rebalancing algorithm after encountering route generation issues. Debugging gas estimation errors related to swap amount calculation logic.

2025-02-24 Mon: Enhanced Portfolio Management UX by streamlining rebalancing workflow. [Integrated Coingecko API](https://github.com/harmony-one/portfolio-management-prototype/pull/1) for real-time token pricing. Refactored UI components for improved clarity and deployed [latest build to fly.io](https://portfolio-rebalancer.fly.dev/). Continued development of swap integration logic.

---
2025-02-21 Fri: Analyzing swap implementation logic from swap.one and harmony-portfolio repositories for integration into Portfolio Management prototype. Deployed DeepSeek r1 paid model to 1Bot, encountering equivalent latency issues as observed with the free tier model. 

2025-02-20 Thu: Resolved fly.io deployment issues for Portfolio Management prototype. Integrated token list from [harmony-one/swap-token-list repo](https://github.com/harmony-one/swap-token-list) filtering for supported assets (ONE, 1WBTC, 1USDT). Enhanced UI to demonstrate rebalancing algorithm through mock rebalancing and swap operations.

2025-02-19: Working on the [Portfolio Management prototype](https://github.com/harmony-one/portfolio-management-prototype/pull/1), integrating RPC calls to fetch supported ERC-20 token balances from user wallet address. Implemented and tested rebalancing algorithm with mock swap calls prior to swap integration. Resolving deployment configurations on fly.io platform.

2025-02-18: Built portfolio management interface with NextJS, implementing view components and custom hooks for asset display. Set up data layer with mock API endpoints for portfolio grid integration.

2025-02-17 Mon: Designed architecture for portfolio rebalancer prototype after scope discussion with Li. Started development of asset allocation grid.

---
2025-02-14 Fri: Developed [deposit website for harmony-llm-api](https://github.com/harmony-one/harmony-llm-api/pull/30) within Flask framework. Pending fixes on deposit-web endpoint integration.

2025-02-13 Thu: Developing payment integration with ONE balance management for harmony-llm-api models access. Started client website for users to add ONE balance.

2025-02-12 Wed: Fixed image generation in 1Bot after vision model discontinuation - all models now include vision features. Deployed DeepSeek model to harmony-llm-api dev and 0Bot for testing. Requests successful despite high latency due to DeepSeek API streaming issues.

2025-02-11 Tue: Integrated harmony-llm backend with [OpenRouter](https://openrouter.ai/) using deepseek-chat:free model for testing as DeepSeek API issues persist. Higher latency observed compared to other models due to free tier limitations. Resolved streaming on [llm-backend](https://github.com/harmony-one/harmony-llm-api/pull/29) and [1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/376). Deployment to fly.io blocked by dependency conflicts after packages upgrade.

2025-02-10 Mon: Implemented stream completion and usage metrics for [DeepSeek model](https://github.com/harmony-one/harmony-llm-api/pull/29). Completed DeepSeek integration between [llm-backend](https://harmony-llm-api-dev.fly.dev/) and [1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/376). Still need funding to enable /sd command.

---
2025-02-07 Fri: Integrated DeepSeek with 1Bot using GPT-3.5-turbo as fallback during payment issues with Deep Seek Platform. Tested Ledger Wallet integration with new configurations from [PR #719](https://github.com/harmony-one/staking-dashboard/issues/719#issuecomment-2645898448) - still blocked by M1 compatibility issues.

2025-02-06 Thu: Resolved Harmony LLM dependencies (openai, anthropic, httpx) but encountered _Insufficient Balance_ error from DeepSeek API. WalletConnect [PR testing](https://github.com/harmony-one/staking-dashboard/issues/719#issuecomment-2641012018) blocked by build errors due to viem/wagmi packages using optional chaining - incompatible with current webpack/babel config.

2025-02-05 Wed: Tested Devin's PR and suggested adding [openssl legacy provider](https://github.com/polymorpher/staking-dashboard/pull/2) to node options env var for M1 compatibility on Devin's PR. Obtained DeepSeek API KEY. The LLM backend integration revealed dependency conflicts from openai package update.

2025-02-04 Tue: Resolved plugin config for [Harmony's deployment integration](https://github.com/harmony-one/eliza-harmony/pull/3). Plugin triggers on contract deployment requests but encountering issues with Telegram client sync. Supporting team with Ledger wallet integration. DeepSeek platform remains inaccessible for API credentials.

2025-02-03 Mon: Advanced Harmony's deployment plugin, patching Client app conflicts affecting agent builds. Supporting Ledger hw wallet integration for Staking dApp - identified M1/Arm64 architecture compatibility [issues](https://github.com/harmony-one/staking-dashboard/issues/717). DeepSeek platform remains down, blocking API access. 

---
2025-01-31 Fri: Implemented and deployed o3-mini model with /r command and r. shortcut for 1Bot. Updated context tokens and pricing for OpenAI models. Troubleshooting monorepo config for [Harmony testnet deployment plugin](https://github.com/harmony-one/eliza-harmony/pull/3) for Eliza's framework. Pending Deep Seek API KEY for 1Bot completion.

2025-01-30 Thu: Advanced Harmony testnet deployment plugin development. Implemented [Deep Seek model](https://github.com/harmony-one/harmony-llm-api/pull/29) integration for 1Bot - blocked by API KEY availability.

2025-01-29 Wed: Added response examples and style directives to [Harmonious configuration](https://github.com/harmony-one/eliza-harmony-agent/pull/2). Started testnet deployment plugin for Eliza's framework.

2025-01-28 Tue: Resolved flyio memory allocation issues and integrated [Twitter client](https://github.com/harmony-one/eliza-harmony-agent/pull/2) with Harmony's Eliza Agent. Advanced research on conversational agent creation within Eliza's framework.

2025-01-27 Mon: Deployed [Eliza Harmony Agent](https://github.com/harmony-one/eliza-harmony-agent/pull/2) with GitBook integration and Telegram client on flyio, scaling instance to 2GB RAM. Researching conversational agent creation using Eliza's framwork.

---
2025-01-24 Fri: 2025-01-24 (Fri): Configured pgvector extension on a dedicated Postgres instance via flyio for Eliza's agent requirements. Added comprehensive [deployment docs](https://github.com/harmony-one/eliza-harmony-agent/pull/2).

2025-01-23 Thu: Enhanced the [Eliza Web3 features document](https://github.com/harmony-one/h/blob/main/docs/eliza-web3-plugin-ecosystem.md) by adding precise URL references and refining plugin classifications. Encountered challenges with Docker configurations during the deployment of Eliza's Agent on Fly.io.

2025-01-22 Wed: [Introduced Harmonious](https://github.com/harmony-one/eliza-harmony-agent/pull/1), a character with a fun, optimistic, and harmonious tone, to Eliza's Harmony Agent. Analyzed the Eliza framework repository to identify blockchain plugins and compiled a comprehensive [feature list](https://github.com/harmony-one/h/blob/main/docs/eliza-web3-plugin-ecosystem.md). Made progress on deploying Harmony's Eliza Agent on Fly.io.
 
2025-01-21 Tue: Added custom GitBook plugin implementation to [harmony-eliza-agent](https://github.com/harmony-one/eliza-harmony-agent/pull/1) and tested with Harmony's Eliza Bot. Configuring fly.io deployment for internal testing. Fixing 1Bot /send command functionality.

2025-01-20 Mon: Troubleshooting 1Bot wallet-connect issue affecting external balance transfers based on user support request. Enhanced our GitBook plugin response handling - implemented [auto-retry](https://github.com/harmony-one/eliza-harmony/pull/1) with suggested follow-up queries to improve AI response quality when initial user inquiry lacks clarity.

---
2025-01-17 Fri: Resolved runtime agent creation issues and implemented endpoints for [agent listing and creation](https://github.com/harmony-one/eliza-harmony/pull/1). Set up GitBook configuration in harmony-eliza repo - plugin integration successful but content retrieval pending.

2025-01-16 Thu: GitBook plugin not available as npm package, preventing direct import to harmony-eliza-agent fork. Testing plugin functionality in harmony-eliza main repo before creating our custom implementation.
And for continuity, here's January 17th again:

2024-01-15 Wed: Migrating Harmony agent to Eliza's starter project architecture. Exploring GitBook plugin potential for the Harmony agent documentation. Working on fixing client-direct module endpoints for agent creation.

2025-01-14 Tue: Deep diving into Eliza's core architecture, noting its plugin ecosystem that extends to SOL, NEAR, TON, AVAX, BNB, and Lens Protocol. Testing character creation mechanics using Harmony chain with Telegram bot integration. Worked on an agent creation user-friendly feature.

2025-01-13 Mon: Started researching Eliza's AI agent and configured the local environment. Worked on creating a Harmony character and integrated Eliza with a Telegram Bot.

---
**2024 Q4 Review** 

In Q4 2024, I developed a proprietary array-based bonding curve contract to address licensing constraints with Mint Club's contracts. The implementation included price calculation and token management functionality, with constructor-initialized stages and standardized curve stages across tokens. I built a Next.js client application with token listing, purchasing, and price calculation features. This work was initially planned for integration with 1.country for domain-based token creation and was later contributed to the pump.fun project.

I enhanced Harmony1Bot by integrating multiple AI models including xAI's Grok, Gemini 1.5, Claude 3.5 Sonnet, and OpenAI's o1, while optimizing their command structures for better user interaction. I implemented a sliding window mechanism for infinite chat context and a session-based cleanup system. The bot's reliability improved through Sentry integration across all environments and telegram error notifications. I also developed a video processing system with semantic search and clip generation capabilities, evolving from MoviePy to an FFmpeg-based approach with subtitle handling features. Currently, I'm extending the harmony-llm-api with a JWT-based payment system for general-purpose usage, implementing prepaid user functionality with balance checks and model cost logic.

---
2025 Goals:

I will develop a Retrieval-Augmented Generation (RAG) system for Harmony to provide our community with real-time, accurate information and development resources. By leveraging established LLM models with our continuously updated knowledge base, I'll create a tool that helps users stay current with Harmony's latest features while providing developers with precise technical guidance for building new applications.

Building on this foundation, I will develop autonomous social agents based on Elon Musk's Grok and Jensen Huang's AI assistants that operate on X and Telegram, leveraging RAG-enhanced AI to generate engaging content and maintain meaningful interactions. The agents will be customizable for different purposes while supporting web3 transactions.

We can combine 1.country with AI-powered meme generation to create cultural content hubs. The idea is for domain owners to generate and curate memes related to their domains, using AI to help with creation and analysis. These memes could then be traded on pump.fun, our existing marketplace, potentially adding value to both the domains and the meme ecosystem in the web3 space.

---
2024-12-20 Fri (ongoing): Split smart contract architecture into basic deposit handler (which will be used by harmony-llm-api) and extended operator-enabled variant with balance management and multi-service integration.

2024-12-19 Thu: Restructured harmony-llm-api with dedicated blockchain module for web3 interactions, segregating smart contracts and backend components. Developing deposit endpoint integration logic.

2024-12-18 Wed: Developed [smart contract architecture](https://github.com/harmony-one/harmony-llm-api/pull/28) for Harmony LLM API deposits with gas-optimized design - storing only user deposit states, operator registry, and owner withdrawal functions, eliminating tx history to minimize chain opertaions.

2024-12-17 Tue: Enhanced cost calculation in balance_check decorator with harmony1bot-compatible payment units, optimized LlmManager class estimation methods. Advanced Harmony LLM API smart contract development.

2024-12-16 Mon: Implemented balance_check decorator for request cost estimation. Extended postgres DB model and resolved migration issues.

---
2024-12-13 Fri: Fixed JWT secret key configuration, enhanced logging across test/local envs, and resolved postgres DB deployment issues in fly.io pipelines. Fixed collection request errors in harmony-llm-api prod environment. 

2024-12-12 Thu: Fixed JWT and token auth decorator logic in harmony-llm-api. Restructured test module into separate scripts for auth flows and API call validations.  

2024-12-11 Wed: Progressing on harmony-llm-api payment system implementation, debugging route configurations, decorator interactions, and resolving library dependency issues. 

2024-12-10 Tue: Integrated [Sentry](https://github.com/harmony-one/HarmonyOneBot/pull/374) across all 1Bot environments and deployed to production. Progressing on payment system in harmony-llm-api, implementing balance checks and model cost logic.

2024-12-09 Mon: Extended video transcript CLI with font size parameter. Checked 1Bot stat command KPI error, and prompt with URL error. Need to configure Sentry.  

---
2024-12-06 Fri: Added [DALL-E endpoint to OpenAI namespace](https://github.com/harmony-one/harmony-llm-api/pull/27). Implemented auth middleware decorators (require_any_auth, require_jwt, require_token) with full test coverage.

2024-12-05 Thu: Completed database design and model implementation for harmony-api-llm, resolving migration issues. Advanced fly.io deployment configuration, pending final testing.

2024-12-04 Wed: Configured prepaid user database structure in harmony-llm-api. Validated token-based and JWT auth on fly.io dev environment. Finalized video transcript demo with optimized subtitle processing.

2024-12-03 Tue: Completed [video transcript demo](https://github.com/harmony-one/transcript-word-timestamp-demo/pull/8) with optimized subtitle handling: migrated from MoviePy per-word to FFmpeg approach using window-size text blocks, eliminating word spacing issues and subtitle flicker. Enhanced logging with ASCII text preservation and terminal escape removal. Extended CLI with SRT input support, enabling clip generation from 5-word text, raw subtitles, or SRT files.

2024-12-02 Mon: Completed [JWT integration in harmony-all-api backend](https://github.com/harmony-one/harmony-llm-api/pull/26), implementing dual auth system: token-based for Harmony services and JWT for general access. Enhanced [video transcript demo](https://github.com/harmony-one/transcript-word-timestamp-demo/pull/7) with automated logging system generating runtime logs and SRT files, optimizing subtitle rendering performance.

---
2024-11-29 Fri: Finished [MoviePy integration](https://github.com/harmony-one/transcript-word-timestamp-demo/pull/6) with CLI optimization, setting default word count per subtitle frame to 1 with configurable --words parameter. Progressing on Web3 auth flow in harmony-llm-api through wallet signatures and JWT integration.

2024-11-28 Thu: Integrated MoviePy library with FFmpeg for enhanced subtitle handling, enabling multi-word subtitle parameters with frame-accurate word highlighting sync.
 
2024-11-27 Wed: Progressing on multi-word subtitles functionality, debugging active word highlight synchronization.

2024-11-26 Tue: Paid Time Off

2024-11-25 Mon: Progressing on multi-word subtitles functionality, debugging active word highlight synchronization. Refactored harmony-llm-api codebase to integrate JWT auth system.

---
2024-11-22 Fri: Integrated full raw phrase input functionality. Enhanced subtitle processing efficiency by implementing single-pass rewrite for complete subtitle text. Researched harmony-llm-api migration to a pay-per-use solution, using JWT authentication.

2024-11-21 Thu: Implemented clip generation pipeline with subtitle support (full text, word-by-word), and integrated subtitles. Resolved core script execution issues.

2024-11-20 Wed: Built video search demo leveraging AssemblyAI's millisecond-level word timestamps, rapidfuzz for semantic matching, ffmpeg for audio processing and yt-dlp for video downloads. Added video clip generation starting from phrase matches with configurable duration (default 30s). Currently troubleshooting implementation issues to achieve stable functionality.

2024-11-19 Tue: 2024-11-19 Tue: Built YouTube video search demo using [youtube-transcript-api](https://github.com/harmony-one/transcript-word-timestamp-demo/pull/3) and rapidfuzz for semantic phrase matching. Implemented word-to-timestamp mapping using position-based calibration and empirical offset correction due to the library phrase-timestamp mapping design, after initial consonant-based timing approach showed drift in longer segments. Enhanced search accuracy by providing three timestamped URLs per match (before, target, after) to handle transcript timing variations.

2024-11-18 Mon: Implementing JWT auth integration for 1.country in tokenClientApi. Researched video transcription solutions - exploring AssemblyAI's API for real-time streaming and word-level timestamps as primary choice, with alternatives like WhisperX (GPU-dependent) and Google Cloud Speech-to-Text (needs audio extraction) as backups. Built command line demo using [youtube-transcript-api](https://github.com/harmony-one/transcript-word-timestamp-demo) lib for quick testing.

---
2024-11-15 Fri: Refactored tokenApiClient, memCoinCommandHandler and WidgetModule implementing modular pattern for better code organization and maintainability. Started JWT auth integration after pump.fun Backend upgrade.

2024-11-14 Thu: Refactored [array-based BondingCurve contract](https://github.com/harmony-one/pump.fun.contracts/pull/8) to initialize stages via constructor rather than method params, standardizing curve stages across tokens and aligning method signatures with exponential-base BondingCurve implementation. Added /c0 command on 1Bot which restes all conversations and generates the completion using Claude's 3.5 Sonnet. Troubleshooting completion message issues while integrating 3.5 Haiku model.

2024-11-13 Wed: Completed the [MemeTokenWidget](https://github.com/harmony-one/1-country.frontend/pull/219), fixing styling issues, but still having issues with user coins held. Reviewing and implementing array-based Bonding Curve contract modifications per [Aaron's feedback](https://github.com/harmony-one/pump.fun.contracts/pull/6).

2024-11-12 Tue: Refactored meme command's widget logic to use single widget pattern for all meme command executions. Worked on Meme Token widget to show user's created tokens, holdings and pump.fun past winners.

2024-11-11 Mon: Refactored [Token creation logic](https://github.com/harmony-one/1-country.frontend/pull/219) and modal UI for 1.country integration. Analyzed pump.fun smart contract and backend architecture to implement user token retrieval functionality.

---
2024-11-08 Fri: Implemented TokenApiClient for [pump.fun](https://github.com/harmony-one/1-country.frontend/pull/219) API integration and smart contract interactions in RootStore. Built memecoin creation modal for 1.country integration. Pending meme command refactor and UI polish.

2024-11-07 Thu: Fixed token limit handling for [Gemini](https://github.com/harmony-one/harmony-llm-api/pull/24) and error reporting system for xAI's Grok model in harmony-llm-api. Advanced pump.fun integration with 1.country, focusing on token creation logic.

2024-11-06 Wed: Completed array-based bonding curve contract implementation and merged into [pump.fun repo](https://github.com/harmony-one/pump.fun.contracts/pull/6). Enhanced harmony-llm-api telegram error reporting for LLM integrations (Claude, Gemini, Luma). Extended [telegram error reporting](https://github.com/harmony-one/HarmonyOneBot/pull/373) on 1Bot for OpenAI and Grammy endpoints. Initiated pump.fun/1.country integration.

2024-11-05 Tue: Worked on splitting BondingCurve contract architecture into price calculation and token management modules for improved separation of concerns. Team sync concluded on integrating BondingCurve contracts into pump.fun repo, enabling token creation via 1.country with embedded widget for token metrics and rankings. Implementing telegram error notification system for harmony-llm-api backend following luma model stability issues in 1Bot.

2024-11-04 Mon: Deployed sliding window implementation on Harmony0Bot for pre-1Bot testing, refactored /new command for multi-conversation refresh. Added prompt command, to set new models context/system message. After reviewing bonding curve repo, architecting solution with two main contracts: MemeCoinBattle for daily WONE prize competitions and BondingCurve for price calculations. Implementing clone contracts for gas-optimized token deployment, where winning tokens collect WONE reserves from eliminated competitors.

---
2024-11-01 Fri: Integrated [Luma](https://github.com/harmony-one/HarmonyOneBot/pull/366/) and resolved master branch conflicts. Implemented [session-based cleanup logic](https://github.com/harmony-one/HarmonyOneBot/pull/371) with 3AM threshold timestamps - cleanup trigger executes once daily via needsCleanup method validation. Started reviewing Bonding Curve implementations from [Aaron's shared repo](https://github.com/qiwihui/pumpeth) for feature analysis.

2024-10-31 Thu: Integrated Luma model in 1Bot with 40¢ base pricing plus adjustments, implementing post-download generation cleanup. Successfully validated sliding window implementation. Optimized idle message deletion logic (1h+ threshold) to prevent conversation integration conflicts from dual user role messages. Merged PR to 1.country incorporating vanity URL deletion, Notion delete command, plus EAS and email deactivation commands.

2024-10-30 Wed: Added MemeCoin Widget integration on 1.country displaying token balances post-creation. Domain holders mint their MEME COIN via meme command. Pending implementation of zero-param meme command for auto-token creation using current domain. Integrated sliding window in 1Bot to mitigate quadratic complexity in infinite chat context. Pending further testing before deployment.

2024-10-29 Tue: Implemented on 1.country app the token creation via _**meme** [TokenName] [TokenSymbol]_ command and getOwnerTokens method to display memecoins per domain holder. Enhanced BC contract with token metadata (timestamp, creator) and optimized updateDailyWinner logic. Deployed updated Bonding Curve contract to Harmony mainnet. In progress: memecoin widget implementation on 1.country.

2024-10-28 Mon: Implementing BC (Bonding Curve) logic integration for 1.country to enable memecoin creation for domain owners. Added token name uniqueness validation in BC contract.

---
2024-10-25 Fri: Fixed token count metrics for non-streaming chatCompletion affecting [grok model integration](https://github.com/harmony-one/HarmonyOneBot/pull/370). Deployed latest version to 1Bot. Patched sell token contract logic in Bonding Curve dApp and refactored buy and sell functionality. Deployed latest build to [ly.io on Harmony Testnet](https://bonding-app.fly.dev/).

2024-10-24 Thu: Completed Grok model (xAI) integration in harmony-llm-api backend and 1Bot (accessible via /gk). Optimized default model commands to utilize highest-tier variants (/g for Gemini 1.5, /c for Claude 3.5 Sonnet, /ask for GPT-4). Fixed BondingCurve token purchase logic issues and enhanced dApp interface for improved UX.

2024-10-23 Wed: Enhanced BondingCurve UI/UX and deployed smart contracts to HarmonyTestnet, debugging tx issues in token purchasing flow. Integrated xAI provider into harmony-llm-api infrastructure, established endpoint and initiated 1Bot integration. Pending API key funding (coordinated with Theo).

2024-10-22 Tue: Resolved balance discrepancies in [bondingCurve contract](https://github.com/harmony-one/bonding-curve-prototype/pull/2) token purchase tests. Enhanced client dApp buy flow, implementing allowance checks. Debugging reserve token approval flow prior to token purchase.

2024-10-21 Mon: Implemented and deployed [fix for o1 model completion in 1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/369), resolving request params mismatch and markdown entity splitting issues. [Completed and deployed Lumo](https://github.com/harmony-one/harmony-llm-api/pull/23) backend logic integration. Will continue Bonding Curve development and Lumo cmd deployment in 1Bot on Tuesday.

---
2024-10-18 Fri: Implemented TokenTrader component for BondingCurve dApp, enabling token buy/sell operations, and updated TokenList and TokenListItem components. Enhanced token hooks with transaction functionalities including purchase, sale, and approval processes.

2024-10-17 Thu: Continued developing BondingCurve contract, implementing token-related methods previously handled by TokenFactory. Addressing balance discrepancies during token purchase tests. Added web3 logic to the frontend, including token list and price hooks, along with token list component.

2024-10-16 Wed: Implemented [BondingCurve and Token contracts](https://github.com/harmony-one/bonding-curve-prototype/pull/1) with corresponding deploy and test scripts. Addressing balance discrepancies in BondingCurve during token purchases. Concurrently, building a Next.js app for memecoin ecosystem: listing, purchasing, and determining daily liquidity winners. Basic template in place, progressively adding core functionalities.

2024-10-15 Tue: Implemented hotfix for 1Bot, enhancing model check to prevent parameter mismatch with OpenAI's o1 models. Commenced development of proprietary bonding curve implementation due to licensing constraints on Mint Club's contracts. Focusing on core smart contract development: BondingCurve, Token, and TokenFactory.

2024-10-14 Mon: Refined user interaction metrics for getUniqueUsersCount, getActiveUsers, and getOnetimeUsers by focusing on isSupportedCommand rows. Implemented date restriction in getUserEngagementByCommand for monthly analysis. [Deployed updates to 1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/369). Initiated work on BondingCurve/1.country project: conceptualizing /meme command for memecoin creation linked to user's owned 1.country domain, and /transfer command for memecoin transfer (domain transfer implications TBD). Envisioning a site like memebattle.country as central hub for purchasing (minting) and selling (burning) memecoins via bonding curve, and showcasing daily liquidity winners. Began reviewing Mint Club contracts on GitHub.

---
2024-10-11 Fri: Completed refactoring of /allstats command. Enhanced user tracking logic to include interactions where isSupportedCommand = true, capturing a broader spectrum of bot engagement beyond chats with 1Bot membership. This update provides a more comprehensive view of user activity, crucial for accurate analytics.

2024-10-10 Thu: Enhancing /allstats command with optional date parameter for monthly reporting (e.g., /allstats mm/dd/YYYY). Refined paid and free credit user queries to accurately track credit usage patterns. Improved user classification logic: now only categorizing users as 'paid' if they've consumed over 100 credits. This adjustment addresses a quirk where users with ONE payments were flagged as paid users, skewing usage statistics, since no commands have been paid in ONE since September 2023. Credit consumption now serves as a more reliable metric for user engagement. Submitted [PR for stats update](https://github.com/harmony-one/HarmonyOneBot/pull/369), asked Artem to review it. Iterating on /allstats output to clearly differentiate weekly and monthly/all-time metrics. Continuing work on improving command output for enhanced clarity and data interpretation.

2024-10-09 Wed: Reviewed, approved, and deployed [Artem's PR](https://github.com/harmony-one/HarmonyOneBot/pull/368), updating telegrah API subgraph url for Swap data. Contributed [Viem tutorial](https://github.com/harmony-one/docs-home/pull/111) to Harmony's doc repo, showcasing minting transactions, HarmonyTestnet integration, and contract interaction. Revamped 1Bot user payment metrics to address classification issues. Implemented new logic: users consuming >100 free ONE credits are now correctly identified as paid users. This fix accounts for the system's initial 100 free credits and subsequent user deposits, ensuring accurate tracking of genuine paid usage across credits and ONE.

2024-10-08 Tue: Reviewed, approved, and deployed [Artem's PR](https://github.com/harmony-one/HarmonyOneBot/pull/367), solving network fees weekly and wallets count weekly stats for 1Bot. Added two user stats for 1Bot: number of users paid in credits and users paid in ONE; before deploying to 1Bot, need to fix local database for testing and review report label text with Amanda. Progressed on Viem's mint example for Harmony docs; PR completion scheduled for tomorrow.

2024-10-07 Mon: Resolved dalle command issues on Harmony1Bot and deployed hotfix. Implemented error handling for luma model in harmony-llms-api, optimized luma video generation process, and adjusted wait time to 45s. Analyzed 1Bot stats command showing NaN or zero values for swap trading volume, network fees weekly, and wallets count weekly; need to consult with Artem regarding outdated endpoints. Provided support for 1.country "buy" domain issues. 

---
2024-10-04 Fri: Completed video gen logic on Harmony1Bot and harmony-llms-api backend. Refinement needed: error handling, post-download cleanup, exploring video configs (loop, size), updating queue info for accurate wait time (>30s), finalizing pricing structure. Awaiting harmony1Bot and harmony0Bot API keys for mainnet deployment (currently on test bot).

2024-10-03 Thu: Developed [Luma backend endpoints](https://github.com/harmony-one/harmony-llm-api/pull/23) on harmony-llm-api for video generation management. Integrated Telegram messaging to user's chatId with inline keyboard functionality. Implemented API for tracking generation counts across statuses (complete, fail, dreaming) and added deletion capability for post-download cleanup. Engineered LumaBot module to handle Luma's command logic and callback queries. Tackling video download functionality, addressing ongoing technical challenges.

2024-10-02 Wed: Developing luma endpoint for harmony-llm-api and implementing lumaBot integration for Harmony1Bot. Exploring asynchronous video generation workflow: backend to dispatch message with download link (featuring in-line keyboard button) to user's chat upon completion, eliminating polling overhead. 

2024-10-01 Tue: Refactored [Harmony1Bot models logic](https://github.com/harmony-one/HarmonyOneBot/pull/365), enabling seamless addition of commands and prefixes to any model without code modifications. Updated model context to mitigate subjectivity bias. Implemented single-letter commands and prefixes across all LLM models. Resolved o1 model's URL handling issues in prompts. Initiated Luma integration, pending API key acquisition.

2024-09-30 Mon: Integrated viem into [Harmony documentation](https://github.com/fegloff/docs-home/tree/developers-viem), implementing client initialization and contract instantiation. Added call aggregation via multicall and sample code for connecting to Harmony Testnet, addressing viem's lack of native support. On Harmony1Bot, worked on subagent initialization to resolve ongoing issues and investigated prompt handling to mitigate inconsistent model completions.

---
**2024 Q3 Review (6 hours)** 

I deployed Vertex contracts on Harmony mainnet and testnet, developed a [MockSequencer contract](https://github.com/fegloff/vertex-contracts/pull/1), PerpetualFactory for contract creation, enhanced PerpOracle, and created OrderBook contract and OrderBookFactory. To address the lack of Harmony-specific components, I developed a [harmonyClient module](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2) for mock calls while working on porting API calls. Despite implementing logging events for MatchOrderAMM transactions across various contracts to aid debugging, challenges persisted with processing both MatchOrderAMM and SwapAMM transactions. 

For Harmony1Bot (1Bot), I introduced a [/broadcast](https://github.com/harmony-one/HarmonyOneBot/pull/365/commits) command for sending Harmony updates to all users and groups, enhanced the /help command to display recent broadcasts, and upgraded VoiceMemo to generate transcriptions for forwarded voice notes. The LlmModelManager class was refactored to accommodate new AI models, including OpenAI's o1-preview and Claude's Sonnet 3.5. New [/o1 and /models commands](https://github.com/harmony-one/HarmonyOneBot/pull/364) were implemented to improve user interaction with various AI models. I developed a workaround for Telegram's message size limit and enhanced error logging. We migrated 1Bot's database to a new cluster, resolving persistent restart issues. For 1.country, I enabled paid-in-advance [domain rental functionality](https://github.com/harmony-one/1-country.frontend/pull/218), enhancing the platform's capabilities and offering users more flexible payment options. Also, I added a [/subdomains command](https://github.com/harmony-one/HarmonyOneBot/pull/362) to Harmony1Bot, allowing admin users to enable subdomains for given domains (among other commands). This integration improves the accessibility and management of 1.country services through the bot interface, streamlining the user experience and bridging multiple Harmony services.

---
2024-09-27 Fri: Paid Time Off

2024-09-26 Thu: Paid Time Off

2024-09-25 Wed: Refining HmnyAgent logic to process latest Harmony ecosystem data. Implementing vector database storage for preloaded Harmony info, streamlining /ask command responses for Harmony-related queries. 

2024-09-24 Tue: Continuing work on SwapAMM tx processing, addressing persistent issues within the Enpoint, MockSequencer contracts. Initiated Harmony Subagent development for real-time chain data integration and DeFi analytics, compensating for AI model knowledge gaps. Deployed Harmony1Bot updates featuring /broadcast functionality, optimizing network-wide communication protocols.

2024-09-23 Mon: Implemented broadcast rate limiting to comply with 30 messages/second cap, along with sent/error reporting functionality. Added /preview command for pre-send broadcast style verification. Dove deep into SwapAMM transaction on Vertex Contracts, encountering Endpoint contract size limitations.

---
2024-09-20 Fri: Enhanced /help command to display latest broadcast when available, resolving HTML parse mode issues. Enabled parsing of broadcast messages in HTML or Markdown format. Stored latest broadcast in session for improved accessibility. Upgraded VoiceMemo functionality to generate transcriptions for forwarded voice notes, contingent on voiceFlag in env variables or OneTimeForward flag activation via /forward command.

2024-09-19 Thu: Progressed on SwapAMM tx implementation for Vertex contracts, but still having issues when processing the transaction. Tackling CVE-2024-45296 vulnerability in harmony-one/gmx-price-keeper repo; migrated to Node v18 for overrides field, facing compilation hurdles. Brainstormed with Theo on 1Bot user engagement strategy, emphasizing AI command-line driven for Harmony build and DeFi interactions using agents and exploring a potential custom LLM integration for the ecosystem.

2024-09-18 Wed: Developed HmnyBot module for 1Bot to manage Harmony's user engagement features, now including /broadcast and /docs commands. Plan to discuss with Theo. Refining MockSequencer contract and test script for SwapAMM tx validation post-Aaron consultation. Conferred with Aaron and Soph on CVE-2024-45296 vulnerability; set to review harmony-one/crosschain-bridge.frontend repo with Yuriy and aim to resolve harmony-one/gmx-price-keeper repo issue using package.json overrides field.

2024-09-17 Tue: Researching Telegram's documentation for features to boost 1Bot's user engagement. Exploring push notification strategies and methods to streamline Harmony's documentation access. Evaluating potential implementations to enhance user retention and interaction within our dApp ecosystem, following yesterday's team discussion with Theo.

2024-09-16 Mon: Added prefix handler to the recently refactored LlmModelManager class. Pruned obsolete models (j2-ultra, gpt-4-32K, etc.) to streamline codebase and offer only current models. Fixed o1-preview model completion issue. Deployed latest refactoring, including new /o1 and /models commands, to Harmony1Bot. Reviewed crosschain-bridge.frontend and harmony-erc-20 repos for CVE-2024-45296 vulnerability impact, pending discussion with Li on mitigation strategies.

---
2024-09-13 Fri: Investigated CVE-2024-45296 vulnerability in harmony-one/gmx-price-keeper. Application not directly affected due to simple GET endpoints. Planning URL length limitation middleware implementation and gradual package updates as mitigation strategy. Refactored 1Bot's model handling, creating LlmModelManager class to support new /models command. Aaron reviewing Vertex's contracts code.

2024-09-12 Thu: Integrated OpenAI's o1-preview and o1-mini-2024-09-12 models, updating openai library. Implemented workaround for Telegram's message size limitation by splitting o1-preview completions into multiple messages. Note: o1-preview completions are non-streaming with extended response times. Rectified prompt/completion pricing for non-streaming chatCompletion requests. Deployed to 0Bot for QA. Optimizing markdown parse mode for enhanced completion readability. Initiated Binance/Telegram integration research. Vertex code review with Aaron scheduled for Friday.

2024-09-11 Wed: Explored prediction market implementations within Vertex ecosystem; no existing solutions found. Debugging MatchOrderAMM tx in test environment. Investigated transaction failures and refined contract logic, focusing on OffchainExchange contract interactions.​​​​​​​​​​​​​​​​

2024-09-10 Tue: [Implementing logging events](https://github.com/fegloff/vertex-contracts/pull/1) for MatchOrderAMM transaction across Endpoint, MockSequencer, and OffchainExchange contracts. Troubleshooting event listener synchronization issues. Escalated to Aaron for code review. Supported integration testing of Dogs Telegram Bot with Alaina.

2024-09-09 Mon: Debugging MatchOrderAMM transaction processing in Vertex ecosystem. Endpoint's submitTransactionCheckedWithGas calls yielding ERR_ORDERS_CANNOT_BE_MATCHED errors. MockSequencer's submitTransactionCheckedWithGas invocations resulting in low-level execution failures.

---
2024-09-06 Fri: Troubleshooting persistent ERR_ORDERS_CANNOT_BE_MATCHED error during Match Order AMM Transaction execution. Implemented contract events and enhanced event handler in test script. Added flag logs for granular tracing. Collaborated with Theo on 1.country to implement prepaid domain rental functionality, eliminating need for autorenew code modifications. 

2024-09-05 Thu: Implemented subdomain enabler for 1Bot's internal use, complementing existing cert, NFT, and domain status features. Activated subdomains for two 1.country domains experiencing Notion page linking issues. Continued [refactoring MockSequencer](https://github.com/fegloff/vertex-contracts/pull/1) contract to resolve ITI (ERR_INVALID_TIME) and OCBM (ERR_ORDERS_CANNOT_BE_MATCHED) errors in trade transactions. ITI errors likely stem from time initialization problems in SpotEngine and PerpEngine, triggered when calling getTime on the Endpoint contract.

2024-09-04 Wed: Implementing collateralDeposit method with successful fund transfers and subaccount registration. Balance updates now functioning correctly. Progressing on local testing of submitTransactionsCheckedWithGasLimit to refine logic in Vertex DeFi client app.

2024-09-03 Tue: Implementing executeSlowModeTransactionImmediately in Endpoint to bypass three-day wait for collateralDeposit execution. While fund transfers occur, subaccount registration and balance updates were lagging. Overhauled MockSequencer to leverage Endpoint for immediate slow mode tx processing, OffchainExchange for matchOrderAMM, and Clearinghouse for collateral withdrawals. Enhanced test scripts to monitor subaccount update events, ensuring robust tx lifecycle tracking across the system.

2024-09-02 Mon: Testing submitTransactionsCheckedWithGasLimit locally. DepositCollateral tx not recording subaccount, causing submitTransactionsCheckedWithGasLimit failure. DepositCollateral method throwing "Transaction reverted without a reason string" when interacting with MockSequencer. Next: enhance MockSequencer error logging, verify executeSlowModeTransaction, examine MockSequencer-Endpoint interaction. Suspect root cause in MockSequencer's slow mode tx handling.

---
2024-09-01 Sun: Continued local testing of placeOrder logic. Enhanced contract handler for harmonyClient in Vertex DeFi client app. Implemented getNonce, nSubmissions, and submitTransactionsCheckedWithGasLimit methods. The latter doesn't require sequencer invocation and has simplified requirements compared to submitTransactionsChecked.

2024-08-30 Fri: Attended to personal health matters.

2024-08-29 Thu: Refactored Mock Sequencer and deployed latest changes, including Orderbook modifications, to mainnet. Local testing of placeOrder logic revealed an issue with depositCollateral method. The token requires collateral deposit for Endpoint contract transactions, but the deposit execution encounters a problem with the transfer method, which utilizes the same transaction method as placeOrder logic. Addressing this to ensure full functionality of placeOrder logic. Additionally, for 1country, working on enabling multi-month advance payments for domains. Encountered rent command execution issues, currently resolving.

2024-08-28 Wed: Working on skipping offchain order book in placeOrder logic. Vertex contract review revealed need for Mock Sequencer refactoring due to sequencer-callable Endpoint's submitTransactionsChecked method. Initiating Sequencer refactoring and setting up local tests for submitTransactionsCheck execution. 

2024-08-27 Tue: Resolved stream issues with Gemini model on harmony-llm-api for Harmony1Bot. Enhanced error logging and modified /s command to support Claude's Sonnet 3.5 model. Regarding Vertex Defi App, implemented getContract call on HarmonyClient, and Completed HarmonyClient refactoring to handle contract calls efficiently.

2024-08-26 Mon: Consulted Simao about AMM contract implementation. Identified matchOrderAmm transaction type in OffchainExchangeContract as key focus. Refactored HarmonyClient library for optimized web3 calls. Working on porting getContracts function to access Harmony contracts.

---
2024-08-23 Fri: Refactored OrderBook contract to implement product-specific orderBooks. Implemented placeOrder method with core logic, integrated sell and buy order arrays, and developed matchOrder function for iterating through orders, pairing compatible trades, and executing matches. Optimized deploy and initialization scripts for main, spotEngine, and perpEngine. Conducted local testing to validate changes.

2024-08-22 Thu: Expanded mock calls for market, perp, and index engine on Vertex's Trade page. While porting vertexClient.context.engineClient.getContracts() to Harmony network, discovered Vertex's multi-contract architecture: one OrderBook per product. Refactoring OrderBook contract and implementing OrderBookFactory for efficient contract instance management.

2024-08-21 Wed: Analyzed Order Form logic, identified and fixed execution conversion price (token order/quote token) issue blocking order processing. Added key market mock calls for tokens latest prices (getLatestMarketPrices method) and perp order placement (placeOrder method). Next steps: expand mock call coverage and fix conversion for tokens with prices lower than the quote token.

2024-08-20 Tue: Tested TimesWalletBot on private and group chats; the wallet is linked to the user, not the chat ID. Shared repository URL and key script location with Simao. Diving deeper into Perp/Spot order logic implementation on Vertex Client App.

2024-08-19 Mon: Presented Vertex porting project status to Artem and Simao. Deployed Vertex token to Harmony mainnet, updating Client App with token address and product ID. Post token listing fixes, analyzing trade page logic for Harmony mainnet integration. Tomorrow, seeking Simao's collaboration on Vertex contract refinements.

---
2024-08-16 Fri: Deployed and initialized Vertex contract on Harmony mainnet. Launched client app with Harmony Mainnet configuration on fe.country. Resolved token listing issues on [Vertex client Apps' trade page](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2).

2024-08-15 Thu: [Implemented PerpetualFactory contract](https://github.com/fegloff/vertex-contracts/pull/1) to streamline creation of new perpetual contracts. Fixed critical issues in perpetual contract creation process, focusing oracle price setting and proper order book initialization. Refined initialization script to efficiently handle perp engine and post-engine tasks.

2024-08-14 Wed: Integrating USDC, USDT, WBTC, WONE, and ETH from Harmony mainnet into Vertex Decentralized Finance Trade application. Updating frontend components, generating mock data, and modifying contract scripts to support these new tokens. 

2024-08-13 Tue: Fixed [deploy and initialization scripts](https://github.com/fegloff/vertex-contracts/pull/1), enhancing Perpetual and PerpOracle contracts. Introduced OrderBook contract and modified hardhat configuration file to support deployments across multiple chains. Progressed with the review of the Vertex trading page, focusing on perpetual operations.

2024-08-12 Mon: Enhanced PerpOracle contract by introducing randomness to the getCustomPrice method, improving price simulation for testing scenarios. Created deploy scripts for Perpetual and PerpOracle contracts. Implemented scripts to set initial custom price for USDC token and add product to PerpEngine contract, facilitating contract initialization. Developing a basic order book contract as an alternative to the OffchainExchange contract.

---
2024-08-09 Fri: Implemented PerpetualContract with constructor parameters for productId, collateral token address, and Oracle address. Incorporated productId to align with PerpEngine's addProduct method, which differs from SpotEngine's token address usage. Enhanced Oracle contract constructor with a boolean parameter, enabling selection between a custom oracle for testing and Chainlink integration for staging/production environments.   

2024-08-08 Thu: Configured fly.io custom domain to link vertex-trade project URL with [fe.country](https://fe.country), following Aaron's DNS mapping of fe.country to the Vertex application. Conducting an ongoing review of the Vertex trading page and associated module, focusing on perpetual trades functionality. Simultaneously analyzing a perpetual contract implementation to gain deeper insights into its structure and behavior.

2024-08-08 Thu: Configured fly.io link vertex-tarde project URL with fe.country, after Aaron mapped fe.country DNS with vertex app. Worked on reviewing Vertex trading page and module to work on mock perp trades. Also, checked perpetual contracts implementations. 

2024-08-07 Wed: Updated [Dockerfile to enhance performance](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2). Modified quote token to USDT on Harmony test network. Reviewed perpetual contract logic and tokens on Harmony bridge. Talked to Aaron about updating country DNS records to link Vertex fly.io URL to fe.country.

2024-08-06 Tue: Deployed Vertex Trade App on [fly.io](https://vertex-trade.fly.dev/). Configured Dockerfile and fly.toml to work with Next.js monorepo. Fixing deploy errors related to ChainDev handling (supporting multiple chain environments such as local, testnet, harmonyMainnet, among others), package.json build scripts, and Sentry configuration.

2024-08-05 Mon: Refactoring TradingView mock interfaces/types to resolve [build script issues](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/3). Successfully running Vertex Trade App's dev and build scripts locally with Harmony Testnet chain integration. Continuing efforts to deploy Vertex App in fly.io and in Harmony mainnet.

---
2024-08-02 Fri: Working on resolving build command issues for the Vertex Trade App frontend, addressing Tailwind problems, and modifying TradingView mock hooks calls. These build-related challenges remain ongoing and require further attention. Monitored the new cluster PostgreSQL database connection with 1Bot, observing no issues and confirming successful insert statements in logs, chats, stat_bot_command, invoice, and users tables. 

2024-08-01 Thu: Migrated 1Bot database to Soph's new cluster, updating primary keys, foreign keys, Indexes, sequences, and data to match the old Database cluster. Next day's plan: monitor 1Bot/Database integration. For Vertex Defi App frontend, accessed Trade menu page locally after modifying components using TradingView mock data.

2024-07-31 Wed: Created and tested backup of 1Bot database. Soph created a cluster on fly.io from a snapshot of the primary server. This new cluster has all machines working (primary, replica, and zombie). The next step is to connect 1Bot to this new database with the update of all subsequent changes (from the snapshot date). For the Vertex Trade App, completed updating all hooks and other files that use TradingView libraries. Currently testing its functionalities with the rest of the app to ensure successful build and deployment on fly.io with no errors.

2024-07-30 Tue: Updated trading charts hooks and other files to use mock types, turning off the use of TradingView Advance libraries (85% progress). Talked to Soph regarding 1bot payments database issues throwing the Connection terminated unexpectedly error. The database zombie machine is down, and we need to back up the databases before creating a new zombie machine that will complete the architecture (primary, replica, and zombie). Tomorrow, the backup will take place.

2024-07-29 Mon: Checked issues with 1.country site and payment database connection issues on Harmony1Bot. Also worked on the Vertex Trade App mocking TradingView components.

---
2024-07-26 Fri: Finished the [withdraw mock call](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2) on the Vertex Trade Client. Also added the [VertexToken contract](https://github.com/fegloff/vertex-contracts/pull/1) to the Vertex Contracts repo and the logic to deploy it through a Proxy. Updated the deploy and initializer scripts. Finally, Kept working on using mock graphs instead of the TradingView library.

2024-07-25 Thu: Working on a mock call of the Withdraw feature due to its use of the Vertex SDK and query endpoint to handle the call. Also talked to Aaron and started to work on deploying the Vertex Token on the Harmony testnet chain. Finally, investigating a way to work with mock graphs instead of using TradingView Advance and free versions. 

2024-07-24 Wed: Talked to Aaron about the Vertex Trading App and listed the components required to have minimal functionalities. Also, worked on fixing the mock data handling on the withdraw feature, which is disabling the feature.

2024-07-23 Tue: Fixed [formatTimestamp](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2) method issues with Harmony mock data. Added spot property to harmonyClient to handle spot engine mock calls and added a method to retrieve the maximum withdrawable amount per token. Kept working on the withdrawal feature.

2024-07-22 Mon: Enabled faucet feature to mint testnet funds for Harmony Testnet on Vertex App and currently working on the withdraw feature.

---
2024-07-19 Fri: Checked TradingView data feed integration with Vertex Trade App, and transitioning to a free alternative would require a significant effort. Reviewed and created a list of missing components to port Vertex to Harmony and sent it to Li. Pushed the latest changes to Vertex Defi App [PR](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2 ) and Vertex contracts [PR](https://github.com/fegloff/vertex-contracts/pull/1).  

2024-07-18 Thu: Was able to retrieve the wallet balance using the custom multi-call hook and make a deposit. Checked TradvingView Advance integration with the Trade app, and it seems that using the free version will require significant refactoring. The TradingView library is required to access the Trade feature. Need to check how the datafeed component could affect the refactoring.

2024-07-17 Wed: Kept working on wallet connection logic and fixed an issue not allowing wallet balance to show on the Vertex Trade app. The problem was related to publicClient's multicall method of the Wagmi package. Added custom multicall hook for not supported chains.  

2024-07-16 Tue: Worked on the Vertex Trade app wallet connection (it's not showing wallet balance) and deposit methods on the Harmony Testnet chain. Had to update mock JSON files to use the mockTokens address (it's not enough to update config files). 

2024-07-15 Mon: Deployed Vertex contracts on the testnet chain for testing on the Vertex Trade app, including mock tokens. Refactored the defi app code to support the harmony testnet chain. On 1Bot disabled bard's model command due to its discontinuation to become Gemini (1bot supports Gemini 1.5, too).

---
2024-07-12 Fri: Added MockQuoteToken (for price reference, fee denomination, liquidity provision, margin, and collateral deposits, etc.) and MockUsdcToken, added localhost/hardhat chain for local testing. Added a [deposit script](https://github.com/fegloff/vertex-contracts/pull/1) to test the depositCollateral method locally on the contract level because it was not working on the Trade App site, and the local test was successful.

2024-07-11 Thu: Reviewed the deposit operation at the contract level. Refactored deploy and initialization scripts, which fixes contracts initialization, to correctly assign Spot and Perp engines to the endpoint contracts, among other improvements. 

2024-07-10 Wed: Kept working with Vertex contracts and Vertex trade app. Was able to add products to the SpotEngine contract. Also added OffchainExchange initialization. Updating the deploy/initialization script is due to contract prerequisites. 

2024-07-09 Tue: Still had issues adding products to the spot and perp engine contracts. Checked other contracts logic and created script to add spot and perp engines to clearingHouse contract, but had the same error when trying to register a product. Adding some emit events to flagging the contract method logic. On 1Bot, added [content policy violation](https://github.com/harmony-one/HarmonyOneBot/pull/362) error handling for the /dalle command (pushed live).    

2024-07-08 Mon: Working on adding products to spotEngine and perpEngine contracts. The offchainExchange address is used as the order book contract (one of the required parameters). Had gas issues, working on solving them. Expecting that after fixing the product addition, the deposit logic will be fulfilled.

---
2024-07-05 Fri: Fixed /stats and /botstats commands, which were throwing 410 errors due to [uniswap-v3-harmony](https://api.thegraph.com/subgraphs/name/nick8319/uniswap-v3-harmony) endpoint has been removed. Added error handling on the rest of API calls for stats-related commands. Looking for an alternative to bring uniswap/harmony data. Updated the new contract address after all Vertex public contracts were initialized, but still working on deposit funds logic and checking Vertex SDK.

2024-07-04 Thu: Updated Vertex's initializable contracts, adding [isInitialized method](https://github.com/fegloff/vertex-contracts/pull/1) to check if the contract was already initialized. The new method calls Openzeppelin Initializable's _getInitializedVersion() method. Also updated the initializer script and fixed ArbAirdrop (with WONE as an airdropped token) contract initialization issues. Checked the 1bot database on fly.io, and the zombie machine is down (primary and replica machines are up and running). Designed a plan to replace the zombie machine and discussed it with Artem, who will check the fly.io configuration. Also, worked on fixing 1Bot /stats and /botstats commands.

2024-07-03 Wed: Initialized perpEngine and spotEngine and had issues with contract owner initializing arbAirdrop contract (with WONE as airdropped token). Had issues initializing. Checked 1bot logs and stats and had issues with the /stats command, working on fixing database connection issues (Request failed with status code 410 error) . 

2024-07-02 Tue: Initialized [Clearinghouse contract](https://explorer.harmony.one/address/0x1dd343adb90548b7af93abb9086b26e6f9c0f280) on Harmony Mainnet. Working on perpEngine and spotEngine initialization. Reviewed TransparentUpgradeableProxy initialization, which is expecting the initial implementation contract address. According to the [bytecode](https://arbiscan.io/bytecode-decompiler?a=0x7a557dddb3f19eb9d81983b67858b6e73c140ac2) of the implementation contract, the contract includes a method of handling user positions, deposits, and withdrawals, executing trades or swaps, etc. The contract address differs from what Vertex gave on their documentation, so I wrote on Vertex Discord to seek help porting Vertex on a chain different from Aribitrum.

2024-07-01 Mon: Fixed [Verifier contract](https://github.com/fegloff/vertex-contracts/pull/1) initialize method issue. Redeployed all contracts after changes were made to the initialize method on the Verifier contract. Reinitialized the Endpoint contract but still had issues with the deposit logic on the Trade App. Kept working on this and other contract initialization methods.

---

**2024 Q2 Review (11 Hours)**

I integrated [GPT-4o to 1Bot](https://x.com/harmonyprotocol/status/1795951553024565259), implemented token-based security and refactored the codebase to facilitate adding new large language models, including Claude, Sonnet, Haiku, and subagent integration. Added model-specific conversation handling and access to Anthropic tool feature, to check stocks and Web3 tokens. I fixed simultaneous command call issues.

Porting and deploying [Vertex Trade](https://github.com/harmony-one/vertex-web-monorepo-snapshot) contracts to Harmony. To address the mono-repo's reliance on the Vertex-typescript-sdk, I implemented a harmonyClient module designed to handle mock calls while facilitating the gradual porting of all API calls to the Harmony network. Additionally, I deployed defi_greeks API which provides endpoints for calculating risk measures and greeks for various financial derivatives and improved 1.country one-and-two-letter domain handling and certificate management.

---
2024-06-30 Sun: Worked on Verifier initialize method.

2024-06-28 Fri: Medical emergency.

2024-06-27 Thu: Medical emergency.

2024-06-26 Wed: Created and deployed MockSequencer and MockSanction contracts. Created initializer script to handle contract initializations. Initialized Endpoint contract, but having issues initializing Verifier contract. Time is limited due to the medical emergency.

2024-06-25 Tue: Medical emergency, catching up on Wednesday.

2024-06-24 Mon: Worked on Portfolio's deposit logic. The deposit logic interacts with the (upgradable) Endpoint contract, calling the depositCollateral method. The Endpoint contract was deployed on Harmony Mainnet, but the initialize method has yet to be called. The method receives a sequencer contract address as a parameter, among other nonpublic contracts. The sequencer contract is linked to the order book, which is the main feature of Vertex mixed architecture. To keep working on the mock Vertex Trade app, I'm working on a mock sequencer contract (needs to create Sactions and OffchainExchange mock contracts, too). The only contract of the Vertex contract repo that uses the sequencer is the Endpoint contract. Also, added a mock method to the subaccount mock client.

---
2024-06-20 Fri: Day off

2024-06-19 Thu: Fixed [BigDecimal type issues](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2) with Arbitrum and Harmony chains, and now the Portfolio overview and deposit components are showing USDC assets for the Harmony chain. Kept working on deposit logic for the Harmony chain.

2024-06-19 Wed: Added [HarmonyContract mock](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2) for utility methods that work with contracts through Vertex SDK packages. Kept working on mock methods for Portfolio Overview and deposit components and worked on fixing issues with deposit logic that don't work with Arbitrum and Harmony chains.  

2024-06-18 Tue: Added [TransparentUpgradeableProxy contract](https://github.com/fegloff/vertex-contracts/pull/1) to the Vertex Contract repo. This contract is labeled querier contract on the Vertex monorepo. The contract was found through the Arbitrum explorer and still needs to be deployed due to the implementation contract needing to be included as part of the constructor parameters. The portfolio overview page doesn't present errors on loading thanks to the mock methods implemented, but now working on issues related to fund deposit. Still can't deploy the app due to the Trading View API key. 

2024-06-17 Mon: Talked with Theo regarding the Trading View advance charts key, which is required for the trading module. Added other market and context indexer mock calls for the Portfolio Overview and Portfolio Marging Manager components. Working on fixing the formatTimestamp error that appears when changing to the Harmony chain. 

---
2024-06-14 Fri: Added market, context indexer client, and engineClient mock calls. Fixed nextjs.config file/webpack cache issue. Need a [Traving View advanced charts](https://www.tradingview.com/charting-library-docs/) API key to solve charting_library error that is blocking the App building process.

2024-06-13 Thu: Worked on engineClient, indexerClient, and subaccount mock calls. Had issues with the Trade app's local build. The issue is related to the trading page, which is accessing a dts-bundle-generator module that can't be resolved. Working on workarounds.

2024-06-12 Wed: After trying different approaches to handle the methods specific to the Harmony chain without affecting the functionality of the existing components on Vertex's Trade app (like creating a separate HarmonyVertexClientContextProvider while keeping the existing VertexClientContextProvider), was able to find a more [straightforward approach](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2) that will help a gradual migration of each method that calls Vertex endpoints. On the data package (@vertex-protocol/web-data), created a harmonyClient module that replicates the structure of the VertexClient class but added the isHarmony attribute to check on what chain the app is working and also included the harmonyClient on VertexClientContext, making it available to the whole app. Made changes on a subaccount and quotePrice hooks to call harmonyClient methods if the isHarmony attribute is true. Still had issues deploying the app on fly.io, and testing the build script locally also didn't work (having issues with CSS directives).    

2024-06-11 Tue: Continue working on mocking [Vertex SDK methods](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2). Had issues deploying the current Vertext version on fly.io, working on fixing the configuration issues. 

2024-06-10 Mon: Started working on Vertex Client SDK Mock for Vertex app monorepo and also working to deploy the first version of the Trade App on fe.country.  

---
2024-06-07 Fri: Progress on the Vertex porting to Harmony One has encountered a roadblock due to the Vertex mono-repo's dependency on the Vertex-typescript-sdk for querying and executing data related to spot, perp, market, and contracts. The mono-repo utilizes this package to retrieve crucial information, including portfolio chart data, bridge token balance, spot balance, staking state, account staking state, and latest perp prices, among 125 queries. Additionally, have implemented an [input validator](https://github.com/harmony-one/defi_greeks/pull/1) for all POST endpoints in the defi_greeks API to ensure data integrity.    

2024-06-06 Thu: Deployed defi_greeks API to fly.io. [Added](https://github.com/fegloff/defi_greeks/pull/1 ) fly.io configuration, environment, and logger logic, and also [API_DOC](https://github.com/harmony-one/defi_greeks/blob/main/API_DOCS.md) markdown documentation. Kept working on the Vertex Trade App, but still having issues retrieving account information.

2024-06-05 Wed: Implemented the [first version of the defi_greek API](https://github.com/fegloff/defi_greeks/pull/1) with the following endpoints: _/concentrated-liquidity_ (Calculates greeks for concentrated liquidity positions in DeFi protocols), _/squeeth_ (Calculates greeks for Ethereum power perpetual contract positions), _/calculate_greeks_ (Calculates option greeks based on input parameters) and _/health_ endpoints. 

2024-06-04 Tue: Reviewed defi_greek repo, which contains a Rust library with functions to calculate various risk measures and greeks for financial derivatives, including perpetual contracts, options, and concentrated liquidity positions. Working on enabling a webservice (although I have yet to experience with Rust) that exposes these risk calculation functionalities to other applications, contracts, or systems.

2024-06-03 Mon: Kept working on the Vertex Trade App, reviewing contract handling and external API calls using the @tanstack package. The app is not retrieving any financial information (as expected), but also neither account info (e.g. wallet balance), working on that. Also, [forked](https://github.com/fegloff/defi_greeks) the defi_greeks repo and started reviewing perpetuals/liquidity positions in Rust.

---
2024-06-02 Sun: Working on reviewing the Portfolio page on the Trade app. 

2024-06-01 Sat: Deployed Vertex contracts on Harmony's mainnet and added [multichain deployment support](https://github.com/fegloff/vertex-contracts/pull/1). Linked clearinghouse, spotEngine, perpEngine, endpoint, and arbAirdrop contracts to Trade app. Using this [contract](https://www.coingecko.com/en/coins/harmony-horizen-bridged-usdc-harmony
) for ONE_USDC token 

2024-05-31 Fri: I was sick
 
2024-05-30 Thu: Finished integrating Harmony's [Mainnet and testnet](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/1) as supported chains for the Trade app. Continued working on the Trade app integration.

2024-05-29 Wed: Deployed 1Bot latest changes, and fixed [openai issue](https://github.com/harmony-one/HarmonyOneBot/pull/362) with system message which limits completion to 100 words. Kept working on trade app porting, had progress on enabling harmonyTestnet. 

2024-05-28 Tue: Fixed simultaneous command calls on 1Bot. When commands run simultaneously, the message context could get mixed, and llms model requests get mixed as well. The solution was to create a single endpoint that handles all llms requests and redirects the request to the respective model resource (as python/flask defined namespace architecture) on harmony-llm-api. This solution requires normalizing streaming handling for Vertex/Gemini models on harmony-llm-api and 1Bot. Now, when a simultaneous command request is handled, each model will be managed by the corresponding LLMs. It will be deployed to 1Bot later today.

2024-05-27 Mon: Deployed GPT-4o model to 1Bot. The following commands and prefixes will work with gpt-4o: _/ask, /gpt, /new, and a. and dot prefixes_. The command _/gpt4_ works for gpt4 model and the command _/gpt32_ for gpt-4-32k model. Fixed an issue with edit telegram messages when processing a stream completion. Also, updated Grammy to the latest version (v1.23.1). Finally, still have issues with simultaneous command calls, and successfully tested a solution on the harmony-llm-api backend that will be implemented tomorrow.

---
2024-05-24 Fri: Fixed 1Bot multiple command handling due to context mixing on llms API calls. Also, added the [Openai GPT-4o model](https://github.com/harmony-one/HarmonyOneBot/pull/362), linked to /gpto command.

2024-05-23 Thu: Fixed chains configuration issues. Had issues linking the Harmony chain to the wallet connection on the navigation component; working on it. 

2024-05-22 Wed: Kept working on adding [Harmony chain and One token](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/1) to the Trade App and added HarmonyTestnet chain.

2024-05-21 Tue: Continued working on Vertex's trade app, adding Harmony chain and One token. After Casey's review, sent PR to the Protofire team regarding the explorer block filter and worked on finding the development server issue on the Swap Interface app.

2024-05-20 Mon: Sent [PR](https://github.com/protofire/interface/pull/5) to change tooltip text on Swap Interface (_Network Fee are paid to the ~~Ethereum~~ Harmony network to secure transactions_). This task was delayed due to local deployment issues, which were tested with different node/yarn configurations on Mac M1 and Windows OS, with no success. There is an issue when running GraphQL scripts due to two files missing. The Protofire team sent me the missing files (src/graphql/data/schema.graphql and src/graphql/thegraph/schema.graphql) and the issue was resolved. Also, worked on adding Harmony metadata/token to the Vertex common package and trade app (will send a PR on Tuesday).  

2-Week Deliverables by 2024-05-20:
Finish Claude's tool implementation to have 1Bot ready for the Defi/AI project. Support Hyperlane and Dune implementation and work on the Arbitrum wallet finder. 

---
2024-05-19 Sun: Completed the required explorer updates: _let's not show/flash empty blocks and hide "network utilization_. The changes affect mobile and desktop versions. Sent the corresponding [PR](https://github.com/fegloff/bs-frontend/pull/1) to Casey for review.

2024-05-17 Fri: Finished the required explorer updates: _autofocus on the search input field when loading, remove the red "testnet" label at the left top corner, capitalize "Harmony Testnet Explorer," spell out "txn hash" -> "transaction hash," "ETH" -> "ETH / ONE address," and remove "Dim" mode option_. Sent the corresponding [PR](https://github.com/protofire/bs-frontend/pull/13). 

2024-05-16 Thu: Despite initial challenges with the Explorer local environment, the issue was that I was working on the wrong repo. Once forked the correct one ([protofire/bs-frontend](https://github.com/protofire/bs-frontend), I was able to make progress. Had personal matters to attend to.   

2024-05-15 Wed: Continued working on Vertex's trade app porting and updating the Explorer app. However, had issues with the local environment with the corepack package and am working on fixing it.  

2024-05-14 Tue: Kept reviewing Vertex's trade app architecture/logic. 

2024-05-13 Mon: Deployed all Vertex contracts to Harmony Testnet. Currently, reviewing trade app architecture and looking at how contracts, GraphQL, and API calls are handled.

---
2024-05-10 Fri: Created the first version of the [deploy script for Vertex contracts](https://github.com/fegloff/vertex-contracts/pull/1) to the Harmony Testnet network and added comments to some contracts. Also, deployed locally mono-repo-apps and started checking out trade app architecture.

2024-05-09 Thu: Worked on porting contracts to the Harmony chain, checking all contracts, and creating a deploy script (work in progress). Also, talked with a Protofire representative regarding swap-interface local deployment issues.

2024-05-08 Wed: Started working on Vertex porting; they had a [contracts repo](https://github.com/vertex-protocol/vertex-contracts) and web apps [mono repo snapshot](https://github.com/vertex-protocol/vertex-web-monorepo-snapshot), which includes trade, dashboard, and marketing apps. 

2024-05-07 Tue: Fixed one- and two-letter domain [issues in 1.country](https://github.com/harmony-one/1-country.frontend/pull/217), skipping Web2 registrations because we already control the domains. Also, fixed certificate handling, checking if the certificate needs to be renewed before creating it. After being reviewed by Artem, changes were published. Also, kept working on the swap site update. 

2024-05-06 Mon: Checked the Hyperlance documentation; they provide the contracts on local and remote chains we want to bridge with. Talked with Yuriy about deploying Hyperlane on Harmony. Also, made some text/URL changes on the [Bridge site](https://github.com/harmony-one/layerzero-bridge.frontend/pull/26) and kept working on the requested changes on the Swap webpage.

---
2024-05-03 Sun: Reviewed 1Bot logging logic. 

2024-05-04 Sat: Started working on the tooltip text change on the swap site. 

2024-05-03 Fri: Theo updated me on the next task: I had to work on the Arbitrum network. I also kept revising the Hyperlance and worked on the requested changes on the Harmony Swap site.

2024-05-02 Thu: Tested and deployed token base security to harmony1bot and harmony-llms-api. Disabled translation prefixes on 1Bot, leaving only translation commands available. Reviewed and discussed harmony.one/defi architecture. Started reviewing [hyperlanexyz ecosystem](https://hyperlanexyz.notion.site/Hyperlane-Ecosystem-1e6d8175baf44ed88502cfba91becc45)

2024-05-01 Wed: Included [token-base security](https://github.com/harmony-one/harmony-llm-api/pull/20) for harmony-llms-api endpoint, using bearer scheme and also httpOnly for web app calls. Updated 1bot to use the new security scheme and talked to Nagesh about updating the iOS app. Fixed issues with streaming on anthropic models and the is_supported method on anthropic tools. Changes deployed on 0Bot and harmony-llm-api-dev.fly.dev. 

2024-04-30 Tue: I included the ToolBox class for related tools and added the CoinGecko toolbox with retrieving token prices and token ID tools. It is currently on 0Bot for testing.  

2024-04-29 Mon: Tested and deployed to 1Bot /ctool and /stool commands, which allow access to the Anthropic tool feature. Started working on integrating AI into harmony.one/defi project.

---
**2-Week Deliverables by 2024-04-26:**
Finish harmony1bot mayor refactoring to help integration with subagents and plugins (like voice commands) and add other subagents like PDF parsing. Also, create a demo of [anthropic tools](https://docs.anthropic.com/claude/docs/tool-use) on harmony1bot.

2024-04-26 Fri: Finished implementing the tool logic on [harmony-llm-api](https://github.com/harmony-one/harmony-llm-api/pull/19) and enabled the ticker symbol info retriever tool, which works with multiple ticker symbols. Also finished implementing the logic on [1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/362) and enabled the /ctool and /stool commands. Currently testing on 0Bot. Finally, the /new command logic was updated to refresh the conversation per active bot.

2024-04-25 Thu: Day off due to flu.  

2024-04-24 Wed: Day off due to flu.  

2024-04-23 Tue: Refactored [tools logic](https://github.com/harmony-one/harmony-llm-api/pull/18), enabling multiple tools per call. Created ToolBase, YahooFinanceTool, and AnthropicHelper classes.  

2024-04-22 Mon: Kept working on enabling tools for Anthropics models. I enabled multiple tool calls, e.g., when asking for multiple ticker symbols. Updated Anthropic packager version.  

---
2024-04-19 Fri: Added [tools logic on 1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/362) and /ct command. Created tools endpoint for Claudes models, and kept working on including a ticker symbol tool. 

2024-04-18 Thu: Finished implementing the [/pdf and /ctx commands](https://github.com/harmony-one/HarmonyOneBot/pull/362) and added logic to allow the same command to be shared between different bots. Also, started working on Claude's tool feature. 

2024-04-17 Wed: Deployed the latest changes, including Gemini 1.5 to 1Bot. Started working on adding pdf and ctx commands. I had food poisoning and took the rest of the day off. 

2024-04-16 Tue: Refactored [harmony-llms-api](https://github.com/harmony-one/harmony-llm-api/pull/17) to work with the latest Gemini packages in order to support Gemini 1.5. Also added [/g15 and /gemini15 commands](https://github.com/harmony-one/HarmonyOneBot/pull/362) to 1Bot, and refactored the session object, and deleted unused modules. 

2024-04-15 Mon: The Llama SubAgent now supports [PDF and multiple URLs](https://github.com/harmony-one/HarmonyOneBot/pull/362). It has Been tested with OpenAI and Gemini commands. Also, improved subagent performance by removing unnecessary logic. The Gemini 1.5 model has been checked and is in Preview mode.  

---
2024-04-12 Fri: Improved user prompt to include subagents output and avoid standard openai error "_I'm sorry, but as an AI language model, I don't have the ability to browse the internet or access external websites in real-time_". Also, updated the bot's context to include subagent capabilities. Here is the new context: "_You are an AI Bot powered by Harmony. Your strengths are AI API aggregation for chat, image, and voice interactions. Leveraging a suite of sophisticated subagents, you have the capability to perform tasks such as internet browsing and accessing various services. Your responses should be adaptable to the conversation while maintaining brevity, ideally not exceeding 100 words._". Finally worked on adding the PDF subagent. 

2024-04-11 Thu: Tested new subagent feature and refactored bot modules. [Fixed issues](https://github.com/harmony-one/HarmonyOneBot/pull/362) with multiple URL inquiries, running URL subagent when replying to a message with an URL.

2024-04-10 Wed: Finished refactoring the openai module into a llmsBase-derived subclass; also finished the first iteration of the [web crawler subagent](https://github.com/harmony-one/HarmonyOneBot/pull/362) and deployed it on harmony0bot for testing. Now, every model that has the subagent can include web crawling on its completion. Currently, Gemini and Openai models have it.  

2024-04-09 Tue: Continued working on AI bots refactoring and adding subagent logic.

2024-04-08 Mon: Keep working on the llamaIndex subAgents for harmony1bot.

---
2024-04-05 Fri: Finished openAI, and Dalle bots as a [derived class of llmsBase](https://github.com/harmony-one/HarmonyOneBot/pull/362), added session handling, and kept refactoring AI bots. Started working on llamaAgent (collection handling for PDF and URL) so each AI bot can use it.

2024-04-04 Thu: Added minimum balance to openAI bot for postpaid commands. Continued [code refactoring](https://github.com/harmony-one/HarmonyOneBot/pull/362) on Harmony1Bot to ease subagents integration: added llms bot base class (llmsBase) and claudeBot, vertexBot, and llmsBot derived classes. Will continue with the refactoring of openaiBot and converting PDF/URL logic to an subagent-like class. 

2024-04-03 Wed: Fixed PDF/URL parsing issues due to a vector database client/server version mismatch. On [Harmony1bot](https://github.com/harmony-one/HarmonyOneBot/pull/361), updated Grammy package to the last stable version and made code refactoring to get the latest version of the getChatAdministrators method to fix the database client isGroupWhitelisted method. Had to update the nodejs version to 20 on the Dockerfile. 

2024-04-02 Tue: Fixed the new command logic and the [minimum balance](https://github.com/harmony-one/HarmonyOneBot/pull/361) to use llmsBot models. Also, fixed the token counter for Anthropopic stream completions. Found the problem with the group whitelisting not working. Finally, fixing an issue with Chromadb that affects PDF/URL handling.  

2024-04-01 Mon: Added conversation per model discrimination on [Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/360) (deployed to harmony1bot). Now, you can have one conversation per model. Also added the /o command to work with the opus model. Finally, worked on team reviews.  

---
**2024 Q1 Review (12 hours)**

I added Harmony1Bot features: OpenAI's DALL-E 3, Vision command, and various models from Claude and Vertex. I implemented code snippets support, an Inscription lottery, voice command functionality, and fixed payment logic while upgrading the bot's performance and stream completion. Additionally, I made notable contributions to Harmony-llm-api by adding endpoints for Whisper, Anthropic, PDF inquiry, and Gemini, along with implementing streaming logic.

I contributed to the 1.country project by adding Inscription image rendering for Telegram's Image subscriptions. For the Social Map project, I implemented Whisper logic, added a markers endpoint, refactored the codebase with TypeScript, and improved the app's styling and state management. Lastly, I made enhancements to the Human Protocol project (h.country) by optimizing the Welcome and UserPage route components and improving the app's overall logic.

In optimizing harmony1bot performance, I tackled various technical challenges with targeted features. This included efficiently implementing an image generation queue to handle multiple DALL-E 3 requests and resolving prompt interpretation errors. I also enhanced stream completion for Anthropics and Vertex models, improving user experience by reducing response times. Additionally, integrating voice-command functionality streamlined user interactions, with features such as command reuse improving overall usability and user experience.

---
2024-03-29 Fri: Day off

2024-03-28 Thu: Day off

2024-03-27 Wed: Added the [CV analysis](https://github.com/harmony-one/harmony-llm-api/pull/16) endpoint to harmony-llm-api. The endpoint returns the score with the reasoning and three recommendations. Fixed word cutting in Anthropic and Gemini completion and cleaned token information on the completion response. Finally, checked the completion agents feature for Anthropic. The feature is brand new, but a [GitHub repo](https://github.com/cxbxmxcx/GPT-Nexus) just added the agent logic for [Anthropic](https://github.com/cxbxmxcx/GPT-Nexus/commit/89694a0bb978e0db1f7e00807bf1bb1d227422b6). We can check that and see how we can include it on harmony1bot. 

2024-03-26 Tue: Fixed [Anthropic namespace](https://github.com/harmony-one/harmony-llm-api/pull/15) key issue on the harmony-llm-api backend and fixed the URL params default values on the PDF inquiry endpoint. It now serves ONEResume app. Created the harmony0bot database on [elephantsql](https://api.elephantsql.com/), a free service, to deploy the Gemini command for testing. Also, the [LLM chat conversation](https://github.com/harmony-one/HarmonyOneBot/pull/359) was normalized to avoid errors when passing from/to Claude's and vertex models. Finally, prepared 1Q self-assessment

2024-03-25 Mon: Fixed the [price calculation logic](https://github.com/harmony-one/HarmonyOneBot/pull/359) of the Gemini command on Harmony1Bot (deployed to harmony0bot)  and a [PDF inquiry endpoint](https://github.com/harmony-one/harmony-llm-api/pull/15) to harmony-llm-api to use Claude's models. The endpoint accepts a URL of the PDF file and a PDF object. Anthropic doesn't support embeddings, so all inquiry requests need to include the PDF. In case multiple inquiries are required, we can use the openai embedding endpoint available on harmony-llm-api

---
2024-03-22 Fri: Continue working on generative-models.demo, keep having issues deploying locally and in Google Colab. Also fixed the Gemini command completion text on Harmony1Bot. 

2024-03-21 Thu: Added the generative-models.demo repo to Google Colab to have access to the GPU processor. Also, working on configuring the new environment and adding the a flask endpoint.

2024-03-20 Wed: Keep working on Stable video 3D integration. Have issues installing the model on my Mac M1 (Nvidia-related error). Finished the token counter [on harmony-llm-api](https://github.com/harmony-one/harmony-llm-api/pull/14) and added logic on Harmony1Bot (changes have yet to be pushed to Harmony0bot).

2024-03-19 Tue: Worked on Stable Video 3D, [forked the repo](https://github.com/fegloff/generative-models.demo), set up the dev environment, and installed the model. Also worked on adding a token counter for Gemini requests.

2024-03-18 Mon: Improved [error handling](https://github.com/harmony-one/harmony-llm-api/pull/13) on the harmony-llm-API backend; still need to make some changes on Harmony1Bot to display the proper error message (for instance, Claude's Sonnet model usually returns an overloaded_error but the bot shows "Error handling your request"). [Deployed to Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/358) Opus (/c, /claude, c.), Sonnet (/sonnet, /s) and Hariku (/hariku, /h) commands, and removed emoji on voice command error message. Added the Gemini model to [harmony-llm-api](https://github.com/harmony-one/harmony-llm-api/pull/14) and [Harmony0Bot](https://github.com/harmony-one/HarmonyOneBot/pull/359); still need to add pricing on HarmonyBot to deploy to production. Started reviewing [Stable video 3D](https://stability.ai/news/introducing-stable-video-3d).

---
2024-03-15 Fri: Fixed conversation history, added Hariku model (/haiku, /h), update Anthropic models pricing, and added [stream completion](https://github.com/harmony-one/HarmonyOneBot/pull/358) for Opus and Sonnet models. However, due to wording truncation, kept the Hariku model as rest completion.

2024-03-14 Thu: Added [stream completion](https://github.com/harmony-one/harmony-llm-api/pull/13) support for harmony-llms-api, and fixed the missing Anthropic module error after deploying. Also, updated Opus and Sonnet prices on [Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/357) and started working on stream completion logic. 

2024-03-13 Wed: Fixed Anthropic backend issue with [completion format](https://github.com/harmony-one/harmony-llm-api/pull/13) and working on deploying issues with the anthropic library. Added opus (/claude, /opus) and sonnet (/claudes, /sonnet command) to [Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/357). Fixed AI conversation error after prompt doesn't receive completion, and fixed action message infinite loop after error for LlmsBot and OpenAI bot.   

2024-03-12 Tue: Added Anthropic's Claude create message endpoint in [harmony-llms-api](https://github.com/harmony-one/harmony-llm-api/pull/13). Also, added /claude command on the Harmony1Bot local test environment.

2024-03-11 Mon: Updated the recharge message on Harmony1Bot due to some confusion regarding what token to send the funds. Also [SdImagesBot and QRCodeBot](https://github.com/harmony-one/HarmonyOneBot/pull/356) were disabled due to the shutdown of the Stable Diffusion servers. Finally, worked on enabling [live transcription](https://github.com/harmony-one/1/pull/14) on the Social Map app and configured a test account on the anthropic AI model. 

----
2024-03-08 Fri: Fixed an issue with the Social Map app that sent the [wrong file format](https://github.com/harmony-one/1/pull/13) to the harmony-llm-api for voice transcript.

2024-03-07 Thu: Keep researching Peapods Finance. Here is a good [video](https://www.youtube.com/watch?v=fW87F-l30KI) explaining how the pods work. Also, here is the last [Audit report](https://reports.yaudit.dev/reports/01-2024-Peapods/), but their repo is private. 

2024-03-06 Wed: Started researching Peapods Finance. They do not share the contracts; the only contract shown is their rewarded token, PEAS.

2024-03-05 Tue: Checked Voice AI app functionality after malfunctions reports. Tested the app live and locally, checked the Sentry log where some issues were found, and discussed them with Aaron; they seem to be isolated issues. Will keep monitoring the app in the following days. Also, I worked on a [hotfix](https://github.com/harmony-one/h.country/pull/105) on h.country where a private key import was leaked, and the filter was showing full-text tags.  

---
2024-03-01 Fri: Finished code refactoring and Typescript migration of [ONE Map app](https://github.com/harmony-one/1/pull/12): created ImageCarouselComponent and MemoCarouselComponent, also fixed recording logic.

2024-02-29 Thu: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/103): Updated the logic of the clear query param. Also worked on the following [tasks ONE Map](https://github.com/harmony-one/1/pull/11): Refactored MapViewComponent, by creating MapMarker component while migrating the code to Typescript.

2024-02-28 Wed: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/101): Updated the display of link actions because most of the time, it took two lines to show 0/B1B1 1760886692 x/17608866 (from address, username, type/username). The proposed change shows the address and the type/username info (0/B1B1 x/17608866). Also, updated the action type color, showing blue if the from address is the same as the page wallet address (key) and yellow otherwise. Also, updated the href to navigate to the payload URL; Fixed filter panel when clicking actions' from/to address. Also worked on the following [tasks ONE Map](https://github.com/harmony-one/1/pull/10): Added a UserContext to handle user wallet address, and useStorage hook to handle local storage.

2024-02-27 Tue: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/99): Updated the h.country menu option logic, setting the filter mode to 'All'; updated the selection logic of actions' from/to address, adding the updated page address to the action filter and changing the filter mode to 'address.'

2024-02-26 Mon: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/96): Updated the check-in message display logic. There is an issue with some check-in action messages (when syncUserLocation) that were unable to get the location address information, showing an empty message. For those cases, we can try to fetch the information again (calling the nomination API again), and with a second not successful operation, simply not store the check-in on Firebase. Updated the UserPage action filter look and fee. Added onClick logic to the h.country menu option; when clicked, it navigates to the UserPage with no active filters.

---
2024-02-25 Sun: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/90): Fixed [object][object] rendering on check-in action messages; fixed runtime error on intersection observer; added Firebase doc's ID to Action Type to set a unique key to every UserAction component to avoid continuing rendering. 

2024-02-24 Sat: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/89): Added user's emoji reaction to action messages; added lazy load and intersection observer to handle action list rendering. Also, I worked on [Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/353), where I fixed suffix issues and added one inquiry limitation per image on each chat.

2024-02-23 Fri: Worked on the fowolling [tasks on h.country](https://github.com/harmony-one/h.country/pull/71): Disable scroll horizontally on mobile; make text on the selection page (/hash) bigger; limit 10 chars for a tag, and locations in the hashtag section; limit 15 chars for the tag on message section; fix slash and hashtag icon; remove new user self-tagging; fixed location action message overlap; updated URL char truncation; added geolocation after the third topic selected on the welcome page; fixed menu address rendering.

2024-02-22 Thu: Worked on the fowolling [tasks on h.country](https://github.com/harmony-one/h.country/pull/71): Updated action type (self/other) color logic; updated /new route logic and fixed double wallet creation; fixed font styling (grey color and size); fixed manual topic selection tag type logic; update Grommet theme and styled component styling. Also worked on [SocialMap app](https://github.com/harmony-one/1/pull/8), finishing the following tasks: updated footer styling and marker callout styling. 

2024-02-21 Wed: Worked on the fowolling [tasks on h.country](https://github.com/harmony-one/h.country/pull/55): Updated UserPage styling; fixed tags and URL logos cut off and added isUserPage logic; updated filter panel styling and added #one and @ai filter logic; added a topic selection limit on the welcome page; added rendering logic on the welcome page when the topic query param is set.

2024-02-20 Tue: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/37): Fixed multiple wallet creation after topic selection on the hash route component, which affects actions rendering on the UserPage component. Updated the UserPage route component styling, including the messages section, texts, and styling when no address is set. Updated /hash look and feel and topic list. Updated recurrent user logic on topic selection. Fixed issues when no topic query param is on /hash route. Update redirect logic for new users to /hash route component.

2024-02-19 Mon: Worked on [h.country](https://github.com/harmony-one/h.country/pull/22). Changed the number of topics to select from 4 to 3. Added logic that creates a Tag Action for each selected topic and a Tag Action from the user to himself. Updated slash and hash colors: blue for himself and yellow for others. Pending green for verified type. Updated HeaderList component to show a 3 x 3 grid of tags in order by frequency. 

---
2024-02-16 Fri: Fixed [dark theme logos rendering](https://github.com/harmony-one/h.country/pull/12), and added meta tag logic. Added dark/light theme logic, but leave dark theme on by default. Fixed mobile full screen redering. 

2024-02-15 Thu: Keep working on the [Human Protocol](https://github.com/harmony-one/human-protocol/pull/20) user interface, updating the welcome page look and feel. Refactored Topic's logo prefetch logic. Added the Nunito font and updated the Welcome and Messages route component's styling.

2024-02-14 Wed: Worked on user interface improvements for the [Human Protocol](https://github.com/harmony-one/human-protocol/pull/18) project. Updated the Welcome route component by adding and grouping topics, changing topic container look and feel, and isSelected logic. 

2024-02-13 Tue: Worked on fixing the [Whisper demo](https://github.com/harmony-one/web-whisper.demo) to make it compatible with Chrome and Safari for mobile by updating codec handling for Safari and audio chunks logic. Here is a working [demo](https://webpage-whisper-demo.fly.dev/).  

2024-02-12 Mon: Worked on the [Whisper demo](https://github.com/harmony-one/web-whisper.demo) on React. Finished the first version of the WebApp that records voice memos and uses Openai's Whisper model to transcribe the audio. Also, added a Web Speech API transcribe option.

---
2024-02-09 Fri: [Refacored SocialMap app](https://github.com/harmony-one/1/pull/7), added the src folder modularizing components, updated the markers interface and logic, and added the Posts component.

2024-02-08 Thu: Finished the API call to the [whisper endpoint](https://github.com/harmony-one/1/pull/5). Fixed multi-voice memo recording issue and updated the code logic from expo to react-native CLI.

2024-02-07 Wed: Worked on the whisper endpoint on [harmony-llm-api](https://github.com/harmony-one/harmony-llm-api/pull/12) backend and API call on the [SocialMap app](https://github.com/harmony-one/1/pull/3). Added [markers API](https://github.com/harmony-one/1/pull/2). 

2024-02-06 Tue: Worked briefly on a Farcaster project. Reviewed the best way to implement a [Farcaster Hub](https://docs.farcaster.xyz/developers/) (like an Ethereum node), which is required to create apps on top of Farcaster and started working on a social map app on react-native.

2024-02-05 Mon: Started briefly working on v.country, a website that records and transcribes voice memos using Openai's Whisper modal. Started working on a [Farcaster](https://docs.farcaster.xyz/) implementation. 

----
2024-02-02 Fri: Added censorship check to dalle text and voice command and included content_policy_violation for [openAI](https://github.com/harmony-one/HarmonyOneBot/pull/353) errors. Also, added refund handling on openAIs and voiceCommand bots. Finally, disabled the inscription lottery.

2024-02-01 Thu: Updated Inscription payload to include user info (username, walletAddress); also added logic to delete the [share button](https://github.com/harmony-one/HarmonyOneBot/pull/353) after a successful Inscription. Updated [dot country](https://github.com/harmony-one/1-country.frontend/pull/216) to work with new inscription payload to hide Telegram's bot token. 

2024-01-31 Wed: Finished 1.country rendering of Telegram/Image subscription on [dot country](https://github.com/harmony-one/1-country.frontend/pull/216). Update [Inscription call data](https://github.com/harmony-one/HarmonyOneBot/pull/353) and fix prefix issues with Dalle and Stable Diffusion.

2024-01-30 Tue: Finished [inscription logic](https://github.com/harmony-one/HarmonyOneBot/pull/353) and progess messaging handling for image and prompt inscription on Harmony1Bot. Also, worked on 1.country with the [Telegram's inscription integration](https://github.com/harmony-one/1-country.frontend/pull/216).

2024-01-29 Mon: Worked on integrating [Inscription logic on Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/353). Created the share button and 0-cost transaction with call data and added initial logic. 

----
2024-01-26 Fri: Cleaned the [prompt-generated text](https://github.com/harmony-one/HarmonyOneBot/pull/351/commits/949701af242848e65990691eef4b73499df433c8) on voice command and updated voice command duration up to 30 seconds. Added a [share button](https://github.com/harmony-one/HarmonyOneBot/pull/353) to Dalle's generated images for inscription logic. 

2024-01-25 Thu: Added payment logic for whisper on voice-command services. [Improved user experience](https://github.com/harmony-one/HarmonyOneBot/pull/351) by adding voice command reuse to avoid the user repeating the command on each interaction. Updated the conversation queue to store the output format (voice, text) and msgId (to replace the progress message with the completion).   

2024-01-24 Wed: Added the [image (dalle) and talk command](https://github.com/harmony-one/HarmonyOneBot/pull/351) to the voice-command bot. For dalle, the user has to send a voice note starting with the command image and then the prompt. When a user sends a voice note with the command talk, the AI completion returns as a voice note.

2024-01-23 Tue: Updated the payment logic for pdf/URL web crawling services. Added [voice-command](https://github.com/harmony-one/HarmonyOneBot/pull/351) functionality for chat GPT and vision features. With voice command, the user sends a voice note starting with the command ('ask' for chat GPT, 'vision' for vision) with the prompt, and the bot generates the completion. For Vision, the voice note has to be a reply to an image. 

2024-01-22 Mon: Fixed [payment issues](https://github.com/harmony-one/HarmonyOneBot/pull/350) with dalle and Chat GPT commands. The app was storing the token and price usage for the conversation but was not using the token usage information to calculate the input token price. The new DALLE 3 implementation requires the price to be handled as cents.

----
2024-01-19 Fri: Worked on fixing whitelist issues and payment issues. Fixed [whitelist issues](https://github.com/harmony-one/HarmonyOneBot/pull/350) with private chats and the updated whitelist environment variable. Checked the implementation of whisper on Harmony1Bot. 

2024-01-18 Thu: Fixed new command prefix error when the new prompt was empty. Refactored command handling on openAi, llms, and 1Country. Added [vision completion context](https://github.com/harmony-one/HarmonyOneBot/pull/350) to provide complete responses within a 100-word limit

2024-01-17 Wed: Fixed prompts with a [code snippets](https://github.com/harmony-one/HarmonyOneBot/pull/350) that were handled as URLs and produced an error messages. Fixed an error with vision calls on group chat by requiring vision command on images reply.

2024-01-16 Tue: Added streaming completion to [vision logic](https://github.com/harmony-one/HarmonyOneBot/pull/348). Also, added /vision command that allows the user to inquire about multiple image URLs. Didn't add vision prompts/completions to the bot conversation because it uses different models, and the content key of the body parameter has a different scheme. 

2024-01-15 Mon: Worked on [deleting prefixes with familiar words](https://github.com/harmony-one/HarmonyOneBot/pull/349) to increase user experience; the removed words were 'am', 'be', 'ny', 'ha', 'no' from Translate bot.  [Deployed Vision on Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/348) as a chatCompletion, not as a part of a conversation, due to a different JSON scheme for the content key. On Tuesday, will work on including in the bot conversation the vision's prompt and completion. Also, will add chunk prompting (stream) and /vision command where the user can send an image URL with a prompt.

---

2024-01-12 Fri: Started working on Vision integration. Fixed [i prefix](https://github.com/harmony-one/HarmonyOneBot/pull/347) bug. 

2024-01-11 Thu: Updated [allstats and stats reports](https://github.com/harmony-one/HarmonyOneBot/pull/346) including one-time users. Added [/i command](https://github.com/harmony-one/HarmonyOneBot/pull/345) to dalle-3.

2024-01-10 Wed: Added and updated weekly and total KPIs to the [stats report](https://github.com/harmony-one/HarmonyOneBot/pull/346), working on adding new users report. Worked on adding images command to dalle-3.

2024-01-09 Tue: Added prefixes and commands to the [dalle-3 logic](https://github.com/harmony-one/HarmonyOneBot/pull/345) and updated the SD image logic. Checked the inconsistencies reported on the bot stats report.

2024-01-08 Mon: Integrated [Dalle-3](https://github.com/harmony-one/HarmonyOneBot/pull/345) to Harmony1Bot with session image generation queue and message status.

---
2023-12-25 Mon - 2024-01-05 Fri: Paid time off.

---
2023-12-22 Fri: Added speech recognition (speech-to-text) to [voiceOn prototype](https://github.com/harmony-one/x/pull/412), and worked on [llms endpoint](https://github.com/harmony-one/harmony-llm-api/pull/11). Deployed to HarmontOneBot dev /alias /aliases command implementation.  

2023-12-21 Thu: Sergey and Yuriy help fix local deployment issues of [layer zero bridge](https://github.com/harmony-one/layerzero-bridge.frontend/pull/22). Added [add document endpoint](https://github.com/harmony-one/harmony-llm-api/pull/11) on the llms backend for the VoiceOn prototype. Found a local on-device vector database for [Swift Apps](https://github.com/Dripfarm/SVDB) to be tested for the VoiceOn prototype. Worked on [alias/aliases command](https://github.com/harmony-one/HarmonyOneBot/pull/344) for HarmonyOneBot. 

2023-12-20 Wed: Working on fixing issues with the configuration of the local development environment for layer zero bridge look and feel updates. Configured local development environment for VoiceOn prototype.

2023-12-19 Tue: Started working on [VoiceOn prototype](https://github.com/harmony-one/x/tree/main/voice/x.on), exploring Chromadb embeddings for voice transcript. Also started working on the [bridge styling](https://bridge.harmony.one/erc20) update. Supported 1.country with a domain registration issue.

2023-12-18 Mon: Worked on [AppConfig unit tests](https://github.com/harmony-one/x/pull/404), reaching 90% coverage. Had to create the RelayAuth protocol to enable RelayAuth dependency injection for unit tests.

----
2023-12-15 Fri: Worked on unit tests for [DataFeed class](https://github.com/harmony-one/x/pull/394/) after new refactoring, reaching 98,9% coverage. Also, worked on [AppConfig unit tests](https://github.com/harmony-one/x/pull/396) reaching 84.9% coverage. 

2023-12-14 Thu: Worked on [AppConfig unit tests](https://github.com/harmony-one/x/pull/388). For unit testing, refactored init and loadConfiguration functions and added an extension to help access private methods, waiting on review after AppConfig refactoring. Finally, started working on updating the DataFeed unit tests after the latest DataFeed refactoring.  

2023-12-13 Wed: Worked on unit tests for [DataFeed](https://github.com/harmony-one/x/pull/374) and reached 99% coverage. Had to redo the unit test due to Data Feed refactoring, getting back to 99% coverage. Worked on the ActivityView unit test and had issues creating a MockContext to test the makeUIViewController function. 


2023-12-12 Tue: Added unit tests for [DataFeed](https://github.com/harmony-one/x/pull/370), [TriviaManager](https://github.com/harmony-one/x/pull/355) and ActivityView. Fixed [isSharing](https://github.com/harmony-one/x/pull/361) issues on unit tests build after refactoring.  

2023-12-11 Mon: Fixed build issues on [unit tests](https://github.com/harmony-one/x/pull/344) after OpenAI refactoring. Updated TextToSpeechConverterTests and OpenAIServiceTests unit tests. Also, added trivia ActionType unit tests. Added trivia context to string Catalog. Had issues with AppleSignInManagerTests, but I am still working on it.

---
2023-12-08 Fri: Fixed AppleTests, NetworkManagerTests, and UserTest [unit tests](https://github.com/harmony-one/x/pull/335) after KeychainService class refactoring, also update CreateUser struc adding memberwise initializer initializer. Added [unit tests](https://github.com/harmony-one/x/pull/339) for the ActionsView struct and UserAPI class. 

2023-12-07 Thu: Worked on unit tests for the Voice AI project. Improved unit tests of [AppleSignInManager class](https://github.com/harmony-one/x/pull/330). 

2023-12-06 Wed: Added Custom Instructions, Shortcode Intents and speech recognition texts to [string catalogs](https://github.com/harmony-one/x/pull/318). Worked on UserAPI [unit tests](https://github.com/harmony-one/x/pull/324). Added Custom Modes [trigger logic](https://github.com/harmony-one/x/pull/325) for Voice AI Settings. Also, worked on HarmonyOneBot issues with text-to-voice and translation commands.     

2023-12-05 Tue: Researched language localization for iOS Swift. Finally, implemented a [String Catalog](https://github.com/harmony-one/x/pull/318/) to handle language localization in a single file location. Still need to figure out what to do with the texts-related function on the Texts folder. 

2023-12-04 Mon: Finished working on [Custom Instructions View](https://github.com/harmony-one/x/pull/299). Solved user experience and styling issues, updated the logic to move the user's custom instruction input to System Settings and left Default, Quick Facts, and Interactive Tutor logic on the View. Finally, reverted [Custom Instruction View Unit Test PR](https://github.com/harmony-one/x/pull/305), manually [reverted Custom Instruction View PR](https://github.com/harmony-one/x/pull/308) and updated the More Actions menu.

---
2023-12-01 Fri: Worked on fuzz test research. Also, worked on [Custom Instructions View](https://github.com/harmony-one/x/pull/299). Users can choose between Interactive Tour, Quick Facts, Default Context, or Custom on an Active Sheet look-like view. On Monday, I will work on styling issues and User Interface behavior. 

2023-11-30 Thu: Changed review [requester logic](https://github.com/harmony-one/x/commit/00c11beced436602f8d3a99b2d6c8cb1a4774b5e) for new session button action. Also, I have started to research fuzz testing for swift projects. There are not up to date tools on the market.

2023-11-29 Wed: The PR review showed issues with published attributes that handle button actions, malfunctioning the app. [Fixed](https://github.com/harmony-one/x/pull/255) property published issues, refactored ActionsViewProtocol, ActionsView struct, and MockActionsView class.  

2023-11-28 Tue: Worked on unit tests for [ActionsView struct](https://github.com/harmony-one/x/pull/255): adding reset, play, openSettings, and closures unit tests. Fixed merge issues with the main branch after ActionsView refactoring. The PR is currently in review. 

2023-11-27 Mon: Fixed unit test errors on [AppleTest](https://github.com/harmony-one/x/pull/274) and ActionsViewTests. Added lastButtonPressed, showInAppPurchase [unit tests](https://github.com/harmony-one/x/pull/270) on ActionViewTest (67%). 

---
2023-11-24 Fri: Fixed unit tests build errors on OpenAIModelsTets, AppConfigurationTests, and SettingsBundleHelper class. Added [Unit Tests](https://github.com/harmony-one/x/pull/260) for ThemeManager (100%), ActionsView (65%), UserApi (55%).

2023-11-23 Thu: Refactored Actions View to add ActionHandler [dependency injection](https://github.com/harmony-one/x/pull/255) to ease unit testing. The changes include creating ActionHandler Protocol and ActionHandlerMock class.

2023-11-22 Wed: Fixed premium expiration date format for [settings bundle](https://github.com/harmony-one/x/pull/243). Keep working on ActionsView [unit tests](https://github.com/harmony-one/x/pull/253), and updated test logic after ButtonData attributes changed. 

2023-11-21 Tue: [Joined configuration files](https://github.com/harmony-one/x/pull/241) of target x and target Sun. Now, all shared media will be handled in x\AssetsShared.xcassets file, while each discting media (like the app logo) will be governed by x\Assets.xcassets and Sun\AssetsShared.xcassets. Also, both targets will share the configuration data with x\Info_shared.plist file. Finally, removed the date's seconds value on the premium expiration date and kept working on Unit tests for ActionsView. 

2023-11-20 Mon: Added [local time](https://github.com/harmony-one/x/pull/234) for System Settings and changed custom instruction label and fixed alignment. Worked with Rikako and Nagesh on unit tests and made some updates on ActionsView unit tests (the coverage % will be updated later today). Worked on Store ObservableObject error while running Unit tests. 

---
2023-11-17 Fri: Reviewed removed [rate limit PR](https://github.com/harmony-one/x/pull/199/), Also, added logic for multiple user taps on [Surprise button](https://github.com/harmony-one/x/pull/223) (waiting on review), adding a 0.5 seconds buffer to disable double tap, and after that new request will kill the previous one. Added [Unit Tests](https://github.com/harmony-one/x/pull/199/) for ActionsView (71%), UserAPI (52%).

2023-11-16 Thu: [Optimized mic initialization](https://github.com/harmony-one/x/pull/207) (audioSession/audioEngine) reducing lagging and user words dropping (first words sometimes were missed). Updated UI for [system settings](https://github.com/harmony-one/x/pull/208) (aligning). Worked on [Unit test](https://github.com/harmony-one/x/pull/199) for Actions View.

2023-11-15 Wed: Added [user review request logic](https://github.com/harmony-one/x/pull/193) when the user presses the new session button and the following conditions occur: pressed the button for 10th times and a random function that adds 25% probability returns true. Each time the user reaches the 10th click, the counter resets. With the help of Nagesh fixed issues in my unit test environment, allowing me to work on [ActionsView unit tests](https://github.com/harmony-one/x/pull/199). Created a new OpenAI API Key for Harmony1Bot and updated and tested the new key on the Bot and on the llm-API backend.

2023-11-14 Tue: Fixed custom instructions logic that was not resetting the conversation after custom instructions changes and fixed custom instruction duplicity. Also, fixed pause/play icon responsiveness due to a 1-second delay after the user presses the pause button.

2023-11-13 Mon: Worked on [custom instructions logic](https://github.com/harmony-one/x/pull/179) enabling the user to change the conversation context. Created app settings to store conversation context and added a Reset toggle switch to reset custom instructions to the default message. One thing to consider with the app settings is that it doesn't have a button (to replace the Reset toggle switch), and the input text field is too short for the default custom instruction text. Also, update the app font to [Dotrice Bold](https://github.com/harmony-one/x/pull/184).

---
2023-11-10 Fri: Fixed _required condition is false: IsFormatSampleRateAndChannelCountValid(format)_, added Persistence and OpenAIResponse [unit tests](https://github.com/harmony-one/x/pull/160), and Speech Recognition [unit tests](https://github.com/harmony-one/x/pull/167)   

2023-11-9 Thu: Added [unit tests](https://github.com/harmony-one/x/pull/156) for ActionHandler and AppConfig classes.

2023-11-8 Wed: Added unit tests for [getTitle](https://github.com/harmony-one/x/pull/150) (surprise Action type), Message model, and added reset and surprise action handler [unit tests](https://github.com/harmony-one/x/pull/151).

2023-11-7 Tue: Added press/hold button logic and updated say more button on [blackred Theme](https://github.com/harmony-one/x/pull/128). Finished [theme logic](Tue: https://github.com/harmony-one/x/pull/124) to ease look and feel testing. The logic includes press/hold effects for buttons, icons, and labels.

2023-11-6 Mon: Worked on play/pause transition after [button pressed](https://github.com/harmony-one/x/pull/126) and also worked on the new [red/black look and feel design](https://github.com/harmony-one/x/pull/128) and pressed/unpressed logic due to button transition and adding new foreground colors.  

---
2023-11-3 Fri: Added basic [theme logic](https://github.com/harmony-one/x/pull/124/) to help look and feel color changes. This PR adds nothing to the phone's layout because it takes the theme from AppConfig.plist. The theme changes can occur by voice commands from the user.   

2023-11-2 Thu: Worked on the user interface [look and feel](https://github.com/harmony-one/x/pull/124/commits/fac6e12cfd884974c4947fd89269ce9df6805f6e), testing new Figma designs.

2023-11-1 Wed: Fixed group whitelist and image issues (the later with the help of Yuriy) on Harmony1Bot. Updated [Voice AI context](https://github.com/harmony-one/x/pull/89), including directives, also updated Wikipedia prompt.

2023-10-31 Tue: Created unit test for Context and messages for [OpeanAIStreaming service](https://github.com/harmony-one/x/pull/102). Check group admin/owner whitelist issues and /image issues on HarmonyOneBot. 

2023-10-30 Mon: Change home grid button spacing and font size to match Figma design. Added custom instructions to message context. Update context and custom instructions to streaming functionality. Started working on the unit tests for OpenAiService module
(Implement unit testing for - OpenAiService (Context) & OpenAiService (Streaming))

---
2023-10-27 Fri: Added conversation context and updated user interface on [Voice AI app](https://github.com/harmony-one/x/pull/83). Worked on fixing harmony1Bot /vkom command.

2023-10-26 Thu: Fix conversation history issues and merge to the main branch. Fixed mobile testing issues. Update Hey Frank to the latest app version. Started working on improving audio streaming on Hey Frank

2023-10-25 Wed: Implemented conversation history for [iOS app](https://github.com/harmony-one/x/pull/70/). Had issues testing it on my mobile (working on fixing it).

2023-10-24 Tue: Merged subscription logic to master branch on [stripe-payments-backend](https://github.com/harmony-one/stripe-payments-backend/pull/4). Added subscription status logic on the Discord bot. Deployed Hey Frank ios app. 

2023-10-23 Mon: Added subscription handling on [Discord bot](https://github.com/harmony-one/harmony-discord-bot/pull/1) and [stripe backend](https://github.com/harmony-one/stripe-payments-backend/pull/4). Regarding 1bot development, the top 3 tasks are as follows: 1) Finish fiat payment on Discord bot (16h), 2) Upgrade voice transcription/summary using llama-index vector database to improve summary and allow the user to inquire about the voice transcript (12h), 3) Implement Dalle 3 when available (10h), 4) (optional) Migrate ChromaDB (vector database) to the hosted solution when available (4h).

---

2023-10-20 Fri: Keep working on fiat payment for the Discord bot in a [subscription model using stripe](https://github.com/harmony-one/stripe-payments-backend/pull/4)

2023-10-19 Thu: Keep working on fiat payment for the Discord bot. Added customer creation to the user/create endpoint. Added user/guild (server) logic on discord bot.

2023-10-18 Wed: Added [group whitelist handling](https://github.com/harmony-one/HarmonyOneBot/pull/342) for HarmonyBot. When a user of the whitelist is the owner or an admin of a group, that group is whitelisted. Keep working on fiat payment for the discord bot, integrating the payment functionality to the existing stripe-payment-backend, and defining the architecture of the image subscribing model for discord users.  

2023-10-17 Tue: Added * prefix/alias for handling inquiries to the [current context (URLs/pdf)](https://github.com/harmony-one/HarmonyOneBot/pull/341). * alias works along /ctx command. Fixed /pdf issues after merging to the master branch. Made changes to the conversation array for llama-index inquiries. Worked on stripe payments backend for discord bot.  

2023-10-16 Mon: Deployed and integrated harmony-llm-api to harmony1Bot. Refactored discord bot, adding command cogs (image and payment), error handling, and basic balance logic. [harmony-discord-bot](https://github.com/harmony-one/harmony-discord-bot). 

---

2023-10-13 Fri: Deployed a hosted Chromadb server for the production environment and fixed collection storage issues for document (URL/PDF) inquiries. Keep working on the discord bot. 

2023-10-12 Thu: Fixed dependencies issues with [harmony-llm-api-dev server](https://github.com/harmony-one/harmony-llm-api/pull/10). The server has llama-index required improvements. The improvements will be tested and published in the production environment on Friday morning. Started working on the discord bot to allow fiat payments.

2023-10-11 Wed: Fixed PDF/URL automatic processing on group chats. Added URL invalid handling. Deployed dev server for llm-api backend.

2023-10-10 Tue: Added gpt-3.5-turbo to llama-index collection handling. Also, added PDF invalid handling and improved completion error handling. Fixed the flyio deployment issue that keeps restarting the server [in review](https://github.com/harmony-one/harmony-llm-api/pull/10). 

2023-10-09 Mon: Added completion message length error handling [complete](https://github.com/harmony-one/HarmonyOneBot/pull/337). Added 5 min processing time to PDF and URL collection processing to avoid unlimited requests to the backend [in review](https://github.com/harmony-one/HarmonyOneBot/pull/338).
