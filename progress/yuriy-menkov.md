2025 Q4 planning

Continue development of analytics scripts for precise calculation of IL, profit, IRR, and optimal strategy search. Testing through running multiple bots, collecting statistics, as well as using historical data and simulations.

Development of the Aerodrome monitoring service for dynamic monitoring and analysis of bot performance, as well as real-time comparison of multiple bots/wallets. Adding a user interface and report visualization for strategy comparison.

Further development and improvements of the Snapshot x Harmony project. Adding new features such as automatic exclusion of low-activity validators from quorum, integration of governance voting into the staking interface, and more.

---

2025 Q3 Review

[Aerodrome Monitoring Service](https://github.com/harmony-one/aerodrome-analytics)

[Snapshot X on Harmony](https://gov.harmony.one/)

Aerodrome Base data verification, including fee checks, dataset validation. Developed and [launched](http://193.233.19.102:8081/api) the Aerodrome [Monitoring Service](https://github.com/harmony-one/aerodrome-analytics), which aggregates contract event and subgraph data into wallet- and position-level statistics. Integrated the service with a custom RPC node and subgraph, and validated its results against external sources such as Dune and custom transaction-level calculations.

Testing of different approaches to identify the most effective strategy: Testing different approaches to identify the most effective strategy: Based on a 3-month analysis of aggregated data (staking events and subgraph positions) from the Aerodrome service, I found that the highest APR is achieved by wallets that open very short positions (typically under an hour) within a narrow range of 100, with most activity concentrated in just a few wallets, while the majority of overall profit is generated through staking. The problems I encountered were that some of the data did not fully match the data from Dune, different method for calculating IL, and it was not entirely clear how to detect a strategy based on list of positions and whether other wallets were using hedging.

[Migration](https://github.com/harmony-one/sx-monorepo) and launch of Snapshot X on [Harmony](https://gov.harmony.one/): deployed contracts, refined and launched the API service, updated and adapted the UI along with related libraries. The project also gained new features — including a validators-only whitelist strategy, a two-stage voting system with an off-chain second phase, integration with the staking dashboard, customizable quorum rules, and more.

---

2025-09-25 Thu: Worked on adjusting the analytics script for cases when position opening/closing and swap operations occur within the same block — it’s necessary to take transaction index into account, and ensure that the swap event log index comes after the mint/burn/collect events.

2025-09-24 Wed: Updated the analytics script with functionality to find and load the initial cbBTC price from the closest swap event to the mint event of position creation. Currently testing and comparing results with the team’s outputs.

2025-09-30 Tue: Updated the script to include retrieval and calculation of the sbBTC price from the nearest swap event at the time of position closure. For IL calculation, I now apply the individual cbBTC price specific to each position at its closing moment. [Exported](https://docs.google.com/spreadsheets/d/1cpnS6IZDzsmK1Zh1bFJSPYsr8R-2tAHYVhucprJEjec/edit?usp=sharing) the results into a summary table for further analysis with team.

2025-09-29 Mon: [Upgraded](https://github.com/harmony-one/aerodrome-analytics/blob/main/research_scripts/getFullStats.js) the script for calculating IL both by individual positions and for the entire wallet, using a fixed BTC price across all positions, followed by a comparison of the results with the team’s data. Current result is 

---

2025-09-26 Fri: Researched Aaron’s data with fees by positions — overall, results matched completely except for minor discrepancies caused by rounding differences. Explored different approaches to loading the BTC price for IL and profit calculation in USD. Created a script that takes the price from the pool based on the swap event closest to a given date or block. Encountered an issue with pool indexing in the custom version of the subgraph — it seems that the official sources are partially outdated and no longer relevant. Worked on fixing the problem.

2025-09-25 Thu: Investigated the reasons for the discrepancy between the collected fees in Aaron’s and Rika’s data and the subgraph data (used events fron different contracts with different rounding). Wrote a script to calculate wallet balance changes based on deposit and withdraw position events.

2025-09-24 Wed: Completed a script to calculates the total fee profit per wallet per date range. Tested with Artem’s wallet and conmparing with Dune data. Result: 0.00059325 cbbtc + 68.531645 usdc. 

2025-09-23 Tue: [Added](https://github.com/harmony-one/aerodrome-analytics/tree/main/research_scripts) statistic by wallet and script to get all positions with fees by address using etherscan api and subgraph. To link addresses to subgraph positions, we first obtain a list of transactions via the etherscan API and then download the positions based on them.

2025-09-22 Mon: synced on team progress over last week, working on wallet statistic by subgraph data with subgraph query.

---

2025-09-15 to 2025-09-19: paid time-off

2025-09-12 Fri: Updated the gov.harmony.one service vote counting algorithm: changed to 50%+1 of total stake wight to reach quorum, and 66.67% of those to vote. Checked the conclusions and statistics for wallet 0x751140b83d289353b3b6da2c7e8659b3a0642f11 (especially for staking indicators) - to confirm the conclusions on the strategy.

2025-09-11 Thu: Studied the strategy text on fee optimization and delta hedging. Looked on the challenges of managing delta drift and ways to smooth it to avoid excessive hedge adjustments. Reviewing new inputs from Steven and Philip; The improvements for the gov.harmony.one release: the disclaimer, favicon, texts etc have been updated.

2025-09-10 Wed: Improvements to customize the graph for indexing selected pools. Studied the mechanics of fee calculation for virtual positions and how state tick values are emitted in swap events, based on Aaron’s new inputs. Tried a new calculation approach using indexer data.

2025-09-09 Tue: Synced with Artem regarding bot improvements. Researched the issue of updating LP state. When closing a position (closeLpPosition), it is necessary to take data from the emitted events (Collect, Burn), as they provide the most accurate information (instead of monitorPosition).

2025-09-08 Mon: Improvements to the subgraph on a custom RPC node — worked on fixing the issue of excessively long indexing by optimizing the code with a filter for specified liquidity pools (cbbtc only). Configured outline client on aerodrome monitoring service to have direct rpc node connection.

---

2025-09-05 Fri: Harmony napshot x has been deployed on gov.harmony.one, and we’ve started beta testing with validators and community. Also updated and released a new version of hmy-snapshot-cli with the ability to create proposals.

2025-09-04 Thu: Expanded the aggregated data of the aerodrome statistic service with a new formula for calculating impermanent loss. Testing the service data against Artem’s bot statistics. Bug fixing for snapshot x.

2025-09-03 Wed: Worked on launching snapshot-x to production — set up the project and deployment via netlify, updated the contracts, updated and redeploy api serivice on fly.io. 

2025-09-02 Tue: Added support for displaying staking validators in the snapshot-x interface: auto-detecting the validator’s image and name from the participant’s address, link to the staking dashboard, etc. Working on migrating the Aerodrome stats service indexer to a server with a Base node to improve performance and enable the use of verified data.

2025-09-01 Mon: Added a role-based system for snapshot x: a manager who can create spaces; validators who can create proposals and vote; and regular users who can only vote in the main space. Also added role support in the interface and set up separate deployments/domains for different participants.

---

2025-08-29 Fri: Attempted to integrate the Aerodrome statistics service with a subgraph on a custom node: updated the request format and data interfaces. Downsides: access only via VPN and slow load speeds; to resolve this, the service needs to be moved to the same server.

2025-08-28 Thu: Tested a subgraph deployed with a custom base node and compared historical data with Dune. Swaps match, but daily profit still doesn’t. Also worked on adding new features for Snapshot X — convert voting power to ONE and display the real validators’ total stake as VP.

2025-08-27 Wed: Comparison of statistics for cbbtc pools by swap/day and all-time between Dune and Aerodrome’s official subgraphs. At a high level the numbers don’t match — analyzing simple swaps and fees, as well as the counting methodologies, to determine the causes of the discrepancies.

2025-08-26 Tue: Testing a custom Base RPC node; researching and selecting subgraphs and indexers to collect position data for Aerodrome Finance pools on a dedicated server: researching and testing the official [indexer](https://github.com/velodrome-finance/indexer) for Aerodrome and Velodrome; the official “aerodrome-base-full” [subgraph](https://github.com/metastable-labs/subgraph).

2025-08-25 Mon: Snapshot-x feature tweaks: display the quorum block as a progress bar for both voting steps; add icons and links to the validator list; fix the recalculation of voting results for the 2nd off-chain step.

---

2025-08-22 Fri: Added a new space for snapshot-x with the ability to vote using the “vanilla” strategy and to create proposals using the “validators only” strategy. Synced with Artem on the core of the APR simulation model.

2025-08-21 Thu: Worked on launching verified subgraph for complete ingestion of aerodrome pools swaps and positions, enabling reliable verification and fully transparent computation of fees and trading volume. Synced with Ulad to connect to our own Base archival node and to accelerate the subgraph sync and ingestion of data from Aaron’s scripts.

2025-08-20 Wed: Collecting statistics on aerodrome positions via Aaron’s scripts — tried locally, but the process is too long due to the large number of requests to the RPC node. Working on deploying the service on a separate server with a connection to a custom Base RPC node. Sync with Artem regarding development of a simulation model for Uniswap v3 LP positions’ APR: calculating APR depending on range, trading volume, price volatility, etc.

2025-08-19 Tue: Comparison daily statistics (lp liquidity volume and total profit in USD) between the aerodrome monitoring service and the dune service. Researched the possibility of extending the Snapshot X engine to add statistics on validators who didn't voted, with subsequent exclusion of them from voting to enable reaching quorum without inactive participants.

2025-08-18 Mon: Exported positions data and converting it to a new format with preserved significant digits to enable verification of APR calculations in Excel spreadsheets. Also working on a script to compare data from the aerodrome monitoring service with data obtained from Aaron’s scripts and stats from Dune service.

---

2025-08-15 Fri: Made several improvements to the aerodrome monitoring service: expanding the API with filters by event name to exclude unnecessary events when integrating with the backtesting service. Worked on creating indexes to speed up database queries. Synced with Artem about developing a time-series simulation model of positions APR and impermanent loss (IL) based on input parameter set. 

2025-08-14 Thu: Worked on calculating APR and other per-wallet statistics for the pool with tick 100, using a year of data (over 3 million events). Also attempted integration with Aaron’s lp data—computing fees from transfer/mint/burn events—for more accurate, ground-truth results without relying on the subgraph.

2025-08-13 Wed: Researched backtesting scripts and repositories from Aaron. Comparing the results of the exported aerodrome pools date by Aaron and the results of the monitoring service.

2025-08-12 Tue: Finished configuring a new instance of the aerodrome service monitoring service for the usdc/cbbtc 100 pair for full unloading of historical data of position events for the year. Was engaged in optimization for real-time calculation of data on positions - since the number of positions for the year is more than 3 million and it is impossible to make calculations through a one-time loading into memory - used the approach with unloading by batches and saving intermediate results in the database.

2025-08-11 Mon: Worked on exporting and aggregating by wallet data, including calculating average APR, average position duration, etc. Deployed a multi-indexer for events across multiple gauges. Working on an API extension for the aerodrome monitoring service.

---

2025-08-08 Fri: Started working on extending the Snapshot X voting engine to add a second off-chain voting step, based on an online calculation of votes proportional to the share of tokens delegated in staking.

2025-08-07 Thu: Worked on exporting and preparing data for USDC/cbBTC positions over the past 90 days, followed by daily breakdowns and compilation of statistics such as average APR, number of positions, average holding time, etc. Most positions open within a minute with fast withdrawal of staking rewards.

2025-08-06 Wed: Reviewed and researched repositories and tasks related to Harmony multisig from Gnosis Safe. Enhanced Snapshot X functionality to enable adding a custom quorum expressed as a percentage proportional to the total stake.

2025-08-05 Tue: Researched and designed the architecture for a two-stage voting system based on Snapshot X: the first stage is on-chain, and the second stage is off-chain, with real-time vote result updates proportional to the distribution of validator delegations.

2025-08-04 Mon: Synced with Artem regarding backtesting service. Added new settings to the monitoring service (including filters and sorting by APR, deposit size filter, etc) to export top Aerodrome pool positions to generate realtime stats.

---

2025-08-01 Fri: Synced with Artem on the latest version of the bot and backtesting, tested the latest version of the portfolio manager using docker-compose, and verified position profit via the monitoring service. Also worked on testing and fixing UI bugs for snapshot x.

2025-07-31 Thu: Explored the possibility of modifying the voting strategy at the contract level to replicate the original Harmony voting behavior — specifically, allowing for a stake check on validators at the end of the voting period. (This enabled users to re-delegate their stake during the two-week voting window to validators whose views aligned with their own). Continuing to work on custom execution strategy.

2025-07-30 Wed: Adding new filters to the Aerodrome Monitoring Service API: classic pagination and date/epoch filters for positions and events api's. New parameters have also been added to the pool hours data.

2025-07-29 Tue: Fixed a data indexing bug for proposals in the Harmony Snapshot X indexer. Continuing work on a custom execution strategy to finalize voting upon reaching quorum.

2025-07-28 Mon:Worked on expanding the aerodrome monitoring service by adding indexing for another cbbtc pool. Currently working on filters for the monitoring service API. Also conducted research on developing custom execution strategies for Harmony Snapshot X — the goal is to enforce quorum checks (50% of total stake weight at the time of the snapshot).

---

2025-07-25 Fri: Updated the Harmony Snapshot X [interface](https://sx-harmony.web.app/#/explore): added restrictions on selecting networks and voting strategies when creating a space, and introduced a custom "Validators Only" strategy. Now, a one-time snapshot of validators and their voting power is taken when the proposal is created.

2025-07-24 Thu: Tested a new validators voting strategy integrated with the interface and relayer. Fixed errors in synchronization and contract logic. Started working on a custom snapshot-x harmony CLI.

2025-07-23 Wed: Updated smart contract for the validator voting strategy — new methods were added for data storage (called via the relayer), role-based access control was implemented, and array value retrieval was added. The new voting strategy was tested via the ui interface.

2025-07-22 Tue: Development of a relayer service for the Snapshot x Whitelist strategy — required for fetching validator list and their amounts. The service queries data via the Staking Explorer API and uploads it to the strategy smart contract.

2025-07-21 Mon: Deployed aerodrome finance pool monitoring service on a dedicated [server](http://193.233.19.102:8080/api#/events-loader/LoaderController_getInfo). Worked on autostart and status check scripts. Worked on the client side for convenient integration of methods into other applications and bots.

---

2025-07-18 Fri: Tested the read-only functions of the Harmony staking precompiles to get validators data via a contract. Based on this [reward](https://talk.harmony.one/t/harmony-read-only-staking-precompile/12720) and this [pull request](https://github.com/MaxMustermann2/harmony-staking-precompiles/pull/3). Tested contract deployment and method calls from solidity as well as via web3. The goal is to use read methods in snapshot x voting contracts.

2025-07-17 Thu: Deploying the aerodrome monitoring service on AWS machines with a configured PostgreSQL database (since fly io's capacity is insufficient to load and calculate current statistics). Performed local testing of sx-cli and attempted to implement wallet usage from a file, similar to hmy-cli.

2025-07-16 Wed: Worked on a corrected AERO rewards calculation — previously, rewards claimed before a withdrawal were not accounted for. Added logic to track intermediate claimRewards events and allocate their amounts across active positions.

2025-07-15 Tue: Extracted the Aerodrome [analytics service](https://github.com/harmony-one/aerodrome-analytics) into a separate repository. Added features for local deployment, including commands for starting and configuring the database, displaying load statistics, and in-memory analytics of loaded data. Shared the setup with Artem for joint testing.

2025-07-14 Mon: Researched the Snapshot X ecosystem for CLI-based voting — including ready-made [MVP solutions](https://github.com/snapshot-labs/sx-cli) and custom implementations using the SDK. Also explored the possibility of accessing validator stake weight within a smart contract for a custom voting strategy, based on the Harmony Read-Only [Staking Precompile](https://talk.harmony.one/t/harmony-read-only-staking-precompile/12720).

---

2025-07-11 Fri: Reviewed the optimal LP Rebalancing Strategy for Aerodrome cbBTC/USDC added by Artem, and discussed key integration points. Made improvements to the Aerodrome analytics service — fixed position close date detection and optimized the performance of the analytics generation function.

2025-07-10 Thu: Synced with Artem regarding the analytics API service and the required analysis. Worked on setting up filters to obtain more accurate median values (since there are many noise positions with 0% APR or very small deposits). Added APIs for retrieving tick-level statistics and grouping by ticks, including min/max price boundaries.

2025-07-09 Wed: Splited the analytics system into three services (to support a larger number of pools and positions): data collection, data aggregation and computation, and an API serving statistics based on the processed data. Deployment setup and testing are in progress.

2025-07-08 Tue: Setting up and deploying the service with the database on Fly.io, testing and refining based on core use cases. Additional improvements for Snapshot X.

2025-07-07 Mon: Started work on integrating a postgress db into the analytics service (for storing events and positions data) to speed up analysis and enable fast loading of historical data, as fetching directly from on-chain events and subgraphs can take up to an hour and is limited. 

---

2025 Q2 Review

Development of [Shadow/Aerodrome](https://github.com/harmony-one/shadow-pool-analytics) positions stats tracker scripts

Advanced analytics and research on yield strategies. Collected and analyzed extensive statistics across USD and BTC pools (Aerodrome, Beefy, SwapX, Shadow, Spectra). Developed multiple scripts to calculate APR, impermanent loss, and time-in-range per wallet. Built datasets with over 50,000 positions. Exported and organized raw data from subgraphs and contract events. Grouped LP strategies by parameters (cutoff, buffer, rebalancing gap), including VFAT and Ichi Vaults. Shadow and VFAT strategy tracking services. Launched shadow-pool-analytics with real-time wallet stats and APIs. Built backend tools (NestJS + Swagger) for LP tracking and rebalancing analysis.

Estimated APR sources for high-yield Aerodrome pools (cbBTC/USDC, cbBTC/WETH). Separated APR sources: trading fees, staking rewards based on contracts events. Explored delta-neutral BTC strategies with Theo & Artem; initiated integration plans with Hyperliquid perps and CLI MVP spec.

Tools for calculating pool shares and dynamic yield (aerofrome): based on the combination of historical data (contract events, subgraph data) and data retrieved from the contract at the time of the request (wallet positions, staking earned, swap fees) - then averaging across positions, or analytics for specific positions. Available through the application or API (under development).

Improved bridging: resolved stuck assets and redeployed contracts (e.g. $AXS, USDC.e) for Unify Bridge. Researched BSC RPCs and began debugging LayerZero V2 universal bridge with dynamic token mapping.

---

2025-07-04 Fri: Made improvements to the extended validator voting strategy (put it on pause for now until sync with Theo. Switched to working on backtesting tools for Artem's bot application.

2025-07-03 Thu: Completed the basic version of Snapshot X for Harmony. Improved the indexer to run through a Docker container and connected it to the internal Fly.io database. The indexer and GraphQL API are available [here](https://hmy-snapshotx-api.fly.dev/). Deployed the frontend [demo app](https://sx-harmony.web.app/#/explore) — with all basic strategies and core functionality: creating spaces, proposals, voting, etc.

2025-07-02 Wed: Sync with BTC strategy team. Resolved issues with the snapshot x indexer - added compatibility with harmony chain in the core library (the number of requested logs was adjusted). Setting up deployment on fly.io, there is still a problem with resource limitations, it may be necessary to set up deployment on an aws machine.

2025-07-01 Tue: Synced with Artem regarding the integration of analytics tools with other strategy management services. It was decided to make a number of improvements to provide API in a specific format: custom LP range, backtesting with rebalancing, support of different pools to test. Continue work on custom validator voting strategy contract.

2025-06-30 Mon: Finished improvements for the indexer and API services. Worked on deploying the postgreSQL database and the indexer to fly.io. Started developing a contract with a custom validator voting strategy based on a whitelist strategy contract.

---

2025-06-27 Fri: Paid time off

2025-06-26 Thu: Worked on adding Harmony chain support to the indexer service and graphQL api. Set up the indexer deployment. Synced with Theo regarding [custom](https://docs.snapshot.box/snapshot-x/protocol/voting-strategies) voting strategies for validators - the working approach seems to be extending the on-chain whitelist strategy contract, with the validator list being stored via a contract method call.

2025-06-25 Wed: Added support for the Harmony chain to the UI frontend repository. Deployed a [demo](https://sx-harmony.web.app/#/explore?p=snapshot-x&n=harmony) version of the frontend. Currently, the available functionality is limited to creating new spaces using four strategies. Displaying the created spaces requires an indexer and API, which are still being configured and deployed.

2025-06-24 Tue: [Finished](https://github.com/harmony-one/sx-evm/blob/main/deployments/harmony.json) deploying Snapshot X contracts on the Harmony chain. Currently working on setting up and integrating the remaining services — frontend and backend.

2025-06-23 Mon: Researched SnapshotX repositories and documentation. Checked these two repos: [sx-monorepo](https://github.com/snapshot-labs/sx-monorepo) and [sx-evm](https://github.com/snapshot-labs/sx-evm) to evaluate the possibility of deploying and configuring them on the Harmony side. It looks like some interface tweaking will be required, but overall, everything should work out of the box.

---

2025-06-20 Fri: Researched Aaron's project and souces. Tried to use and test on main cases: hyperliquid real-time position and price tracking, end-to-end strategy execution. Checked real-time price monitoring modules for Deribit, Aerodrome.

2025-06-19 Thu: Researched portfolio manager app by Artem: testing cases for hedging impermanent loss using Hyperliquid perpetual futures and automating position management. Reviewing the code for potential integration into the delta hedge CLI.

2025-06-18 Wed: Sync with Theo and Li for the next goals. Started diving into Artyom's and Aaron's projects. Look at the main user cases of the MVP delta hedge CLI. Planning the architecture for integrating Aerodrome and Hyperliquid.

Expectations, complete deep dive into Artem and Aaron's code and putting the Hyperliquid and Aerodrome implementations together. Completed product requirement document for our DeltaHedge minimal product, with CLI interface.

2025-06-17 Tue: Research and bug fixing of the bridge explorer related to RPC polling and integration with the LayerZero API. Switched to reviewing and refining the LP tracking scripts and open hedge on Hyperliquid.

2025-06-16 Mon: Made several fixes in the stats calculation scripts related to accounting for impermanent loss during price increase. Published a new version and shared it with Philipp. Continuing work on the API wrapper service for dynamic user position calculation.

---

2025-06-13 Fri: Updated the reports with statistics for the aerodrome btc pool: added data from the last two weeks (good volatility for calculating impermanent loss), split the APR into several columns — from staking, from trading fees, and from price appreciation/depreciation. Working on the report description for Philipp.

2025-06-12 Thu: Finished the script for dynamic analysis of status, data, and APR of staked positions by user address. Currently working on an API wrapper service to enable calls by rest requests.

2025-06-11 Wed: Continue develop a service for dynamically tracking a user’s aerodrome finance position status: potential APR based on their share in the pool’s gauge, the gauge’s total yield, and the amount of impermanent loss.

2025-06-10 Tue: Researched the issue with the Binance Smart Chain RPC used in the bridge explorer (as requested by support). I reviewed both public and private BSC RPC options, but unfortunately, they are not suitable due to limited request quotas and reliability. Setting up a dedicated node via QuickNode appears to be the best solution.

2025-06-09 Mon: Developing scripts to calculate real-time APR for a wallet on aerodrome. The idea is to estimate the user’s expected share of the weekly AERO rewards distributed to the pool’s gauge, based on their proportion of the total staked liquidity. 

---

2025-06-06 Fri: Synced with Theo about best range and BTC yield strategies - that another iteration of the analysis of the Aerodrome pools is required, along with a partial modification of the scripts for aggregating positions by wallets, in order to obtain more accurate statistics closer to the platform's data, with over 100% APR to to understand more precise parameters of the strategy.

2025-06-05 Thu: Continue the analysis of [Hyperliquid](https://hyperfoundation.org/) to check positions to profitable based on short and long rates: comparison of rates, calculation of break-even point, time horizon consideration. Creating new positions without analyzing historical data.

2025-06-04 Wed: synced with Theo regarding the stats we're getting for the USDC/cbBTC positions — the most popular tick range is from -68,000 to -66,000 (20% range), with an APR of 5.3% and an average position duration of ~8.70 days. However, the biggest USD profit comes from price changes due to high volatility. Working on the issue of merging user positions when different staking mechanisms are used.

2025-06-03 Tue: Added more stats and raw [data](https://github.com/harmony-one/shadow-pool-analytics/tree/main/aerodrome/export_USDC_cbBTC) on the liquidity pool. Switched focus to researching long and Short BTC perp via [Hyperliquid](https://hyperfoundation.org/).

2025-06-02 Mon: Fixed the issue with APR calculation by anchoring it to the token prices at the time of deposit and withdrawal, as well as accounting for changes in the reward token’s price at the time of withdrawal. Made adjustments for both types of positions — those staked in clGauge and those held directly by the user.

---

2025-05-30 Fri: Working on a mechanism to determine how rewards relate to specific positions and to organize positions by timeframe, in order to identify entry and exit positions times with reference to BTC prices and calculate impermanent loss. Switched to reviewing and testing the [scripts](https://github.com/lijiang2087/bitcoin) for creating BTC liquidity pools from Li.

2025-05-29 Thu: Additionally [exported](https://github.com/harmony-one/shadow-pool-analytics/blob/main/aerodrome/export_USDC_cbBTC/rewards_USDC_cbBTC.jsonl) the reward events for staked positions in clGauge. Since the contract sends rewards for all of a user's positions at once, it's only possible to accurately determine the APR for individual staked positions. Working on updating the calculation scripts for the statistic based on additional events.

2025-05-28 Wed: Synced with Theo regarding the target strategy: Outperform passive BTC by ≥ 15% annual alpha while maintaining near-zero BTC delta. Continuing to work on tracking the owners of positions staked in CLGauge by tracing the position token’s path through events.

2025-05-27 Tue: [Exported](https://github.com/harmony-one/shadow-pool-analytics/tree/main/aerodrome/export_USDC_cbBTC) the raw position data for the cbbtc-usdc pool for the entire period. Discovered an issue with the reward calculation for positions — since some of them participate in staking, the owner is actually the CLGauge contract, which makes it harder to identify the real owner and their yield.

2025-05-26 Mon: Worked on tracking the optimal strategy for the cbbtc/USDC pool on Aerodrome. Researched the Hyperliquid platform — for perp shorts, long BTC via perps or spot wallet, etc. Also explored the ecosystem to assess opportunities for building analytics and yield evaluation.

---

2025-05-24 Sat (3.0h): [Exported](https://github.com/harmony-one/shadow-pool-analytics/tree/main/vfat_shadow_stats/export_S_USDC) the raw data for the S/USDC pool, finished report and shared the final statistics for the pool.

2025-05-23 Fri: Loaded all the data and completed the analysis of the statistics for the Shadow pool [S/USDC](https://www.shadow.so/liquidity/0x324963c267c354c7660ce8ca3f5f167e05649970) from 05.15 to 22.15 (17th epoch). Currently working on the final report. Synced with Theo regarding new focus on the cbbtc/usdc position analysis from Aerodrome wallets to find the best range for our LP.

2025-05-22 Thu: Switched to analyzing statistics for the Shadow pool [S/USDC](https://www.shadow.so/liquidity/0x324963c267c354c7660ce8ca3f5f167e05649970): wallets with earnings over $1000, top 10 earning wallets, breakdown of the 327% APY for the 7.5% range, total trading fees, rebalancing frequencies.

2025-05-21 Wed: Synced with Artem regarding the Beets Protocol tracker and the optimal calculation of strategy profitability. Reviewed the [pull request](https://github.com/harmony-one/shadow-scraper/pull/16) for beets-protocol in shadow ccaper. Currently working on the updated APR calculation and other parameters for all wallets stats.

2025-05-20 Tue: Analyzed the Balancer V3 Gyro Pool contracts to collect missing event data for the following beets.fi pools: scETH/scBTC, SolvBTC.BBN/SolvBTC, and scBTC/LBTC on sonic. Additionally, developing new scripts to aggregate data and compute wallet-level statistics.

2025-05-19 Mon: Opened several positions on beets.fi and spectra for yield testing, as well as event tracking and verifying the accuracy of information from the pools against real data. Started researching contracts, events, and subgraphs to collect data on beets.fi based on the [docs](https://docs.beets.fi/technicals/subgraphs).

---

2025-05-16 Fri: [Updated](https://github.com/harmony-one/shadow-pool-analytics/tree/main/export_swapx_ichi) and expanded the data on swapx ichi wallets stats. Completed the general comparison of btc pools on vfat, shadow, and swapx based on the collected statistics. Continuing research on the Spectra platform for data export and analytic.

2025-05-15 Thu: Finished exporting data and analyzing wallet statistics from the pools of Beefy and SwapX Ichi: wbtc-scbtc, scbtc-wbtc, ws/scbtc, usdc.e/scbtc. Researching the Beets and Spectra platforms for data export and wallet analysis, as well as strategies for btc pools.

2025-05-14 Wed: Added statistics for positions and wallets for several pools [WBTC_scBTC](https://github.com/harmony-one/shadow-pool-analytics/tree/main/vfat_shadow_stats/export_WBTC_%20scBTC) (914 positions) and [scBTC_LBTC](https://github.com/harmony-one/shadow-pool-analytics/tree/main/vfat_shadow_stats/export_scBTC_LBTC) (98 positions) - for vfat and shadow exchange. Working on data collection and analysis of BTC pools in Beefy Ichi Vaults.

2025-05-13 Tue: Added a separate [export](https://github.com/harmony-one/shadow-pool-analytics/blob/main/export_swapx_ichi/big_wallets.tsv) for big wallets with a deposit value of more than $1000. Finishing the analysis of BTC pools – the issues with reward calculations have been fixed, and an alternative [subgraph](https://thegraph.com/explorer/subgraphs/DTNjoPNU1TiDk1oHVmhz3rBcBbPJjPSqBtg52pRfpH71?view=Query&chain=arbitrum-one) is being used to re-collect the rewards data. In total, the analysis is being conducted for 50,000 positions.

2025-05-12 Mon: Finished extracting data for the aerodrome pools cbBTC/USDC and cbBTC/WETH with the promised APR of over 100%. Working on a script for analyzing the new data and a scheme for determining real impermanent losses. 

---

2025-05-09 Fri: Exploring yield strategies for Bitcoin on the Aerodrome Finance platform, focusing on the cbBTC/USDC and cbBTC/WETH pools — following a similar research approach used for other platforms: collecting data through the subgraph and reward information via contract events, followed by analysis and calculation of actual APRs per wallet.

2025-05-08 Thu: Made several adjustments to the data format for the ichi vaults sources / vfat: switched from csv to tsv and corrected an error that caused some amounts to be misinterpreted as dates. Additionally, begun researching yield strategies for bitcoin.

2025-05-07 Wed: Fixed issue with transfers USDC.e from Harmony to Linea: the problem was with the version update on the unify bridge assets (error in contract sources). The contract was fixed and redeployed, also updated the related frontend and backend services. Users in the community have been notified.

2025-05-06 Tue: [Added](https://github.com/harmony-one/shadow-pool-analytics/commit/e10fbefe04101ede92830b875b14fb7cc61aba69) export of an extended version of the raw data for all pools used to calculate the vfat position metrics. Switched to supporting the bridge (upon request from support) — investigating an issue with transferring funds from Harmony to Linea. It looks like there is a problem with some contract settings on the harmony side" 

2025-05-05 Mon: Synced with Theo regarding the final comparison between VFAT and Swapx ICHI vaults — we agreed that the most accurate approach is to compare the USDC.e/USDT and frxUSD/scUSD pools separately. Accordingly, I [generated](https://github.com/harmony-one/shadow-pool-analytics/blob/main/export_swapx_ichi/swapx-ichi-wallets-usdc-usdt.csv) the data for the USDT pool on Swapx ICHI and wrote the final report — it's currently under review with Theo.

---

2025-05-02 Fri: Exported data for all swap operations in the frxUSD/scUSD pool to more accurately determine price changes and calculate the average in-range time for wallets, as well as impermanent loss. Working on the final analysis and conclusion comparing vfat and beefy swapx ichi vaults.

2025-05-01 Thu: [Finished](https://github.com/harmony-one/shadow-pool-analytics/blob/main/export_swapx_ichi/all_wallets.tsv) generating statistics on closed wallets based on data from the Ichi subgraph and gauge contract events. The challenge lies in the fact that a single wallet can have multiple deposits and withdrawals at different times, so I have to calculate the APR for time intervals and average them. Also prepared an [export](https://github.com/harmony-one/shadow-pool-analytics/blob/main/export_swapx_ichi/top_wallets.tsv) for the top wallets with a profit of over 10 dollars.

2025-04-29 Wed: [Added](https://github.com/harmony-one/shadow-pool-analytics/blob/main/export_swapx_ichi/active_wallets.tsv) statistics for the swapx ichi vault frxUSD/scUSD – 60 active wallets with calculated rewards and APR. Some difficulties arise because rewards need to be calculated differently for active and closed positions (via contract method calls or events). I will also expand this table with data on time in range and loss.

2025-04-29 Tue: Continue research on swapx vault ICHI strategies: Exported data on the vaults, including deposit, withdrawal, fee collection, and rebalancing events. Currently exporting the final positions from AlgebraPools to build comparison statistics between manually managed positions and those managed by the vault strategies.

2025-04-28 Mon: Made an additional export and analysis for vfat USD pools. Started collecting data on ichi's strategies beefy's pools to create a comparative analysis with vfat. Discussing the current analytics results with the team, making adjustments.

---

2025-04-25 Fri: Finished analyzing VFAT positions and strategies based on the collected data. Added a [document](https://github.com/harmony-one/shadow-pool-analytics/blob/main/docs/vfat_analysis.md) with key findings on pools, losses, the impact of auto-rebalancing, and overall conclusions. Fixed errors in range tracking calculations and corrected the alignment of position timestamps with hours_pool_data.

2025-04-24 Thu: [Added](https://github.com/harmony-one/shadow-pool-analytics/tree/main/export_all) missing pool data. Updated script integration and collected statistical information — [resulting](https://github.com/harmony-one/shadow-pool-analytics/blob/main/export_all/positions-stats-all.tsv) in a complete dataset including: position, price range, deposits, profit, annual percentage rate, time in range, impermanent loss, wallet, strategy settings, pool, and more.

2025-04-23 Wed: Finished exporting all rewards across all tokens, as well as hourly data on pool states. Currently working on the final script for data aggregation and position statistics calculation — vfat strategies (the exported data covers 45% of all vfat positions and the top 10 pools with 90% of the TVL). 

2025-04-22 Tue: [Finished](https://github.com/harmony-one/shadow-pool-analytics/tree/main/export_all) the full data export for positions in the top 10 vfat pools. Still need to load the rewards from gauges for the entire period — after that, we’ll be able to launch advanced analytics to calculate pool strategies. Also did some research on [SnapshotX](https://www.starknet.io/blog/snapshot-x-onchain-voting/) (open-source Snapshot) to work with Harmony, for a governance solution.

2025-04-21 Mon: Continuing work on exporting data for all Shadow pools to generate extended statistics for VFAT. There are several issues with the subgraph when retrieving old positions from many pools — working on resolving them. [Grouped](https://github.com/harmony-one/shadow-pool-analytics/blob/main/export/grouped_vfat_positions.tsv) all VFAT position-settings by cutoff and buffer parameters — most strategies monitor the entire Uniswap price range without restrictions. With no buffer and auto-rebalance enabled, the system instantly reacts as soon as the price moves out of range.

---

2025-04-17 Fri: Since the vfat sample of positions shows too little data with almost identical rebalancing settings for the USDC.e/scUSD and USDC.e/USDT pools, Theo and I decided to expand the data collection range to include all usd* pools — goal is to find the most profitable usd* pool from the last 90 days - working on scripts extending.

2025-04-16 Thu: Investigated user issues related to using Ledger Nano for staking. Then returned to analyzing USD strategies, [exported](https://github.com/harmony-one/shadow-pool-analytics/blob/main/export/vfat_positions.tsv) the settings for all vfat positions — still have the main question is how to analyze params correctly. Synced with Theo about next steps.

2025-04-16 Wed: Finished fixing the bridge issues related to the loss of AXS tokens. The core problem was that Horizon legacy tokens operate through an intermediate contract, which requires more gas, and this wasn't calculated correctly in the proxy on the Ethereum side. Also fixed the issue with the explorer service interacting with the Arbitrum RPC.

2025-04-15 Tue: Switched to fixing several outstanding bridge issues from the community: $AXS asset stuck when bridging $1AXS from Ethereum to HarmonyONE, and a LEDGER Nano-related issue. Also finishing the final export of scUSD strategies (will update later today).

2025-04-14 Mon: [Exported](https://github.com/harmony-one/shadow-pool-analytics/blob/main/export/price_historical_data_USDC.e_scUSD.csv) the historical price data of scUSDC for the entire period, based on the subgraph events swaps and historyPoolData, and plotted its distribution using AI. I'm continuing to work on researching how to tie vfat rebalancing strategy parameters to scUSD positions — currently, there's an issue where too few vfat strategies are found for the scUSD pool, and the parameters are repeating, so I'm double-checking the approach.

---

2025-04-11 Fri: [Finished](https://github.com/harmony-one/shadow-pool-analytics/commit/e9ecb57fc04d2116fe177aa0299ba810d6af6fbd) the service for loading NftSettingsSet events and finding positions related to those settings. As a result, there’s now an extended [tsv table](https://github.com/harmony-one/shadow-pool-analytics/blob/main/export/vfat_positions_USDC.e_USDT_pool_0x9053fe060f412ad5677f934f89e07524343ee8e7.tsv) with vfat positions. Parameters like cutoff, buffer, etc., have been added. However, as we can see for the USDC.e/USDT pool, the settings are almost identical across all positions.

2025-04-10 Thu: Worked on linking historical shadow exchange positions to vfat strategies, mainly by checking for the SickleDepositedNft event in position creation [transactions](https://sonicscan.org/tx/0x4eb38e38c893d49636b0ccbf23b684d313059920a3b830a5b49caa16fea5bc81#eventlog#29) or mapping NftSettingsSet events from the NftSettingsRegistry [contract](https://sonicscan.org/address/0xb7190708356b592cdaa0082e15a43baa983cb72c) by tokenId. This will let us group positions by wallet and strategy parameters like cutoff and buffer. Building scripts to load event data and refresh the stats.

2025-04-09 Wed: Researched issues with performance limitations of the shadow-pool-analytics application on fly.io, configured the deployment. Switching to vfat contract analysis and searching for a subgraph or writing a custom event listener to bind vfat parameters (cutoff / buffer) to positions and generate general statistics.

2025-04-08 Tue: [Completed](https://github.com/harmony-one/shadow-pool-analytics) shadow pool analytics service for receiving full statistics on positions (including impermanent losses) and wallets in real time. Added swagger on developed APIs (by position, by wallet, general list etc). Working on optimization: due to the fact that the analysis of the entire pool of about 10 thousand positions takes up too many processor resources fly.io

2025-04-07 Mon: Finished a script for loading data and calculating the parameters of impermanent Loss percent and short term volatility percent. Working on wrapping the script in the nestjs service with an api to be able to make requests to custom pools in real time.

---

2025-04-04 Fri: Started working on a service for assessing impermanent loss for positions opened via vfat.io. Data for analysis about the position and pool is loaded via subgraphs and token prices are taken via open APIs coingecko, binance.

2025-04-03 Thu: Added a script for determining the optimal strategy by positions: first grouping by wallets and ticks, then averaging values of APR, deposited, time in range, position duration, and then calculating parameters like total profit in usd, number of rebalances, and rebalances gap in hours. [Exported](https://github.com/potvik/shadow-scraper/commit/d0b3d89fa199b89079dda0fa8b1b0d5fed059e03) the results to TSV tables.

2025-04-02 Wed: To determine whether a position was in-range, two approaches were used: based on pool hours data (with hourly accuracy) and by exporting all swap events (more precise). [Updated](https://github.com/potvik/shadow-scraper/commit/366f24e9c89f8efd3d91c7881b94a1b5fafd45a4) the statistics calculation script according to the new data and performed the final export.

2025-04-01 Tue: [Added](https://github.com/potvik/shadow-scraper/commit/d04f9d8eae84ab5311cdaa37c4877e219227c136) a script for exporting burn events to determine the exact lifetime of each position, and accordingly added recalculation of the actual APR.

---

2025 Q1 Review

Improvements and launch of Pump.ONE [contracts](https://github.com/harmony-one/pump.fun.contracts). All contracts are made upgradable. Added a second alternative version of the Token Factory contract without competitions with the preserved functionality of trading and publishing in Uniswap V3 pools. Transition to AсcessControl with the division of functionality between the roles of administrator and manager. Added utility methods for withdrawing rewards and liquidity. Fixed critical errors in interaction with Uniswap and price calculation. Assistance with integration with backend and frontend services. Support at [Pump.ONE application](https://pump.one/board) launch.

Completed Unify Bridge Assets V1 feature: USDC converter contract allow converting legacy USDC to USDC.e at a rate of 1-1, extended ProxyHRC20 layerzero contracts to support bridging USDC tokens from different chains to one USDC.e on the harmony side, the frontend was also updated to support unify assets feature. Now the conversion works for the linea and base networks.

Started working on Layerzero V2 bridge contract: one common contract for all tokens, dynamic addition of new tokens via contract method calls, auto deployment of token wrapper on the harmony side. Draft version is ready, currently in debugging stage. Researched options for transferring liquidity from v1 contracts to v2.

Researched contracts for auto balance strategies: vfat Farm Strategy, beefy, arrakis, gamma. Created contract based on FarmStrategy with predefined parameters. The contract checks for range out-of-range and calls rebalancing methods. The goal is to collect statistics for analysis in-range fee-collecting performance in sonic mainnet.

---

2025-03-31 Mon: Added a script to determine the best strategies by grouping by average price and range, as well as by tick. Added calculation of the ROI parameter, total profitability and average APR. Because most of the positions are concentrated in the most profitable group, it is difficult to isolate winning strategies. Working on adding rebalancing parameters and time in the range.

---

2025-03-28 Fri: Fixed calculation errors, corrected data. Researched to understand which positions were opened via vfat and which via shadow ux. Added position lifespan analysis for more accurate calculation for apr.

2025-03-27 Thu: [Completed](https://github.com/potvik/shadow-scraper/commit/40680aa05ff229ca3b8d307c03672f645c2cff4a) final version of the statistic script using a combined approach to loading rewards and calculating apr - all methods are used: totalFeeCollateral and claimRewards from the subgraph, direct call earned for positions for which there was no withdrawal of rewards, analysis of transfers of reward tokens from the guard address to the address of the position owner. Also expanded the range of information collection to 1 month - to capture more positions and rewards (since most open them for a long time). 

2025-03-26 Wed: Tried an alternative method for loading rewards by unloading reward token transfer operations via sonic api. Based on the developed python [script](https://github.com/rikaa15/sonic-rewards/blob/main/user-stats.py) from Rika. [Updated](https://github.com/potvik/shadow-scraper/blob/main/export/filtered_limited_positions_stats_USDC_e_USDT.tsv) some stats tsv data.

2025-03-25 Tue: Worked on solving the problem of calculating apr with reference to positions - loaded part of the data from the subgraph via claimRewards and part by directly calling the earned method of the contract. When unloading for the week, the general data does not match the declared in the shadow total rewards interface. Doing a deeper research of the problem of linking rewards to positions.

2025-03-24 Mon: Converted tables with reports to tsv format, redid rounding and grouping by prices. There is still a problem with the APR calculation - some of them are negative or 0, which does not correspond to the general statistics. It seems that the problem is in the extended time range of creating positions and collecting rewards, also part of positions still not claim rewards.

---

2025-03-21 Fri: Worked on a script for loading (directly through my subgraph) and generating statistics for specified pools, positions: tick-range in usdc/usd* pools, rebalance occurrences (calculated through mint/burn events), trading fees, liquid rewards (through subgraph queries), future points, overall return.

2025-03-20 Thu: Researched way to detect how much tvl is in shadow’s vaults via direct deposits vs managed by vfat’s "auto rebalancing" or "auto compounding" strategies. Deployed and [configured](https://github.com/harmony-one/h/blob/main/docs/subgraph-deployment.md) custom Shadow Pool Subgraph.

2025-03-19 Wed: Researched graphql queries to get data (positions and rewards). Completed a script to calculate TVL and rewards for a price in range of 90% (from $1). some problem with linking rewards to swap transactions (ie grouping by price range)

2025-03-18 Tue: [Added](https://github.com/harmony-one/shadow-scraper/pull/3) scripts for uploading swap data from swapX. Uploaded more data on USDC.e/scUSD pools, updated the script for calculating stats range by volume. Started researching the possibility of linking swap events to position commission data - to calculate rewards in the 90% range.

2025-03-17 Mon: Used portfolio tracker to output all trades of the last 7 days in csv format for shadow’s and swapX USDC.e/USDT pool. [Added](https://github.com/harmony-one/shadow-scraper/pull/1) scripts for calculating the range (centered around $1) where 90% of trades were in for maximizing gains from fees.

---

2025-03-15 Sat: Added more contract events to support analytics collection (rebalancing prices, fee, ticks etc).  Worked on Q1 Review.

2025-03-14 Fri: Completed integration with shadow exchange pools via Ramses V3 Protocol [interfaces](https://github.com/code-423n4/2024-10-ramses-exchange/blob/main/contracts/CL/core/RamsesV3Factory.sol) (used shadow exchange for managing pools). Added a simple backend service for calling methods for checking out-of-range with automatic rebalancing. Testing the contract and strategy.

2025-03-13 Thu: sick day-off

2025-03-12 Wed: sick day-off

2025-03-11 Tue: Researched interaction with shadow exchange pools, including via vfat (Farm Strategy) adapters. Transferred the logic of making decisions on rebalance to the contract level, testing Farm Strategy on the usdc shadow pool.

2025-03-10 Mon: Worked on developing a contract based on FarmStrategy: predefined parameters, limited settings, application consists of a contract and a client. The client checks for out-of-range and calls rebalance methods. The goal is to collect statistics for analysis in-range fee-collecting performance in sonic mainnet.

---

2025-03-07 Fri: Researched contracts for auto balance strategies: vfat Farm Strategy, beefy, arrakis, gamma. Research of the sonic mainnet eco system, analysis of interaction with liquidity pools using Farm Strategy as an example.

2025-03-06 Thu: [Added](https://github.com/harmony-one/layerzero-bridge-v2/commit/1059ce846da4ead22e8e956984ccb84f9ab2a779) improvements for layerzero v2 receiver: automatic wrapped token registration, fee handling for token transfers, validation of supported chains, and improved event logging for better tracking and security. Added more tests.

2025-03-05 Wed: [Added](https://github.com/harmony-one/layerzero-bridge-v2/commit/e9d9c4e50c397e5598facb03c691afac3f3206d0) layer zero v2 receiver contract for use on the harmony side: standard methods for receiving and sending tokens + deploy wrapper token contract in case of a new token. Now the main problem is the correct calculation of the cost of deployment and increasing the fee for cases when deploying a new token.

2025-03-04 Tue: [Published](https://github.com/harmony-one/layerzero-bridge-v2) layerzero v2 bridge contracts first version: allows the owner to add and remove supported tokens, transmitted message contains token address, amount and receiver, token wrappers still should be deployed manually. Continue working on dynamic token wrappers deployment.

2025-03-03 Mon: Researched the socket bridge proposal, compared it with existing analogues; dealt with the problem of deploying new contracts on layerzero v1 (Destination transaction caused payload stored). Contacted layerzero developers to register configs of new contracts.

---

2025-02-28 Fri: Support for layerzero v1 bridge: several bugs blocking the transfer of bnb/one tokens have been fixed (reports from Sopha and Theo). Studying statistics on operations - there are many explorer errors associated with the limited unavailability of free bsc rpc (considering the option of returning to our own node for bsc). Finishing up updating the interface for the hidden conversion of legacy assets, preparing a demo.

2025-02-27 Thu: [Updated](https://github.com/harmony-one/unify-bridge-assets/pull/1) OFTCore contract for unify bridge assets: allows specifying a token in the sendFrom method and includes a whitelist mechanism. Testing new version. Researched sonic gateway bridge solutions: [repositories](https://github.com/Fantom-foundation/), [audit](audit here https://blog.openzeppelin.com/sonic-gateway-audit), [docs](https://docs.soniclabs.com/sonic/sonic-gateway), possibility of porting to harmony.

2025-02-26 Wed: Unify assets: improvements to the proxy contract V1 - one more parameter has been added to the constructor that indicates a usdc-supported legacy token (burning only). Also, in the _debitFrom method you can now explicitly indicate which token will be burned. Debugging and fixing problematic USDC (Base) bridge transactions.

2025-02-25 Tue: Synchronized with Theo and Philip about the current version of [unify assets](https://docs.google.com/document/d/1K39LcmO8Z1AHg380HA_kU0aSPW-N3w-r4yVzJ_dxtfA) - it was decided to finalize the architecture to make it possible to do hidden legace usdc conversion without redirects to the conversion interface. Helped Rika with contract deployment, debugging and understanding of bridge contract structure.

2025-02-24 Mon: [Added](https://docs.google.com/document/d/1K39LcmO8Z1AHg380HA_kU0aSPW-N3w-r4yVzJ_dxtfA) a description with screenshots and comments on the current flow of unidy bridge assets translations (for discussion with Theo and Philip). Layerzero V2 - research for the possibility of transferring liquidity to new contracts with V1. Research for bridge solutions based on liquidity pools from the Socket protocol team (suggestion from Philip). 

---

2025-02-21 Fri: [Added](https://github.com/harmony-one/layerzero-bridge.frontend/pull/28) ux improvements for the layerzero bridge: a fix for displaying legacy assets, displaying tokens available for transfer, and validation at the stage of entering the transfer amount. Published the latest version on the [bridge](https://bridge.harmony.one) prod. [Tested](https://github.com/harmony-one/layerzero-bridge.frontend/pull/27) the full bridge AERO flow from Rika.


2025-02-20 Thu: Reviewed staking dashboard [update](https://github.com/harmony-one/staking-dashboard/pull/721) (Ledger App Integration via Ledger SDK feature). Continue to work on the architecture of the common contract of the V2 bridge.

2025-02-19 Wed: [Added](https://github.com/harmony-one/usdc-converter/commit/e3933d1eba4d11a4dea63280abf761446748e482) fixes for ui usdc converter: fixed error when converting decimals, updated configs and contract addresses. A new version of ui has been [deployed](https://usdc-converter.web.app). Sent all updates to Aaron for security review.

2025-02-18 Tue: [Fixed](https://github.com/harmony-one/pump.fun.contracts/pull/25/files) tests for pump.one contracts: support for interfaces of updated contracts, fixed a bug with the withdrawal of commissions by the administrator, fixed a bug with waiting for a delay between publication on Uniswap and the conversion of tokens.

2025-02-17 Mon: Deploy hrc20 production contacts for usdc tokens (eth, arb, bsc, base, linea). Detailing and planning work to update the bridge - transition to LayerZero V2, creation of a common contract for all tokens with the dynamic connection of new tokens.

---

2025-02-14 Fri: [Improvements](https://github.com/harmony-one/usdc-converter/pull/5) to the USDC converter: since bscUSDC differs in decimals from USDC of other chains - amount normalization has been added when converting tokens - now the decimals of input and output tokens are taken into account. Tests have been updated and contracts redeployed.

2025-02-13 Thu: The transition from Ownable to Access Control contracts has been [implemented](https://github.com/harmony-one/pump.fun.contracts/pull/24) to make it possible to allocate a separate Manager role, which will initiate the start of a new competition. The Administrator role will still be responsible for updating the contract and setting up the configuration.

2025-02-12 Wed: Researched the issue with pablish to uniswap after competition ending. [Reviewed](https://github.com/harmony-one/pump.fun.contracts/pull/23) a pull request from Aaron with a bug fixes. Transferred fixes to Token Factory Base. Synchronized with Artem about updates. A reqiredCollateral parameter has also been added to control the minimum collateral before publishing.

2025-02-11 Tue: After synchronizing with Artem and Aaron, it was decided to add publishing methods on Uniswap to the contract and make the token non-tradable after publication. Pushed new [version](https://github.com/harmony-one/pump.fun.contracts/pull/22/commits/27ce4e5eae0a9da5d55772600828800fab4e83d2). Tested new contract version, found an error "execution reverted: LOK" (uniswap intercation) - Working with Aaron on a fix.

2025-02-10 Mon: [Completed](https://github.com/harmony-one/pump.fun.contracts/pull/22/commits/aff875bff2ed28391b3ffbb562a2ac847e451baa) the Token Factory Base contract: only token release, purchase, sale. I gave it to Aaron for review. Working with Artem on integration.

---

2025-02-07 Fri: Improvements to the Reward Distributor contract: transition from Ownable to AccessControl. [Added](https://github.com/harmony-one/erc-4626/pull/7) manager role to set epoch duration and epoch reward. Withdrawal methods are available only to the main admin role. Synchronized with Artem regarding improvements to Token Factory - working on another modification for the factory without competition but with support for all events and methods of the original (for full compatibility in the frontend).

2025-02-06 Thu: Completed deploying smart contracts: proxy, USDCe, converter, [published](https://usdc-converter.web.app/?token=0xBC594CABd205bD993e7FfA6F3e9ceA75c1110da5) the frontend demo of the usdc converter, and [added](https://github.com/harmony-one/usdc-converter/pull/4) several ui corrections. Working on a flow description for testing a unify bridge assets full demo.

2025-02-05 Wed: Deployment and configuration of the production version of contracts for the USDCe token, proxy contracts for the bsc USDC and USDCe harmony bundle, deployment USDC converter contracts and frontend app, etc.

2025-02-04 Tue: Improvement of the USDC converter and layerzero bridge frontend services to implement a full flow with redirection and conversion of tokens: a return to the bridge after conversion has been added, on the bridge side support for going to the USDCe token page after conversion has been added. Testing the full flow and fix errors.

2025-02-03 Mon: Reviewed [changes](https://github.com/harmony-one/usdc-converter/pull/3) from Artem. Worked on additional front-end features of the USDC converter: selecting tokens from a drop-down list, following a link - passing the token address through the url, as a result of which the USDC converter opens with a pre-installed token for exchange (bridge crossing integration).

---

2025-01-31 Fri: Researched the possibility of withdrawing ROT/MAGGOT tokens from Harmony, or adding them to an existing bridge (at the request of community partners). Testing an updated version of pump.one with upgradable contracts in conjunction with backend and frontend services.

2025-01-30 Thu: Synchronized with Artem about improvements to pump.one before launch: at Theo’s request, we are making a version with the optional inclusion of competitions. I made several improvements that allow you to use Token Factory without competitions, with the subsequent optional inclusion of competitions. Several manage methods have also been added for emergency withdrawal of user funds and transfer tokwns ownership.

2025-01-29 Wed: Worked on integrating the USDC converter into the layerzero bridge interface: if the user selects legacy assets and the balance is non-zero, he is prompted to go to a separate usdc converter page. After successful conversion, a redirect is made back to the bridge to continue the operation.

2025-01-28 Tue: [Added](https://github.com/harmony-one/pump.fun.contracts/pull/20/files) more changes to pump.one Upgradeable-contracts version. Changed package versions to support compatibility with ethers 5 (used in deployment and update scripts). Shared with Aaron for security review.

2025-01-27 Mon: Changed USDC converter contract - according to [issue](https://github.com/harmony-one/usdc-converter/issues/2) from Aaron. Transfer of tokens has been replaced by burning. Started working on improvements to the front end of the usdc converter service.

---

2025-01-24 Fri: Review and test of the front-end part of the usdc converter - [pull request](https://github.com/harmony-one/usdc-converter/pull/1) from Teo. Assessing integration into the main bridge application, it looks like the converter should be a separate application or a separate widget.

2025-01-23 Thu: Tested updating contracts via hardhat Upgradeable Contracts. [Added](https://github.com/harmony-one/pump.fun.contracts/commit/d17f70d4d83d5c462461f66f731f62dc342b0c42) update support for Token Factory and Liquidity Manager contracts. Added new deployment and update scripts.

2025-01-22 Wed: Synchronized with Artem regarding improvements to the pump.one contract. Worked on an upgradable version of the Token Factory contract.

2025-01-21 Tue: Tested unify assets full flow: transferred bsсUSDC to harmony, converted to USDCe, transferred back through a proxy USDCe contract. Worked on rest lz bridge frontend fixes: renaming legacy tokens to legacyAssets, adding lz logo banner. Waiting for a decision from Theo and Alaina on the way to integrate the USDCe converter: inside the bridge application or redirect to a separate application.

2025-01-20 Mon: Worked on updating the [frontend part](https://github.com/harmony-one/layerzero-bridge.frontend) of the bridge application - added checks for the available transfer limit for all USDC tokens by calling a new contract proxy method. Also working on displaying warnings and changing token links.

---

2025-01-17 Fri: Refactoring of the proxy layerzero oft contract - updating the solidity version, adding service methods to manage contract parameters, adjusted the calculation of the amount of tokens during transfer, added safeERC20.

2025-01-16 Thu: Deployed a usdc converter with test tokens, created an [example](https://github.com/harmony-one/usdc-converter/blob/main/scripts/example.js) of use with ethers. Shared instructions with Teo for further development of the interface. Working on optimizing the Proxy contract.

2025-01-15 Wed: [Completed](https://github.com/harmony-one/usdc-converter/tree/main) USDC Converter contract: allow converting legacy USDC to USDC.e at a rate of 1-1. Added e2e tests. Currently working with test tokens.

2025-01-14 Tue: [Extended](https://github.com/harmony-one/unify-bridge-assets) the existing LZ Proxy contract to store the number of tokens locked on the external chain side on the Harmony side. Increase and decrease this value accordingly during transfers. Added contract-level validation.

2025-01-13 Mon: [Completed](https://github.com/harmony-one/erc-4626/commit/59962af1c87c3b5881334615bf14d9a264b39dc6) corrections based on review comments: removed the subtraction of the fee basis value when calculating the commission, corrected the tests. Continue work on unify bridge assets.

---

2025-01-10 Fri: Worked on Unify Bridge Assets new proxy contract, based on [task](https://docs.google.com/document/d/1K39LcmO8Z1AHg380HA_kU0aSPW-N3w-r4yVzJ_dxtfA/edit?usp=sharing). Another round of testing for pump.one contracts (update from Aaron).

2025-01-09 Thu: [Completed](https://github.com/harmony-one/erc-4626/pull/6/files) fixing all tasks on the erc4626 issues [list](https://github.com/harmony-one/erc-4626/issues). Prepared a list of improvements: fee calculation, resolved unnecessary and risky dependencies, added fallback methods to withdraw assets for reward contract, use of the current balance in case it is not enough for rewards per epoch.

2025-01-08 Wed: Looked at the [contract issues](https://github.com/harmony-one/erc-4626/issues) that Aaron found as a result of the security audit. Working on adding fallback methods to withdraw assets from Reward Contract. Also started working on adjusting the commission deduction in accordance with the [documentation](https://docs.openzeppelin.com/contracts/4.x/erc4626#fees) from Aaron.

2025-01-07 Tue: [Added](https://github.com/harmony-one/erc4626-rewards-distributor/commit/2c81857fde9d91648ef3ca6f430491447cb82ffc) Rewards Deposited events storing to erc4626 rewards distributor backend. Research to evaluate the complexity of adding an additional competition function to Pump.One contracts

2025-01-06 Mon: [Added](https://github.com/harmony-one/erc-4626/commit/29b6de33b5ccceb8900357000981ebfd793bffeb) several fixes for the Staking Vault contract. Shared contracts with Aaron for a security audit. Synchronized with Artem to update the client.

---

2024 Q4 Review

Development Pump.ONE [contracts](https://github.com/harmony-one/pump.fun.contracts): the logic for the token factory, competition and liquidity manager is fully implemented. Implemented counting of investments, determining the winner and publishing on Uniswap v3. Additional logic has been developed for linking tokens to the competition ID: buying and selling is allowed only within the current competition - then the user can only convert his tokens into winner tokens, or publish on Uniswap if this token is the winner. Several integration tests have been developed. Contracts serve as the basis for the [Pump.ONE application](https://pump.one/board). Added integrations with API services and frontend client.

Developed Staking Vault [contracts](https://github.com/harmony-one/erc-4626) based on Erc-4626 with a Reward distributor contract. Additionally, the 1sDAI token was added to the bridge, which was integrated into the Staking Vault. Added logic for commission deduction, as well as rewards by epoch.

Also worked on the development of several new layerzero bridge features: integration with Solana (with the transition to LayerZero V2) - implemented draft only for the test network. Updating npm bridge packages and worked on bridge-cli for translations from the command line.

---

2025 Goals:

In 2025, I will enhance the Harmony Bridge with features like migration to LayerZero V2, Solana support, a unified contract for multiple tokens with dynamic additions, and USDCe support for all chains. UX improvements will also be implemented for a smoother experience.

Additionally, I'll release DeFi applications such as Pump ONE contracts, ERC-4626-based Staking Vaults, GMX V1, and an upgraded GMX version with autocompounder, leveraged GLP, and delta-neutral vaults. DeFi games integrated with Telegram will also be launched.

I’ll develop autonomous yield optimization agents and AI-driven trading bots for real-time decision-making, as well as integrate AI into staking and liquidity management for seamless portfolio rebalancing and auto-compounding.

---

2024-12-24 Tue: Added more tests for the Reward and Staking Vault contracts: testing the change in the price of share tokens and the sequential addition of rewards. Testing the withdrawal of the full amount of share tokens. Added methods for editing all internal parameters of the Reward contract, as well as the ownership model.

2024-12-23 Mon: Fixed the erc4626 Staking Vault contract issue, related to the deduction of commissions when withdrawing funds through the withdrawal and redeem methods: in the current version, the commission is deducted from the general pool, which makes the price of share tokens lower for all holders. This problem is fixed in the new version.

---

2024-12-20 Fri: Reviewed and tested the new pump one contracts [update](https://github.com/harmony-one/pump.fun.contracts/pull/19). Tested changes related to new burn and convert mechanism, reduced liquidity at publishing pool.

2024-12-19 Thu: Expanded the contract - added methods for editing internal variables, epoch length, number of rewards, etc. Updated e2e tests. Added indexing of reward payment events to the web 2 service. Synchronized with Artem regarding the service method for integration with the UI.

2024-12-18 Wed: Added web2 service [API](https://hmy-erc4626-reward-dist.fly.dev/api#/rewards/RewardDistController_getInfo) to display vairables and statistics of the rewards distributor contract: the current balance, next epoch flip, rewards streamed per day, rewards streamed per epoch. Also set up deployment of the service on fly.io.

2024-12-17 Tue: [Added](https://github.com/harmony-one/erc4626-rewards-distributor) erc4626 rewards distributor web2 service that monitors the current balance and calls rewards distributor contract methods every epoch to transfer rewards to StakingVault. 

2024-12-16 Mon: Synchronized with Artem about the Staking Vault contract methods, as well as the main use cases. Shared a [test script](https://github.com/harmony-one/erc-4626/blob/main/scripts/deploy.js) with main use cases. Involved in testing and debugging errors. Added Q4 reviews.

---

2024-12-13 Fri: Worked on a prototype for a new Proxy bridge contract with the ability to unify bridge assets - the main difference on the Harmony side will be the ability to link several proxy oft contracts to one token and accounting for liquidity on the side of the external chain by increasing the counter inside the contract on the Harmony side.

2024-12-12 Thu: Worked on foundry tests for Erc-4626 Staking Vault and Reward distributor contract. Reviewed Unify Bridge Assets [doc](https://docs.google.com/document/d/1K39LcmO8Z1AHg380HA_kU0aSPW-N3w-r4yVzJ_dxtfA/edit?usp=sharing), explored the possibility of avoiding liquidity fragmentation, assets bridged from any chain into Harmony should result in one single asset. 

2024-12-11 Wed: Completed the e2e tests for integration cases with Uniswap and the creation of a pool - publishToUniswap. Unfortunately, there remains a problem with running tests on local emulator with deploying UniswapV3Factory from tests (different versions of Uniswap and token factory).

2024-12-10 Tue: Worked on tests for TokenFactory: buying, selling, price changes, commission, publishing on Uniswap. Correction of contract settings to resolve [issue](https://github.com/harmony-one/pump.fun.contracts/issues/17). [Fixed](https://github.com/harmony-one/pump.fun.contracts/commit/213caf130f5688fd042f659322026d83b72cb77e) bug on call mint for not winner with low token price. Redeploy all contracts. Researched bridge rpc connection issue.

2024-12-09 Mon: Pumpfun launch: [fixed](https://github.com/harmony-one/pump.fun.contracts/commit/699e440c26c8f9a2a81aa745ed0fc119272d3c13) issue with uniswap initial supply calculation. Review and [merged](https://github.com/harmony-one/pump.fun.contracts/commit/1f538436ad6f0dea51e81d97b542f3171ce26386) latest changes from Aaron. Redeployed all contracts. Testing complex e2e cases.

---

2024-12-07 Sun: Reviewed and tested several [merge requests](https://github.com/harmony-one/pump.fun.contracts/pulls?q=is%3Apr+is%3Aclosed) from Aaron. Found several issues.

2024-12-06 Fri: Pupmpfun launch testing. Researched computeMintingAmountFromPrice using issue. Synchronized with Aaron regarding the distribution of tasks - to speed up the launch process.

2024-12-05 Thu: [Worked](https://github.com/harmony-one/erc-4626) on Staking Vault tests and reward distribution logic extensions. Received a [list](https://github.com/harmony-one/pump.fun.contracts/pull/12) of review edits from Aaron - worked on the fixes.

2024-12-04 Wed: [Added](https://github.com/harmony-one/erc-4626) Staking Vault (1sDAI) contract based on erc-4626 with Reward contract. Added custom fetures: 0.1% of deposits or withdrawals are levied as a fee and transferred to a separate walletsupport, Reward distribution: Before each epoch the reward contract checks the available 1sDAI balance and will distribute the amount set by us OR the maximum amount available. 

2024-12-03 Tue: Worked on other edits for token factory and liquidity manager contracts: ensuring the assembly is compatible with uniswap/v3-periphery through the use of foundry remappings, calculating tickLower and tickMax based on price, comparing token addresses and correcting their order when creating a pool.

2024-12-02 Mon: Synced with Aaron and Artem about pumpfun launch, [pushed](https://github.com/harmony-one/pump.fun.contracts/pull/12/commits/999d0438e0fae318533bcda170e30a51912b9274) contract fixes based on Aaron review: getSqrtPriceX96 calculation function has been fixed, the logic for calculating the initial number of winner tokens for a pool has been changed, pool creation has been separated into a separate method, etc.


---

2024-11-29 Fri: Researched issues with correct ticks and sqrtPriceX96 calculation. Helped Artem with the integration of new contracts into the client and backend services. Working on more tests: swap via created pools, pools mamagement from contract creator accounts, adding more liquidity.

2024-11-28 Thu: [Completed](https://github.com/harmony-one/pump.fun.contracts/pull/12) Liquidity Manager contract based on NonfungiblePositionManager and UniswapV3Pool iteractions. Extended TokenFactory woth new winner logic, added more events and public views. Updated test scripts.

2024-11-27 Wed: Researched other ways to manage the liquidity pool. Made a new version based on NonfungiblePositionManager class to mint a liquidity position and then modify the provided liquidity. (this way also reccomeded in uniswap v3 [docs](https://docs.uniswap.org/sdk/v3/guides/liquidity/modifying-position)). Additionally, it is necessary to work out the issue of storing and managing tokens received when adding liquidity.

2024-11-26 Tue: [Pushed](https://github.com/harmony-one/pump.fun.contracts/commit/800617a068ae7c01e25714596b538f29f9a08c9a) new version with mint fill range feature based on PanopticFactory [example](https://github.com/polymorpher/panoptic-v1-core/blob/0a0f8172159b09edd76cbe215d9766d116fc9240/contracts/PanopticFactory.sol#L495). But still have LOK error (reentrancy guard. A transaction cannot re-enter the pool mid-swap) on execution.

2024-11-25 Mon: Synchronized with Artem and Aaron regarding the launch of the pumpfun service, and identified the missing core features. Working on final improvements and tests.  

---

2024-11-22 Fri: Worked on the remaining logic for the winner after calling burnTokenAndMintWinner: adding liquidity to uniswap, sending events, defining a fixed inital supply, recalculating native tokens with which a new pull will be created.

2024-11-21 Thu: Worked with Artem on the integration of new contract methods into the client and backend pump-fun services. Received [new version](https://github.com/harmony-one/pump.fun.contracts/pull/10) of the bonding curve contract from Aaron - working on integrating the contract into the current token factory and writing foundry tests.

2024-11-20 Wed: Added support for the [sDAI](https://etherscan.io/token/0x83F20F44975D03b1b09e64809B757c47f942BEeA) token to the Harmony Bridge. Researched possibility of implementing the erc-4626 standard  on Harmony for the [DeFi-Strategy](https://www.notion.so/harmonyone/DeFi-Strategy-13fa38fc0487807a8afaefea24c1e1d0) project. Other improvements for the bridge ux.

2024-11-19 Tue: Added more fixes for pump fun token factory contract: [resolved](https://github.com/harmony-one/pump.fun.contracts/pull/7/commits/30a6d9ed5413a4fb2601358774bd38b7ce2a67ab) wrong competitionId issue (in _sell method called from burnTokenAndMintWinner) and [changed](https://github.com/harmony-one/pump.fun.contracts/pull/7/commits/5fa75752c7e3d283b08ac9229ecf03e810e70b47) the types of several structures to optimize storage. Started working on tests using foundry.

2024-11-18 Mon: Pused [review edits](https://github.com/harmony-one/pump.fun.contracts/pull/7/commits/61b534455b63eff0df591e5e330eb656398644f9), as well as integration with the latest updates. There is still a problem with calculating the price when selling and calling the burnTokenAndMintWinner method. There is a big difference between the blocked collateral and the new price calculated using the bounding curve. Synchronized with Aaron on current issues and further improvements.

---

2024-11-15 Fri: Reviewed and teseted Aaron's pr with [new bonding curve](https://github.com/harmony-one/pump.fun.contracts/pull/9) using Bancor Formula. Started integrating new updates into the current release version with expanded logic for determining the winner.

2024-11-14 Thu: Researched potential [issue](https://github.com/harmony-one/pump.fun.contracts/pull/5#issuecomment-2473512986) with burnTokenAndMintWinner method: whoever wants to sell first (when burning-to-covert becomes eligible) gets to sell it at a much higher price. Inspected cases we should enforce using a linear bonding curve (i.e. constant price) for calculating ONEs (ETH) obtained for burning.

2024-11-13 Wed: Continue to work on improving the contract based on pull revest [review](https://github.com/harmony-one/pump.fun.contracts/pull/7): allow each token to choose their own bonding curve, switched to higher solidity version, switched to Foundry for deployment, testing, and scripts, added custom error structs.

2024-11-12 Tue: Got feedback from Aaron on the [latest updates](https://github.com/harmony-one/pump.fun.contracts/pull/7). Working on fixing and improving reliability: switched keys from "day number" to some sort of "competition series id", to avoid collision when competition interval varies (instead of always 1 day), also changed all related logic in various methods.

2024-11-11 Mon: Continue to work on developing further logic for managing tokens issued through pump.fun TokenFactory after the winner is determined: scenarios with the addition of liquidity on Uniswap, minting more tokens, withdrawal of rewards, closing positions.

---

2024-11-08 Fri: Helped with integration contract methods into the pump.fun client application and backend services. Tested different contract cases, [Fixed](https://github.com/harmony-one/pump.fun.contracts/commit/baf60b859d5bdf65acba8e62d38c13b362aaf086) errors related to setting the start date of the competition for new tokens and breaking the logic of determining the winner.

2024-11-07 Thu: Synced with Artem regarding UX cases - decided that after winning the token ceases to participate in the competition and can only be converted into a Uniswap liquidity pool with a fixed initial supply. Added winners list - to prevent the winner from participating in the voting again and to support payments for past dates.

2024-11-06 Wed: [Added](https://github.com/harmony-one/pump.fun.contracts/pull/7/files) more features to pump contracts: stored contracts creation date, restriction of buy and sale operations by funding rate interval (1 day after contract creation date), added get winner by date view.

2024-11-05 Tue: Finished implementing the logic for determining the winner on the contract side. Synchronized with Aaron and Frank to adjust the business logic of the application. Working on adding new cases: after the winner is determined, the token is eliminated from the competition and winners liquidity pool is automatically created to Uniswap.

2024-11-04 Mon: Synchronized with Artem regarding the launch of the pump demo application, helped with the integration of contract methods and testing. Continue to implement the logic for determining the winner by day on the contract side.

---

2024-11-01 Fri: Working on the logic for determining the winner of the contract side: store a map that accumulates money paid for each token for each day, and the total number of token created so far until each day. 

2024-10-31 Thu: Synced with Aaron about the best token burning flow. [Updated](https://github.com/harmony-one/pump.fun.contracts/commit/33bc46bea0fbf6b9c1f6f2d94b9ecd072d800f6b) the contract with new logic - now after determining the winner, each user must call a method that check if a token they hold is the winner for the day, and if not, mints the winner token for the user based on an amount calculated by the accumulated money ( across all days) paid for the token which the user hold, divide by the accumulated money paid for the winning token. [Added](https://github.com/harmony-one/pump.fun.contracts/blob/main/scripts/test.js) example for Artem.

2024-10-30 Wed: Expanding the logic when burning (non-winning) tokens - now there are 2 ways: either we allow liquidity to be created and pairs are stored on the pump_eth contract, or we allow only one user to mint tokens, otherwise we will not be able to reset all balances (burn everything). Discussing both options with Aaron.

2024-10-29 Tue: [Extended](https://github.com/harmony-one/pump.fun.contracts/pull/4) TokenFactory contract with uri tokens params, [added](https://github.com/harmony-one/pump.fun.contracts/pull/4) more test cases: create several tokens with winner selecting. Updated create tokens logic: store new token numbers in an array - so that we can iterate through them when burning.

2024-10-28 Mon: Synchronized with the team regarding the development of pumpeth features. Received adjustments and [references](https://github.com/polymorpher/panoptic-v1-core/blob/0a0f8172159b09edd76cbe215d9766d116fc9240/contracts/PanopticFactory.sol#L495) from Aaron regarding integration with Uniswap V3. Working on deploying a new pool [feature](https://github.com/Uniswap/v3-core/blob/4024732be626f4b4299a4314150d5c5471d59ed9/contracts/UniswapV3Factory.sol#L35) and minting from an existing pool.

---

2024-10-25 Fri: Working on finalizing the burnAllAndReleaseWinner method - Changed the Token data structure and added a new class that will allow me to work with Uniswap V3 via PositionManager, instead of V2, which is used in the current version. Based on open Uniswap [documentation](https://docs.uniswap.org/contracts/v3/guides/providing-liquidity/mint-a-position) and examples.

2024-10-24 Thu: [Added](https://github.com/harmony-one/pump.fun.contracts/pull/3/files) contracts v2 (based on [repository](https://github.com/qiwihui/pumpeth)). Added tests for token creating and sell/buy with factory. Added more events and burnAllAndReleaseWinner method (The same logic for determining the winner with web2 service - then we call this method and it burns all tokens except the winner, for the winner we create a liquidity pool)

2024-10-23 Wed: Synced with Aaron about the contracts [repository](https://github.com/qiwihui/pumpeth). Researched a possible solution to the problem that burnLiquidityToken is transferring to 0 address, which would revert in some ERC20 implementation. Working on changing the [factory](https://github.com/qiwihui/pumpeth/blob/master/src/TokenFactory.sol) contract (paid for non-winning coins towards the winning coin, and mint more winning coins for each user (who minted other coins).

2024-10-22 Tue: Working on new "burnAll" contract method that will burn tokens in all liquidity pools and mint new tokens in the winner's liquidity pool. Method must be called by the keeper service, which will pass the winner's pool address as a parameter. 

2024-10-21 Mon: [Added](https://github.com/harmony-one/pump.fun.contracts/commit/beb6120ab7481b3f10a33f422031ecba86657638) more contracts events for swap operations. Also added expanded statistics to determine liquidity and trading volume per day and all the time. Synchronized with the team regarding the next steps.

---

2024-10-18 Fri: [Added](https://github.com/harmony-one/pump.fun.contracts/pull/2) more test script: adds a new token to the system (launch: deploy through a factory, add liquidity, add a user profile) and then buy this token for ONE (swapETHForTokens). Began implementing new features - such as transferring a fee to the winner.

2024-10-17 Thu: [Forked](https://github.com/harmony-one/pump.fun.contracts) pump eth contracts repo to harmony. [Added](https://github.com/harmony-one/pump.fun.contracts/pull/1) extended deploy scripts with more func wrappers and utils for better testing. Testing launch and swap methods.

2024-10-16 Wed: Completed the auto deployment script. I'm working on testing the main methods: mint, burn, createPair. Working on a simple scripts to reproduce cases of adding tokens and liquidity on harmony mainnet.

2024-10-15 Tue: Synchronized with Li, Artem and Aaron regarding further integration of pump.fun. Вistributed tasks and made a plan. Started deploying the [repository](https://github.com/sourlodine/Pump.fun-Smart-Contract) - locally and on the mainnet. Writing a script for auto deployment. 

2024-10-14 Mon: Started developing a new platform fees for creating memecoins (similar to https://pump.fun). Pumping all liquidity into ONE winner per day. I looked at the original [repository](https://github.com/enlomy/pump.fun) on rust. Researched existing evm based forks (such as [pumpeth](https://github.com/qiwihui/pumpeth)).

---

2024-10-11 Fri: I synchronized with the developers of the layerzero team regarding multiple token for OftAdapter support - but unfortunately they do not currently have a ready-made solution and it is necessary to deploy a separate OftAdapter for each token. Started working on Multiple tokens OftAdapter: init new contract for rust, working on logic.

2024-10-10 Thu: Completed a working prototype for SOL devnet -> Harmony testnet: OftAdapter on Solana side and OFT token contracts on the Harmony side. Integrated into bridge cli. Now there is a problem with deployment to production - since the cost of deploying a contract on the Solana side is about 5 SOL (to high for testing and adding new tokens). 

2024-10-09 Wed: I explored the possibility of reusing layerzero oft adapter v2 on the solana side for different tokens - to simplify adding new tokens and save deployment costs. Created and testing new solana version.

2024-10-08 Tue: Tested and fixed errors in harmony bridge cli. Added new features - such as loading a wallet from the command line, on request and with an aws file. [Published](https://www.npmjs.com/package/hmy-bridge-cli) latest version to npm. 

2024-10-07 Mon: Completed and [published](https://github.com/harmony-one/hmy-bridge-cli) the harmony bridge cli for transferring tokens to Harmony from EVM based chains (eth, binance, base, linea, arb). Shared instructions for use with Theo. Synced with Li and team about next goals (bridge multi tokens contract, solana support).

---

2024-10-04 Fri: Developed the structure and set of commands for harmony bridge cli. Moved sdk support for the current bridge there. I'm working on implementing support for direct transfers SOL to ONE with lz-solana-sdk-v2 and solana keys.

2024-10-03 Thu: Developed wrapper contracts for Oft and OftAdapter lz version 2 (those send and quota methods require the formation of structures). Redeployed the contracts - testing sending between chains. Still have errors on sending - synchronizing with the layerzero team to solve the problem. 

2024-10-02 Wed: Added [doc](https://github.com/harmony-one/h/blob/main/docs/bridge-add-token.md) with step-by-step description of adding a new token to the bridge (deploying 3 contracts and configs for front, back repositories). Added [lz-solana-sdk-v2](https://www.npmjs.com/package/@layerzerolabs/lz-solana-sdk-v2) and [@solana/web3.js](https://solana-labs.github.io/solana-web3.js/) libs to bridge client to interact with OFTAdapter on Solana side. Continue configuring and testing lz v2 bridging.

2024-10-01 Tue: During testing, OFT proxy on Solana received several problems related to setting the recipient's application address and receiving messages on the Harmony side. Synchronized with the layerzaero team on this issue - The Endpoint V1 and V2 contracts are backwards compatible but need to hang the OFT Program to support EPV1 OFT's message encoding. Worked on updating the recipient's contract.

2024-09-30 Mon: Added support for Moo Deng token to harmony bridge. Deployed [programs](https://github.com/LayerZero-Labs/example-oft) for solana layerzero OFT token. Working on client side scripts (based on solana web3) to call programs methods and token transfers.

---

2024-09-27 Fri: Studied ways to develop programs woth Rust lang for Solana. Researched Layerzero solana repositories for transferring messages and tokens. Researched the possibility of implementing one base contract on the Solana side for all tokens. Working on proxy oft program on solana side to do simple 1-1 bridge binding.

2024-09-26 Thu: Inspected and resolved bridge issue - related to the transfer of tokens from the base chain. Switched to work on the bridge: developing a new proxy contract to support transfers Solana <-> Harmony. Based on layerzero v2 endpoint. Design [overview](https://docs.layerzero.network/v2/developers/solana/oapp/overview).

2024-09-25 Wed: Worked on command line utility for bridging ERC20 tokens (based on sdk [repo](https://github.com/harmony-one/layerzero-bridge.sdk)). Additional functionality will be network binary download, wallet creation etc

2024-09-24 Tue: Redeployed contracts with new fixes, adding more tokens and ux fixes according to Aaron's review. Tested the [pano cli](https://github.com/polymorpher/pano) tool from Aaron. Synced with Li and Aaron about next goals.

2024-09-23 Mon: Worked on fixing the "insufficient collateral for fees" error - which occurred when an order is executing by the price keeper service (due to incorrect calculation of _sizeDelta in USD). Continue testing long positions (2x - 50x) feature with stable coins pairs.

---

2024-09-20 Fri: Worked on the ability to use stable coins in gmx long positions (we still get errors when executing positions with stable coins - since this is not provided for in contracts)

2024-09-19 Thu: By request from Soph i was investigating the problem that npm package name hmy-bridge-sdk ([repo](https://github.com/harmony-one/layerzero-bridge.sdk/tree/main)) was previously unclaimed on NPM (If this package had been claimed by an attacker, this would have led to arbitrary code execution on the affected server, as well as allowing the attacker to add backdoors inside the affected project(s) during the build process). additional [info](https://medium.com/@alex.birsan/dependency-confusion-4a5d60fec610).

2024-09-16 Mon - 2024-09-19 Thu: Paid Time Off

---

2024-09-12 Fri: Fixed security vulnerabilities related to path-to-regexp in several repositories. Fixed another error found by Aaron - related to stuck of long positions executions (when opening USDC to ONE).

2024-09-12 Thu: completed corrections based of the review; simplified the script and contracts for adding new tokens - adjusted the settings of the contract with roles (in the old version, only the GOV address can add new tokens). Сontinue to research the possibilities of increasing Leverage GXP x10 with current design.

2024-09-11 Wed: [updated](https://gx.country/) GMX interface after Aaron's final review notes, worked on more updates: changing "Long" to "USD" on trading page, adding USD token as the target token under "Short" either, added links to adding liquidity for "insufficient liquidity" case.

2024-09-10 Tue: Got GX [review notes](https://hackmd.io/@polymorpher/gx-country-note) from Aaron. Worked to solve issues: fixes ui texts and links, resolved leverage stuck at pending under "Positions" ans other fixes for sell and trading pages.

2024-09-09 Mon: Synced with Aaron about UniswapV3Oracles issues, looks like it's a matter of incorrect settings and pools addresses (waiting for updated information). Added a script for quickly adding/configuring tokens to gmx vault and adding liquidity via the console (for new tokens from Aaron).

---

2024-09-06 Fri: [Added](https://github.com/harmony-one/h-gmx-contracts/pull/2) test price feeds with all oracles: UniswapV3MedianOracle, UniswapV3SpotOracle, BandOracleReader - currently only BandOracleReader returns correct values. Tested Fast price feeds and updated [doc](https://docs.google.com/document/d/1N6vLiH4Z691rMn62uZSaUCj5l2jXgJdDmz_ZYCeeCMM) with new items for Aaron.

2024-09-05 Thu: Fixed SecondPriceFeed delta issue, tested price switching with new [UniswapV3MedianOracle]((https://github.com/polymorpher/synth-oracle/commit/51df7093914a275d8093232ae3bda4533ce71598)) from Aaron - working stable. Finishing up working on test cases. Sync with Theo about documentation and missing features for the current version.

2024-09-04 Wed: Worked on test cases and test scripts for keepers services: case of price changes after creating an position, borderline cases of price differences of various oracles (firstPriceFeed and SecondPriceFeed). Got issue with auto switching to firstPriceFeed if the price goes beyond the delta. Working on a fix.

2024-09-03 Tue: Synced with Li and Aaron on priorities and next goals. Started working on test cases (and test scripts) to verify keeper services (Aaron says this is mandatory before release into production). Reviewed [documentation](https://www.notion.so/harmonyone/GX-Technical-Documentation-cca26326258d400cab08f6c3d49013eb) from Theo; Get Uniswap [median-over-time oracle](https://github.com/polymorpher/synth-oracle/commit/51df7093914a275d8093232ae3bda4533ce71598) from Aaron - reviewed and start implementing.

2024-09-02 Mon: Switched to supporting the current version of [gx.country](https://gx.country/) to fix several price synchronization issues in price keeper (To give Aaron a working version for auditing). Need another update for the new oracles used for synthetics (Planning to sync with Aaron to get the final set of tokens and addresses). Continue work on the "Auto-compounding Wrapper page".

---

2024-08-30 Fri: Completed integration and bug fixes in the base gmx interface with morphex contracts (autocompounding). Checked the main cases of adding liquidity, exchange, etc. Deployed a [new version](https://autcompounding.web.app). Start work on the "[Auto-compounding Wrapper page](https://www.morphex.trade/wrapper)" migration - unfortunately did not find the source code for this part of the functionality in the morphex github and need to research requests and contracts call.

2024-08-29 Thu: Сreated a [separate branch](https://github.com/harmony-one/gmx-interface/tree/compounding) for the gmx interface with morphex contracts, configured deployment to a separate [test domain](https://autcompounding.web.app/#/buy). Still have some errors - in the process of being fixed.

2024-08-28 Wed: Researched morphex leveraged trading features for the possibility of their integration into the standard gmx interface and the current stats service. 

2024-08-27 Tue: Moved updates for subgraphs in accordance with the [latest versions](https://github.com/morphex-labs/morphex-subgraph) from morphex to fix synchronization errors. Renamed the names of tokens and wrappers on the contract side for morphex-autocompounder version.

2024-08-26 Mon: Updated subgraphs with new contract version (morphex based). Continue to correct integration errors. Updated Oracles for the main version of gmx. Synced with Li and team about next goals and gmx launch.

---

2024-08-23 Fri: Getting errors when testing ux using the merged (autocompounder features to harmony gmx) version of contracts. [Created](https://github.com/harmony-one/h-gmx-contracts/commit/48c71a05609b3e907ad77d730a6d3fcd617be764) a separate branch with a version of contracts from morphex - will use it as a basis. Deployed a new version of contracts and continue testing.

2024-08-22 Thu: Worked on updating the rewards page. Fixed subgraph and ux issues. Working on compiling documentation on deployment and changes for gmx autocompounder version.

2024-08-21 Wed: Created a separate version of the gmx interface for autocompounder fetaure. Integrated morphex contracts (with autocompounder support) to gmx interface. Mograted staked GXP page to new interface. Working on rewards page.

2024-08-20 Tue: After discussing the roadmap with the team, we decided that we are making 2 versions of GMX - in the first we fix the already working functionality (and have passed the security audit) and at the same time I am working on a version with new features: I have divided the code base and working on a separate repository and interface for the autocompounder version.

2024-08-19 Mon: Continue to work on a simple demo for the auto compounder feature within the gmx application. Implemented a page with the ability to staked GXP for deposits. Testing and debugging. Synced with Li, Frank and Artem about goals and roadmaps.

---

2024-08-16 Fri: Researched morphex app sources to reproduce [earn wMLP](https://www.morphex.trade/wrapper) and [Rewards](https://www.morphex.trade/earn) features. Unfortunately, there are no sources for ux, but the algorithm is clear from the documentation. Started working on a simple demo to demonstrate the auto compounder feature.

2024-08-15 Thu: Worked on scripts for testing the full staking cycle from deposit to get claimable rewards using contracts: RewardRouterV4, StakedGmxTracker, BonusGmxTracker, FeeGmxTracker. Get errors at the step when RewardRouter deposits the StakedGmxTracker tokens into the BonusGmxTracker - debugging the problem, working on fixing it and selecting the correct configuration.

2024-08-14 Wed: Continue work on new deploying and configuring scripts with new staking contracts for autocompounder feature. Reviewed and integrated an new oracles [synth-oracle](https://github.com/polymorpher/synth-oracle/tree/main/contracts) from Aaron for gmx first priceFeed.

2024-08-13 Tue: [Added](https://github.com/harmony-one/h-gmx-contracts/commit/e7e4e1f2a45cc42a9b39d0d4965bcb3256dc5f4e) RewardRouterV4 and [StakingRewardRouter](https://github.com/harmony-one/h-gmx-contracts/commit/83044f2ec3dcfcfcf217d1ddbc2ed8624fd9987a) based on contracts that use [morphex.trade](https://docs.morphex.trade). Worked on updating the deployment scripts and integrating new contracts into the current system.

2024-08-12 Mon: Corrected and improved the update of Rewards scripts. Worked on adding paired wGXP with native-protocol token, GMX, to form our native liquidity pair (wGXP-GMX) without the need for a or second native liquidity pair. Synchronized with Artem regarding bug in staking dashboard validator profile update (request from Soph) - looks like there is a problem with SSR caching.

---

2024-08-09 Fri: Worked on autocompounder feature. Expanded the deployment script by adding the StakedGlp contract to the deployment (provide a way to transfer staked GLP tokens by unstaking from the sender and staking for the receiver). Testing with RewardRouterV2.

2024-08-08 Thu: Synced with Pablo and Theo about the most relevant additional features on top of GMX. We decided that the simplest and most relevant would be the integration of autocompounder. Morphex (gmx fork) does it natively. Researched morphex [staked GLP contract](https://github.com/morphex-labs/morphex-contracts/blob/main/contracts/staking/StakedGlp.sol). Working on integrating these contracts into our ecosystem.


2024-08-07 Wed: Synchronized with Pablo about adding additional features for GMX v1. Researched [features](https://www.notion.so/harmonyone/Campaigns-and-Incentives-06f7083707614025a6d92b9d32f054ce) that can be implemented on top of GMX: Autocompounding vaults, Leverage GLP, [Delta-netutral vault](https://medium.com/deus-ex-dao/deep-dive-into-rage-trades-delta-neutral-vaults-3e8f71af82c3) (by example [Umami delta-neutral vaults](https://frogsanon.neworder.network/articles/delta-neutral-yield-with-umami-finance) for GMX).

2024-08-06 Tue: Reviewed the draft technical [documentation](https://www.notion.so/harmonyone/GX-Technical-Documentation-cca26326258d400cab08f6c3d49013eb) from Theo and Pablo. Worked om resolving earn page issues: stake v1 feature, reward stats display etc.

2024-08-05 Mon: Created an integration test to check price keeper service work (secondPriceFeed oracle) in different cases: correct price update, case when price keeper stopped updating the price, case when price keeper is hacked and sets a false price - blocking and switching to firts priceFeed (band oracle). Switched to working on the Earn page (together with Rikako).

---

2024-08-02 Fri: Synchronized with Artem about the latest version of the [BandOracleReader](https://github.com/harmony-one/band-oracle-reader) contract (used as priceFeed for gmx), added support for the gmx vaultPriceFeed contract (latestAnswer view), deployed contracts for tokens used in gx.country. Testing the entire system: priceFeed contract, secondPriceFeed contract, [price keeper](https://github.com/harmony-one/gmx-price-keeper), [watcher](https://github.com/harmony-one/gmx-price-keeper), [band-oracle-updater](https://github.com/harmony-one/band-oracle-updater).

2024-08-01 Thu: [Added](https://github.com/harmony-one/gmx-price-keeper/commit/30e4fad96b8fb604deae6f5513d5a0204bf98fe0) fastPriceFeed contract price monitoring service (takes the price from independent sources, compares it with the price in the contract and blocks contracts if the delta is exceeded). Working on updating the security audit documentation to take into account the new service.

2024-07-31 Wed: Worked on adding a new watcher service for price feed keeper - which should monitor the state of the price in contracts and [disable](https://github.com/harmony-one/h-gmx-contracts/blob/master/contracts/oracle/FastPriceFeed.sol#%20L287) receiving prices from second price keeper if it becomes incorrect (In accordance with the security requirements of secondPriceFeed developers and security audit from Aaron).

2024-07-30 Tue: [Integrated](https://github.com/harmony-one/gmx-interface/commit/eec8abaa5e9485af794690b36891e86d531a1353) dashboard page to gmx interface. Got feedback on the [security audit](https://docs.google.com/document/d/1N6vLiH4Z691rMn62uZSaUCj5l2jXgJdDmz_ZYCeeCMM/edit?usp=sharing) from Aaron - researching the highlighted points and generate a report on the necessary list of services to eliminate potential vulnerabilities. 

2024-07-29 Mon: Connected a band oracle [contract](https://github.com/ArtemKolodko/synthetix/pull/3/files) with a chainlink interface as first price feed (for now only for WBTC). Tested the price update. Fixed gmx interface ui issues.

---

2024-07-26 Fri: Created a [document](https://docs.google.com/document/d/1N6vLiH4Z691rMn62uZSaUCj5l2jXgJdDmz_ZYCeeCMM/edit?usp=sharing) to discuss security audit. Added more information about using keepers and price oracles. Continue the security audit with Aaron. Working on the integration [BandOracleReader](https://github.com/ArtemKolodko/synthetix/pull/3/files) (from Aaron) as priceFeed for gmx Vault. it looks like we will be able to use the same oracles for gmx and synthetix, which is much more convenient and safer.

2024-07-25 Thu: Fixed a problem with displaying charts: [added](https://github.com/harmony-one/gmx-subgraph/commit/a31cbb6f1b03c05556da9c1256da085abd1f8ce8) gmx-h-prices subgraph, [updated](https://github.com/harmony-one/gmx-stats/commit/78451b479b7bf1f79706893ad40626e9f6e3d749) gmx-stats service. [Reviewed](https://github.com/harmony-one/gmx-interface/pull/7) and merged Rikako's interface updates. Received the first feedback on the security audit from Aaron - he highlighted the main vulnerabilities associated with the work of keepers. I will prepare additional documentation describing the work of these services and related contracts.

2024-07-24 Wed: Had a meeting with Pablo and Alania about the launch of gmx. Worked on fixes based on feedback from Pablo. Deployed an updated version of the contracts/interface/keeper.

2024-07-23 Tue: [Forked](https://github.com/harmony-one/h-gmx-contracts) a completely new gmx-contracts repository so that it had all the latest changes and also transferred edited [deployment scripts](https://github.com/harmony-one/h-gmx-contracts/commit/3edccd0ffeedf8b44e471b7bdacb97d73bc19a33) and other changes to it. Updated [deployment](https://github.com/harmony-one/h/blob/main/docs/gmx-v1-deploy.md) documentation and [changelog](https://github.com/harmony-one/h/blob/main/docs/gmx-changes.md). Synced with Aaron to start a security audit.

2024-07-22 Mon: [Updated](https://github.com/harmony-one/gmx-price-keeper/commit/d2a0a3e2d1269ff94ecc93e72217a5e8f23e03b6) price keeper: functionality for updating prices bedore executing positions, added binance api for loading prices, added more [APIs](https://gmx-keeper.fly.dev/ap) to track the status of the service. Worked on [deploy scripts](https://github.com/harmony-one/h-gmx-contracts/commit/3edccd0ffeedf8b44e471b7bdacb97d73bc19a33) refactoring: combined the deployment into a single file, added a config with addresses that will have access to contact management, removed unnecessary comments etc

---

2024-07-19 Fri: [Competed](https://github.com/harmony-one/gmx-price-keeper/commit/41954f309f190bd3c84f6f432397bfaa6be4edf4) position keeper service module. [Fixed](https://github.com/harmony-one/gmx-contracts-v1/pull/3) several contracts settings on deploy: liquidation fee usd was too high and blocked ececution for increased positions, also changed access settings for routers. Continue working on production deploy script/docs.

2024-07-18 Thu: Fixed several bugs in the contract settings that interfered with the execution of positions. Also for a complete ecosystem - started working on the position keeper service (keeper executes the position at the current index price). Received feedback from Rikako on contract deployment scripts - based on this optimizing deployment scripts to make them simpler and easier to understand for auditing (plan to finish by Monday). 

2024-07-17 Wed: Worked on bug fixes based on Alaina and Rikako's feedback: negative liquidation price in ux, issue with position list display, etc.; Worked on technical tests fpr swap, buy USDG, creating long/short positions.

2024-07-16 Tue: [Updated](https://github.com/harmony-one/gmx-contracts-v1/pull/1/commits/f3b1b1dff9cb4c0e334133b79324f384a03ccc3b) deploy script: added OrderBook, redid the section with setting up PositionRouter and PositionManager contracts (This update resolved issue with long positions creation). [Updated](https://github.com/harmony-one/gmx-interface/pull/5/files) interface with new contracts.

2024-07-15 Mon: [Added](https://github.com/harmony-one/gmx-contracts/pull/2/commits/5898cf388c9b4dcbbc08eacaa3dc97f7377eb905) script for auto configuring new tokens by list (ONE, 1ETH, wBTC, 1USDC, 1USDT). Deployed [new version](https://gx.country/) with new contracts, token lists and ux fixes. Synced with Alaina about MVP version. Working on fixing bugs that appear during testing. (Now one of the known bugs is the display of long positions - it seems that the problem is in the configuration of the OrderBook contract)

---

2024-07-12 Fri: Working on updating GLP (and other) token names in the interface and at the contract level. Also working on fixing a page crash due to caching of old addresses in the local storage. Also plan to add the final set of supported tokens: ONE, 1ETH, wBTC, 1USDC, 1USDT. 

2024-07-11 Thu: [Fixed](https://github.com/potvik/gmx-contracts/commit/44106a0add88d14a33577ffb7d0cbdc707c3c096) issue on adding liquidity via interface (mintAndStakeGlp method): added several missing contracts and corrected the address of the native token during deployment and initialization of RewardRouter. [Updated](https://github.com/harmony-one/gmx-interface/commit/2ce7418d5f4ce86aa3220f645f80c7a903477ce7) interface with new contracts addresses.

2024-07-10 Wed: [Updated](https://github.com/harmony-one/h/commit/fd00044843a5b89b476568cda6d723782d84e077) deploy docs (added items for setting up the fastPriceFeed contract). [Fixed](https://github.com/harmony-one/gmx-interface/pull/3/commits/c7be94878a17414a05c1617c7dc733c714db682c) interface issues: loading token balances, correct list of tokens, interaction with the contract. Actual version [here](https://gx.country/#/). Have issue on adding liquidity via interface (on call mintAndStakeGlpETH method) - working on fix.

2024-07-09 Tue: Continued work on integrating the liquidity addition page ([buying GLP](https://gx.country/#/buy_glp)). There are still several errors related to the fact that the price of glp is incorrectly calculated relative to tokens. Localized the problem in the contract settings during deployment - working on a fix.

2024-07-08 Mon: Integrated functionality for [buying GLP](https://gx.country/#/buy_glp) and [adding liquidity](https://gmx-docs.io/docs/providing-liquidity/v1) across the interface. After buying GLP tokens will automatically be staked and user will start earning Escrowed GMX. There are problems with the correct calculation of prices and commissions on this page - working on fixing.

---

2024-07-05 Fri: Synchronized with Theo about the current state of the gmx project and future goals. We identified [adding liquidity](https://gmx-docs.io/docs/providing-liquidity/v1) as the highest priority goal, and began work on integrating functionality for buying GLP and adding liquidity across the interface. I’m also considering the possibility of using already existing uniswap pools, similar to jupiter.

2024-07-04 Thu: [Updated](https://github.com/harmony-one/gmx-price-keeper/commit/9369d4832512de3cc635350f1fdf9cc2e062b367) keeper service (refactoring and bug fixes). Worked on adding test tokens on the mainnet fmx - looking for a way to create liquidity without using real native tokens, so as not to lose balance during the testing process.

2024-07-03 Wed: Tried to deploy the gmx ecosystem on the testnet - but there were problems with the deployment of the subgraph (not supported on the testnet). Therefore, for the demonstration I decided to use the existing version on the mainnet and then add test tokens to it (deployed several test tokens). Reconfigured Vault and Price Keeper for new test tokens. Working on interface updated. Also summarize the results (review of the working functionality) to form a list of remaining technical tasks.

2024-07-02 Tue: Tested the subgraph with events of the FastPriceFeedEvents contract using the new keeper. Worked on changing part of the subgraph: replacing ChainLinkAggregator events handlers. Also began deploying testnet contracts with a large number of tokens to demonstrate realistic pools, etc.

2024-07-01 Mon: Added more APIs for the keeper service: getting the average price for a token, updating the price, getting the price based on the first or second priceFeed (for debugging). The logic for calculating the median price (obtained from coinbase, redstone etc) has also been updated. Engaged in comprehensive testing: keeper - gmx swap - subgraph.

---

**2024 Q2 Review**

Porting GMX v1 to Harmony: [contracts](https://github.com/harmony-one/gmx-contracts-v1), [interface](https://github.com/harmony-one/gmx-interface), [stats](https://github.com/harmony-one/gmx-stats/pull/1/files) and [subgraph](https://github.com/harmony-one/gmx-subgraph/pull/1/files); Created contracts deploy [script](https://github.com/potvik/gmx-contracts/blob/gmx_v1_deploy_script/scripts/deployAll.js), created [scripts](https://github.com/potvik/gmx-contracts/tree/gmx_v1_deploy_script/scripts) for adding tokens and liquidity, added [docs](https://github.com/harmony-one/h/blob/main/docs/gmx-v1-deploy.md) with deploy steps description, added Harmony chain support to all repos. Configured sync and deploy for all services: [subgraph](https://thegraph.com/studio/subgraph/gmx-h-stats/playground), [stats](https://gmx-stats.fly.dev/harmony), [interface](https://gx-country.web.app). I have successfully tested adding liquidity, swap and position creation.

For LayerZero token airdrop, I created scripts to collect statistics for all users who used the LayerZero bridge and scripts for statistics on Swap liquidity pools that used tokens transferred through the bridge (via Swap subgraph). Reviewed and publish the [proposal](https://commonwealth.im/layerzero/discussion/21730-harmony-bridge-rfp).

---

2024-06-28 Fri: Configured gmx keeper service deployment to fly.io. Service APIs are available [here](https://gmx-keeper.fly.dev/api) (now only metrics). Reworked FastPriceFeed deployment scripts to correctly add signers (multiple watcher accounts are currently setup to have the ability to send the transaction to enable spreads). Continue test/bug fixing, writing documentation on using the service and API extension for more convenient testing.

2024-06-27 Thu: [Worked](https://github.com/harmony-one/gmx-price-keeper/commit/a5817f73dc3d1eb349d4c4d1d792f9af2a290f0f) on Position keeper part - added eventLogger for tracking PositionRouter contract events and updating the price in the FastPriceFeed contract when executing a position. Continue working on keeper service deployment and complex service testing. 

2024-06-26 Wed: [Created](https://github.com/harmony-one/gmx-price-keeper) a separate service (based on nest.js) for price feed keeper. It will be deployed on fly.io. The service consists of two parts: Price feed keeper (submits prices routinely for swaps) and Position keeper (submits prices when executing a position).

2024-06-25 Tue: Worked on keepers scripts integration. [Added](https://github.com/harmony-one/gmx-contracts-v1/pull/1/commits/8b9ef57049f825cf479d414933b3d0c27039d6e8) draft version for set price keepers scripts. Setting Price functionality and next price calculation working correctly. Working on coinbase api integration and and migration to the structure of an independent service.

2024-06-24 Mon: Researched various options for gmx secondary price feed (used to compare prices and identify deviations). Current implementation of GMX contracts relies on keppers (more about it [in the following doc (Price Feeds section).](https://gmx-io.notion.site/gmx-io/GMX-Technical-Overview-47fc5ed832e243afb9e97e8a4a036353)). To get the price, kepper can use both oracle and the api of one/several cex. Found a good [implementation of keeper](https://github.com/redstone-finance/gmx-contracts/blob/master/scripts/redstone/keeper/keeper.js) from the redstone-finance team. Working on migration and integration of keeper with our contracts and CoinBase api.

---

2024-06-21 Fri: Gmx v1 on harmony: Worked on updating the gmx subgraph for token price aggregation - in the current version uses secondary priceFeed events and chainlinkAggregator, reworking it to interact with Band Protocol. Also researching other oracles we can use on Harmony for second PriceFeed.

2024-06-20 Thu: Gmx v1 on harmony: completed integration of the primary price feed with Band Protocol, updated deploy scripts and redeployed contracts. Worked on secondary price feed configuration and testing (currently returns an incorrect price when using 2 priceFeed with test values)

2024-06-19 Wed: Gmx v1 on harmony: fixed volume charts issue, updated [gmx stats]( gmx-stats.fly.dev) service - now volume display correctly. Synced with Artem about Band Protocol integration, continue working on new gmx priceFeed contracts and subgraphs (for supporting new price change events).

2024-06-18 Tue: Gmx v1 on harmony:  Resolved deploy issue, now frontend on [gx.country](https://gx.country/#/v1). Worked on migration Gmx priceFeed contracts from Chainlink (chainlink pricefeed deprecated on Harmony) to [BandChain](https://docs.harmony.one/home/developers/tools/oracles/oracle-band-protocol). Researched the reasons why volume is not saved for charts, [fixed](https://github.com/harmony-one/gmx-subgraph/commit/4bf1a26f27124c79221a6161ce45e53de7e866db) several subgraph issues and deployed a new version. Continue testing.

2024-06-17 Mon: Worked on compiling my Q2 results. Gmx v1 on harmony: continue work on the deployment and integration of interface services, gmx stats and subgraph - for displaying graphs (still not displayed in the final interface).

---

2024-06-14 Fri: Gmx v1 on harmony: Fixed sync issue for stats subgraph and [deployd](https://thegraph.com/studio/subgraph/gmx-h-stats/playground) new version. Current subgraph sources [here](https://github.com/harmony-one/gmx-subgraph/pull/1/files). [Updated](https://github.com/harmony-one/gmx-stats/pull/1/files) harmony-gmx-stats with new subgraph urls and harmony contracts. [Deployed](https://gmx-stats.fly.dev/harmony) harmony-gmx-stats to fly.io. Still have issue with volume charts, other should working correct.

2024-06-13 Thu: Gmx v1 on harmony: localized the problem in the stats subgraph - removed some of the problematic contracts and events that interfered with synchronization, also updated the versions of ts packages for assembling the subgraph. Deploying a new subgraph version and continuing to test the statistics service; Also worked on deploy statistic service to fly.io;

2024-06-12 Wed: Created a script to check how many bridge wallets for airdrop LayerZero transferred more than 10, 100, 1000 USD (requested by Theo); Gmx v1 on harmony: Several more problems were found when integrating the gmx stats service with the gmx-harmony subgraph, continue debugging to localize the problem.

2024-06-11 Tue: Gmx v1 on harmony: [updated](https://github.com/harmony-one/gmx-interface/commit/caaac57c1d51f075dd9d82096acf1130644062c3) ux - removed unnecessary texts and meta data; Updated contracts for gmx-raw subgraph (required to display a list of positions). Continue integration and testing subgraphs with gmx stats service. Working on new documentation on connecting and integrating subgraphs.

2024-06-10 Mon: Gmx v1 on harmony: received feedback from Rikako on the deployment script and made corrections - [added](https://github.com/potvik/gmx-contracts/commit/d77fdf035cdd60b43ad72ceb3c641e2c3c42fc1a) deployment of the PositionRouter contract and setting up token pairs; Redeployed priceFeed contracts for tokens with correct [Harmony ChainlinkAggregator](https://docs.harmony.one/home/developers/tools/oracles/chainlink) integration. Updated contracts for gmx-stats subgraph and continue testing.

---

2024-06-07 Fri: Gmx v1 on harmony: [fixed](https://gx-country.web.app/#/v1) all titles, meta and icons in the interface. Waiting for approval from Aaron for deployment to gx.country. During the gmx subgraph research, it turned out that we had the integration of contracts with ChainlinkAggregator configured incorrectly. Reworking the deployment script for the correct interaction of VaultPriceFeed contracts with harmony ChainLink.

2024-06-06 Thu: Gmx v1 on harmony: investigated the issue related to the [license](https://gov.gmx.io/t/labs-proposal/788) to use the gmx interface source code and contracts - since registrar suspended the domain and ask for official permission from GMX. Worked on changing the ux interface to remove corporate logos and gmx names from there. Continue working on stats service integration/launching: pools, positions lists.

2024-06-05 Wed: Gmx v1 on harmony: Fixed issue with long/shorts positions - problem was in incorrected configured Position Router. Redeployed contracts and updated version on [gm.country](https://gm.country). Long/Shorts positions creating correctly, however still have problem with displaying charts and positions lists. Working on issue resolving.

2024-06-04 Tue: Gmx v1 on harmony: worked on deploying interface to gm.country (with Aaron). [Configured](https://github.com/gmx-io/gmx-stats/compare/master...harmony-one:gmx-stats:harmony) and deployed stats service, now testing prices charts with new service. Still have issue with long/shorts positions, continue debugging contracts.

2024-06-03 Mon: Gmx v1 on harmony: part of the interface related to trading V2 has been removed, the current frontend is deployed on the [stand](https://gmx-harmony.web.app/#/v1/swap). Tested the functionality related to the creation of long and shorts - an error was found related to the formation of amount - fixing it. Testing the formation of price charts.

---

2024-05-31 Fri: Gmx v1 on harmony: Resolved issue with wrong price on swap. [Created](https://github.com/potvik/gmx-contracts/commit/1391ca674d1db0b6863daadf8f93d1a59e92b544) new scripts for configuring tokens and add liqudity. Configured and [added](https://github.com/harmony-one/gmx-interface/commit/329be2d900c3d80e929f1eb51f4dc8317dce012d) new tokens to [demo](https://gmx-harmony.web.app/#/v1) stand - right now we can test WONE/BUSD/LINK swap, but with small liqudity. Working on docs for adding new tokens/liqudity.

2024-05-30 Thu: Gmx v1 on harmony: continue to investigate the problem of contracts when swapping tokens, I managed to localize the problem in the VaultReader contract in the getVaultTokenInfoV4 method. Made several fixes for the Vault, VaultReader and GlpManager contracts. Testing a new build.

2024-05-29 Wed: [Posted](https://commonwealth.im/layerzero/discussion/21730-harmony-bridge-rfp) Harmony Bridge RFP proposal using OApps’ deployer address on Ethereum;  Gmx v1 on harmony: [added](https://github.com/harmony-one/gmx-contracts/pull/1/commits/4ce1718dfe91ca7e67cbcb5efcd49667468985d2) contracts abis to deploy scripts repo, [created](https://github.com/harmony-one/gmx-contracts/pull/1/commits/7717541b88398cbf60b8aa32d360d0cb62ab5c69) script for setting new tokens configs and adding liquidity. Continue adding and testing new tokens to swap interface. There is a problem (error on the contract side) when swap tokens with a changing price (not stable coins). There are also errors when placing long positions. I'm debugging the problems and working on a fix.

2024-05-28 Tue: Gmx v1 on harmony: redeployed contracts with new corrected adresses (native token, gov, hrc20 etc), fixed bugs with add liquidity functionality, continue testing. Working on deploy frontend demo to gm.country; Reviewed new proposal on the “RFP Submission" from Theo. Working on submiting a proposal: post proposal using OApps’ deployer address on Ethereum.

2024-05-27 Mon: [Deployed](https://gmx-harmony.web.app/#/v1/swap) harmony-gmx v1 swap interface draft version. Now supported WONE,ONE and USDC tokens. [Working](https://github.com/harmony-one/gmx-interface/pull/1) on bug fixing, charts and stats integration. Reviewed Aaron's vertex [notes](https://github.com/harmony-one/h/blob/main/docs/review-notes-vertex-protocol.md).

---

2024-05-24 Fri: Migration gmx v1 to harmony: Have several issues with [gmx-harmony-subgraph](https://github.com/harmony-one/gmx-subgraph) synchronisation. Looks like several contracts was configured incorrect. Looking for a possible cause of the problem and checking the deployment step by step;

2024-05-23 Thu: Worked on harmony gmx v1 interface: [added](https://github.com/harmony-one/gmx-interface/commit/6aebf5ac42468e44395d93272fd105869dfc2a5a) more harmony configuration settings, fixed bugs. Forked [gmx-subgraph](https://github.com/harmony-one/gmx-subgraph) to harmony. Inspected other backend services for gmx app: stats and main api. [Stats](https://github.com/gmx-io/gmx-stats) looks ok for migration. However, сould not find repositories for the main API service, continue research.

2024-05-22 Wed: [Added](https://github.com/harmony-one/h/blob/main/docs/gmx-v1-deploy.md) gmx contracts deploy notes (links, changes description, deploy instruction and logs). [Forked](https://github.com/harmony-one/gmx-interface) GMX app interface repo to harmony and [added]([https://github.com/harmony-one/gmx-interface/commits/harmony](https://github.com/harmony-one/gmx-interface/commit/73f9e097a6504034f7263ec71c93c3808dceb274)) harmony contracts for testing. Studing server side part integration required to run the gmx app. 

2024-05-21 Tue: [Completed](https://github.com/harmony-one/gmx-contracts/pull/1) draft version for gmx deploy script to harmony. Contracts deploy working correct, continue testing base cases with base [gmx tests](https://github.com/harmony-one/gmx-contracts/tree/master/test). Also inspecting gmx [frontend](https://github.com/gmx-io/gmx-interface) part to integrate it with harmony contracts.

2024-05-20 Mon: Updated script for a more correct selection of Uniswap liquidity pools owners. Now, to get all Uniswap operations, we load all Mint events from [Uniswap subgraph](https://api.thegraph.com/subgraphs/name/nick8319/uniswap-v3-harmony/graphql) api and then filter events by tokens, so that the Uniswap liquidity pool creation operation contain one or more bridge token; Continue work on gmx v1 deploy script: fixed a bug with the gasPrice and gasLimit used, adjusted the binding to the native WONE token. 

---

2024-05-17 Fri: LayerZero oken airdrop: Created a script to load user balances through the explorer API - this is how we want to identify holders with a balance of more than $50; Studied the API and methods for downloading addresses of Swap LP holders - to compare x with LZ broge transfers and generate LP owners list; Reviewed the [proposal](https://www.notion.so/harmonyone/Harmony-LayerZero-Bridge-Form-d8bc6c090d274b9dad28a7b5191d4078) from Theo; Returning to gmx v1 tasks;

2024-05-16 Thu: Received new instructions from Theo regarding the terms of token allocation. We want to introduce 3 new categories: users that bridged, users that provided layerzero LP in Swap, users that hold at least $100 worth of layerzero OFT. For the first category we already have statistics, for the 3rd category we can obtain them based on bridge operations. I'm working on getting statistics on interaction with Swap.

2024-05-15 Wed: LayerZero oken airdrop: completed firbase dump parser and generated several csv documents with a list of addresses and the number of operations on these addresses. In total, there were about 500k unique users based on the analysis of 1.5 million transactions. Continue work on gmx v1 deploy script.

2024-05-14 Tue: LayerZero oken airdrop: Worked on calculating wallet distribution (users who bridged OFTs from 2022/07 to 091/2024). To do this, I have exported firebase db. At the moment there is a difficulty with the number of operations ~ 1.5 million - firebase does not allow running databases of this size on a local emulator or conert to csv another methods. Therefore, I am writing a parser that will go through all the dump files and pull out the necessary data. 

2024-05-13 Mon: Continue working on harmony version for fmx v1 deploy/configure script. Switched to Layer Zero v2 and Sybil actions tasks. Started work on getting a statistic csv of everyone that has interacted with the bridge.

---

2024-05-10 Fri: Continue researching [fork list](https://defillama.com/forks/GMX%20V1) and github [repos](https://github.com/gmx-io/gmx-contracts/forks). I haven’t been able to find a ready-made script for deploying and configuring all contracts yet, so I’m writing our own version based on what I can find in other projects. For example how this [implemented](https://github.com/acria-dominik/gmx-contracts/blob/master/scripts/deployAll.js) for acria-dominik project. 

2024-05-09 Thu: Double check researching results from Tej - checked GMX and other protocols that forked GMX v1. Also don't found suitable protocol for us. Right now main problem that GMX repo doesn’t have the deployment script.

2024-05-08 Wed: Inspected GMX v1 contracts deploy [logs](https://harmonyone.notion.site/Tej-Daily-tasks-and-progress-80ab954954c944acb7f2c3276ff7d439) from Tej. Have a problem that all protocols including the gmx itself didn’t share the deployment script so we need to write it ourselves. Looked at repo for gmx v1 from Tej on harmony GitHub [gmx-contracts](https://github.com/harmony-one/gmx-contracts).

2024-05-07 Tue: Switched to [Port GMX v1](https://www.x.country/q2-tasks-for-defi-48202a8726aa4382800c964bd479060c). Started researching GMX v1 contracts [docs](https://gmx-docs.io/docs/api/contracts-v1/) and [github repo](https://github.com/gmx-io/gmx-contracts). Also looked at other gmx repos: [gmx-interface](https://github.com/gmx-io/gmx-interface) and [gmx-subgraph](https://github.com/gmx-io/gmx-subgraph).

2024-05-06 Mon: Synced with Artem on adding bridge page to Harmony Portfolio. Made a review of the architecture and source code; Started researching and deploying hyperlane according to the [instructions](https://docs.hyperlane.xyz/docs/deploy-hyperlane).

---

2024-05-03 Fri: Got an update on the tasks from Theo, looking at the projects from the [post](https://twitter.com/ayyyeandy/status/1786017371490050270?s=12) and exploring them further on the opportunities fork to Harmony.

2024-05-02 Thu: Synchronized with Frank regarding the integration of 1Bot and harmony-llm-api with swap, bridge and copy-trading services. Working on the overall system architecture.

2024-05-01 Wed: Bridge support: Fixed several bridge explorer issues. On the recommendation of CoinGecko, we have prepared a bridge transition to a new API for fetching asset prices (new demo key plan). Continue to study available copy trading projects in various chains.

2024-04-29 Tue: Studied the list of popular [GitHub projects](https://github.com/search?q=copytrad+forks%3A%3E1&type=repositories) dedicated to online copy trading. Look at several popular copy trade projects: [copycat dex](https://copycat.finance/) and [MQL-CopyTrade](https://github.com/jiowcl/MQL-CopyTrade). So far, it has not been possible to find ready-made solutions for onchain copy trading that could be migrated to Harmony.

2024-04-28 Mon: Synchronized with Theo and Frank for new tasks. Started working on the [Cross-Chain Copy-Trade](https://www.x.country/harmony-2024-defi-a3e0e851036c45c8ace41bd2aadd6f56) project. I plan to focus on the bridge/swap services part. Started exploring available options for bridges from Arbitrium the 100 assets via layerzero or other services.

---

2024-04-25 Fri: Synchronized with Artem regarding  Layer 3 docs for Timeless with general description of decentralized protocols for open social graph ([link1](https://docs.google.com/document/d/1UzcdSHSmSiJDMoqyJxgUjFLq-b6ENHric3LGY3c5hZU/edit#heading=h.c19i328f5vkb), [link2](https://docs.google.com/document/d/1_X4Yltq5PH2mpRrJ5v__EXG2rePQs6W3502v9ltlxLQ/edit#heading=h.i6qb1k6n8fs6)). Сontinue to explore the implementation steps.

2024-04-24 Thu: Сontinue to explore the implementation steps (technologies and architecture) and variants of using cross-chain social profiles in shard 1 (for data availability using celestia rollup) as "layer 3" for timeless.

2024-04-24 Wed: Received from Theo and Zi new [documents](https://docs.google.com/document/d/1_X4Yltq5PH2mpRrJ5v__EXG2rePQs6W3502v9ltlxLQ/edit#heading=h.4ihjx9h9iq7m) on a general description of the concept of decentralized protocols for an open social graph. Continue study the possibility of building layer 3 protocol as an open social graph that users onboard to through his timeless wallet.

2024-04-23 Tue: Inspected and fixed an issue with the Horizon Bridge explorer backend that was losing connection to Firestore, causing the explorer and layerzero operations to become out of sync. Synced with Theo regarding Layer 3 protocol implementation plan [docs](https://docs.google.com/document/d/1UzcdSHSmSiJDMoqyJxgUjFLq-b6ENHric3LGY3c5hZU/edit#heading=h.c19i328f5vkb).

2024-04-22 Mon: Fixed several bugs for LlamaIndex and Together.ai RAG chatbot [demo](http://52.34.253.225:8080). Started research zi timeless integration [docs](https://docs.google.com/document/d/1UzcdSHSmSiJDMoqyJxgUjFLq-b6ENHric3LGY3c5hZU/edit#heading=h.k2ersq95akhf).

---

2024-04-19 Fri: Configured and [published demo](http://52.34.253.225:8080) for LlamaIndex and Together.ai RAG chatbot, with vector store data generated by [pdf summary](https://github.com/harmony-one/rag-llama-together/tree/main/example_data) (linkedin resume). This can be tested [here](http://52.34.253.225:8080) by asking the bot questions such as "What is a summary of this document?" etc. Sources where published [here](https://github.com/harmony-one/rag-llama-together).

2024-04-18 Thu: [Created app](https://github.com/harmony-one/rag-llama-together): powered by [LlamaIndex](https://www.llamaindex.ai/) and [Together.ai](https://www.together.ai/) RAG chatbot using Next.js bootstrapped with [LlamaIndexTS](https://github.com/run-llama/LlamaIndexTS/tree/main). Also using Mixtral (through Together AI Inference) and [Together Embeddings](https://docs.together.ai/docs/embeddings-rag). It'll embed the PDF file in data, generate embeddings stored locally, then give you a RAG chatbot to ask questions to.

2024-04-17 Wed: Continue researching [LlamaIndex TogetherLLM](https://docs.llamaindex.ai/en/stable/examples/llm/together) / sick half-day-off

2024-04-16 Tue: Researched other solutions based on ElasticSearch and LlamaIndex. Researched [Together.ai](https://www.together.ai/) [RAG Integrations](https://docs.together.ai/docs/embeddings-rag). The most promising and appropriate assembly looks [LlamaIndex TogetherLLM](https://docs.llamaindex.ai/en/stable/examples/llm/together)

2024-04-15 Mon: Studied the possibility of using SingleStore with AWS and use cases with Shard 1. Still lacking a general architectural understanding of the system. I'm planning to do another sync with Aaron.

---

2024-04-12 Fri: Synced with Aaron regarding the vector store. Discussed the [article](https://arxiv.org/pdf/2402.13435.pdf): not something we can copy and paste since it is uses a lot of LinkedIn proprietary data and unique structure. We decided that we could start development with some existing systems such as SingleStore

2024-04-11 Thu: Started studying RAG and vector store for the LinkedIn resumes we have collected. Planning design vector store for Shard 1 Resume collection (have a system that can efficiently retrieve a reasonably small collection of relevant resume (100-500) from a very large pool (1M) given some context text descriptions)

2024-04-10 Wed: Fixed several errors that prevented services from starting [op-batcher](https://github.com/ethereum-optimism/optimism/tree/develop/op-batcher) and [op-proposer](https://github.com/ethereum-optimism/optimism/tree/develop/op-proposer) services. Started testing the interaction of rollup layers using
 [optimism sdk](https://docs.optimism.io/builders/chain-operators/tutorials/sdk).

2024-04-09 Tue: Testing and fixing synchronization stage errors for the rollup services on an aws machine. Started deploying [op-batcher](https://github.com/ethereum-optimism/optimism/tree/develop/op-batcher) and [op-proposer](https://github.com/ethereum-optimism/optimism/tree/develop/op-proposer) services.

2024-04-08 Mon: Deployed the op-node and op-g-eth services corrected for harmony shard 1 on an aws machine. [Generated](https://github.com/potvik/optimism/pull/1/commits/b3c3f939e29cfa2923bec950b41cc5c9a7e9fc44) artifacts for contracts and transferred them to the AWS instance. Started testing rollup synchronization step on an AWS machine.

---

2024-04-05 Fri: During local testing, I received a set of block validation errors when synchronizing L2 with Harmony Shard 1 (L1). Partially [disabled](https://github.com/potvik/optimism/pull/1/commits/33e9b3449757190e13629a4cc93e3872f3b3e7e6) block validation to continue synchronization. I continue to debug the op-node service and search for the cause of the errors.

2024-04-04 Thu: To solve the problem with deploying contracts to L1 Harmony Shard 1 (described earlier), [disabled](https://github.com/potvik/optimism/pull/1/commits/e0d272c6c226adf871523b3fc770f70480633a91) the use of create 2. Also corrected several scripts to use legacy transactions instead of the EIP-1559 ones.

2024-04-03 Wed: Tried to solve the problem using [Create2](https://book.getfoundry.sh/guides/deterministic-deployments-using-create2) [deployer](https://github.com/Arachnid/deterministic-deployment-proxy) on Harmony. It is possible to deploy create2 to another (not default) address on Harmony. The only issue is to force Foundry to use another address instead of default one. It is technically doable, just need a bit more time to do this. But keep in mind, that the permit2 address will be different than the default (official) one. And it is impossible to deploy it to the official address, unless Harmony Mainnet will disable EIP-155 (at least for 1 transaction). Here is a long issue thread on foundry github related this [issue](https://github.com/foundry-rs/foundry/issues/2638). It is still opened btw.

2024-04-02 Tue: Continue building custom [Op Stack rollup](https://docs.optimism.io/builders/chain-operators/tutorials/create-l2-rollup) and deploying L1 contracts on Harmony Shard 1. A problem was discovered when deploying contracts. Create2 deployer that is used by Foundry (and therefore by script for deploying permit2) is not deployed on Harmony, and it cannot be deployed, because its transaction is presigned without chainId, and Harmony is EIP-155 protected, which requires chainId to be a part of the transaction.

2024-04-01 Mon: Continue building custom [Op Stack rollup](https://docs.optimism.io/builders/chain-operators/tutorials/create-l2-rollup). Configured configs for op-node and op-geth services to support Harmony Shard 1. Proceeded to deploying and configuring contracts.

---

2024 Q1 Review (8 hours)

I developed the Inscriptions indexer backend and the OneScriptions hrc20 frontend. Additionally, I created the Inscriptions lottery main page and implemented the lottery backend and stats API. For the Human Protocol project, I focused on Firebase design and interaction, frontend features, locations features. 

Added optimisations for the Human Protocol project: added firestore persistent Local Cache for all queries, connected infinity scroll for the actions table with lazy loading of 100 elements, optimized pages loading time (main page, feeds list) from 8 sec to 1 seс.

I conducted an architecture study for a sovereign rollup on our Shard 1. Furthermore, I deployed and integrated an OP Stack Rollup with Harmony Shard 1, which is currently in progress.

2-Week Deliverables by 2024-03-31:

Build sovereign Celestia rollup on Harmony Shard 1, deliver benchmark metrics for shard 1 as a data availability competitor to Near and Celestia (see Near's graphic)

---

2024-03-29 Fri: Unfortunately, it was not possible to integrate the ready-made [Op Stack rollup Node](https://github.com/smartcontracts/simple-optimism-node/tree/7a962f5f6c9fedfd082a72369257af086d2e30c9) build to work with Harmony Shard 1. For full deployment and support on Harmony Shard 1, we will need to build all services from source code, prepare configs, deploy and configure L1 and L2 contracts.

2024-03-28 Thu: There were compatibility problems when synchronizing op-node (optimism L2) and Harmony Shard 1. I am studying the source code and the rpc request format used to localize the problem.

2024-03-27 Wed: Synchronized with Diego about creating an aws instance for an op stack node containing op-geth and modules op-node. Deployed a op simple node in a docker container on aws, configured a grafana dashboard to display synchronization.

2024-03-26 Tue: Synchronized with Sun. Based on his meeting with Stephen, we decided to continue deploying Op Stack rollup without Celestia and Celestia with Rollkit in parallel. Because it is not yet clear what final architecture we will choose - we continue to work on several options.

2024-03-25 Mon: Launched an AWS instance to deploy a rollup. Started setting up and deploying rollup on a production instance. 

---

2024-03-22 Fri: Launched Polaris EVM locally. Connected to celestia dev node. Looking into how we can submit proofs in to Harmony Shard 1.

2024-03-21 Thu: Had a meeting with Sun. Started working on the intial approach of deploying a rollup on Celestia as the data availability layer with Shard 1 as the proof storage. Worked on running the Polaris EVM using Rollkit by [instructions](https://rollkit.dev/tutorials/polaris-evm).

2024-03-20 Wed: Based on the latest update from Stephen started looking at Polaris implementation for Rollkit. Looked at the following architecture Celestia as Data Availability - Shard 1 as just storing proof. Realized that we would need a wrapper around our Harmony nodes, in order for it to work as a data availability layer.

2024-03-19 Tue: Started Celestia Optimism Stack [integration](https://docs.celestia.org/developers/intro-to-op-stack). Researched [optimism](https://github.com/celestiaorg/optimism/) services structure. Tried deploy a smart contract to the celestia testnet. Also tried deploy an OP Stack devnet on Celestia by [instruction](https://docs.celestia.org/developers/optimism).

2024-03-18 Mon: Had a meeting with Sun. Explored our options and concluded that non-sovereign rollups might be a better fit for our project (using Celestia as the data availability layer and Shard 1 as the settlement layer). We think that the simplest and most convenient solution would be Сelestia [Optimism](https://github.com/celestiaorg/optimism/). Started research an deployment of Сelestia Optimistic rollup on Shard 1.

---

2024-03-15 Fri: Build sovereign Celestia rollup on Harmony Shard 1: looked at Op Stack as an alternative: studied Op Stack docs, looked at [optimism](https://github.com/ethereum-optimism/optimism) main services sources: op-program, op-node, op-batcher. 

2024-03-14 Thu: Build sovereign Celestia rollup on Harmony Shard 1: Continue researching rollup contracts for capable of receiving, verifying proofs and transaction summaries. Looking at [Blobstream](https://docs.celestia.org/developers/blobstream) as data availability - this solution contains ready-made solutions and [contracts](https://github.com/celestiaorg/blobstream-contracts) that we can try to fork and use.

2024-03-13 Wed: Build sovereign Celestia rollup on Harmony Shard 1: reviwed new [docs](https://www.notion.so/Sovereign-Celestia-Rollup-on-Harmony-Shard-1-1429d67a09f7462dac242a0ca126a776) from Sun, studied the option of using Rollkit SDK, learning how other EVM rollups interact using smart contracts.

2024-03-12 Tue: Meeting with Sun at which we discussed sovereign rollup development ways. Discussed the difficulties of using sovereign-sdk and cosoms-sdk. Made payments for the remaining 1BTC redeems requests (BTC bridge redeems). Prepared the BTC website (redeems program) for closure.

2024-03-11 Mon: Dived into building rollups using [sovereign-sdk](https://github.com/Sovereign-Labs/sovereign-sdk) (Unfortunately, I don't have enough expirience with Rust - which prevents me from understanding some things). Also could not find adapters on Ethereum EVM. Helped Frank with shutting down the Stable Diffusion servers.

___

2024-03-08 Fri: sick day-off

2024-03-07 Thu: Continue researching [libs](https://github.com/Sovereign-Labs/sovereign-sdk), and [docs](https://docs.celestia.org/developers/rollup-overview) to deploy a rollup using Celestia's SDK on Harmony Shard 1 (for AI, social, game data). 

2024-03-06 Wed: Study of architecture [sovereign rollup](https://celestia.org/learn/sovereign-rollups/an-introduction/) to use it for Harmony Shard 1 (for AI, social, game data).  Researching Zero Gravity [0g.ai](https://0g.ai/) integration.

2024-03-05 Tue: Deployed BOB (Build on Bitcoin) relayer [contracts](https://github.com/bob-collective/bob/tree/master/src/relay) on Harmony testnet and tried to launch BOB relayer service with testnet rpc.

2024-03-04 Mon: Exploring the possibility of launching the BOB (Build on Bitcoin) [ecosystem](https://github.com/bob-collective/bob) on the Harmony side. Reviewing relayer [contracts](https://github.com/bob-collective/bob/tree/master/src/relay).

___

2024-03-02 Fri: Started researching [bitcoin renaissance](https://bitcoin-renaissance.com/) and BOB (Build on Bitcoin) ecosystems. Inspect BOB bitcoin light client [docs](https://docs.gobob.xyz/docs/build/bob-sdk/relay).

2024-03-01 Thu: Worked on the following tasks on h.country: [Added](https://github.com/harmony-one/h.country/pull/103) support for multiple joint filters: address, tag and location. If filter selected and selecting “all” should show all actions with that filter, selecting the user should then toggle to all actions of that filter and that user (nothing if there are no actions) 

2024-02-28 Wed: Worked on the following tasks on h.country: [Fixed](https://github.com/harmony-one/h.country/pull/100) lazy loading issue. Some UI fixes and source code refactorings.

2024-02-27 Tue: Worked on the following tasks on h.country: [Fixed](https://github.com/harmony-one/h.country/pull/97) google maps links format - now the link also includes country, city and postcode. Removed from the list actions that include check-in without an address, also removed false positives for changing location. Minor style edits.

2024-02-26 Mon: Worked on the following tasks on h.country ([PR](https://github.com/harmony-one/h.country/pull/92)): Connected firestore local cache in multiple tab mode. Connected infinity scroll for the actions table with lazy loading of 100 elements. Optimizations speed up page loading from 8 sec to 1 sec.

___

2024-02-25 Sun: Worked on the following tasks on h.country: looked at possible options for optimizing queries in firebase db to speed up application load. Considered cache options (access data offline). [Reviewed](https://github.com/harmony-one/h.country/pull/90/files) user reactions feature. 

2024-02-24 Sat: Worked on the following tasks on h.country [PR](https://github.com/harmony-one/h.country/pull/84): Added ability to set custom location on click to top right location button. Display check-in action in feeds table. Automatically update the current location if the new location is different.

2024-02-23 Fri: Worked on the following tasks on h.country: [Added](https://github.com/harmony-one/h.country/pull/77) location pin button with new logic - opening google maps with preset location on clik. Removed m/ from slash section. [Added](https://github.com/harmony-one/h.country/pull/80) new logic: Click on a location, get taken to that filter page. Next to the location name, there is a pin symbol. Click on that to open the google maps link to that street.

2024-02-22 Thu: Worked on the following tasks on h.country: [Updated](https://github.com/harmony-one/h.country/pull/56/files) display of user links (custom links and social links) in the links area and feeds table. [Added](https://github.com/harmony-one/h.country/pull/58) new logic: every time user refresh page, open a new tab, etc. -  trigger new action of type "check_in" and update the location at the top of the page. [Moved](https://github.com/harmony-one/h.country/pull/63) all fetch hooks to separate files. [Added](https://github.com/harmony-one/h.country/pull/64) top locations display.

2024-02-21 Wed: [Added](https://github.com/harmony-one/h.country/pull/40) filter by location: includes all actions that were performed by users on this street, as well as marks of some users by others. Refactored filters mechanism api.

2024-02-20 Tue: [Added](https://github.com/harmony-one/h.country/pull/27) latest user location display to header (top left). Updated latest location search mechanism. [Added](https://github.com/harmony-one/h.country/pull/32) logic to marked user (page owner) location when you click on a location (top left header); [Added](https://github.com/harmony-one/h.country/pull/34) display for "locates" actions in the actions list (0/f445 (location) 0/EC68); [Created](https://github.com/harmony-one/h.country/pull/33) Actions Context - to reload actions list from any components.

2024-02-19 Mon: [Added](https://github.com/harmony-one/h.country/pull/20) Street name display, added display links actions, fixed links adding issue. [Corrected](https://github.com/harmony-one/h.country/pull/21) street display format, show all actions for new users (first time visit). [Added](https://github.com/harmony-one/h.country/pull/23) displaying latest location address in links section.

___

2024-02-16 Fri: [Added](https://github.com/harmony-one/h.country/pull/4) shortcuts for user page to load page by id, address or social links. Added shortcuts for tag page. Started tag page migration. [Improved](https://github.com/harmony-one/h.country/pull/7) adding links mechanism and url's parsing. Fixed bugs.

2024-02-15 Thu: Tested and reviewed new auth0 [features](https://github.com/harmony-one/human-protocol/pull/21). Synchronized with Theo about migration to a new [project](https://github.com/harmony-one/h.country). Started transferring the logic for creating actions and selecting tags. 

2024-02-14 Wed: [Reviwed](https://github.com/harmony-one/human-protocol/pull/13) auth0 interactioin PR. [Integrated](https://github.com/harmony-one/human-protocol/pull/16) auth0 provider to main page header. Added user's nickname (from auth0) display to main page. New messages are created with a link to the wallet address. Storing auth0 metadata in firebase (by wallet address key).

2024-02-13 Tue: [Migrated](https://github.com/harmony-one/human-protocol/pull/12/commits/15f65efc2ab3d180021f0f86f568c21a3db8e6e3) more updates from remote-emitter. Fixed bugs. Started working on auth0 integration and storing oauth metadata in firebase.

2024-02-12 Mon: [Merged](https://github.com/harmony-one/human-protocol/pull/12) Julia's remote-emitter to human-protocol client, migrated to typescript, refactoring.

___

2024-01-09 Fri: Configured telegram [lottery](https://q.country). Updated lottery statistic. Worked on schema and flow for "message", "mention", and "interest" for human-protocol client and firebase store.

2024-01-08 Thu: [Added](https://github.com/harmony-one/human-protocol/pull/5) firebase based api, for all current cases: adding user with topics, adding actions, auto increment topics counter. Configured firestore. Integrated with frontend part.

2024-01-07 Wed: [Added](https://github.com/harmony-one/human-protocol/pull/1) api based on cloudflare KV service worker. Api support: adding user with topics, adding actions, auto increment topics counter. Integrated with frontend, testing, bug fixing. Added readme with api description. 

2024-02-06 Tue: [Added](https://github.com/harmony-one/human-protocol/commit/c915544727f13678c4927f0929877b21ce66fdfc) Cloudflare KV worker. Configured and [deployed](https://kv-dev-message.humanprotocol.workers.dev/messages) to harmony account. Currently, the service worker supports adding messages (in any format), receiving messages by key, and a list of keys and messages.

2024-02-05 Mon: Synced with Sun and Jenya. Researched ElastiCache: get/set data (location, media etc), and metrics. Researched ETH Denver [project](https://www.x.country/human-protocol-social-shard-1-00e81d36535a4f2981a18012854b2c1e). Started working on service worker.

___

2024-01-02 Fri: Updated lottery statistic [api](https://inscription-indexer.fly.dev/api#/app/AppController_getLotteryStats): added statistic by telegram username. Worked on indexer api optimisations, to add universal support for all inscription types.

2024-01-01 Thu: Updated [frontend](https://github.com/harmony-one/inscription.demo/pull/10) and [backend](https://github.com/harmony-one/inscription.indexer/pull/11) parts for telegram lottery. Extended lottery service: The algorithm for determining the winner has been changed (added 6 winners support). Updated filters by which lottery transactions are indexed.

*2024-01-31 Wed: Сomplete telegram bot image lottery feature. Added telegram inscriptions support to indexer. Extended indexer [api](https://inscription-indexer.fly.dev/api#/app/AppController_getMetaByDomain) to load and return telegram images by imageId from inscription.

*2024-01-30 Tue: [Added](https://github.com/harmony-one/inscription.indexer/pull/10) support for subdomain and redirect paths from indexer so that they can be used by the client side (endpoint for .country, to get content from inscriptions). Expand the database table and add search for new fields, optimisations.

*2024-01-29 Mon: Сompleted set up for lottery 2.0. [Updated](https://github.com/harmony-one/inscription.demo/pull/9) frontend part. Reviewed backend PR's. 

___

2024-01-26 Fri: [Added](https://github.com/harmony-one/inscription.indexer/pull/7) filter for inscriptions, domains monitoring service and provide an endpoint which .country frontend can query to host content. Validation by url, parsing by types. Updated inscriptions indexer instance.

2024-01-25 Thu: [Added](https://github.com/harmony-one/inscription.indexer/pull/6) stats api to get statistic by lottery inscriptions, unique wallets, txs by wallet. Extended logic for calculation winner: diff by 3 symbol if find several winners. [Updated](https://github.com/harmony-one/inscription.demo/commits/main) frontend part.

2024-01-24 Wed: Inscription lottery launch support. [Added](https://github.com/harmony-one/inscription.indexer/pull/4) api to get tweet link by 2 letter domains, correct lottery time interval, fixed bugs. Did several ui [fixes](https://github.com/harmony-one/inscription.demo/pull/7). Deployed main page to [production](https://q.country/) url.

2024-01-23 Tue: [Finished](https://github.com/harmony-one/inscription.demo/pull/3) the demo version for the [lottery main page](https://hmy-inscription.web.app/) (transaction sending, indexer, winner display). [Added](https://github.com/harmony-one/inscription.indexer/pull/2/files) logic to the backend for monitoring and determining the winner, tweet link validations.

2024-01-22 Mon: Dive in the logic of operation of the inscription lottery. Started working on the [main page](https://hmy-inscription.web.app/) for lottery.

___

2024-01-19 Fri: [Worked](https://github.com/harmony-one/inscription.demo/pull/2) on inscription for .country commands. Auctions through gas fee (we get information about the latest domain inscriptions from the indexer and then use it as a minimum gas for the next domain inscription). Still in progress.

2024-01-18 Thu: Reviewed XRCFactory contract from [gwx.one](https://gwx.one). Reviewed Artem's [updates](https://github.com/harmony-one/inscription.indexer/pull/1) for [Indexer](https://inscription-indexer.fly.dev/api). Starting frontend integration with new api.

2024-01-17 Wed: Demo and transfer of the [Indexer](https://github.com/harmony-one/inscription.indexer) codebase to Artem for further development of .country inscriptions. Started XRCFactory contract review. 

2024-01-16 Tue: Worked on resolving a bridge issue related to upgrading the default proof type to 2 (from mpt to FP). Continue research and migration of the ethscriptions-indexer into Harmony.

2024-01-15 Mon: Researched [facet-vm](https://github.com/0xFacet/facet-vm) and [ethscriptions-indexer](https://github.com/0xFacet/ethscriptions-indexer) repos to explore the possibility of migrating ready-made ethscriptions solutions to Harmony.

---

2024-01-12 Fri: Deployed indexer and hrc20 inscriptions [demo](https://hmy-inscription.web.app/). Researched [github.com/okx](https://github.com/okx) to added harmony chain support.

2024-01-11 Thu: [Worked](https://github.com/harmony-one/inscription.demo/pull/1) on frontend demo for OneScription and inscription indexer.

2024-01-10 Wed: Worked on moe project iprovements and migration to to nestjs engine. Inspecting reason and statistics of bridge errors.

2024-01-09 Tue: Looked into inscription implementation and indexer design

2024-01-08 Mon: Fixed stable diffusion backend server issues (inspected server settings for automatic disk cleanup), reviewed moe repository code

---

2024-12-25 Mon - 2024-01-05 Fri: Paid time off.

---

2023-12-22 Fri: Added indexer [demo](https://inscription-indexer.fly.dev/api) for inscriptions. [Repository](https://github.com/harmony-one/inscription.indexer)

2023-12-21 Thu: Helped Frank solve the problem of building a bridge on a local machine. Started working on indexer for inscriptions.

2023-12-20 Wed: [Added](https://github.com/harmony-one/inscription.demo) frontend [demo](https://hmy-inscription.web.app) for sending transactions with inscription via Metamask.

2023-12-19 Tue: Investigated the problem with purchasing domains on 1.country. Research into inscription tokens.

2023-12-18 Mon: [Added](https://github.com/harmony-one/x/pull/399) twitter lists manage feature, which allowed to configure sources via API endpoints (Any user with API key will be able to add / remove / update twitter list in x-api-backend). Started exploring the possibilities of deploying [evm.ink](https://evm.ink/) to Harmony.

---

2023-12-15 Fri: [Implemented](https://github.com/harmony-one/x/pull/391) "Talk to Me" reading data, loaded from backend. Continue working on "twitter-backend" features.

2023-12-14 Thu: Working with Artem on twitter-api backend. [Added](https://github.com/harmony-one/x/commit/5255a1a70c835ec6454d5bcfac16ca0cb59429b5) table, module and controller to store and manage twitter lists. Next it will be used to load tweets for each list.

2023-12-13 Wed: The tutorial for [deploying Harmony Bridge Tokens](https://delirious-crepe-4c3.notion.site/Add-Bridge-support-for-ERC20-dde13f7f64bf44af9aa93f2dfa2e35ba) and [adding new chains](https://delirious-crepe-4c3.notion.site/Add-Bridge-support-for-new-chain-5748fc212a6d4909b64bf2d26802f2e6) has been completed. [Fixed](https://github.com/harmony-one/layerzero-bridge.appengine/commit/f3cdf2ee6a6460ed7fdfa3ef655ff58917054cc6) an issue with displaying "total locked" tokens. Did a live session with Sun during which we added Linea USDT support to Harmony bridge

2023-12-12 Tue: Added Linea chain and Linea usdc token support to harmony bridge: deployed contracts and update configs ([1](https://github.com/harmony-one/layerzero-bridge.frontend/commit/abedb14b9e73ae9d124ca04e66eda06b8fa4cdb3), [2](https://github.com/harmony-one/layerzero-bridge.frontend/commit/5cf0389d0b0ea8febe943857d8ba3e12a76b6620), [3](https://github.com/harmony-one/layerzero-bridge.appengine/commit/f3e71e016973f273fba57f50afd7b1d81d1474aa), [4](https://github.com/harmony-one/layerzero-bridge.appengine/commit/04ca61f993411644d8e9d69e73dac15bba0bbae6)]). Debugged issues, synced with layer zero team to enable linea<->harmony bridging.

2023-12-11 Mon: [Refactored](https://github.com/harmony-one/layerzero-bridge.frontend/pull/20) layerzero bridge frontend & [backend](https://github.com/harmony-one/layerzero-bridge.appengine/commit/a296a8a9b317d58b9d1d405b1db9273cd457b8c1) to do deployment steps more simple. Preparing a training manual.
 
---

2023-12-8 Fri: [Splited](https://github.com/harmony-one/x/pull/329/commits/e303d086f8a4ec664af950a2060ca59b0eb64574) the benchmarks measurement into 5 steps. The steps are done according to Aaron's [instructions](https://github.com/harmony-one/x/blob/main/doc/benchmarking.md). [Extended](https://github.com/harmony-one/x/pull/329/commits/a26e4d960bc23c61bf67025da75a83c140ec6a6a) relay to support more fields.

2023-12-7 Thu: [Added](https://github.com/harmony-one/x/pull/329) benchmarks for "text to speach" and "speach to text" steps. [Extended](https://github.com/harmony-one/x/pull/329/commits/b7331f0bbea63337b3fd0f5a11fa4efbb94a76fc) relay service to support stt, tts metrics. Continue working on kibana manage to display table with all benchmark stats.

2023-12-6 Wed: Tested [build](https://github.com/harmony-one/x/commit/63fa70f6c4118d7bf5fe66cc2a80f2b9d9c83513) with DeepgaramASR to speed up record start. Working on benchmarks with Kibana.

2023-12-5 Tue: Looking for a solution for microphone handling, specifically to resolve the issue where the first word often cuts off. 

2023-12-4 Mon: [Fixed](https://github.com/harmony-one/x/pull/300) build errors for VoiceAi_2 app. [Added](https://github.com/harmony-one/x/commit/8cfd889d3c760d61aa65843110e9a3f91b68ae9e) more tests for CustomInstructionsHandler. Working on benchmark.

---

2023-12-1 Fri: [Added](https://github.com/harmony-one/x/pull/296) elastic client to collect the stats for elasticsearch and next analyze the request time result in kibana. Working with Segey on resolving "Press and Hold" bug.

2023-11-30 Thu: Inspected different ways to collect benchmarks for open ai requests with different network speed. [Added](https://github.com/harmony-one/x/pull/290) sentry perfomance monitoring example. Working on TimeLogger extension to collect the stats for elasticsearch and next analyze the result in kibana.

2023-11-29 Wed: Working on OpenAI Stream benchmark tests for poor network [tests draft](https://github.com/harmony-one/x/pull/284). Continue working on [AppleSignInManager](https://github.com/harmony-one/x/pull/279) tests.

2023-11-28 Tue: Worked on unit tests for [TimeLogger](https://github.com/harmony-one/x/commit/3ae423546370fef7e8a703709a0a6e73e033e1c7), [AppleSignInManager](https://github.com/harmony-one/x/pull/279) and [SettingsView](https://github.com/harmony-one/x/commit/57423c36bd32ad664c846dacb4c6f7b9823fe9c8) modules. [Added](https://github.com/harmony-one/x/pull/277) refacoring optimisations.

2023-11-27 Mon: [Added](https://github.com/harmony-one/x/pull/269) buttons unit tests: GridButton, PressEffectButtonStyle, Theme. Resolving conflicts nad continue refacoring ActionsView [module](https://github.com/harmony-one/x/pull/259) to decrease cyclomatic complexity.

---

2023-11-24 Fri: [Resolved](https://github.com/harmony-one/x/pull/249) conflicts. [Resolved](https://github.com/harmony-one/x/pull/258) Cancel "Tap to speak" record on press any other button. Fixed eslint errors and build issues. [Refactored](https://github.com/harmony-one/x/pull/259) ActionsView to decrease cyclomatic complexity.

2023-11-23 Thu: [Fixed](https://github.com/harmony-one/x/pull/249) problems when pressing multiple buttons at the same time (now you can't use "Tap to speak" and "Press and hold" at the same time).

2023-11-22 Wed: [Improved](https://github.com/harmony-one/x/pull/245) "Pres & Hold" button handling (fixed lags on spam). [Removed](https://github.com/harmony-one/x/pull/246) long press handling from all buttons; Added "More Action" button. Working on improving buttons handling on "many buttons press case".

2023-11-21 Tue: [Fixed](https://github.com/harmony-one/x/pull/237) "Tap to Speak" issues: changed to "Tap to Speak" instead of "Tap to SPEAK", fixed colors blink on spam, fixed button delay and lags on spam. [Increased](https://github.com/harmony-one/x/pull/239) openAI rate limits. Continue working on tests.

2023-11-20 Mon: [Added](https://github.com/harmony-one/x/pull/231/files) unit tests for: ThemeManager, NetworkManager, AppleSignInManager modules. Updated NetworkManager module to improve test coverage; Added mocks for emulation network response.

---

2023-11-17 Fri: [Configured](https://github.com/harmony-one/x/pull/211) "Voice 2" build for internal testing. Сontinue work on unit tests for stream modules and ui buttons.

2023-11-16 Thu: [Resolved](https://github.com/harmony-one/x/pull/197) bugs regarding long press triggering tap functionality (when pressing long, unnecessary actions were triggered). Investigating the possibility of eliminate mic initialization lag when using "Press & Hold".

2023-11-15 Wed: [Implemented](https://github.com/harmony-one/x/pull/189) button debounce after 10 taps to prevent crashes, also fixed pause/play lag. [Added](https://github.com/harmony-one/x/pull/192) UI tests for new cases. Working on delay correction long press triggers in App purchase.

2023-11-14 Tue: Working on setup more comprehensive/granular sentry logs. Helped Nagesh with setup/test [branch](https://github.com/harmony-one/x/pull/182) (uploads dsym file). [Added](https://github.com/harmony-one/x/pull/183) swiftlint tool to enforce Swift style and conventions. Fixed project sources lint styles.

2023-11-13 Mon: Working on setup buttons [debounce](https://github.com/harmony-one/x/pull/170/files) to have better app stability (prevent crashes etc). Working on setup more comprehensive/granular logs (sentry)

---

2023-11-10 Fri: [Resolved](https://github.com/harmony-one/x/pull/161) issue with long press actions (Ensure long press actions do not trigger tap actions vice versa). Working on tracking active using app time and showing suggestions to share with friends and share on Twitter.

2023-11-9 Thu: [Added](https://github.com/harmony-one/x/pull/148/files) the ability to repeat the current session to resolve repeat bug (When hitting "Repeat" during the first stream, it says "Hey" while the stream is going. It should just start again from the beginning instead.) 

2023-11-8 Wed: Continue working on [error capturing](https://github.com/harmony-one/x/pull/136) based on Aaron's [checklist](https://github.com/harmony-one/x/blob/main/doc/checklist.md). Added action buttons metrics based on sentry ui metrics.

2023-11-7 Tue: [Working](https://github.com/harmony-one/x/pull/136) on logging an iOS application using sentry.io as a platform for storing and viewing logs

2023-11-6 Mon: Working on reolving "speaker popping" issue (reproduced on quickly pause/play switch and new sessioan start). Bridge tasks support (btc tranquil payments).

---

2023-11-3 Fri: Working on build and review unit tests for voice ai. Updated staking dashboard ui. bridge tickets support.

2023-11-2 Thu: Working on different UI fixes: beep signal on released speak button, speak and pause bottons color changing sync, pause button blinks. Continue working on unit tests update. 

2023-11-1 Wed: Working on UI fixes for Press to Speak button (colors, stuck). Unit tests for GPT Streaming module (in progress). Support for staking dashboard with mainnet shard reduction from 4 to 2.

2023-10-31 Tue: [Added](https://github.com/harmony-one/x/pull/94) ChatGPTSwift lib for better gpt streaming stability / resolving bugs. Working on unit tests for Streaming module and UI components.

2023-10-30 Mon: (Resolve bugs in GPT streaming PR, specifically button interaction and async request/response handling) Continue working on GPT streaming [PR](https://github.com/harmony-one/x/pull/84)

---

2023-10-27 Fri: [Added](https://github.com/harmony-one/x/pull/80/files) deepgram streaming to main app. Working on button integration with streaming workflow.

2023-10-26 Thu: Reviewed Aaron's streaming code pr's. [Copied](https://github.com/harmony-one/x/pull/72) streaming core sources to ios-yuriy for next whishper integration. Continue working on bugs from kanban board.

2023-10-25 Wed: Working on bug fixes for Voice AI app: the "Speak" button becomes non-functional while ChatGPT is processing, and the "Pause" button loses its functionality while the response is being processed.    

2023-10-24 Tue: Continue working on full IOS end-to-end demo using Whipser, GPT4, and Elevenlabs: setup build and starting integrate Whipser speach to text via rest api.

2023-10-23 Mon: Started working on full IOS end-to-end demo "Emotion Build" (using Whipser, GPT4, and Elevenlabs). Reviewed Hey Julia project sources. [Added](https://github.com/harmony-one/x/tree/ios-emotion-build/mobile/samantha) project structure.
 
---

2023-10-20 Fri: Added more text to speech integrations to willow demo: [Google Cloud](https://github.com/harmony-one/x/pull/44), [Microsoft Azure](https://github.com/harmony-one/x/pull/50). [Added](https://github.com/harmony-one/x/pull/48) select dropdown for speach to text to willow demo. Started setting up play.ht

2023-10-19 Thu: [Added](https://github.com/harmony-one/x/pull/44) STT Deepgram streaming widget for wis demo. Working on table to see historical latency data to compare.

2023-10-18 Wed: 
Started work on Emotion build. [Added](https://github.com/harmony-one/x/pull/39) TTS Core select (Elevenlabs + Willow microsoft model) for WIS end to end [demo](https://yuriy.x.country/). [Added](https://github.com/harmony-one/x/pull/41) more metrics (stt + llm + tts).

2023-10-17 Tue: 
Completed WIS end to end [demo](https://yuriy.x.country/) Working on streaming for WIS STT.

2023-10-16 Mon: 
[Working](https://github.com/harmony-one/x/pull/27) on full end-to-end gui for Willow based on Willow [rest api](https://54.186.221.210:19000/api/docs#/)

---

2023-10-13 Fri:
[Willow demo draft](https://github.com/harmony-one/x/pull/17) Added willow demo draft. webrtc stt working, continue working on other functions (tts, sts, speaker change). [Resemble AI demo](https://github.com/harmony-one/x/pull/19)

2023-10-12 Thu:
[Added](https://github.com/harmony-one/x/pull/10) the gdansk-ai repository, worked on deployment and setting up the environment. Started diving into api/docs for Willow inference server - for the next creation of a webapp demo.

2023-10-11 Wed: [1 part](https://github.com/harmony-one/x/pull/7) [2 part](https://github.com/harmony-one/x/pull/8) - Added storing/displaying of gpt chat history + updated UI; [Refactoring](https://github.com/harmony-one/x/pull/6) - Added Mobx state manager, update layout; Working on store/display metrics for (stt-gpt-tts) (eta - today)

2023-10-10 Tue: [Completed](https://github.com/harmony-one/x/pull/4) - Added tts audio player, integrated with elevenlabs (rest) and gpt streams, integrated with Artem's PR's. Code refactoring. Started work on UI improvements.

2023-10-09 Mon: I tried different options for working with TTS Elevenlabs (rest, ws), tried different sentence breakdowns. At the moment, we managed to achieve requests of 1.3 seconds for each sentences from the chatgpt stream. Also the current tts engine has many problems and often audio tracks overlap each other - a player is needed to manage them. Then i started working on the adding the tts audio player to project (smart management of audio chunks), and its integration with the chatgpt and elevenlabs stream [Worked](https://github.com/harmony-one/x/pull/4)
