2025-04-04 Fri: started researching vfat auto-rebalancing for [USDC.e/scUSD](https://vfat.io/farm?chainId=146&farmAddress=0xf8440c989c72751c3a36419e61b6f62dfeb7630e&poolId=0) vault to compare with other volatility models. Checked vfat and underlying shadow pool contracts, [collected](https://github.com/harmony-one/shadow-scraper/commit/f780cff6e9d49c77dd13aca183487d7876df9af5) methods to track position ticks range and current tick in the pool.

2025-04-03 Thu: [completed](https://github.com/harmony-one/shadow-scraper/commit/30323f03fdff135c5ee99b15a30da48ce8af1811) magpie pendle portfolio [export](https://github.com/harmony-one/shadow-scraper/blob/main/export/portfolio_0x881E625E5C30973b47ceE3a0f3Ef456012F13f7D_1743673030.tsv) (#5 in /farms): base apr is around 3% for aUSDC pool, this number correlates with base reward from the dashboard. Additional rewards, such as SY, wasn't found in reward contracts, continue researching. Started looking at the rest pools from /farms: euler (#2), silo (#3), beefy (#7).

2025-04-02 Wed: [added](https://github.com/harmony-one/shadow-scraper/commit/2e98c1daf071255ec8b19dc9e988a9f6a77c9a39) address transactions history to portfolio [export](https://github.com/harmony-one/shadow-scraper/blob/main/export/portfolio_0x881E625E5C30973b47ceE3a0f3Ef456012F13f7D_1743604632.tsv); data is fetched from Sonicscan API, wallet balance is calculated in USD and S at the time of each transaction.

2025-04-01 Tue: completed manual research of [magpie usdc](https://www.pendle.magpiexyz.io/stake/0x3F5EA53d1160177445B1898afbB16da111182418) pool and calculation of pending rewards based on data from smart contracts, results fully matched with magpie dashboard; started implementation in portfolio script.

2025-03-31 Mon: portfolio script: updated formatting of APR and amount fields, added pool label, deposit link, [exported](https://github.com/harmony-one/shadow-scraper/blob/main/export/portfolio_0x4E430992Db6F3BdDbC6A50d1513845f087E9af4A_1743422366.tsv) new version. Started looking at Silo, Pendle and Beefy pools to collect rewards data in portfolio script. Added [article](https://github.com/harmony-one/shadow-scraper/blob/main/docs/uniswap_liquidity_calculation.md) on Uniswap V3 liquidity calculation with step-by-step explanation, that clarify unproportional token amounts in some edge cases. All formulas found on Uniswap V3 [docs](https://uniswapv3book.com/milestone_1/calculating-liquidity.html) page.

---

Q1 Review:

In Q1 2025, I focused on advancing DeFi analytics. I started portfolio performance tracking across Sonic-based DeFi protocols like Silo, Shadow, and Aave, depositing funds and looking for APIs for data aggregation. I completed research on ALM (Automated Liquidity Management) protocols, identifying Gamma as optimal for dynamic volatility strategies, and shared findings with Stephen and Li. Created Shadow Exchange scraper, a set of scripts to export pool's deposits and withdrawals events from the Shadow Subgrarph to CSV, and developed scripts for TVL and APY analysis of Beefy and vfat pools. Additionally, I contributed to Pump.ONE’s client and backend updates, improving competition features and launching production services. I also started researching UniswapX, resolved deployment issues with Aaron's help, and started testing contract deployments on Harmony. My work focused on analyzing DeFi liquidity pools, validating the data, and working with the team on the analysis results.

---

2025-03-29 Sat (3.0 h): vicunafinance.com [strategy](https://github.com/harmony-one/shadow-scraper/blob/main/docs/vicuna-finance-vault.md) analysis: researched strategy, completed 5 iterations of supply - borrow - swap loop, prepared [report draft](https://github.com/harmony-one/shadow-scraper/blob/main/docs/vicuna-finance-vault.md). On Sunday, March 30, the situation changed: the rates drastically dropped which made this strategy unprofitable.

2025-03-28 Fri: portfolio: [refactored](https://github.com/harmony-one/shadow-scraper/commit/f0b59a334d9e43ee8d486c6ac882f89386b1a256) SwapX script to get total amounts of token0 and token1 deposited into vault to add it to a new version of report. [Added](https://github.com/harmony-one/shadow-scraper/commit/44e03a5b52094781c2aadeea9f796b9f4852ce6f) APR calculation for SwapX vault which matched with dashboard values with small deviation. Started working on [vicuna](https://vicunafinance.com/markets) finance algorhytm to test potential returns on USDC/USDT vaults.

2025-03-27 Thu: invested into Pendle pools (mint pt+yt tokens of aUSDC, LP PTaUSDC, Stake LP on Magpie) to test potential rewards. Portfolio tracker: [found](https://github.com/harmony-one/shadow-scraper/commit/592e86911e79dc164e70972ee77a158cdc877735) a way ot get pending rewards for any pool (reward pool address is not hardcoded anymore), [exported](https://github.com/harmony-one/shadow-scraper/blob/main/export/portfolio_0x4E430992Db6F3BdDbC6A50d1513845f087E9af4A_1743086471.tsv) updated version of portfolio.

2025-03-26 Wed: portfolio report [fixes](https://github.com/harmony-one/shadow-scraper/commit/5dce75f88b8dcfc44a24ddcfce5d827e2aaff208) and improvements: more accurate values with 6 significant digits, formatted columns with underscore, calculate APR using only values from table. [Finalized](https://github.com/harmony-one/shadow-scraper/blob/main/export/portfolio_0x4E430992Db6F3BdDbC6A50d1513845f087E9af4A_1743011328.tsv) portfolio export format. Looking at other vault APIs.

2025-03-25 Tue: [added](https://github.com/harmony-one/shadow-scraper/commit/bccbda978bbe2173548a519e80b68f361b66b8e8) more fields to portfolio output: deposit values for each token, rewards, blocks number elapsed and total days; updated TSV output. 

2025-03-24 Mon: Shadow portfolio: [updated](https://github.com/harmony-one/shadow-scraper/commit/7986f53cd0ba6ae9316db727aae73ec98e948910) total claimed rewards calculation in USD and [added](https://github.com/harmony-one/shadow-scraper/commit/b77d4ef87ca33eeca469726f25646430275d80db) APR calculation for the pool, updated export in TSV.

---

2025-03-23 Sun (3.0h): portfolio tracker: researched [Subgraph API](https://sonic.kingdomsubgraph.com/subgraphs/name/shadow-migration) and [implemented](https://github.com/harmony-one/shadow-scraper/commit/c832ff2b6d81ace84bba8a23221bfbd9b7f895fe) logic to get the full history of rewards claimed by a user. Continie working on the APY calculation for Shadow pools.

2025-03-21 Fri: [added](https://github.com/harmony-one/shadow-scraper/commit/5227a40f4f51cf12b37077dad6c3bef91f863e34) values and balances in USD in portfolio tracker for all coins available in Coingecko API. Started working on the APR calclation for pools.

2025-03-20 Thu: portfolio tracker: [added](https://github.com/harmony-one/shadow-scraper/commit/3f080efddafa31e49738a30165a146e91ea88610) Shadow pool pending rewards with all 3 reward tokens: Shadow, XShadow and X33. [Added](https://github.com/harmony-one/shadow-scraper/commit/c34e3f42b1cb8bfe6a21408cb19bd8a54923602d) ERC20 tokens balance. [Improved](https://github.com/harmony-one/shadow-scraper/commit/dbfeae5902f5c2883b4e19ecadef113168863735) export to tsv format.

2025-03-19 Wed: portfolio tracker: [added](https://github.com/harmony-one/shadow-scraper/commit/3c149392eb2ba62553fc1607f5b1f2dd352c7461) export to tsv, refactored output to paste into excel table. Looked at koinly portfolio and compared it with our portfolio prototype. Researching methods to calculate total rewards for Shadow exchange.

2025-03-18 Tue: [improved](https://github.com/harmony-one/shadow-scraper/commit/b7cf3e9812390ef1e568a13bfc542c5d5ce04d8d) portfolio tracker with adding support of all concentrated liquidity pools on SwapX; added support of --userAddress command line parameter. [Configured](https://github.com/harmony-one/shadow-scraper/tree/main/src/subgraph/sonic-shadow) and [launched](https://thegraph.com/studio/subgraph/sonic-shadow/) Shadow subgraph on graph network, [created](https://github.com/harmony-one/h/blob/main/docs/subgraph-deployment.md) manual in /docs how to replicate all steps.

2025-03-17 Mon: portfolio tracker: [added](https://github.com/harmony-one/shadow-scraper/blob/main/src/portfolio-tracker/swapx.ts) SwapX rewards amount info. Exported all Sonic Shadow swaps for the USDC.e-USDT pool and created a [script](https://github.com/harmony-one/shadow-scraper/blob/main/src/shadow_trades/stats.ts) to calculate price range for 90% amount of trades for the given pool ($1 +- 0.5126%).

---

2025-03-16 Sun: (2.0h) portfolio tracker: looking at Shadow and [UniswapV3](https://docs.uniswap.org/contracts/v3/reference/core/interfaces/pool/IUniswapV3PoolState) documentation on how to calculate active position fees. Working on portfolio tracker prototype, [implemented code](https://github.com/harmony-one/shadow-scraper/commit/a2690eafe75e521b2e46a68bf6936faaf46e05f0) to collect active position data for the given pool.

2025-03-15 Sat: (2.0h) started working on tracking overall portfolio performance across multiple defi protocols on sonic. Deposited small amount of funds into [silo](https://v2.silo.finance/markets/sonic/s-usdc-20), [shadow](https://www.shadow.so/liquidity/0x324963c267c354c7660ce8ca3f5f167e05649970), [swapx](https://swapx.fi/earn?search=wS/USDC.e), [beets](https://beets.fi/pools/sonic/v2/0x25ca5451cd5a50ab1d324b5e64f32c0799661891000200000000000000000018), [euler](https://app.euler.finance/vault/0xeEb1DC1Ca7ffC5b54aD1cc4c1088Db4E5657Cb6c?network=sonic), [aave](https://app.aave.com/reserve-overview/?underlyingAsset=0x039e2fb66102314ce7b64ce5ce3e5183bc94ad38&marketName=proto_sonic_v3) and [curve](https://curve.fi/dex/sonic/pools/factory-stable-ng-4/deposit) sonic pools. Started looking for APIs for the given pools to get portfolio performance data.

2025-03-14 Fri: prepared [detailed report](https://github.com/harmony-one/h/blob/main/docs/automated-liquidity-manager.md#analysis-of-existing-pools) about beefy and vfat pools in /docs (TVL, APY, weekly rewards, methodology). Prepared scripts and exported raw vault data to csv: [vfat_wS-USDC.e](https://github.com/harmony-one/shadow-scraper/blob/main/export/vfat_wS-USDC.e_daily_snapshots.csv), [beefy_wS-USDC.e](https://github.com/harmony-one/shadow-scraper/blob/main/export/beefy_wS-USDC.e_harvest_events.csv).

2025-03-13 Thu: beefy [wS-USDC.e vault](https://app.beefy.com/vault/shadow-cow-sonic-ws-usdc.e-vault) research: collected and validated TVL and APY data, shared info

2025-03-12 Wed: research and verification of vfat [wS/USDC.e](https://vfat.io/farm?chainId=146&farmAddress=0xe879d0e44e6873cf4ab71686055a4f6817685f02&poolId=0) stats  (TVL, APR, fees) with onchain data from subgraph events, shared report with Stephen and Li

2025-03-11 Tue: completed research of ALM (Automated Liquidity Management) protocols, based on information from Gauntlet report, dashboards and DeFilLama. Gamma looks like the best choise for dynamic volatility and narrow range strategy; summarized data and shared report with Stephen and Li. Checked latest Gamma development updates and security reports. Started working on verifying numbers from vfat [wS/USDC.e](https://vfat.io/farm?chainId=146&farmAddress=0xe879d0e44e6873cf4ab71686055a4f6817685f02&poolId=0) pool dashboard.

2025-03-10 Mon: started research of [Bancor](https://arxiv.org/pdf/2111.09192) analysis, [Gauntlet](https://www.gauntlet.xyz/resources/uniswap-alm-analysis) Automated Liquidity Management report to verify the idea of rebalancing using dynamic volatility

---

2025-03-09 Sun: (3.0h) started research of automated liquidity manager. [Drafted](https://github.com/harmony-one/h/blob/main/docs/automated-liquidity-manager.md) document with key concepts, data structures and basic strategy. [Improved](https://github.com/harmony-one/shadow-scraper/commit/4737c77d32311e8ede6443038563229db2e2237e) jsonl export script in shadow-scraper to support Swap events which can be useful for the first auto-balancer strategy implementation. [Optimized](https://github.com/harmony-one/shadow-scraper/commit/ce113fa8e1ef7d2e9100dbf5d1d9fecde1bddf9c) jsonl export script, full mints and burns export now takes about 40 minutes instead of 1.5 hours.

2025-03-08 Sat: (1.0h) tested [fixed version](https://github.com/Uniswap/UniswapX/compare/main...polymorpher:UniswapX:main) of UniswapX contracts created by Aaron: the issue was related to some EVM features that are not currently supported in the Harmony chain. Configured and deployed [DutchOrderReactorV2](https://explorer.harmony.one/address/0x35a87Ee887dFD4145B277B59998b3Bb4b2A50274?tab=txs&shard=0) contract.

2025-03-07 Fri: working on full Shadow exchange export to jsonl format: refactored Graphql queries to support faster filtering by blockNumber, [created](https://github.com/ArtemKolodko/shadow-scraper/blob/main/src/jsonl/index.ts) export script; exported data contains 500Mb of data, 334220 mint and 317501 burn events. Looking at vfat [FarmStrategy](https://github.com/vfat-io/sickle-public/blob/main/contracts/strategies/FarmStrategy.sol) contract.

2025-03-06 Thu: [creacted](https://github.com/ArtemKolodko/shadow-scraper/commit/f49446e74e4bd247cb03e5eb7f651cee5a1f10ae) script to calculate Shadow TVL for Theo. [Added](https://github.com/ArtemKolodko/shadow-scraper/commit/4a72bb93dfdff7d843b898ea900a6500086868bb) script to calculate average TVL based on data at the end of each day, shared results with Stephen and Li.

2025-03-05 Wed: completed first version of Shadow Exchange scraper tool, and [exported](https://github.com/ArtemKolodko/shadow-scraper/tree/main/export_dump) over 150K of mint and burn transactions from the wS/USDC.e pool (all transactions since the launch of the pool at the end of December 2024).

2025-03-04 Tue: switched to a task about parsing and storing analytics data from Shadow liquidity pools. Looked at [Shadow subgrapgh](https://sonic.kingdomsubgraph.com/subgraphs/name/exp/graphql), played with graphql queries, made some deposits and withdraws on Shadow from my personal address to test it, and started the development.

2025-03-03 Mon: continue on UniswapX deployment: during the DutchOrderReactor debugging, deployed DutchOrderReactor in Arbitrum Sepolia without any issues: [transaction](https://sepolia.arbiscan.io/tx/0x444c1b432254aa02dae019d887d59146e52bbf49f8cc42a66ed9be0f0769ab66), [contract address](https://sepolia.arbiscan.io/address/0x744aa5638e503e73957f07087745684e0afc2b9f). Synced with Aaron and Li, started checking contract source code for hardcoded values. Created [UniswapX page](https://github.com/harmony-one/h/blob/main/docs/UniswapX.md) in /docs to share deployment steps and updates with the team.

---

2025-03-01 Sat: (2.0h) investigating issue with failing UniswapX DutchOrderReactor deployment: [created](https://github.com/ArtemKolodko/uniswapx-demo/blob/main/test/contracts/Create2Factory.sol) custom create2factory contract, [deployed](https://explorer.harmony.one/address/0x4caA6ae8a53deBcDaDEf5C03F2b03D1c1FAFB7B6?shard=0) new permit2 contract, required in DutchOrderReactor, but issue still presented; continue work on the solution.

2025-02-28 Fri: UniswapX: working on [DutchOrderReactor](https://github.com/Uniswap/UniswapX/blob/main/src/reactors/DutchOrderReactor.sol) deployment, but have some failed transactions related to create2 contract; synced with Aaron, working on solution. Sonic: read Philip's DeFi Ecosystem overview document, started playing with soniclabs dapps.

2025-02-27 Thu: UniswapX: started working on demo implementation, [created](https://github.com/ArtemKolodko/uniswapx-demo/blob/main/backend/src/index.ts) DutchOrder script, researching DutchOrderReactor contract sources. Pump.ONE: [launched](https://pump.one/board) production backend and client, monitored the services for the first few hours after the launch.

2025-02-26 Wed: UniswapX: [deployed](https://explorer.harmony.one/address/0xC5f4c7C1C20532CdCB84dcf9A2B4FfB8F431246C?shard=0) Permit2 contract that is used in the UniswapX logic, Aaron helped to resolve issue with create2 factory contract. Continue on UniswapX contracts deploy script.

2025-02-25 Tue: UniswapX: exploring prototol codebase, deploying [permit2](https://github.com/Uniswap/permit2) contract but got error "missing CREATE2 deployer". Create2 deployer contract is required to deploy contract to deterministic address; working on solution. Pump.ONE: [minor](https://github.com/harmony-one/pump.fun.client/commit/46cf22fc218cb45a49cb240d8eeb19348744c632) updates following Aaron's comments.  

2025-02-24 Mon: UniswapX: completed initial research, started researching questions that require clarification: [Permit2](https://eips.ethereum.org/EIPS/eip-2612) order sign on Harmony; can we integrate swap.country with UniswapX. Discussed UniswapX technical details with Aaron. Created Pump.ONE launch steps and shared with team.

---

2025-02-21 Fri: continue on UniswapX: researching architecture, [whitepaper](https://app.uniswap.org/whitepaper-uniswapx.pdf) and official [repo](https://github.com/Uniswap/UniswapX)

2025-02-20 Thu: Pump.ONE: tested [updated](https://github.com/harmony-one/pump.fun.contracts/pull/25) contracts with fixed bug with burn token method. [Added](https://github.com/harmony-one/pump.fun.backend/commit/97a564205390c227b24e6c8ad62253a27a8bdd9b) initial competition in tokens indexer, [added](https://github.com/harmony-one/pump.fun.client/commit/a304f1f017ffe4aa3aa9b9326025d401364b7fc3) winner icon in tokens feed, deployed an update.

2025-02-19 Wed: started researching UniswapX docs and [source](https://github.com/Uniswap/UniswapX) code. Pump.ONE client: [added](https://github.com/harmony-one/pump.fun.client/commit/71c0365a941549bb529fc66c4f94f44d4e749491) Discord link in disclaimer.

2025-02-18 Tue: Pump.ONE client: [added](https://github.com/harmony-one/pump.fun.client/commit/de68883092b544a63190901c95e963fed1c8bed8) token collateral progress on competition token page, [added](https://github.com/harmony-one/pump.fun.client/commit/40b885f7e195ccedf3aa59f60c00ee0c352a1d9f) running competition info on token create page, [market cap](https://github.com/harmony-one/pump.fun.client/commit/0cdbed7c953b0a7c03a39ee9a151d7282c8fa38e) in USD. Updated [staging client](https://pump-one-staging.netlify.app/board).

2025-02-17 Mon: Pump.ONE: [added](https://github.com/harmony-one/pump.fun.backend/commit/c76cc6a615c5c66e53e7b620c7ba9961b98591f0) total number of participants in competitions list; continue testing: [fixed](https://github.com/harmony-one/pump.fun.client/commit/30763189154011063def0ee9ba24db1e76ea5c49) check is burn token available for competition token, found bug in contract method burnTokenAndMintWinner, sent info to Yuriy.

---

2025-02-14 Fri: Pump.ONE: deployed [new version](https://github.com/harmony-one/pump.fun.contracts/pull/24) of contracts with access control, [added](https://github.com/harmony-one/pump.fun.client/commit/466d203a7ba687d493fbeb1b76495a70188dc972) new Competitions page and [publish](https://github.com/harmony-one/pump.fun.client/commit/d985ac10a8de103b21c387c455b77ee4a50e80c6) to swap.country for non-competition token in client. [Updated](https://pump-one-staging.netlify.app/board) and tested staging client.

2025-02-13 Thu: Pump.ONE: completed support of [updated version](https://github.com/harmony-one/pump.fun.contracts/pull/22/commits) of contracts in client and backend, [added](https://github.com/harmony-one/pump.fun.client/commit/f4c7e7b8b5dc85a0b6515812d5ccce8d2dcdbd52) collateral progress bar in client on the token page. Synced with Yuriy on issue with publishToUniswap method; [staging](https://pump-one-staging.netlify.app/) client update will be deployed after the fix.

2025-02-12 Wed: Pump.ONE: synced with Yuriy on [updated contracts](https://github.com/harmony-one/pump.fun.contracts/pull/22) with TokenFactoryBase, started working on adding support. Added new ABI and CreateToken event in [backend](https://github.com/harmony-one/pump.fun.backend/pull/7/commits/c9621ad5455d79fd4d451ed081678ed3afee09b5) and [client](https://github.com/harmony-one/pump.fun.client/commit/cc79f8159d9b96dec039c09b97604078f2b8d9e7), tested token creation.

2025-02-11 Tue: Pump.ONE: [added](https://github.com/harmony-one/pump.fun.backend/pull/7/commits/d17fcf1a981c754ce6c934c2a22f371e5bbbb7cf) [new filter](https://github.com/harmony-one/pump.fun.client/commit/061926c1be949757510f68ff3a2991c15e6b79fc) to show only competition tokens. Checked contract [update](https://github.com/harmony-one/pump.fun.contracts/pull/22) with simple TokenFactory; will prepare new client deployment after contracts are finalized.

2025-02-10 Mon: Pump.ONE client: [added](https://github.com/harmony-one/pump.fun.client/commit/d14ef8ab4509c68bb164ee51affc0a266dff422d) option to create token with or without competition mode; completed refactoring to support two contracts (with enabled and disabled competitions). [Added](https://github.com/harmony-one/pump.fun.client/commit/c6c467fcc9e56e6eacb78ec82d687a6c230cd395) competition rules on token creation page.

---

2025-02-07 Fri: Pump.ONE: started working on client update to support two different token factories (with competitions and simple one, only trading). Synced with Yueiy on technical details regarding Pump.ONE contract updates.

2025-02-06 Thu: Pump.ONE: [completed](https://github.com/harmony-one/pump.fun.backend/pull/7/commits/a5ffb9b1828f1fb1d4e1b5006a51e33ca8b96393) multiple tokens factory support in tokens indexer; send suggestions about gamification of Pump.ONE competitions to Aaron for review

2025-02-05 Wed: Pump.ONE: [started](https://github.com/harmony-one/pump.fun.backend/pull/7/commits/82c17fc54b491d6a0b2f2404e42b34b7da60b5c2) working on multiple token factories to support optional competitions; updated database scheme in tokens indexer.

2025-02-04 Tue: yield enhancer: [added](https://github.com/harmony-one/yield-enhancer/commit/10e067353e65a1f80b6b01746b2631fb2780dab9) button to add boostDAI token to Metamask with 1 click. Completed USDC-converter [pull request](https://github.com/harmony-one/usdc-converter/pull/3/files) with interface updates and send for the review.

2025-02-03 Mon: USDC converter client: [added](https://github.com/harmony-one/usdc-converter/pull/3/files#diff-e56cb91573ddb6a97ecd071925fe26504bb5a65f921dc64c63e534162950e1ebR38) insufficient balance validation, moved params to separate config file, fixed "max" amount button styles

---

2025-01-31 Fri: Pump.ONE: [deployed](https://github.com/harmony-one/pump.fun.backend/commit/14ad1b7ac7094389145ac995f9659153305ca675#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5R142) contracts with disabled competitions; [removed](https://github.com/harmony-one/pump.fun.client/commit/325f20f86819f2968769ce65923f0f99e53e08de) competitions from client and [updated](https://pump-one-staging.netlify.app/) staging client and backend

2025-01-30 Thu: Pump.ONE: deployed and tested [new version](https://github.com/harmony-one/pump.fun.contracts/pull/20) of Pump.ONE upgradable conracts with client and backend; [updated](https://pump-fun-backend-staging.fly.dev/api) staging backend. Synced with Yuriy on the final version of Pump.ONE contacts.

2025-01-29 Wed: Pump.ONE: [added](https://github.com/harmony-one/pump.fun.backend/commit/8b894d41907e2b7ae60d2fdbe521ea5da1a37394) POST and GET /report endpoints on the backend side, [completed](https://github.com/harmony-one/pump.fun.client/commit/a704cb6b5cf5fa30ab662194b1b79418365ab0f0) integration with client

2025-01-28 Tue: Pump.ONE: [added](https://github.com/harmony-one/pump.fun.client/commit/f562d50ae261ad0f44242f8753b714ef4cc2351b) token report page in Client; started working on reports support on the backend side

2025-01-27 Mon: Eliza AI agent: [improved](https://github.com/harmony-one/eliza-harmony/pull/2/commits/f826e49b0f3f47d62baf2e91e200cc669171712a) staking information response, [added](https://github.com/harmony-one/eliza-harmony/pull/2/commits/e4435c8f6d7575c0960af66928fd9ca6f617b531) validators by lowest fees response. Sync with the team about steps to prepare for the upcoming Pump.ONE launch.

---

2025-01-24 Fri: Pump.ONE: implemented user restriction on the [backend](https://github.com/harmony-one/pump.fun.backend/pull/6/commits/c1bd9000643d8c2f22d606b829c1623cd8fdb6e3) and [client](https://github.com/harmony-one/pump.fun.client/pull/16/commits/9b249096d469c2ee7eb6e1c82801f447b19e2098) side, added restricted access disclaimer; Pump.ONE admin can now disable publishing the new tokens for the user.
 
2025-01-23 Thu: Eliza AI agent: [added](https://github.com/harmony-one/eliza-harmony/pull/2/commits/af773c97b8a901693305e5fd89076bbd1869d3fa) integration with staking validators info; tested requests to Eliza for information about validators

2025-01-22 Wed: Eliza AI agent: [created](https://github.com/harmony-one/eliza-harmony/commit/128623ccfa2e540c343c55e69807d19c52f65104) base structures to implement Harmony plugin with staking and validators info; tested responses with simple requests to Eliza bot; started working on internal logic

2025-01-21 Tue: started working on harmony plugin based on [Eliza EVM](https://github.com/harmony-one/eliza-harmony/tree/develop/packages/plugin-evm) plugin. Discussed with the team about features to implement, explored Harmony staking and Swap API.

2025-01-20 Mon: ElizaAI agent: researched docs and various plugins to use with Harmony chain, configured [plugin-env](https://github.com/elizaOS/community-plugins/tree/develop/packages/plugin-evm), tested wallet balance check and ONE token transfers

---

2025-01-17 Fri: Eliza AI agents: researching [plugins](https://github.com/elizaOS/eliza/tree/develop/packages/plugin-evm) structure, started working on Harmony EVM agent plugin. Explorer client: [merged](https://github.com/protofire/bs-frontend/pull/23/commits/382ec47d7d38f2c4504649d54fe1774055d2a745) the staging branch, which includes recent updates to staking transaction values, into Pull Request #23 with transaction value in USD

2025-01-16 Thu: yield enhancer: fixed bug with max button amount, added 18 decimals support, [added](https://github.com/harmony-one/yield-enhancer/commit/d62156c303775bcf496efd8f29ceeebca833b601) insufficient amount check; [reviewed](https://github.com/harmony-one/yield-enhancer/pull/2) and merged PR#2 from Theo, [updated](https://harmony-vault.netlify.app/) the client

2025-01-15 Wed: pump.ONE client: [added](https://github.com/harmony-one/pump.fun.client/pull/16/commits/e3c2e74c83305fd0e99bdb9e6b7b008a60655cbf) Harmony Testnet support for testing purposes. Tested Trading View candles: launched [trading bot](https://github.com/harmony-one/pump-fun-trading-bot/commit/5617b51e9e1da3e73c629b800f9a4a34e32b6e95) with trades every 30 seconds for 8 hours.

2025-01-14 Tue: yield-enhancer: [added](https://github.com/harmony-one/yield-enhancer/commit/d1a080c0ac4472dc85e9097cb28c6c5c422293eb) current exchange ratio to "How it works" section; disable Deposit / Withdraw buttons if no amount is entered in the input field; updated the [client](https://harmony-vault.netlify.app/). Pump.ONE: started final tests on Harmony Testnet: [deployed](https://explorer.testnet.harmony.one/address/0xdb6E7eb8Bac36981A910928F8342825113F0Dbc6) a contracts with production bonding curve params, started testing the client.

2025-01-13 Mon: yield-enhancer: [changed](https://github.com/harmony-one/yield-enhancer/commit/3d826c18cd2fbcc50ecf07c3d9e5f22a30cf86fd) APY calculation to remove historical APY from calculation, after discussion with Aaron. [Added](https://github.com/harmony-one/yield-enhancer/commit/52beb4b960d534931254ff8c9896076049fdca40) Harmony logo, [deployed](https://harmony-vault.netlify.app/) new client version.

---

2025-01-10 Fri: tested Eliza [plugin-env](https://github.com/elizaOS/eliza/tree/develop/packages/plugin-evm), that allows agent to make a token transfers: configured required environment variables and run agent locally; transfers are displayed in logs but transaction hash is incorrect, transfer cannot be foubd in Explorer. Researching the internal structure of Eliza [packages](https://github.com/elizaOS/eliza/tree/develop/packages).

2025-01-09 Thu: yield enhancer: [fixed](https://github.com/harmony-one/yield-enhancer/commit/2ca235a6ed40e81b0790ee1a2cf0c2f2fe50b679) APY calculation since day 1 from launch; pump.ONE: [added](https://github.com/harmony-one/pump.fun.backend/pull/6/commits/878e67209fdb914db2ffc6f07fabae5211e46afa) tokens sorting by last trade timestamp, [added](https://github.com/harmony-one/pump.fun.backend/pull/6/commits/4749420352f364e85d6344ae36c1cdce1e66523b) minimum message length validation in token comment, [added](https://github.com/harmony-one/pump.fun.backend/pull/6/commits/7ba031202d7a6e8c6a024061a21a837fbfbe62c3) comments sorting by time

2025-01-08 Wed: pump.ONE: [added](https://github.com/harmony-one/pump.fun.backend/pull/6/commits/705868dda026c4bc110f29d4ca7ba07b347b6f80) [sorting](https://github.com/harmony-one/pump.fun.client/pull/16/commits/f8f268aa51c267deaa6c2f18a1f384811f7e4433) by latest comment on the tokens page, fixed compilation warnings, [deployed](https://pump-one-staging.netlify.app/board) staging client update

2025-01-07 Tue: configured Eliza AI agent with Twitter integration, post are published to the [Twitter account](https://x.com/CrimsonCipher1); [created](https://github.com/harmony-one/h/blob/main/docs/ElizaAIAgent.md) docs article on how to launch it locally

2025-01-06 Mon: pump.ONE backend: [refactored](https://github.com/harmony-one/pump.fun.backend/pull/6/commits/36243f10b6ecc0754cd735d58c64ed7ac837af68) candles SQL query, [added](https://github.com/harmony-one/pump.fun.backend/pull/6/commits/a6054f4715c4c0fe08b5d1f6ba5cb03f6c00d127) 1h and 1d intervals, [fixed](https://github.com/harmony-one/pump.fun.backend/pull/6/commits/1f5bf24f1e537fd65a6bf445af68ca767b09fe0f) bug in pump.ONE tokens indexer

---

2025-01-03 Fri: AI agent - resolved issue with database connection, configured and refilled OpenAI test account; continue research

2025-01-02 Thu: started researching [Eliza](https://github.com/elizaOS/eliza-starter) AI agent: configured local environment, added test Twitter account details; got an error about DB connection on launch, started debugging

---

2024 Q4 Review

This quarter, I focused on launching of Pump.ONE project, a memecoin marketplace on the Harmony chain.

While working on this project, I [created](https://pump.one/board) various services: Pump.ONE [client](https://github.com/harmony-one/pump.fun.client), [backend](https://github.com/harmony-one/pump.fun.backend) (indexer + API service) and [trading bot](https://github.com/harmony-one/pump-fun-trading-bot). During the development process I worked on the user interface, integration with [smart contracts](https://github.com/harmony-one/pump.fun.contracts), end-to-end testing and improvements based on user feedback. In the backend app, I implemented mechanics to store token metadata, upload images, user authorization based on signed messages and JWT tokens, [REST API](https://pump-fun-backend.fly.dev/api) and tokens indexer.

I've also implemented Harmony yield enhancer [client](https://harmony-vault.netlify.app/), added new features for the new Harmony Explorer: ONE/ETH toggle persistent state, [displaying](https://github.com/protofire/bs-frontend/pull/23) transaction value at the time of transfer.

---

2025 Goals:

In 2025, I aim to advance trading technologies and decentralized markets by enhancing Pump ONE, integrating AI agents, and launching a decentralized perpetual market.

Pump ONE:
I will introduce features like WebSockets for faster price updates, AI-generated memecoins within the client application, and improved UI for a better trading experience.

AI Agents Integration:
I will create AI agents inspired by Eliza, designed to operate across protocols, assist with trading decisions, and support portfolio rebalancing based on market conditions and price predictions.

DEX:
I plan to launch a decentralized perpetual market offering seamless trading, robust liquidity, and user-friendly interfaces, building on proven products.

---

2024-12-30 Mon: pump.ONE backend: [fixed](https://github.com/harmony-one/pump.fun.backend/pull/6/commits/c8c782c90e1c9143ecdeacbdfc68f211ecb47f70) candles ordering, [updated](https://github.com/harmony-one/pump.fun.backend/pull/6/commits/e20acd4b4d35fb3fb4d774798be2f90addfb338c) candles SQL query: added open and close price

2024-12-27 Fri: pump.ONE client: [added](https://github.com/harmony-one/pump.fun.client/pull/16) advanced Trading view on the client side

2024-12-26 Thu: pump.ONE client: [fixed](https://github.com/harmony-one/pump.fun.client/commit/e5ea9cf8a148ca38b350e5e992088492f4f055de) bug with Walllet connect status; started working on integration with advanced Trading View chart with candles

2024-12-25 Wed: pump.ONE client: [updated](https://github.com/harmony-one/pump.fun.client/commit/06d5cc243f37be421092995c75828d1c3f5181f5) numbers component, added tooltips to numbers and dates

2024-12-24 Tue: pump.ONE client: [added](https://github.com/harmony-one/pump.fun.client/commit/6383a0ec39903d11d4f1faa2e1314e7aeb664aa2) uniqueness check for token symbol on token creation form

2024-12-23 Mon: yield enhancer: [added](https://github.com/harmony-one/yield-enhancer/commit/eb9f23c63bab07971a987623007758842e13c5ff) advanced APY calculation based on daily rewards, deployed [new version](https://harmony-vault.netlify.app/) of client. Pump.one: deployed [new version](https://github.com/harmony-one/pump.fun.contracts/pull/19) of contracts, prepared staging [backend](https://github.com/harmony-one/pump.fun.backend/pull/6/files) and [client](https://pump-one-staging.netlify.app/) environment.

---

2024-12-20 Fri: Pump.ONE client: [added](https://github.com/harmony-one/pump.fun.client/commit/362a1394991e1a65323383a7b87702bdd5deec35) mobile version to the token details page. Explorer client - added additional fixes to [Pull Request](https://github.com/protofire/bs-frontend/pull/23/commits) following the review from Protofire team.

2024-12-19 Thu: yield enhancer: [added](https://github.com/harmony-one/yield-enhancer/commit/9e7e8216bed53af52f58a21019532c66c3cd412d) historical APY calculation, [added](https://github.com/harmony-one/yield-enhancer/commit/b39f3398ef7306c9d55a53b99ac30883f8aee438) switching to harmony network on deposit request

2024-12-18 Wed: yield enhancer: [fixed](https://github.com/harmony-one/yield-enhancer/commit/88076031ec08a3db10c6875e6faae9411f899ffa) withdraw and withdraw preview amount, [added](https://github.com/harmony-one/yield-enhancer/commit/6f5a215cb061b45ee1f09ac4ac1acfc136648ade) current allowance check before depositing, [deployed](https://harmony-vault.netlify.app/) client update. Continue working on displaying ONE value in a new harmony explorer at the date of transaction.

2024-12-17 Tue: yield enhancer project: deployed contracts, wokred on client integration: [added](https://github.com/harmony-one/yield-enhancer/commit/9d1d936770bbee57d9ec62d77c66869a038ad399) connect kit to support wallets, [implemented](https://github.com/harmony-one/yield-enhancer/commit/18df36e321630ab7af9606dc8e8a94d967693505) deposit, withdraw methods, [TVL](https://github.com/harmony-one/yield-enhancer/commit/9d97dc78176dd25316c1e6b7a333305091311887) and deposit / withdraw quote. [Deployed](https://harmony-vault.netlify.app/) yield enhancer client to netlify to test.

2024-12-16 Mon: Pump.ONE backend: [implemented](https://github.com/harmony-one/pump.fun.backend/commit/2c22c0149d6ddf3b9e127f23d99dba470043aed5) new competition scheduler with 7-days interval and liquidity threshold. Pump.ONE client: [added](https://github.com/harmony-one/pump.fun.client/commit/32e0ebe20189fcd57c01766fc66a226a6876428f) information about competition in the tooltip (start date, end date). Explorer app: started working on displaying value at the date of transaction.

---

2024-12-13 Fri: pump.ONE: [added](https://github.com/harmony-one/pump.fun.backend/commit/a478829e28ee6537943eb71b68eb4631b94d2cc3) blacklist for tokens feed (managed by backend admin), [added](https://github.com/harmony-one/pump.fun.client/commit/1e25b99f43dd8c50a0ef22a0d858c6ac239461c2) mobile version for tokens page, [added](https://github.com/harmony-one/pump.fun.client/commit/b4dec2af6b68cd85b6eee63395a63aa8adde9b92) disclaimer, update rules page

2024-12-12 Thu: Pump.ONE client update: [added](https://github.com/harmony-one/pump.fun.client/commit/1bfd4206f7b6ce4e4e0a25bf10c8a5ff72bed564) information about competition and winner token on token page, [updated](https://github.com/harmony-one/pump.fun.backend/commit/4a62930ef16b618ce8b944f3aa9f2b89c01d400a) backend API, [updated](https://github.com/harmony-one/pump.fun.client/commit/427fee3cf82c4da649ad4899313366253c4f397a) "How it works" page, deployed latest version of client

2024-12-11 Wed: pump.one client: [added](https://github.com/harmony-one/pump.fun.client/commit/f07e25b18d13fcb71dc9fd287812297e26703d1b) [/rules](https://pump-app.netlify.app/) page, redeployed protocol and services to support [latest updates](https://github.com/harmony-one/pump.fun.contracts/commit/213caf130f5688fd042f659322026d83b72cb77e) in pump.one contracts.

2024-12-10 Tue: pump.one indexer: [added](https://github.com/harmony-one/pump.fun.backend/commit/3bb31ccd2639b6a3c08ccd095572d78fe4a17a37) indexer optimization: fetching transaction logs in batches (max=5 batches with 1000 blocks in each); [updated](https://github.com/harmony-one/pump-fun-trading-bot/commit/7f0a86048cd3601cfb38acf4fab2f08a5ca6e429) pump.one trading bot to trade with 3 newest tokens.

2024-12-09 Mon: pump.one - [added](https://github.com/harmony-one/pump.fun.backend/commit/9ee1ace2ff82355e6da15f821c70df04efef67c0) sorting by market cap and creation time on tokens page, tokens indexer speed [increased](https://github.com/harmony-one/pump.fun.backend/commit/c04524ad364999213c14920935b21ecc63339470) by 3-4 times, [added](https://github.com/harmony-one/pump.fun.backend/commit/10fd44465f491eca87962838422c754118cc7553) caching in some backend endpoints; [deployed](https://pump-app.netlify.app/) new version of client.

---

2024-12-08 Sun: continue on pump.fun fixes before the launch: [fixed](https://github.com/harmony-one/pump.fun.backend/commit/374bc721905c85fc24ee70e6e09fb757a88d5b4c) market cap and token price calculation, [added](https://github.com/harmony-one/pump.fun.backend/commit/184830c5dd779f119cbb8093ca94f803b5777e92) GIF and PNG files support, added file size and type validation on the BE side, [improved](https://github.com/harmony-one/pump.fun.client/commit/34b591d92e2d2764769887366f124e2d830e7d6e) trade notification.

2024-12-07 Sat: pump.one issues - preparation for launch: [fixed](https://github.com/harmony-one/pump.fun.client/issues/1) price chart labels, removed TradingView logo, [added](https://github.com/harmony-one/pump.fun.client/issues/2) multiple wallets support

2024-12-06 Fri: updated pump.one client: [added](https://github.com/harmony-one/pump.fun.client/commit/0fd18cccb3bf153c26707300a00006c666ad4766) support of a new contracts, [added](https://github.com/harmony-one/pump.fun.client/commit/2da79c8b1d3649cd29e64c7f907147bfe3d55b1e) trade estimate, updated trading form UI; [deployed](https://pump-app.netlify.app/board) new version of client.

2024-12-05 Thu: started [backend](https://github.com/harmony-one/pump.fun.backend/commit/94b84479a7bfa78f05b44ba55c3ca31f62de8d17) update to add support of a new version of pump.one contracts, refactored competition entities, started updating pump.one client

2024-12-04 Wed: pump.one token creation form: [added](https://github.com/harmony-one/pump.fun.client/commit/d4c43848f0777d0e7fb934949cd81848f288e490) optional twitter, telegram and website links. Started researching trade price estimate.

2024-12-03 Tue: pump.fun client: trading form [improvements](https://github.com/harmony-one/pump.fun.client/commit/12adcaccd222a82488ce5c44f59ab7ee45f055a6) - added user balance check, predefined values with quick access, added token icon.

2024-12-02 Mon: pump.fun: [added](https://github.com/harmony-one/pump.fun.backend/commit/4657517a6f815ef161f3300bb8adabe61367be1e) new events, updated ABI, [updated](https://github.com/harmony-one/pump.fun.client/commit/4ab8a459816bef49362d70b6dbb86d33207246cc) burn token call logic, added number of comments for each token item; [deployed](https://pump-app.netlify.app/) new version of client. Discussed last steps before the launch with the team: minor contract changes, testing.

---

2024-11-29 Fri: started integration with a [new version](https://github.com/harmony-one/pump.fun.contracts/tree/uniswap_liquidity_manager) of contracts: deployed new contracts, started updating backend and client

2024-11-28 Thu: synced with Yuriy on recent contract changes. pump.fun client: [added](https://github.com/harmony-one/pump.fun.client/commit/d172e7b34a941668a5356c0b1ed27fd72d382d98) daily winners page

2024-11-27 Wed: [completed](https://github.com/harmony-one/pump-fun-trading-bot/commit/483a96dff6458468a04e708ec9d50d50450e1c5f) simple trading strategy in pump.fun trading bot: buy and sell memecoin with random probability.

2024-11-26 Tue: pump.fun trading bot: [added](https://github.com/harmony-one/pump-fun-trading-bot/commit/4fa929d749f7d9df0c9b5ed292ae4c03ef9943ff) trade implementation, started working on basic trading strategy. Client: [improved](https://github.com/harmony-one/pump.fun.client/commit/4686c341bce2390bac52c69ebfb8329b7fbe91b8) trading notifications, added token price chart live update.

2024-11-25 Mon: synced with Yuriy and Aaron on pump.fun last feauture before the launch; [continue](https://github.com/harmony-one/pump-fun-trading-bot/commit/c8d1e5d7ac1b948051cdd1c678495fa35f2f146e) working on trading bot for pump.fun: initialized contracts, added intiial tokens request

---

2024-11-22 Fri: fixed couple of bugs from Aaron's pump.fun backend [review](https://github.com/harmony-one/pump.fun.backend/issues), commented some questions regarding JWT tokens. [Updated](https://github.com/harmony-one/pump.fun.backend/commit/e009ae4628237fe84ead660042107f6e0981bde9) backend API. [Added](https://github.com/harmony-one/pump.fun.client/commit/5418539481d4519265073d10ada4d18ff66e7743) tracking of token burn transaction status in pump.fun client.

2024-11-21 Thu: pump.fun client: [added](https://github.com/harmony-one/pump.fun.client/commit/57408e64db00f898f4a79218bc2e863246ec1b06) support of burnTokenAndMintWinner call for non-winner tokens; started adding this event on the backend side. [Redeployed](https://pump-app.netlify.app/board) contracts, backend and client.

2024-11-20 Wed: [added](https://github.com/harmony-one/pump.fun.backend/commit/b8bbb0932b61385a5241cad9f1ce06617a487180) support of a new contracts in pump.fun backend and [client](https://github.com/harmony-one/pump.fun.client/commit/1b743f2bccc0e90b9a99f72f3b42424c2ad4ae57), updated setWinner call on the backend side

2024-11-19 Tue: started working on pumpfun trading bot: [created](https://github.com/harmony-one/pump-fun-trading-bot) initial project structure, added basic types

2024-11-18 Mon: pump.fun: [added](https://github.com/harmony-one/pump.fun.client/commit/8e8a1d2fa55d051e6363d7572e1ecf61a0591556) SimpleSwap widget, [tokens](https://github.com/harmony-one/pump.fun.client/commit/82fbefb11ebbee7dea66915d682677b4c03a0585) search, updated header UI; [deployed](https://pump-app.netlify.app/board) new verson of client.

---

2024-11-15 Fri: pump.fun: [added](https://github.com/harmony-one/pump.fun.client/commit/a5da8b1a1e17ba734557cd6a4a0ec157e2264759) token price chart, [added](https://github.com/harmony-one/pump.fun.client/commit/26e62f0ad3ff5f8016886f68d577157aa1f35bcb) ability to update username in user profile modal. On backend side: [added](https://github.com/harmony-one/pump.fun.backend/commit/ab2b9d998192af015d2ab2f520e9711f93f0e645) API to support profile updates and token price data. [Deployed](https://pump-app.netlify.app/board) pump demo client update.

2024-11-14 Thu: [added](https://github.com/harmony-one/pump.fun.client/commit/17e1e6a414aa1872fc745ec777134d9900269649) sign-in with Metamask and JWT tokens support in pump.fun client

2024-11-13 Wed: pump.fun backend: [implemented](https://github.com/harmony-one/pump.fun.backend/commit/404cf15d2dbdaf45da7e7012498acc1a2a882d67) sign-in with Metamask. Started working on sign in with Metamask on the client side.

2024-11-12 Tue: pump.fun backend: [added](https://github.com/harmony-one/pump.fun.backend/commit/cb99e01e2fd76c6e022205a07dbe743a96a2abdb) token price to token entity; started working on Metamask login on the backend side.

2024-11-11 Mon: pump.fun client: [updated](https://github.com/harmony-one/pump.fun.client/commit/914b70d217552fdbaad3a8147cb5218f8c5af045) tokens list UI, [refactored](https://github.com/harmony-one/pump.fun.backend/commit/3016619f8d32752fd4f354fc942543086d8662b2) indexer logic with correct items orders, [added](https://github.com/harmony-one/pump.fun.backend/commit/fbd13131440d8adfbc4e9db077ef77331482c842) transcational insert of trade and token creation events in postgres DB. Redeployed contracts with fixed setWinner logic, updated [demo client](https://pump-app.netlify.app).

---

2024-11-08 Fri: pump.fun backend: [added](https://github.com/harmony-one/pump.fun.backend/commit/1baf798186395c1c4d7b584bb1e89d07369d2907) daily addWinner transaction call and AddWinner events [indexing](https://github.com/harmony-one/pump.fun.backend/commit/860398e71347fb52e4784dc0702b40d4d1634bc8). Client: [added](https://github.com/harmony-one/pump.fun.client/commit/06b063b6c3167e0816aacdf20b46cc24e8b06576) daily winner on the top of the page, tokens market cap, deployed [demo client](https://pump-app.netlify.app/board) update.

2024-11-07 Thu: pump.fun backend: [added](https://github.com/harmony-one/pump.fun.backend/commit/6fbafc28e0ff1d70aac04db5e4187a776f2802e1) token holders and totalSupply indexing; client: [added](https://github.com/harmony-one/pump.fun.client/commit/087a0f34e90b73c164a86a83efdf8b0aab10771e) token holders list

2024-11-06 Wed: pump.fun: [added](https://github.com/harmony-one/pump.fun.client/commit/337d71f6cadcfcf31d1971da7a9428d130aaa591) user profile page with the list of created tokens; started working on latest trade and token items on the top of the page

2024-11-05 Tue: pump.fun client update: [added](https://github.com/harmony-one/pump.fun.client/commit/cad884d88c90052bfffae55cc7eb6e4fe9d2de64) user tag and reply highlight, deployed [demo](https://pump-app.netlify.app) update. Collected internal feedback from the team; started working on the user profile page with the list of purchased tokens.

2024-11-04 Mon: prepared new features and deploed the first version of [demo client](https://pump-app.netlify.app/): [added](https://github.com/harmony-one/pump.fun.client/commit/8e16b9e9b3245fa4ec47bac499f682f2108d52aa) token trades history tab on token page, [implemented](https://github.com/harmony-one/pump.fun.client/commit/1d47f1007901752e4897aba23a1c3384c31db95f) token trade (buy / sell), user [profile](https://github.com/harmony-one/pump.fun.client/commit/1551ae5bde8611344d2e6c6f73ee5211240abdcc) info and token balances.

---

2024-11-01 Fri: pump.fun: implemented token [image](https://github.com/harmony-one/pump.fun.backend/commit/379bde4929bc3f017b037b1115fb5943012ca1ce) and token [metadata](https://github.com/harmony-one/pump.fun.backend/commit/9b3037018067e00e704a3884ac5c3a5f5bd59905) upload (metadata will be stored in Google Cloud Storage), [implemented](https://github.com/harmony-one/pump.fun.client/commit/15fad4ff15f863b63275e3cf63914f6e90345ac4) full flow of token creation in the client. Started last steps to update API and show token image in Client.

2024-10-31 Thu: pump.fun client: [implemented](https://github.com/harmony-one/pump.fun.client/commit/0915a3f0d7d8b245654bb0c6d3bb9ef8440feb70) tokens board page, token page and comments related to specific token (post and read). pump.fun backend: [updated](https://github.com/harmony-one/pump.fun.backend/commit/a4f064a4a7eb020f2929a99fc153171f8ed6da57) database schema and API to support new features.

2024-10-30 Wed: pump.fun client: initialized basic project structure using latest versions of viem and wagmi; started working on tokens page. pump.fun backend: [added](https://github.com/harmony-one/pump.fun.backend/commit/040c8efd41fe51f5cdce4b29417bb135aa70a12e) indexer state, added symbol and name param in Token entity in database.

2024-10-29 Tue: [prepared](https://github.com/harmony-one/pump.fun.backend/commit/655ce09157c1a63e911582ba1e91285323b38519) pump.fun backend and [deployed](https://pump-fun-backend.fly.dev/api) on fly.io. Current features: tracking of the new tokens, calculating winner by trading amount every day, API for comments and tokens. Discussed details with Yuriy, started working on pump.fun client app.

2024-10-28 Mon: [migrated](https://github.com/harmony-one/pump.fun.backend/commit/02c189b4aa6c7fd65673ff34a6e26c46c1122f2d) pump.fun backend to a [new contracts](https://github.com/harmony-one/pump.fun.contracts); preparing service for deployment.

---

2024-10-25 Fri: after Aaron's review of pump.fun contracts, we decided to switch to [another](https://github.com/harmony-one/pump.fun.contracts/commit/941994e7f8b83d0041f6a7e753355eaaac114f72) fork of pump.fun contracts, started updating pump.fun [backend](https://github.com/harmony-one/pump.fun.backend) to support new version of contracts.

2024-10-24 Thu: pump.fun backend [update](https://github.com/harmony-one/pump.fun.backend/commit/03e66556ed277c729012e751674058619bf5d920): added winner determination by daily volume

2024-10-23 Wed: continue on pump.fun backend: [added](https://github.com/harmony-one/pump.fun.backend/commit/f1927d3bbe6519909ff2262535d5d2b8b014a9fb) indexing of trade events and storing in database.

2024-10-22 Tue: pump.fun backend: tested tokens indexer; [implemented](https://github.com/harmony-one/pump.fun.backend/commit/9253487b906846c168906c616aa2a6976823797e) methods to save comments in the database, and get comments and tokens from the API.

2024-10-21 Mon: pump.fun tokens indexer: [added](https://github.com/harmony-one/pump.fun.backend/commit/a6431dfae50973fa4cfcca4db0851f87397e4daa) database support; store tokens in the database; started winner determination logic on the backend.

---

2024-10-18 Fri: completed first version of pump.fun tokens [indexer](https://github.com/harmony-one/pump.fun.backend)

2024-10-17 Thu: started working on pump.fun backend core logic: listen for blockchain events, parse pump.fun token Launched method

2024-10-16 Wed: deployed Pump.fun Solidity [implementation](https://github.com/sourlodine/Pump.fun-Smart-Contract) locally, researched project architecture and Unsiwap V2 logic, started testing integration with Uniswap V2. Synced with Yuriy on pump.fun tasks.

2024-10-15 Tue: researching pump.fun Solidity implementations, found [this one](https://github.com/sourlodine/Pump.fun-Smart-Contract), 157 github stars and forks. Started testing it locally.

2024-10-14 Mon: Explorer [improvements](https://github.com/protofire/bs-frontend/pull/21): save ETH / ONE toggle state across reload and navigation, removed banner about chain indexing. Started exploring new project: memecoin platform; checking pump.fun contract sources.

---

2024-10-11 Fri: 1market demo update: [display](https://github.com/harmony-one/1market-demo/pull/1/commits/7b98b37b40d17f6419be16fdd9b39e83a2658e30) active market even when user's wallet is disconnected, [added](https://github.com/harmony-one/1market-demo/pull/1/commits/7b98b37b40d17f6419be16fdd9b39e83a2658e30) indicator of transaction status (spinner)

2024-10-10 Thu: [reviewed](https://github.com/harmony-one/HarmonyOneBot/pull/369) 1bot PR from Frank with improved /allstats report, tested it locally. [Created](https://github.com/harmony-one/h/blob/main/docs/forge-test-script.md#erc20-token) detailed manual how to deploy ERC20 token using foundry. Continue on 1market demo updates.

2024-10-09 Wed: [fixed](https://github.com/harmony-one/HarmonyOneBot/pull/368) 1country weekly stats in 1bot /stats report; tested "forge create" script: [created an example](https://github.com/harmony-one/h/blob/main/docs/forge-test-script.md) for Harmony mainnet and testnet; for some reason foundry didn't report the transaction status, but the transaction was succesfully mined and appeared in the Explorer.

2024-10-08 Tue: [fixed](https://github.com/harmony-one/HarmonyOneBot/pull/367) network weekly fees and weekly users /stats in harmony1bot. Working on setting up buy.country domain. Continue on 1market updates based on [review](https://hackmd.io/@polymorpher/note-1market-demo).

2024-10-07 Mon: 1market: [fixed](https://github.com/harmony-one/1market-demo/pull/1/commits) 5 bugs from the Aaron's [review](https://hackmd.io/@polymorpher/note-1market-demo), sent details to Aaron and deployed [client](https://1market-demo.netlify.app/) update. Found and localized bug in 1bot /stats command, which is related to the old Explorer API. Checked new Explorer endpoints, started working on 1bot requests fix.

---

2024-10-04 Fri: continue on [1market review](https://hackmd.io/@polymorpher/note-1market-demo) fixes: updated bignumber.js library, [fixed](https://github.com/harmony-one/1market-demo/pull/1/commits/9ffbf9debbbb081c4a09653dcbe2084eda0a8a93) bug with tokens amount. Started migration from outdated web3connect to wagmi / wallet connect stack.

2024-10-03 Thu: [launched](https://1m.country/) new test market on 1Market demo; started working on fixes following [1Market review](https://hackmd.io/@polymorpher/note-1market-demo) from Aaron.

2024-10-02 Wed: 1market: [fixed](https://github.com/harmony-one/1market-demo/pull/1/commits/12828faf2a53c8aee1ac007b3e51ca624c897e4f) error with oracles state buttons, updated the [client](https://1market-demo.netlify.app/). Completed local setup of a new Blockscout Explorer [client](https://github.com/protofire/bs-frontend).

2024-10-01 Tue: [added](https://github.com/harmony-one/h/blob/main/docs/panoptic-v1-test.md) panoptics USDC/WETH swap script to /docs; setting up new [Explorer client](https://github.com/protofire/bs-frontend) locally, researching the client architecture

2024-09-30 Mon: updates styles in 1market client, [deployed](https://1market-demo.netlify.app/) an update. Tested pano [swap USDC](https://github.com/polymorpher/panoptic-v1-core/blob/main/swap-local-usdc.sh) script on Harmony mainnet with new env variables from Aaron, it worked! Sent steps how to use this script to our group chat with Stephen & Aaron.

---

2024 Q3 Review

Developed a [port](https://sy.country/) of Synthetix V2 and beginning work on [1Market](https://github.com/harmony-one/1market-demo/pull/1), a Polymarket analog. I successfully completed the porting of Synthetix v2 which included [deploy scripts](https://github.com/harmony-one/h/blob/main/docs/synthetix-v2-deployment.md), [contracts](https://github.com/harmony-one/synthetix/tree/develop/publish/deployed/harmony4) and a [new client](https://github.com/harmony-one/synthetix-js-monorepo). During the work I solved many difficulties at each stage of the complex 200 contract files on-chain and refactored the oracle feeds, some of which had to be rewritten due to unavailability of Chainlink used in the original system. At the moment, we have a sy.country client, deployed contracts on Harmony Mainnet, and a [1SY / 1USDC](https://info.swap.harmony.one/#/harmony/pools/0xbc4af4ee9164c469b9e90f7d9b5f7854556133d6) pair available to trade on [swap.country](https://swap.country/).

I've also started work on [1Market](https://github.com/harmony-one/1market-demo/pull/1). After studying the original code sources available on github, I decided not to make a Polymarket fork, as some parts of the system are not available including client application, order book. Instead, for the initial version, I used the [Gnosis Conditional Tokens demo](https://docs.gnosis.io/conditionaltokens/docs/pmtutorial1) as a basis, contracts from which are also used in Polymarket. At the moment I'm [working](https://github.com/harmony-one/1market-demo/pull/1) on adapting the demo client to our network and creating a more attractive interface that can be used for initial demo as well as in the final product.

---

2024-09-27 Fri: updated 1market demo: [added](https://github.com/harmony-one/1market-demo/pull/1/commits/7cd7b2ab6aa446c31f3a50b3c5d7be917b87a98a) Redeem button for resolved market, refactored layout, added dark theme. Tested [panoptic](https://github.com/polymorpher/panoptic-v1-core/blob/main/swap-local-usdc.sh) swap script but got a configuration error, asked Aaron to help to resolve it.

2024-09-26 Thu: tested [panoptic scripts](https://github.com/polymorpher/panoptic-v1-core/blob/main/swap-local-usdc.sh) (swap tokens from cli), but had a troubles with configuration params, asked Aaron for help. Completed the first version of 1market interface, [deployed](https://1market-demo.netlify.app/) the update.

2024-09-25 Wed: 1market demo client update: refactored basic layout, changed voting widget (added "buy" and "sell" tabs like on Polymarket), deployed [1market client](https://1market-demo.netlify.app/) update. Aaron will help with 1m.country domain. Synced with the team. Contacted Protofire frontend dev to make Explorer search bar dropdown fix (I'll setup Explorer client locally later, it will take some time). Started researching panoptic scripts to make swap on Harmony from command line interface.

2024-09-24 Tue: continue on 1market demo client update: started changing main trade widget layout to look more polymarket-style (buy/sell tabs on top, colored buttons inside tabs)

2024-09-23 Mon: 1market demo client: [working](https://github.com/harmony-one/1market-demo/pull/1/commits/6315606d05edf8c97d082c70b039d9040b21ab39) on user interface: updated layout, moved account section to header, added dark theme, updated trader and operator buttons

---

2024-09-20 Fri: 1Market: discussed next steps with Aaron, started working on [user interface](https://1market-demo.netlify.app/) improvements to show 1Market MVP next week; continue researching Gnosis conditional tokens contracts.

2024-09-19 Thu: researched polymarket docs and architecture, prepared the report with comparison with Gnosis Conditional tokens framework demo, and sent it to Aaron. Researching Gnosis [contracts](https://github.com/gnosis/conditional-tokens-market-makers) to understand how order matching works on-chain.

2024-09-18 Wed: 1market demo: added market expiration time (user can't vote after specific timestamp), deployed client on [1market-demo.netlify.app](https://1market-demo.netlify.app/)

2024-09-17 Tue: preparing 1market prototype for demo: [created](https://github.com/harmony-one/1market-demo/pull/1) PR with harmony deployment, asked Aaron to review contracts and client

2024-09-16 Mon: configured and [deployed](https://github.com/harmony-one/1market-demo/pull/1/commits/5f6ba6b9a1ba58ae817483f453d73a8bb2d9b816) 1market-demo contracts on Harmony mainnet; testing and updating demo client.

---

2024-09-13 Fri: tested Gnosis conditional tokens [demo](https://docs.gnosis.io/conditionaltokens/docs/pmtutorial1) locally, looking good, we can use for 1market demo. Started working on 1market prototype: single market, keywords from speech as a starting point.

2024-09-12 Thu: researched open source alternatives for polymarket and found a [tutorial](https://docs.gnosis.io/conditionaltokens/docs/pmtutorial5) with Gnosis conditional tokens. Setting up the enviromnent to test the prototype with a single question.

2024-09-11 Wed: [updated](https://sy.country/) SY client after Aaron's [final review](https://hackmd.io/@polymorpher/sy-country-note#sUSD-Utilities): [removed](https://github.com/harmony-one/synthetix-js-monorepo/commits/master/) mentions of SNX token in Terms of Service popup, removed Ethereum and Optimism from network select, disabled sUSD Utilities bottom panel, updated links to external resources (discord, forum).

2024-09-10 Tue: researched Polymarket [ctf-exchange](https://github.com/Polymarket/ctf-exchange) contracts and dependencies: deployed [proxy-factory](https://github.com/Polymarket/proxy-factories), but had some troubles with proxy-safe contract, because parameters are not well documented. Polymarket doesn't look like a good candidate for 1market for me - too many missing pieces in their github. Discussed it with Rika; looking for alternatives, including [sx-bet](https://github.com/sx-bet).

2024-09-09 Mon: did initial research of Polymarket infrastructure: all contracts and subgraphs are available in github, but client and centralized order book (CLOB) sources are not available; looking for alternatives and solutions with existed oracles for our 1market.

---

2024-09-06 Fri: started prediction market research: [gnosis](https://docs.gnosis.io/conditionaltokens/) and [polymarket docs](https://docs.polymarket.com/#overview-9). Setting up test contracts.

2024-09-05 Thu: deployed [new oracles](https://github.com/polymorpher/synth-oracle/commit/51df7093914a275d8093232ae3bda4533ce71598) contract from Aaron, tested and [updated](https://github.com/harmony-one/synthetix/commit/7ad7b075ab642135d61f4c3f8c0ad2ac3d5d787f) 1SY/1USDC oracle feed.

2024-09-02 Mon - 2024-09-04 Wed: Paid Time Off

---

2024-08-30 Fri: completed Harmony docs / developer section refactoring, fixed typos, created [pull request](https://github.com/harmony-one/docs-home/pull/110/files).

2024-08-29 Thu: [continue](https://github.com/harmony-one/docs-home/pull/110/files) on Harmony docs refactoring: updated deploy section, checked all scripts locally and refactored hardhat, truffle and web3 deploy docs.

2024-08-28 Wed: [created](https://github.com/harmony-one/synthetix/commit/1044563e1dbf4bfc8c6968c9b446e1a33bc83e42) test deployment with Synthetix [Perps V2](https://blog.synthetix.io/synthetix-perps-v2-is-now-live/) markets, started testing.

2024-08-27 Tue: [updated](https://github.com/harmony-one/docs-home/pull/109/files) Harmony docs (request from Soph): fixed testnet Explorer links, removed dead links, updated outdated transaction gas params. Continue on PerpsV2Markets (Synthetix).

2024-08-26 Mon: found that [PerpsV2Markets](https://blog.synthetix.io/synthetix-perps-v2-is-now-live/) contracts are not available on current deployment, working on updating current deployment script to include it. Synced with the team; Aaron mentioned that we'll need to update current oracles contract before sy.country launch.

---

2024-08-23 Fri: [added](https://github.com/harmony-one/swap-token-list/pull/18) 1SY token icon to swap-tokens-list (icon will appear on swap.country after the merge). [Added](https://github.com/harmony-one/h/blob/main/docs/synthetix-v2-deployment.md#testing) docs for manual testing of 1SY price feed and collaterization ratio on sy.country.

2024-08-22 Thu: reviewed profitable trades [PR](https://github.com/harmony-one/synthetix/pull/1) from Simao; tested it locally, [fixed](https://github.com/harmony-one/synthetix/commit/b944fc7ff4c32b2cb2b95c24905bb62e3244c929) typos, sent feedback to Simao.

2024-08-21 Wed: [updated](https://github.com/harmony-one/h/blob/main/docs/synthetix-v2-deployment.md) Synthetix v2 deployment docs with repositories cloned to /harmony-one organization. Added notes for harmony roadmap. Continue on sy.country testing; started adding basic testings steps and scenarios to documentation.

2024-08-20 Tue: completed basic 1SY oracles test: staked 1SY on sy.country, provided more liquidity to [1SY / 1USDC pool](https://info.swap.harmony.one/#/harmony/tokens/0xf88ebd99e1f776fbfd08186e1edbdad949114d1c), traded pair to impact 1SY price and checked that collaterization ratio changed according the token price change. Added Synthetix V2 deployment docs to [/h/docs/synthetix-v2-deployment.md](https://github.com/harmony-one/h/blob/main/docs/synthetix-v2-deployment.md).

2024-08-19 Mon: [sy.country](https://sy.country/) testing; [minor](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/6b3195bfcd4bdb80aa9f1df5efc3fded0a9fba57) interface fix related to 1SY token name. Synced with Li, Yuriy on the current status; continue on SY docs and testing.

---

2024-08-16 Fri: combined all information about Synthetics and oracles deployment into [one document](https://github.com/ArtemKolodko/synthetix/pull/2/commits/f92766194a1f4fca5ad65f7aacb63d4f3c97e786#diff-70c19f96c212f266fc91ab7a021a7919eaa7fa77315a264e6c1a2d1d6dc8f5a7). Provided more liquidity to 1SY/1USDC [pool](https://swap.country/#/pools/869), tested trade on swap.country and 1SY oracles prices.

2024-08-15 Thu: tested new synth oracles and [updated](https://github.com/ArtemKolodko/synthetix/pull/2/files#diff-bd1f4a8d6b9fc2a14c0ca58971b1b633d2068d11a8734c5df3814f89765ffe4b) "production" SY contracts with a new price feeds. [sy.country](https://sy.country/) works now with actual values for 1SY token, taken from swap.country ([1SY address](https://explorer.harmony.one/address/one1lz8tmx0p7am0hlggrphpak76m9y3znguj8wdsl)). We can start e2e tests: provide liquidity on swap.country, trade 1SY / 1USDC, check token price on sy.country and stake.

2024-08-14 Wed: using the new oracles [synth-oracle](https://github.com/polymorpher/synth-oracle), created by Aaron, [deployed](https://github.com/ArtemKolodko/synthetix/pull/2/commits/b060171a8bf960433371310496a88d497a2cc0f3) price feed for 1SY/USDC token pair. [Provided liquidity](https://info.swap.harmony.one/#/harmony/pools/0xbc4af4ee9164c469b9e90f7d9b5f7854556133d6) for 1USDC/1SY on swap.country and tested oracle price feed, everything works correctly. New oracles are ready to be used for 1SY price feed in Synthetix.

2024-08-13 Tue: [created](https://github.com/ArtemKolodko/synthetix/pull/2/commits/4eedacf9c72c0e8f6ee1537053166a63a3d94259) a script to change the price feed for existed synth (preparation for 1SY feed launch). Researched Synthetix [litepaper](https://developer.synthetix.io/litepaper/) to better understand the core principles and what kind of projects can be launched on top of SY.

2024-08-12 Mon: [renamed](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/9f96c642c51b762983d6a4bd427c6c208a17b928) SNX -> 1SY token in [sy.country](https://sy.country/) client, deployed an update. Checking possible bug in staking dashboard validator profile update (request from Soph).

---

2024-08-09 Fri: [added](https://github.com/protofire/interface/pull/7/files) [1SY](https://github.com/ArtemKolodko/swap-token-list/pull/1/files) token to swap.country (for now running locally), provided liquidity and tested ONE/1SY pair swap. swap.country pull requests ready for review, will be merged to main branch after we'll implement oracles feed for 1SY token.

2024-08-08 Thu: [deployed](https://github.com/ArtemKolodko/synthetix/pull/2/commits/40b11fd2a1020dad5257a0dd82f279c65cfa0901) new version of Synthetix with renamed system token (SNX -> 1SY); 1SY token in [Explorer](https://explorer.harmony.one/address/one1lz8tmx0p7am0hlggrphpak76m9y3znguj8wdsl). Updated [sy.country](https://sy.country/). Working on adding 1SY token to swap.country.

2024-08-07 Wed: researched swap.country client and [added](https://github.com/ArtemKolodko/swap-token-list/pull/1) test 1SY token to swap.country client tokens list, tested liquidity provision and [swapped](https://explorer.harmony.one/tx/0xcd550607a9c1e9a7bbb61bf0f41badce45b37b3723fc2d2f9f615b5d59e05ca2) ONE -> 1SY. The next step is to add 1SY price feed to Band oracles, I'll ask Aaron to help with that. [Launched](https://fly.io/apps/band-oracles-updater) band-oracle-updater app on fly.io.

2024-08-06 Tue: resolved issue with missing graphql file and launched [swap.country](https://swap.country/) client locally, did initial research how to add 1SY token to swap UI. Preparing new, pre-production Synthetix deployment with renamed SNX -> 1SY token.

2024-08-05 Mon: call with Pablo from Three Sigma, got a positive feedback about sy.country; agreed to check it again before going live. Checked indexing of s.country: access to DNS record is required, asked Aaron to help. We'll need to launch 1SNX token on the exchange to have fair token price, the best candidate is swap.country. Cloned [swap.country repo](https://github.com/protofire/interface/tree/harmony) locally, working on fixing installation bugs related to graphql schema.

---

2024-08-02 Fri: [updated](https://github.com/ArtemKolodko/synthetix/blob/d8eeb652f434add77d8180f768f813c5a5666bf1/v2-harmony-deployment.md) Synthetix V2 deployment instructions with information about oracle feeds. Tested [band-oracle-updater](https://github.com/harmony-one/band-oracle-updater) bot locally. Continue testing [sy.country](https://sy.country/) client. Scheduled call to discuss Synthetix launch with Pablo from ThreeSigma on Monday (Aug 05).

2024-08-01 Thu: created a bot [band-oracle-updater](https://github.com/ArtemKolodko/band-oracle-updater) that trigger [BandOracleReader](https://github.com/ArtemKolodko/band-oracle-reader) contract update. Bot will be used in Synthetix and GMX releases as a part of the oracles system.

2024-07-31 Wed: replaced all Synthetix to SY in the client; added Harmony logo to the network select. Deployed client update: [sy.country/](https://sy.country/).

2024-07-30 Tue: [updated](https://github.com/ArtemKolodko/synthetix/blob/0d9262e1af01a9fb0cecd6ab6ae836209006d5be/v2-harmony-deployment.md) complete guide how to deploy Synthetix on Harmony and run client. Helped Aaron with DNS records for sy.country domain. Testing Synthetix [client](https://harmony-synthetix.netlify.app/).

2024-07-29 Mon: [fixed](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/a5d1c2957538ec2a4fbc3ad75de25e6b139879e0) Burn transaction call in Synthetix client; fixed Explorer links, deployed client update: [harmony-synthetix.netlify.app](https://harmony-synthetix.netlify.app/). Checking Synthetix [litepaper](https://developer.synthetix.io/litepaper/).

---

2024-07-26 Fri: created new Synthetix deployment on Harmony with increased SNX supply (100 mil tokens) for testing purposes, updated contract addresses in client, deployed [client](https://harmony-synthetix.netlify.app/) update. Had a great progress, because finally I was able to borrow sUSD token for SNX. The only missing thing is oracles data for SNX token: it's not available in BAND oracles. currently I'm using BTC price for testing.

2024-07-25 Thu: investigated and [fixed](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/36369d88664f857eaf3442dbbccee14c55d6c79a) error in Mint operation in Synthetix client. Deployed client update: [harmony-synthetix.netlify.app](https://harmony-synthetix.netlify.app). Working on new contracts deployment with increased SNX supply.

2024-07-24 Wed: Synthetix deployment process on Harmony with updated scripts and docs. Discussed creation of SNX-like token with Aaron, we need to have similar token with real price to use it in client. Working on adding token supply in deployment scripts to have some SNX on balance to test.

2024-07-23 Tue: working on different bugs in Synthetix client: "current network does not support EIP-1559" on minting attempt and minting initial [SNX token](https://explorer.harmony.one/address/one1gj68vrrcdnkklcv2240lu7uann27u9dghsuk2l) supply to use in staking. Deployed BandOracleReader [contract](https://explorer.harmony.one/address/one1dj60qgw3v0fcwehfq56tyxn3kgy9kcdg25nfuy?tab=txs&shard=0) with ONE token price.

2024-07-22 Mon: Aaron fixed a bug in BandOracle proxy, and I updated Harmony  Synthetix deployment. Price quote on Mint page is working now!  Deployed client update: [harmony-synthetix.netlify.app/staking/mint](https://harmony-synthetix.netlify.app/staking/mint). To test price estimate, select Harmony in the top right network selector, connect wallet and type something in stake or borrow inputs on Mint page, quotes will be fetched from the contract. Currently it's using only Bitcoin price, later I'll update the feeds accordingly to the actual token (ETH, SNX, BTC).

---

2024-07-19 Fri: got an error while adding custom oracles aggregator to ExchangeRates contract. While debugging the problem, [created](https://github.com/ArtemKolodko/synthetix/pull/2/commits/e0d4bdaf371e935e66ba01245aab0a5402da9033) a script to test previously deployed BandOracleReader contract, and found a bug in BandOracleReader contract: latestRound method return error, which maybe caused the original error. Sent all information to Aaron (he is an author of BandOracleReader contract).
 
2024-07-18 Thu: deployed BandOracleReader with BTC and ETH currencies; [re-runned](https://github.com/ArtemKolodko/synthetix/pull/2/commits/e251ec352ac6050b856f51c5f6efd3e36b82ddba) harmony deploy with new aggregator addresses, started testing

2024-07-17 Wed: reviewed Aaron's [PR](https://github.com/ArtemKolodko/synthetix/pull/3), started integration of Band oracles with Synthetix deployment script

2024-07-16 Tue: sick time-off

2024-07-15 Mon: fixes in Synthetix v2 client: [included](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/bff8c0d148f37cdd3c74b92bf27caf27abb723ec) Reward contract, [disabled](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/418f6ed32098a49acea2f02ff2f16623e45a55af) some optional features. Debugging error in Mint quote: "No aggregator for asset".

---

2024-07-12 Fri: [Fixed](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/3647a79e508dd72904e49b4085b477b7ceb0f5d1) runtime errors, related to contract imports and number conversions, deployed synthetix client to [harmony-synthetix.netlify.app/](https://harmony-synthetix.netlify.app/). Minting is not working right now, need prepare new contracts with no mocks and real oracles support.

2024-07-11 Thu: [updated](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/fa4efa17240121822e03879edeed54a5688ed4e1) codegen script in Synthetix v2 UI repo; fixed Synthetix instance initialization with correct harmony contracts import. Continue Synthetix subgraphs research.

2024-07-10 Wed: continue working on Synthetix v2 client: [added](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/dfc9decabfed89f8d2ea26d9fec915421ac6563a) Harmony to networks switch, updated typings to support new chain. Started working on [subgraphs](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/bdb1eabb7988619ae94a766f2309cfe8867e0c5d) (required in client).

2024-07-09 Tue: [working](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/files) on adding Harmony support to Synthetix v2 client: updated menu, adding contracts build and addresses

2024-07-08 Mon: [found](https://github.com/ArtemKolodko/synthetix-js-monorepo) Synthetix v2 UI sources, researching codebase to add new contracts deployed on Harmony network

---

2024-07-05 Fri: completed Synthetix v2 deployment script, created [PR](https://github.com/ArtemKolodko/synthetix/pull/2/files); full list of deployed contracts available in [this file](https://github.com/ArtemKolodko/synthetix/pull/2/files#diff-0bb1fbd32dcd1d4dc9fd150564ba5e695d6b9adad04fb70ecd52ca287d445119). Started working on launching Synthetix v2 client locally.

2024-07-04 Thu: tried last attempt to deploy Synthetix v2 and found a way to avoid using Cannon library. Changing scripst to deploy on Harmony network.

2024-07-03 Wed: Synthetix v1.0.1: fixed deployment script bugs, mostly related to outdated web3 python library, and deployed Synthetix V1 to Harmony Mainnet. Created [PR](https://github.com/ArtemKolodko/synthetix/pull/1/files) and full [deployment logs](https://github.com/ArtemKolodko/synthetix/pull/1/files#diff-4bca52b34ed845521283b68253f10f57a0be7608eda9f08b98f15cde853aa2d6) with contract addresses.

2024-07-02 Tue: tested Synthetix V1 compile script: [fixed](https://github.com/ArtemKolodko/synthetix/pull/1/files) multiple bugs, mostly related to the outdated python and solidity libs, and compiled contract sources. Started researching deploy script.

2024-07-01 Mon: researched [Synthetix V1](https://github.com/Synthetixio/synthetix/tree/v1.0.1) dtext of using Oracle contracts, sent full report to Aaron for review

---

**2024 Q2 Review**

I'm working on porting Synthetix protocol to Harmony. The blockers have been the unavailable Chainlink and Pyth oracles on Harmony and an unfamiliar environment, [Cannon](https://usecannon.com/), for building and deploying smart contracts. I managed to solve part of the problems and to [deploy](https://github.com/ArtemKolodko/synthetix-deployments/pull/1) the protocol without oracles for now. I am currently investigating using BAND oracles, and after that I will move directly to testing Synthetix protocol on the Harmony chain.

I've made progress on [Harmony Portfolio](https://harmony-portfolio.netlify.app/dashboard), the analog of Metamask Portfolio: implemented basic Swap and Bridge page functionality in a single client. This actually required reverse-engineering the existing separate Uniswap and Harmony Bridge client apps. The portfolio project requires more testing and UI improvements before we will consider publishing it.

---

2024-06-28 Fri: worked on issue with deploying updated Synthetix oracle manager - debugged Cannon library sources, it's expect that utility create2 [contract](https://github.com/Arachnid/deterministic-deployment-proxy) to be deployed on address [0x4e59b44847b379578588920ca78fbf26c0b4956c](https://explorer.harmony.one/address/0x4e59b44847b379578588920ca78fbf26c0b4956c) on Harmony chain. It's currently a blocker, asked Aaron to help with this issue.

2024-06-27 Thu: spent some time researching how to publish Cannon package to specific network, finally [updated](https://github.com/ArtemKolodko/synthetix-v3/pull/1/commits/992fa8cd823af6174077f1f1269f382827e1e198) publish script to deploy new oracles package. Received error message regarding missing arachnid create2 contract on Harmony chain, asked Aaron for any help with that.

2024-06-26 Wed: Synthetix and Band oracles: [prepared](https://github.com/ArtemKolodko/synthetix-v3/pull/1/commits/fb052d20f50eb9e1d6ba56ec8e85c0185d86ef4f) alpha version of Cannon package with band oracles support, [created](https://github.com/ArtemKolodko/synthetix-deployments/pull/1/commits/c9d999cedb42e09d60058a855936dce923af8c5b) Band oracles config in synthetix-deployent repo. Having some issues with publishing alpha version to Cannot registry (it's required to publish new version of Sythetix protocol), working on resolving these issues.

2024-06-25 Tue: Band oracles & Synthetix: [added](https://github.com/ArtemKolodko/synthetix-v3/pull/1/commits/30d0af2b03f08e77a21f2e18412302b91a55f6f7) integration test, implented mocked Band oracles node

2024-06-24 Mon: working on integration Band oracles with Synthetix v3: [refactored](https://github.com/ArtemKolodko/synthetix-v3/pull/1/commits/73b2aab266106aaba1165dca595f86b62d21be62) inner oracles manager logic to support Band oracles node, [fixed](https://github.com/ArtemKolodko/synthetix-v3/pull/1/commits/2d7335f32428fdc166b1aa51e05327f866fd325b) imports; continue working on BandNode unit test.

---

2024-06-21 Fri: Synthetix v3: [working](https://github.com/ArtemKolodko/synthetix-v3/pull/1/files) on Band oracles integration tests

2024-06-20 Thu: Band oracles: created and verified Band oracle test [contract](https://explorer.harmony.one/address/0x182ab0923eca5889ffbf462e9995ed0f6332d4f7?activeTab=6) to validate oracle values in Explorer (currently only Bitcoin price supported). [Continue](https://github.com/ArtemKolodko/synthetix-v3/pull/1/commits/b693f4b924176441a27120752243732078f737f2) working on integrating Synthetix with Band data feed.

2024-06-19 Wed: Synthetix & Band oracles: checked sample contract with Band oracles in [Harmony docs](https://docs.harmony.one/home/developers/tools/oracles/oracle-band-protocol#de69), [started](https://github.com/ArtemKolodko/synthetix-v3/pull/1/files) working on BandNode contract in Synthetix v3 oracle manager.

2024-06-18 Tue: solved issue with Band oracles test contract (with help from Soph), deployed and played with [test contracts](https://github.com/harmony-one/band_oracle). New Explorer: helped Protofire team with determining the range of blocks with transactions spam from 2021-2022. Started research how to [add](https://docs.harmony.one/home/developers/tools/oracles/oracle-band-protocol#cc5a) Band oracles into existing contract.

2024-06-17 Mon: researched Band oracles to use it in Synthetix protocol: checked [docs](https://docs.harmony.one/home/developers/tools/oracles/oracle-band-protocol) and band oracles [test repo](https://github.com/harmony-one/band_oracle), run scripts. Unfortunately, contract returns only "0x" for all test requests. Deployed new [test contract](https://explorer.harmony.one/address/0x79b310d3070c581bd42681587a81427cd4b38b1c), but results are the same. Asked Soph for help, because he was working on Band tests before, according to Github [commits](https://github.com/harmony-one/band_oracle/commits/main/).

---

2024-06-14 Fri: [excluded](https://github.com/ArtemKolodko/synthetix-deployments/pull/1/commits/fc14415d516c7f028bc0ce667c7661a6abdc6f6c) Chainlink CCIP from Synthetix deployment script; deloyed Synthetix contracts to Harmony Mainnet Shard 0, addresses are available in the [deployer address](https://explorer.harmony.one/address/0x98f0c3d42b8dafb1f73d8f105344c6a4434a0109) transactions history. Two things to be done before testing: implement mocked Chainlink feed contracts (I used a random address) and verify deployed contracts; existed verification script for Cannon deployment will not work for Harmony (it's written for Etherscan API), so I'll need to find a way to verify it using our verification service.

2024-06-13 Thu: did some research on [Synthetix v2](https://github.com/Synthetixio/synthetix/tree/v2.101.2/contracts): it [utilize](https://github.com/Synthetixio/synthetix/blob/v2.101.2/contracts/ExchangeRates.sol) Chainlink price feeds, but doesn't require Pyth and Chainlink CCIP (like v3), so it should be easier to launch. We will need to implement mocked oracle contracts to replace Chainlink feed. Launched Synthetix [v2 client](https://github.com/Synthetixio/js-monorepo/tree/master/v2/ui) locally.

2024-06-12 Wed: discussed issues with deterministic contract (required to deploy Synthetix) with Aaron, made some [changes](https://github.com/ArtemKolodko/deterministic-deployment-proxy/pull/2/files) to the compilation and deployment scripts following his advice. After all updates got "transaction already finalized" response from the deterministic contract script; will check it from Synthetix deployment script side on Thursday.

2024-06-11 Tue: worked on deploying arachnid create2 contract that is necessary for Synthetix deployment. Found [repo](https://github.com/Arachnid/deterministic-deployment-proxy) with original contract, created deployment [script](https://github.com/ArtemKolodko/deterministic-deployment-proxy/pull/1/files) for Harmony chain, but got an error with chainid mismatch for compiled contract and target network; working on fix.

2024-06-10 Mon: started discussion with Difeng Jiang - manager from Chainlink Labs - regarding launching CCIP on Harmony chain; shared some basic details and requirements from our side. Continue working on other problems with Synthetix deployment: investigating error "could not populate arachnid signer address" that was raised during the deployment script run.

---

2024-06-07 Fri: Synthetix use two oracle providers - Chainlink CCIP and Pyth ([docs](https://docs.synthetix.io/synthetix-protocol/the-synthetix-protocol/oracles)). Sent a request to Pyth to add support of Harmony chain. Received a response from Chainlink about adding CCIP support on Harmony and replied with a general description of our requirements for launching the Synthetix port. Checked Chainlink CCIP [router](https://optimistic.etherscan.io/address/0x261c05167db67B2b619f9d312e0753f3721ad6E8#readContract) and [token pool](https://optimistic.etherscan.io/address/0xe470A3068302CF045Eec3B800dDBFf42B42e18D8#readContract) contracts - the number of methods is not so large and it is possible to create a mocked version for a test, but this is not enough - a CCIP backend is required for real operation; for me it is better to wait for a response from CCIP support regarding integration first, they should respond early next week.

2024-06-06 Thu: Synthetix deployment issues: contacted Chainlink CCIP support through the [website form](https://chain.link/ccip-contact) to inquire about adding the Harmony chain. Aaron suggested to try to use mocked CCIP contracts; checking [contracts](https://github.com/smartcontractkit/ccip) to have a list of methods to implement that will needed in Synthetix protocol.

2024-06-05 Wed: researched Chainlink CCIP architecture docs and deployment [instructions](https://docs.chain.link/ccip/getting-started) as part of Synthetix deployment; we are currently blocked on the [first step](https://docs.chain.link/ccip/getting-started#deploy-the-sender-contract) because Chainlink CCIP doesn't support Harmony chain and have to be added by Chainlink team ([full list](https://docs.chain.link/ccip/supported-networks/v1_2_0/mainnet) of supported chains).

2024-06-04 Tue: researched Chainlink contracts on Harmony: [previous](https://docs.harmony.one/home/developers/tools/oracles/chainlink) deployment is not supported anymore; also Synthetix uses [Chainlink CCIP](https://blog.chain.link/ccip-mainnet-early-access/) that was launched in 2023; currently Synthetix deployment is blocked by Chainlink [CCIP](https://docs.chain.link/ccip).

2024-06-03 Mon: some progress regarding Synthetics deployment: [fixed](https://github.com/ArtemKolodko/synthetix-deployments/pull/1/commits/d7117eeb9d20082d7b900c59accd56d29be2dcfe) errors in deployment script; launched the script, some of the [transactions](https://explorer.harmony.one/address/0x98f0c3d42b8dafb1f73d8f105344c6a4434a0109) were succesfull, but the deployment wasn't complete because of the missing contracts that should be prepared on Harmony chain before the deployment. List of the contracts (can be updated later): "arachnid create2", [Chainlink weth aggregator](https://docs.chain.link/data-feeds/price-feeds/addresses/?network=base), [Chainlink router](https://docs.chain.link/ccip/supported-networks/v1_2_0/mainnet). Working on preparing this contracts to deployed on Harmony chain.

---

2024-05-31 Fri: had a conversation with Synthetix devs in discord channel and DMs, but we haven't found any resolution yet - they claim that `cannon build`, which I successfully [executed](https://github.com/ArtemKolodko/synthetix-deployments/pull/1/files#diff-a9184833f3672b3da54fb788c8fe696ccb8b79627217245e7a74bd0847459408R2), should have already deploy the protocol, but I don't see any transactions in Harmony network (double-checked). Synthetix deployment currently stuck because of this issue.

2024-05-30 Thu: continue researching Cannon commands. Looks like package published on IPFS ([it's available on Cannon website](https://usecannon.com/packages/synthetix-test-harmony/latest/1666600000-main)) but not deployed; tried to deploy with `cannon deploy` with different set of arguments but also not successful. Finally, I [raised a question](https://discord.com/channels/413890591840272394/459603818246701056/1245834477226299473) in Synthetix discord dev channel.

2024-05-29 Wed: continue researching Cannon docs to deploy a package; discussed deployment issues with Aaron

2024-05-28 Tue: prepared first version of Synthetix deployment script for Harmony network, published Cannon package ([commands and logs](https://github.com/ArtemKolodko/synthetix-deployments/pull/1/commits/6b404a2f6b88c975563095ee521712aebe411a25)). Cannon package seems to be published, but there is not transaction on Harmony chain. Asked Aaron to review [PR](https://github.com/ArtemKolodko/synthetix-deployments/pull/1) and help with deployment issues.
 
2024-05-27 Mon: didn't find sequencer sources in Vertex Protocol [GitHub](https://github.com/orgs/vertex-protocol/repositories), asked in discord channel. Looking on Vertex architecture following Vertex protocol [review](https://github.com/harmony-one/h/blob/main/docs/review-notes-vertex-protocol.md#key-designs), docs and web app. Issue with sequencer sources was also [addressed](https://github.com/harmony-one/h/blob/main/docs/review-notes-vertex-protocol.md#some-issues) by Aaron in protocol review.

---

2024-05-24 Fri: Tried to adjust existed Cannon scripts to deploy Systetix on Harmony chain, tried different configs from their repo, getting errors on piblish ("Could not find any deployments"). Tried to get some help from Systetix dev channel in discord ([link](https://discord.com/channels/413890591840272394/459603818246701056/1243302442205188156)), but getting only common advices.

2024-05-23 Thu: Researching Cannon deploy scripts and docs (framework that used by Systetix team to deploy the protocol)

2024-05-22 Wed: [prepared PR](https://github.com/ArtemKolodko/synthetix-deployments/pull/1/files) with Systetix deploy script; working on adjusting script for Harmony network 

2024-05-21 Tue: cotinued working on Syntetix deployment: discussed deployment issues with Syntetix devs in discord channel, got some advices regarging cannon tool they use to build and publish; started preparing custom set of deployment scripts following their advice.

2024-05-20 Mon: working on synthetix deployment: fixed issue with IPFS, almost completed test deploy on Arbitrum Sepolia, but got an error "Signer does not have publishing permissions on the "synthetix-perps-market" package" on the last step - protocol publishing. Didn't find any information about granting permissions, [asked](https://discord.com/channels/413890591840272394/459603818246701056/1242168007434698803) synthetix community to help in official Discord channel.

---

2-Week Deliverables by 2024-05-20:

Harmony Portfolio: implement Bridge page that repeats all major features of the Harmony Bridge client: [https://bridge.harmony.one](https://bridge.harmony.one/one).

While working on implementing the Bridge in the Harmony Portfolio, I aimed to utilize best practices – the design was inspired by the existing bridge in the Metamask Portfolio, familiar to users but with the internal logic of the Harmony Bridge. I encountered nuances in the implementation, some rooted in Layerzero, and each token transfer needed manual testing, consuming significantly more time; nevertheless, I managed to thoroughly understand the architecture of the current Harmony Bridge and start implementation within a few days, which was quite swift given the complexity of this application.

---

2024-05-17 Fri: configured IPFS (it's required to deploy systetix), testing existed Syntetix deployment scripts for Arbitrum Sepolia

2024-05-16 Thu: Syntetix deployment: researching [core protocol](https://github.com/Synthetixio/v3-contracts) repo and scripts, settings up local IPFS

2024-05-15 Wed: Harmony Portfolio: [added](https://github.com/harmony-one/harmony-portfolio/commit/2e2fcd16366423d147a46251a9c73b050cc2ad1a) notification of latest bridge operation, if user close the page before it completes; continue working on [Systetix](https://github.com/Synthetixio/synthetix-deployments) deployment

2024-05-14 Tue: Look into Syntetix [deployment scripts](https://github.com/Synthetixio/synthetix-deployments) and docs

2024-05-13 Mon: completed bridge MVP in Harmony Portfolio client, tested Arbitrum and BNB chains, [deployed](https://harmony-portfolio.netlify.app/dashboard) an update.

---

2024-05-10 Fri: Harmony Portfolio: [added](https://github.com/harmony-one/harmony-portfolio/commit/c86f6fcec6c86b6365389a5344043bd613f3836e) modal to track current bridging operation; [completed](https://github.com/harmony-one/harmony-portfolio/commit/e06531b0f230bf749323c8802cbc1dd0bcfc203c) 1 of 4 bridging steps: "approveEthManger" (for now for Arbitrum - Harmony route with erc20 token).

2024-05-09 Thu: fetching bridge tokens from bridge API endpoints, [added](https://github.com/harmony-one/harmony-portfolio/commit/a0c58627d8c357b60aa2f1b829ea1cf0a044834f) modal with list of available tokens in Portfolio - Bridge page

2024-05-08 Wed: contunue researching Harmony Bridge sources to implement bridge features in Portfolio. Look into [Synthetix](https://github.com/Synthetixio/synthetix-v3) repos to port it to Harmony chain.

2024-05-07 Tue: [added](https://github.com/harmony-one/harmony-portfolio/commit/55e340f86e8fc17dbe6a8a9e4638272f796de0a5) bridge data privider, updated bridge API methods in Harmony Portfolio client. Researching main Bridge client architecture.

2024-05-06 Mon: synced with Yuriy on adding bridge page to Harmony Portfolio; started [researching](https://github.com/harmony-one/layerzero-bridge.frontend) main bridge client architecture to add same features on Harmony Portfolio page. Checked confidential data in harmony1bot logs: some logs can be improved but no sensitive data like hot wallet primary keys is printed in logs.

---

2024-05-03 Fri: Harmony Portfolio: [fixed](https://github.com/harmony-one/harmony-portfolio/commit/80ffb5fa309a2cb9f59d0ef59eb9db6be489b5c5) USDT token price in Dashboard, started working on Bridge page. Explorer client support: [removed](https://github.com/harmony-one/explorer-v2-frontend/commit/8d1143d05a3e4c8dec57ae9a6ef2e5dfff7bf321) last data provider with direct request to Coingecko API (no more "Too many requests" from Coingecko, all data fetched from our backend with cache enabled).

2024-05-02 Thu: Explorer support: it took some time, but finally [fixed](https://github.com/harmony-one/explorer-v2-frontend/pull/288) Explorer client build on [Netlify](https://app.netlify.com/sites/explorer-v2/deploys/6633ca1c8f683a0008c81e0b) side and deployed [Explorer](https://explorer.harmony.one/) update. ONE token price now fetched from Explorer API instead of direct request to Coingecko API; data on backend updated every 5 minutes.

2024-05-01 Wed: Explorer support: Soph asked to refactor Coingecko requests from client side to our Explorer backend to reduce the number of requests to Coingecko API; added fix on [backend](https://github.com/harmony-one/explorer-v2-backend/pull/115) and explorer [client](https://github.com/harmony-one/explorer-v2-frontend/pull/286/files) side; updated backend. Client update failed during build on Netlify, investigating the problem.

2024-04-30 Tue: Harmony Portfolio: [added](https://github.com/harmony-one/harmony-portfolio/commit/48e61e3b038b0501a281a40e49172552f1d5d165) support of ERC20 tokens send on Send & Receive page. Added erc20 balance check and MAX buttons, deployed an [update](https://harmony-portfolio.netlify.app/send). Researched [https://harmony.one/defi](https://harmony.one/defi) page, had a call with Yuriy about next project.

2024-04-29 Mon: researching Layer 3 docs for Timeless with general description of decentralized protocols for open social graph ([link1](https://docs.google.com/document/d/1UzcdSHSmSiJDMoqyJxgUjFLq-b6ENHric3LGY3c5hZU/edit#heading=h.c19i328f5vkb), [link2](https://docs.google.com/document/d/1_X4Yltq5PH2mpRrJ5v__EXG2rePQs6W3502v9ltlxLQ/edit#heading=h.i6qb1k6n8fs6)).

---

2024-04-26 Fri: Paid Time Off.

2024-04-25 Thu: Paid Time Off.

2024-04-24 Wed: Polygon CDK - continue source code research; checking configs and main [docker-compose](https://github.com/0xPolygonHermez/zkevm-node/blob/develop/test/docker-compose.yml) file.

2024-04-23 Tue: Harmony Portfolio: [completed](https://harmony-portfolio.netlify.app/send) Send page with ONE tokens support (ERC20 need to be added as well). Polygon CDK - started researching sources to use it in Harmony blockchain.

2024-04-22 Mon: continue on Polygon CDK: configured workaround for Apple M1 and finally launched network on local machine; launched test suit with sample transactions.

---

2024-04-19 Fri: investingating Polygon CDK: followed [tutorial](https://docs.polygon.technology/cdk/get-started/quickstart-rollup/) tried to run Rollup on local machine, but got some error in one of the docker containers. After some research [found](https://github.com/0xPolygonHermez/zkevm-node/blob/develop/docs/running_local.md#warning) that it cannot be runned on ARM-powered Macs.

2024-04-18 Thu: started working on Polygon CDK, researching docs, [preparing](https://docs.polygon.technology/cdk/get-started/quickstart-rollup/) local environment to launch it on local machine to check how it works.

2024-04-17 Wed: Harmony Portfolio - added Receive page with QR code (similar to this one: https://portfolio.metamask.io/send?tab=receive); started working on validations on Send page

2024-04-16 Tue: [Added](https://github.com/harmony-one/harmony-portfolio/commit/a98131b96b3fd285ec43ed2d661017af0c5566a2) basic components for Send & Receive page, [added](https://github.com/harmony-one/harmony-portfolio/commit/1f93617af13bfa3229da041e581325054d39452c) insufficiend balance message on Swap page and [calculation](https://github.com/harmony-one/harmony-portfolio/commit/22753efc82955901dd02513bde38981df586c731) of total USD value in Portfolio.

2024-04-15 Mon: Harmony Portfolio: added USD amount data for ERC20 user tokens in Dashboard (prices fetched from Harmony Bridge), [updated](https://harmony-portfolio.netlify.app/dashboard) the client

---

2024-04-12 Fri: Harmony Portfolio: [added](https://github.com/harmony-one/harmony-portfolio/commit/cfc292e642d80c1f49c2aa8b9a0056a19c57470e) ERC20 tokens list in Dashboard, deployed an [update](https://harmony-portfolio.netlify.app/dashboard)

2024-04-11 Thu: investingated issue with ERC20 contract indexer with Soph (Joskins need this data for rewards, based on ERC20 holders list), prepared [PR](https://github.com/harmony-one/explorer-v2-backend/pull/114/files) with fix, updated tokens indexer.

2024-04-10 Wed: [completed](https://github.com/harmony-one/ONE-Resume-AI/pull/1) web build for OneResumeAI, deployed an update: [https://one-resume-ai.netlify.app/](https://one-resume-ai.netlify.app/); but having wrong response from our AI service (https://harmony-llm-api-dev.fly.dev), asked Nagesh for help. Investingating issue with indexing [ERC20 contract](https://explorer.harmony.one/address/0x51d76b3324074e8255fafe699408ec4401b29c4e) (request from Soph).

2024-04-09 Tue: [added](https://github.com/harmony-one/harmony-portfolio/commit/78308760ca77aceff01edbf102f924d66be5d1d0) trade quote loading status, improved swpa UI in Harmony Portfolio, [deployed](https://harmony-portfolio.netlify.app/swap) an update. Investigating a bug in Explorer client - missing Holders tab on [address page](https://explorer.harmony.one/address/0x51d76b3324074e8255fafe699408ec4401b29c4e?activeTab=6) (Soph asked for it).

2024-04-08 Mon: [implemented](https://github.com/harmony-one/harmony-portfolio/commit/54de2d8a8a9a071989bf4fa5e4ab059918d830ca) tokens swap on Swap page in Harmony Portfolio, deployed an update: [https://harmony-portfolio.netlify.app/swap](https://harmony-portfolio.netlify.app/swap)

---

2024-04-05 Fri: sick day-off

2024-04-04 Thu: sick day-off

2024-04-03 Wed: sick day-off

2024-04-02 Tue: [created](https://github.com/harmony-one/ONE-Resume-AI/pull/1/commits/06988b235341d36b2dab2f4db58254a198a6b6aa) separate App root component for OneResumeAI web build, working on splitting internal code into separate pieces to exclude iOS-only React Native modules from web build.

2024-04-01 Mon: researched solution for integration of harmony1bot chat with OneResumeAI with Nagesh; continue working on web version of OneResumeAI.

---

**2024 Q1 Review (14 hours)**

During the Q1, I contributed to the development team of the VoiceAI app, focusing on UI elements and writing tests. Developed an inscriptions indexer backend utilized in an inscriptions lottery. Maintained harmony1bot.

Successfully launched a Human Protocol client at h.country: created a prototype for the client app, added support of key features such as routing, core user interface components, and Firebase integration. Started working on Harmony Portfolio client, a counterpart to the Metamask portfolio, with the alpha version scheduled for release by the end of March 2024.

During work on the Swap page in the Harmony Portfolio, I encountered difficulties due to the need to copy some features from the Harmony Swap client (https://swap.harmony.one), which is based on Uniswap. Researching the client's code and Uniswap documentation took much more time than planned; however, I managed to implement basic operations: Swap Quote, Wrap (ONE -> WONE), and Unwrap. Currently in the process of implementing the final operation (Swap), after which I can move on to improving the user interface.

---

2024-03-31 Sun:

2024-03-30 Sat: [continue](https://github.com/harmony-one/harmony-portfolio/commits/main/) working on implementing erc20 tokens swap in Harmony Portfolio. Researched Uniswap code in existed swap.harmony.one client, but got an error in Uniswap SDK lib when tried same approach locally in Portfolio client. Looking for solutions, debugging lib code.

2024-03-29 Fri: researched and [implemented](https://github.com/harmony-one/harmony-portfolio/commit/bc977ec1ad0e6c24893c0d2e52f7d9047be3e0a4) swap quote in Harmony portfolio, deployed an update to [https://harmony-portfolio.netlify.app/swap](https://harmony-portfolio.netlify.app/swap)

2024-03-28 Thu: researching swap mechanism implementation in [https://swap.harmony.one](https://swap.harmony.one), [started](https://github.com/harmony-one/harmony-portfolio/commit/26e1c8b85e8bbe39188d05ca7855e9d986fedde0) implementing ERC20 tokens swap in Harmony Portfolio.

2024-03-27 Wed: Harmony Portfolio: [added](https://github.com/harmony-one/harmony-portfolio/commit/10ff75b6c46b3c46d3473d5b3dbdd26882925e69) ERC20 token balance fetch in Swap page, fixed issue with SVG icons exported from Figma.

2024-03-26 Tue: worked on web build for ONE resume AI, prepared [PR](https://github.com/harmony-one/ONE-Resume-AI/pull/1). Web build was successfully prepared but document picker doesn't work as expected. Checking different solutions, prepared temp web page with current build to [one-resume-ai.netlify.app](one-resume-ai.netlify.app).

2024-03-25 Mon: Harmony Portfolio client: [added](https://github.com/harmony-one/harmony-portfolio/commit/9bd991b845dc8dc89cbe4922d257373ecc3dc41f) support of native token wrap (ONE to WONE); started working on unwrap method (WONE to ONE). Started working on AI Match Maker initiative, checking description on [https://harmony.one/aimm](https://harmony.one/aimm).

---

2024-03-22 Fri: researching [swap.harmony.one](https://github.com/protofire/interface/tree/harmony) client app sources and [Uniswap SDK](https://docs.uniswap.org/sdk/v3/overview): how to create and sign a transaction to include it in Harmony Portfolio [swap](https://harmony-portfolio.netlify.app/swap) page.

2024-03-21 Thu: start working on swap page: implemented basic swap page components, [deployed](https://harmony-portfolio.netlify.app/swap) the update. Started researching current [https://swap.harmony.one](https://swap.harmony.one/) sources.

2024-03-20 Wed: [updated](https://github.com/harmony-one/harmony-portfolio/commit/db873d52231c145b5c0d0e566334d332d7be3c4b) harmony portfolio client layout, menu and app styles according new figma prototypes from Alaina, [published](https://harmony-portfolio.netlify.app/dashboard) update to netlify.

2024-03-19 Tue: added total user balance and tokens list in Harmony Portfolio dashboard (currently only native token supported), deployed the updates to [https://harmony-portfolio.netlify.app](https://harmony-portfolio.netlify.app).

2024-03-18 Mon: Harmony portfolio client: added connect / disconnect Metamask wallet, display user wallet address in the menu. Started working on fetching total balance in USD. [Pushed](https://github.com/harmony-one/harmony-portfolio) all changes to harmony-portfolio repo.

---

2024-03-15 Fri: continue working on portfolio client (Metamask portfolio copy): added menu, updated common layout, added dark-light theme switch.

2024-03-14 Thu:  started working on [Metamask portfolio](https://portfolio.metamask.io/): source code for existed metamask portfolio is not available, will work on out own app. Initialized basic React app, added routing, removed boilerplate code.

2024-03-13 Wed: synced with Theo P on a new 2-week deliverables. [Added](https://github.com/harmony-one/explorer-v2-backend/commit/d648c9df84b11d8c065d653f40a83ff9cc8060c1) decimals data to ERC20 transfer info. Started telegram client on web, preparing basic app prototype.

2024-03-12 Tue: helped Soph to implement endpoint to get ERC20 transfer info (sender, recipient, amount). Completed basic implementation, created [PR](https://github.com/harmony-one/explorer-v2-backend/pull/112).

2024-03-11 Mon: started searching for top AI models for voice/conversation data. Investigated a bug reported by Soph: incorrect ERC20 circulation supply in the Explorer; decided not to implement a fix as it might take a couple days and we expect to release a new Blockscout Explorer in the next 1-2 months.

---

2024-03-08 Fri: researching [Peapods finance](https://docs.peapods.finance/) docs and webapp. Contract sources are not avaialble, [found](https://etherscan.io/token/0x02f92800F57BCD74066F5709F1Daa1A4302Df875#code) only PEAS ERC20 contract.

2024-03-07 Thu: continue researching Bitcoin L1 projects. Started researching [Peapods Finance](https://peapods.finance/).

2024-03-06 Wed: Checked MAI finance docs. Token MAI is [depegged](https://coinmarketcap.com/currencies/mai/) since July 2023; it's a algorithmic stablecoin, which brings additional risks compared to traditional fiat-backed stablecoins.

2024-03-05 Tue: Checked Baseline website and docs. Contract sources are not available right now (checked the website, github, discord), it's marked as "will be available soon". It can be related to the recent [protocol audit](https://docs.baseline.markets/assets/audit_trust_security.pdf). They have a concept of "non-liquidatable leverage" mentioned on the website; it's not very clear how it works, trying to dive deeper into the docs.

2024-03-04 Mon: Researching [BOB](https://github.com/bob-collective/bob) contracts and docs.

---

2024-03-01 Fri: Started [researching](https://bitcoin-renaissance.com/) bitcoin light client [docs](https://docs.gobob.xyz/docs/build/bob-sdk/relay)

2024-02-29 Thu: [completed](https://github.com/harmony-one/h.country/pull/102) client updates and refactoring, merged PR

2024-02-28 Wed: [working](https://github.com/harmony-one/h.country/pull/102) on minor UI fixes and refactoring

2024-02-27 Tue: [fixed](https://github.com/harmony-one/h.country/commit/b21b9876155647220e33ea96ad2315365c8fb99f) long hashtags in actions feed - show in one line 

2024-02-26 Mon: [fixed](https://github.com/harmony-one/h.country/pull/95) user page filters UI bug (wrong alignment), [improved](https://github.com/harmony-one/h.country/pull/91) styles to match figma prototypes

---

2024-02-25 Sun: [added](https://github.com/polymorpher/dot-country-embedder/pull/9/files) mint method call in dot-country-embedder, added empty metadata for tokens.

2024-02-24 Sat: investigated bug with 3rd column in links header, [added](https://github.com/harmony-one/h.country/commit/60ca971a49c6886aebd848137a5a8c90d25fcd69) fix. Started working on mint feature for dot-contry-embedder service.

2024-02-23 Fri: [worked](https://github.com/harmony-one/h.country/pull/75) on h.country interface: fixed display names, fixed links in actions feed, new user goes to hash picker even if it’s from a profile link.  

2024-02-22 Thu: [added](https://github.com/harmony-one/h.country/pull/57) referrer address to user create message (“0/abcd adds 0/4298”), added live counter to actions feed time (1s -> 2s -> 3s...), [implemented](https://github.com/harmony-one/h.country/pull/61) actions feed live update.

2024-02-21 Wed: [updated](https://github.com/harmony-one/h.country/pull/39) header list: changed main icons, updated layout. Fixed bug with missing date in user join action.

2024-02-20 Tue: [added](https://github.com/harmony-one/h.country/pull/25) 3 shortcuts: /new, hashtags and hashtags with counter

2024-02-19 Mon: [updated](https://github.com/harmony-one/h.country/pull/17) action feed: moved date to the right side, added relative date formatting. [Added](https://github.com/harmony-one/h.country/pull/18) filter by hashtag.

---

2024-02-16 Fri: worked on h.country client interface update: [added](https://github.com/harmony-one/h.country/pull/2) fixed menu, loading state, refactored duplicated code, moved Welcome page from human-protocol, updated fonts.

2024-02-15 Thu: created new client h.country, added main page with mocked data based on design prototype from Theo, optimized for mobile devices, [pushed](https://github.com/harmony-one/h.country/tree/main/client) to the new repo, deployed on [https://h-country.pages.dev](https://h-country.pages.dev/).

2024-02-14 Wed: [added](https://github.com/harmony-one/human-protocol/commit/fb98d0870aa651ac9d188c42cd50eaa7190f7cef) hashtags instead of "periodic table" elements on welcome page, removed notification. [Added](https://github.com/harmony-one/human-protocol/pull/14) color icons on welcome page.

2024-02-13 Tue: [reviewed](https://github.com/harmony-one/human-protocol/pull/12) PR with merging Julia's code to human-protocol, updated the website. Started working on new user profile page with user data and OAuth options.  

2024-02-12 Mon: worked on human protocol client: [updated](https://github.com/harmony-one/human-protocol/pull/9) layout with periodic table-style interface, [refactored](https://github.com/harmony-one/human-protocol/pull/10) wallet generation

---

2024-02-09 Fri: worked on human protocol client, [added](https://github.com/harmony-one/human-protocol/commit/948f9a9031bd2c97c5c620af99d62f1604ad98cb) Github and Twitter Oauth, [added](https://github.com/harmony-one/human-protocol/commit/aef29f1ff5f5b3e456b802e51c683f76da695557) menu with user profile and LogOut button. [Deployed](https://human-protocol.pages.dev/) an update.

2024-02-08 Thu: [deployed](https://human-protocol.pages.dev/welcome) human-protocol client in harmony Cloudflare account. Reviwed and merged [PR#2](https://github.com/harmony-one/human-protocol/pull/2) and [PR#3](https://github.com/harmony-one/human-protocol/pull/3) from Theo P. [Added](https://github.com/harmony-one/human-protocol/commit/ceb9db1a4e3dd66769f384aaf120890724a0288d) mobile view optimizations in Welcome page, updated styles.

2024-02-07 Wed: [implemented](https://github.com/harmony-one/human-protocol/commit/769a0771c6f8ad0988aa4a63cf9d638b958ed486) topics list, feed (Global and Harmony), completed basic integration with API, [deployed](https://client-ehl.pages.dev/) demo client on Cloudflare.

2024-02-06 Tue: working on Human Protocol client: initialized [client app](https://github.com/harmony-one/human-protocol/tree/main/client), working on topics list page

2024-02-05 Mon: researched ETH Denver [project](https://www.x.country/human-protocol-social-shard-1-00e81d36535a4f2981a18012854b2c1e), synced with Sun and Yuriy. Started working on client app, [deployed](https://denver-app.pages.dev/) it on Cloudflare to test, testing Geolocation API in browser.

---

2024-02-02 Fri: added Substack embed support: implemented custom Substack URL param in 1country-embedder service, created [PR #1](https://github.com/harmony-one/dot-country-embedder/pull/1), it's under the review by Aaron. Added embed Substack pages in 1country-client for inscription domains, created PR [#215](https://github.com/harmony-one/1-country.frontend/pull/215). 

2024-02-01 Thu: [fixed](https://github.com/harmony-one/HarmonyOneBot/pull/353/commits/cfd9d7537305f5950e1a15c88556d70fae0e3f1f) bug in 1bot with holding 1 ONE in user hot wallet. Researched Aaron's [1country-embedder](https://github.com/harmony-one/dot-country-embedder) service, started working on supporting Substack links from request url. This is required to add Substack embed page to 1.country domains inscriptions.

2024-01-31 Wed: took day-off to prepare docs for upcoming portugues immigration office visit next day, notified Sun about that.

2024-01-30 Tue: reviewed [PR 353](https://github.com/harmony-one/HarmonyOneBot/pull/353) from Frank in with inscriptions support in 1bot. [Added](https://github.com/harmony-one/1-country.frontend/commit/01ad406bde1f7e053d102d35e2dbd264fd93110b) embed Notion page for inscription domains. Researched embed Substack, found issues on embedded service (it works only with contracts) asked Aaron to help with embedder.

2024-01-29 Mon: ONE bot credits refill [update](https://github.com/harmony-one/HarmonyOneBot/pull/352): 1 ONE should remain in the wallet to cover gas, the rest goes to multisig. Start 1.country: inscription domains data, embed notion.

---

2024-01-26 Fri: [added](https://github.com/harmony-one/inscription.indexer/pull/8/files) restricted domains list in inscriptions indexer; implemented access control for 1 letter domains. Updated inscriptions indexer instance. Working on embed notion and substack urls support in 1.country client.

2024-01-25 Thu: synced with Yuriy for the latest lottery updates, [updated](https://github.com/harmony-one/inscription.indexer/pull/5) inscriptions indexer, moved hardcoded variables to config, improve typings. Skipped second half of the day because of some food poisoning, recovering.

2024-01-24 Wed: implemented full process of registering 1.country domain for inscriptions lottery, created [PR #3](https://github.com/harmony-one/inscription.indexer/pull/3/files) in inscriptions indexer.

2024-01-23 Tue: [Added](https://github.com/harmony-one/inscription.indexer/commit/9fd1b329451201e5815132e9934a87242d65b8cb) new fields to inscriptions indexer database schema, implemented flexible filers support in GET /inscriptions endpoint. Helped Yuriy with examples of renting 1country domains with one-country-sdk to use it in lottery.

2024-01-22 Mon: made a couple of minor updates, [configured](https://github.com/harmony-one/inscription.indexer/commit/17d5d9bdef3c7555054bde19d6fb8631dafd1f66) and deployed inscriptions indexer on fly.io. Drafted architecture for inscriptions lottery with Yuriy.

---

2024-01-19 Fri: completed integration of inscriptions indexer with Postgres storage, tested sync on Harmony mainnet. Added GET /inscriptions endpoint to get parsed data, created [PR](https://github.com/harmony-one/inscription.indexer/pull/1) to review.

2024-01-18 Thu: [Added](https://github.com/harmony-one/inscription.indexer/pull/1/files) database entities in inscription indexer, configured indexer state table and saving inscriptions into Postgres database.

2024-01-17 Wed: Learning inscription [indexer](https://github.com/harmony-one/inscription.indexer) codebase, started working on storing inscriptions in database.

2024-01-16 Tue: Completed address limiter, created [PR #11](https://github.com/harmony-one/s/pull/11).

2024-01-15 Mon: [added](https://github.com/harmony-one/s/pull/11/commits/5be853b5260ac34ccbff38a0bbbff0949ce0fc0d) executed status to completed transactons. Started working on limits by user address by hour.

---

2024-01-12 Fri: working on transfer amount limiter. Added new DB table to store pending transactions. Completed first version of transfer limiter, started testing.

2024-01-11 Thu: sick day-off

2024-01-10 Wed: sick day-off

2024-01-09 Tue: synced with devs about new moe project, started working on rate limiter

2024-01-08 Mon: reviewed [moe](https://github.com/harmony-one/s/tree/main/moe) repository code, sent review with couple of notes to Sun. Researching [moe](https://harmony.one/moe).

---

2023-12-25 Mon - 2024-01-05 Fri: Paid time off.

---

2023-12-22 Fri: [added](https://github.com/harmony-one/x/commit/122b33cddb97914f1b383a90209b229fd9ead688) in-memory cache to x-api backend endpoints

2023-12-21 Thu: [Added](https://github.com/harmony-one/x/pull/411) progressView tests, researched new [inscription](https://github.com/harmony-one/1country-inscription) project, discussed  inscription indexer architecture with Yuriy.

2023-12-20 Wed: Twitter API service: [update](https://github.com/harmony-one/x/commit/55a9ed1aabe8249fd3110f7613a746b5ea9009ce) new Twitter list on create; added default rate limiter. Check current state of X app unit tests.

2023-12-19 Tue: [updated](https://github.com/harmony-one/x/commit/aba84ba598be94706bddec0ed9f8ef50f49ddd24) x-api backend: added params to GET /list, improved delete and update twitter list endpoints. [Added](https://github.com/harmony-one/explorer-v2-frontend/pull/285) total undelegated info to Staked dropdown in Harmony Explorer (from Aaron).

2023-12-18 Mon: [reviewed](https://github.com/harmony-one/x/pull/399) Twitter lists PR from Yuriy. [Refactored](https://github.com/harmony-one/x/commit/cce850cf8681b38c508323c361ebab97726aa81a) Twitter lists: removed separate module and controller, improved /update endpoint. [Added](https://github.com/harmony-one/explorer-v2-frontend/commit/1924e42975d8218b298635705f2808ac16754b8f) undelegation info to Staking tab in Explorer client (request from Aaron).

---

2023-12-15 Fri: [implemented](https://github.com/harmony-one/x/commit/9d9206930f30b369aea65809a1e54a2893dbf684) endpoints getListByName and getLists in x-api backend service, configured twitter Lists as described [here](https://github.com/harmony-one/x/blob/main/doc/follows). Tweets from the lists are updated every 30 minutes and can be used to provide additional context to ChatGPT. [Deployed](https://x-api-backend.fly.dev/api#/) x-api backend.

2023-12-14 Thu: [added](https://github.com/harmony-one/x/commit/81289e0fb5fed1131d8a7802306452dcd26a4270) database table to store a list of tweets for each topic, implemented a cron job to update this list in our database every 30 minutes. Tested with real Twitter API.

2023-12-13 Wed: [added](https://github.com/harmony-one/x/commit/67cdd4a7845e5a2476f2a4c24b0c5244b605de6d) basic implementation of twitter list endpoint in x-api backend; working on database schema. 

2023-12-12 Tue: synced with Sun and Yuriy about new [twitter-api](https://github.com/harmony-one/x/pull/342/files) project; [started](https://github.com/harmony-one/x/tree/main/backend/x-api) working on backend app, implemented basic features :project structure, configuration, database, Swagger API.

2023-12-11 Mon: researched Aaron's [docs](https://github.com/harmony-one/x/pull/342/files) on X (twitter) API, prepared for the call with Sun. [Added](https://github.com/harmony-one/x-payments-backend/commit/0957b6373d7052d2f11c16769703889e8b1fa28f) new endpoint `GET /users` to X app backend.

---

2023-12-08 Fri: [Added](https://github.com/harmony-one/x-payments-backend/pull/8) blockchain address associated with appleId in Payments backend, added DB migration. [Fixed](https://github.com/harmony-one/x/pull/333) exporting logs to Notes app, changed logs order.

2023-12-07 Thu: completed logs refactoring: added custom logger to ActionHandler, RelayAuth, AppleSignInManager, TextToSpeechConverter, and more classes. Added formatted timestamp to logs export. [PR#309](https://github.com/harmony-one/x/pull/319) is merged into main branch.

2023-12-06 Wed: working on exporting logs: implemented custom logs system, added export, started refactoring current logs to a new logger. Updated ActionsView, SettingsView, SpeechRecognition classes, working on the rest app. PR [#309](https://github.com/harmony-one/x/pull/319).

2023-12-05 Tue: [added](https://github.com/harmony-one/x/commit/bf0e2df0821493b9ffd543404846f8a67c350023) app version alert: if the app version is lower than the version from the App Store, the user will see a notification prompting to update the app.

2023-12-04 Mon: [added](https://github.com/harmony-one/x/pull/301) user appVersion field in iOS app; update appVersion on app init

---

2023-12-01 Fri: [added](https://github.com/harmony-one/x/commit/92b91981e0981a10538dc3081be7f2dd28ceca02) new appVersion and isSubscriber fields to user account; tested VoiceAI app. [Updated](https://github.com/harmony-one/x-payments-backend/commit/36de1a1a13f15f455365712d443ddd5c8523fce7) Payments api typings.

2023-11-30 Thu: [added](https://github.com/harmony-one/x-payments-backend/commit/5cb2a46900171b8fd05c2c833ffd4f1416a7982c) appVersion to user account in VoiceAI payments service, implemented new endpoint `/users/update`.

2023-11-29 Wed: Updated [backend](https://x-payments-api.fly.dev/api) to support production in-App Purchase handling; [launched](https://x-payments-api-sandbox.fly.dev/api) second backend instance to support sandbox in-App purchases for TestFlight build. Working on adding app version control in user account on backend side (request from Nagesh).

2023-11-28 Tue: started working on SettingsView unit tests, [PR#281](https://github.com/harmony-one/x/pull/281/files)

2023-11-27 Mon: [Updated](https://github.com/harmony-one/x/pull/271) user properties, added `isSubscriptionActive` field from Payments backend response to check is user subscribed, updated user API test.

---

2023-11-24 Fri: Fixed test in [PR#247](https://github.com/harmony-one/x/pull/247), merged. [Refactored](https://github.com/harmony-one/x/pull/266) repeatButton type, refactored Action button tests, improved SettingsView test.

2023-11-23 Thu: [measured](https://github.com/harmony-one/x/pull/252) relayer first response latency, average value is around 1.2 seconds until first response. [Added](https://github.com/harmony-one/stripe-payments-backend/commit/60778134b93620f52bbd8bba103917974f410d76) isSubscriptionActive field to user account in Payment service.

2023-11-22 Wed: [added](https://github.com/harmony-one/x/pull/247) UI test for Settings modal, fixed actions buttons test; working on relay service latency measurements.

2023-11-21 Tue: worked on Settings modal: fixed black overlay issue, fixed close settings handler, updated link to a new "Voice AI: Super-Intelligence" app in Share button, added Tweet. Pushed al changes into `dev_1.1120.9` branch, PR [#225](https://github.com/harmony-one/x/pull/225).

2023-11-20 Mon: [helped](https://github.com/harmony-one/explorer-v2-frontend/pull/283) Aaron to track Explorer visits for specific address pages, configured Google Tag Manager and Fingerprint.com. [Implemented](https://github.com/harmony-one/x/pull/221) Settings modal with 3 buttons in VoiceAI, created PR.

---

2023-11-17 Fri: [updated](https://github.com/harmony-one/stripe-payments-backend/commit/58b217da44a6c5ee41d64a70cc81cf4878f2dd1c) productId to "com.country.x.purchase.3day", [refactored API](https://github.com/harmony-one/stripe-payments-backend/commit/ffa4b5c40139bc35db1600bcd3581471e1043ea2), deployed [update](https://x-payments-api.fly.dev/api).

2023-11-16 Thu: [added](https://github.com/harmony-one/stripe-payments-backend/commit/0084a613108cffd0aa1cea855ed81e022fd82585) a new field to user account: expirationDate; this field is updated when a 3-day subscription is purchased and is used to determine if the user currently has a subscription. [Added](https://github.com/harmony-one/stripe-payments-backend/commit/3bc72662f19c925d350422ef3291e0dca0f2afa0) new endpoint for deleting user account (required API_KEY to use), renamed /withdraw to /spend, improved logs.

2023-11-15 Wed: [check](https://github.com/harmony-one/stripe-payments-backend/commit/31b71c5ad4fd0a6d09a1b33fd62d0eda05c91b8d) uniqueness of transactionId identifier, add API key guard for /purchases and /spend endpoints, added production App Store enviroment support, improved logging

2023-11-14 Tue: [added](https://github.com/harmony-one/stripe-payments-backend/commit/39d28353696a0fb8c59a786fdeed70edfc1970d9) new product support on Payments service side; now the amount of credits purchased by a user is calculated based on productId. [Deployed](https://x-payments-api.fly.dev/api) payments service update to integrate it with VoiceAI app. Working on authorization guard for /users/withdraw endpoint.

2023-11-13 Mon: [added](https://github.com/harmony-one/stripe-payments-backend/commit/0d85b4c137a707168837cc690630998c1d211f67) tokensAmount param to /withdraw endpoint; credits amount to withdraw will be calculated on Payments backend side based on tokensAmount and configuration params. Added `withdrawals` database table to store all withdraw requests and user credits balance data (before and after transaction).

---

2023-11-10 Fri: [added](https://github.com/harmony-one/stripe-payments-backend/pull/6/commits/c530d2ffb2156301afbb8fef815e6797259bb47f) integration with AppStore API to get payment transaction (and credits amount by productId) by transactionId from iOS app. Added purchases database table with list of all in-app purchases. [Implemented](https://github.com/harmony-one/stripe-payments-backend/pull/6/commits/7f099cb5eec711233bab97fa63b7a3066c5fb628) endpoint to get all user purchases. [Deployed](https://x-payments-api.fly.dev/api#/) Payments service with latest updates.

2023-11-09 Thu: [added](https://github.com/harmony-one/stripe-payments-backend/pull/6/commits/568088f801558bc5d558439eda205b8a762e12d3) authorization guard in Payments backend, [implemented](https://github.com/harmony-one/stripe-payments-backend/pull/6/commits/dfb73ec94f2d765bef0c31e43c8d0b2cc0bf47e0) new method to get transactionId after successful purchase and [linking](https://github.com/harmony-one/stripe-payments-backend/pull/6/commits/53aa54eef40e26e171363ab991fe184c92c8b601) appleId to existed account after SignIn. [Updated](https://x-payments-api.fly.dev/api) Payments service.

2023-11-08 Wed: [added](https://github.com/harmony-one/stripe-payments-backend/pull/6/commits/011bb24f59b46c88a58866b4fc6832f373f8537d) new endpoints to Payments service after conversation with Nagesh and Theo F: create user, get user balance, pay (only for test purposes) and withdraw. Deployed [Payments service](https://x-payments-api.fly.dev/api), shared all information with Nagesh and Theo. Continue working on JWT guard on Payments service side.


2023-11-07 Tue: [implemented](https://github.com/harmony-one/stripe-payments-backend/pull/6/commits) endpoints on Payments backend side to create a new user, associated with AppleId, drafted architecture and payments flow, discussed details with Nagesh and Theo F (free credits, tokens refill, JWT authorization). Started working on JWT authorization on payments backend side.

2023-11-06 Mon: switched VoiceAI to Simple Rules, added synced Products list, published new version in TestFlight ([PR #121](https://github.com/harmony-one/x/commit/bbad4869b9e1cd67fa60c2c21f17eb2caaf58884)). Now in-app purchases working in TestFlight build! Started implementing logging for TestFlight build, we will need logs to get originalTransactionId and listen for transaction history in payments backend (limitation from AppStore API).

---

2023-11-03 Fri: started working on in-app purchase tracking: researched AppStore API basic methods, transactions structure, [created](https://github.com/harmony-one/stripe-payments-backend/pull/6) test module in X backend to listen user transactions. We need activated Paid Apps in Simple Rules account because it's impossible to track in-app transactions with XCode build (missing real transactionId).

2023-11-02 Thu: [Added](https://github.com/harmony-one/x/pull/115) in-app purchase to VoiceAI bot (hold "skip" button for 2 second to purchase 500 "credits"). Works only for local build for now. Investigated how to enable in-app purchases on TestFlight, we need to move VoiceAI to Simple Rules and activate Paid Apps (currently [in pending](https://appstoreconnect.apple.com/agreements/#/) status).

2023-11-01 Wed: [implemented](https://github.com/harmony-one/x/pull/100) in-apps purchase demo with products and subscriptions, using native iOS StoreKit. After publishing in TestFlight I noticed that products list is empty and asked Nagesh to help me with that. It will require some time to setup a new application in a different org with enabled paid apps so in-app purchases will work in TestFlight (not only locally).

2023-10-31 Tue: [Completed](https://github.com/harmony-one/stripe-payments-backend/pull/5) basic methods for X payments service: it support creating new users, refund and widthdraw funds. [Deployed](https://x-payments-api.fly.dev/api#/users) service to fly.io, asked Aaron to review it and discuss the next steps. Continue research Apple [Storekit](https://developer.apple.com/storekit/) to implement payments in iOS app.

2023-10-30 Mon: [implemented](https://github.com/harmony-one/x/commit/f748d5ea3e8779de8fb07d7b187b6126404f0d4a) simple unit test for Payment module in Hey Artem, checking how to implement UI tests. Continue working on payments service DB schema, need to discuss details with Aaron.

---

2023-10-27 Fri: Worked on X iOS app and Payments service. [Added](https://github.com/harmony-one/x/pull/78/commits/9d5dd1a41eef45db3f394d01529a809e1b8574f9) Stripe payments widget to iOS app in ios-artem folder, made the first test payment with credit card using payment service, launched locally. [Implemented](https://github.com/harmony-one/stripe-payments-backend/pull/5/commits/0a4a0b8025f1fdc5daa8248f5a0efeaba77bcb2a) Stripe payment request endpoint in payments service. Started working on handling successful and failed payments from iOS app on the payments service side.

2023-10-26 Thu: Reviewed Aaron's [PR](https://github.com/harmony-one/x/pull/63) with PlayHT support, added it to Hey Artem app. Started reviewing [PR](https://github.com/harmony-one/x/pull/61) with iOS stream. X app payments: [implemented](https://github.com/ArtemKolodko/stripe-payments-backend/pull/6) user balance on payments backend side, added initial credits, implemented Stripe payment intent for X app. Researching Stripe docs with iOS integration.

2023-10-25 Wed: Started working on payments for X app: refactoring DB schema in [stripe-payments-backend](https://github.com/harmony-one/stripe-payments-backend) to support free credits, adding new Stripe payment intent event handler to support Apple Pay.

2023-10-24 Tue: Completed local environment setup for ios-anne. Had s call with Sergey to split the tasks and discuss common pitfalls while working on ios projects. Started setting up com.country.x.artem as a separate project (work in progress).

2023-10-23 Mon: [Implemented](https://github.com/harmony-one/x/pull/55) Google Text-to-Speech using Google API, without a proxy server (this can be used in iOS app). Synced with devs regarding new iOS tasks. Started iOS environment setup. 

2023-10-20 Fri: [Added](https://github.com/harmony-one/x/pull/45) url params for speech and text models, fixed sound interruption: the complete sentence will now be sent to google text-to-speech API. Explored latency issue, it's caused by proxy service and google API latency. Checking for a solution to use Google text-to-speech directly from client app. As another option we can switch to PlayHT.

2023-10-19 Thu: [Added](https://github.com/harmony-one/x/pull/42) TTS drop-down menu to webapp demo with two options: Google / Elevenlabs. Refactored audio tts plugin. Started working on reducing latency (WIP).

2023-10-18 Wed: [Fixed](https://github.com/harmony-one/x/commit/21ebe56a8f813957c2906deb23fbb4faec248682) GPT4 message queue bug; implemented GPT4 stream interruption on a new message from user. Deployed update on https://artem.x.country/.

2023-10-17 Tue: Fixed [issue](https://www.notion.so/harmonyone/No-Audio-Emit-on-Artem-x-country-f9d2ac489e004dc4b9d37b698f5b759f?pvs=4) with audio emitting. Deployed webapp demo on netlify: https://harmony-x.netlify.app, Theo linked it to artem.x.country; deleted fly.io deploy.

2023-10-16 Mon: Added STT model selector to test different models: Deepgram Nova 2 and Deepgram ConversationalAI. [Added](https://github.com/harmony-one/x/pull/25) previous messages to GPT4 request to keep the conversation context.

---

2023-10-13 Fri: [Added](https://github.com/harmony-one/x/commit/d91d171430ffa976d71677b27da95cf1a6d7719e) full Deepgram Nova 2 support in speech-to-text module; [improved](https://github.com/harmony-one/x/commit/dccc64b51dbefd5fef8072bf40839387f2ad575d) interaction with GPT4: speech-to-text module collects chunks of a text and sends them to gpt4 after a delay of 1.5 seconds.

2023-10-12 Thu: Deepgram Nova 2: researched official [docs](https://developers.deepgram.com/docs/getting-started-with-live-streaming-audio), tested Nova 2 with stream support with a test script. Created simple relayer service to keep secrets on backend, [working](https://github.com/harmony-one/x/pull/13) on the X webapp integration with Nova 2 API.

2023-10-11 Wed: [Implemented](https://github.com/harmony-one/x/pull/9/files) sending an STT result to GPT4 by user command. Improved STT chunks parsing and overall UX.

2023-10-10 Tue: Picovoice STT doesn't work very well with text recognition. Checked other models: Speechmatics, Google, RevAI, [added](https://github.com/harmony-one/x/pull/3) Speechmatics streaming STT and started testing.

2023-10-09 Mon: [Worked](https://github.com/harmony-one/x/commit/a4fd48bbb15be869618a14c02d6f909f3c89d314) on improving X app UI. [Added](https://github.com/harmony-one/x/commit/8977ce4739d34df8fecf1a8d956654786a7023c5) start-stop STT.

