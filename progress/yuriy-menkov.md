2024-09-11 Wed: [updated](https://gx.country/) GMX interface after Aaron's final review notes, worked on pore updates: changing "Long" to "USD" on trading page, adding USD token as the target token under "Short" either, added links to adding liquidity for "insufficient liquidity" case.

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

2024-04-03 Wed: Tried to solve the problem using [Create2](https://book.getfoundry.sh/tutorials/create2-tutorial) [deployer](https://github.com/Arachnid/deterministic-deployment-proxy) on Harmony. It is possible to deploy create2 to another (not default) address on Harmony. The only issue is to force Foundry to use another address instead of default one. It is technically doable, just need a bit more time to do this. But keep in mind, that the permit2 address will be different than the default (official) one. And it is impossible to deploy it to the official address, unless Harmony Mainnet will disable EIP-155 (at least for 1 transaction). Here is a long issue thread on foundry github related this [issue](https://github.com/foundry-rs/foundry/issues/2638). It is still opened btw.

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
