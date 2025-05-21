2025-05-21 Wed: [completed](https://github.com/harmony-one/shadow-scraper/tree/main/src/portfolio-tracker/vfat) vfat btc* script, started testing the resulst on CL1-WBTC/scBTC and CL1-scBTC/LBTC positions. Checking Silo vaults structure and subgraphs to add btc* vaults.

2025-05-20 Tue: [implemented](https://github.com/harmony-one/shadow-scraper/blob/main/src/portfolio-tracker/vfat/index.ts) basic vfat btc* position performance: deposited amount, unclaimed rewards and APR. Started adding calculation of claimed rewards amount, it's important for vfat due to active auto-rebalancing of positions.

2025-05-19 Mon: completed initial reseach on Lombard binance BTC staking, shared in group. Started working on script to calculate APR for VFAT btc* positions,

---

2025-05-18 Sun (2.0h): continue research on Lombard finance: looked at documentation, underlying [Babylon](https://btcstaking.babylonlabs.io/) BTC yield, LBTC token and [Veda](https://app.veda.tech/points) points program.

2025-05-16 Fri: [reviewed](https://github.com/harmony-one/shadow-scraper/pull/15) and tested locally Rika's PR with Pendle stats. Checked Spectra btc* vault, unable to deposit funds due to some internal error on contracts side (non-btc vaults are working fine). Started researching [lombard](https://www.lombard.finance/sonic/) vaults on Sonic.

2025-05-15 Thu: completed analysis for all SwapX btc* vaults (USDC.e/scBTC, WBTC/scBTC, wS/scBTC). [Improved](https://github.com/harmony-one/portfolio-tracker/commit/7b9dac59ce63c22b2405c34837b6979bceb5b46f) portfolio tracker chart and snapshots data, fixed metrics.

2025-05-14 Wed: [completed](https://github.com/harmony-one/shadow-scraper/commit/3995ca67e4e6fba3738595d6279ffd8915bb1421) script for SwapX USDC/scBTC, the result is 12.1200%; continue on other SwapX btc* vaults. Reviewed and merged pull requests from Frank and Rika with [Beefy WBTC pools](https://github.com/harmony-one/shadow-scraper/pull/13) and [Shadow WBTC](https://github.com/harmony-one/shadow-scraper/pull/14).

2025-05-13 Tue: started BTC vaults analysis, invested into swapx, shadow and beefy vaults. Prepared export in TSV with transactions history. Calculated Merkl rewards APR (in wS tokens) for the positions in MEV USDC and Re7.

2025-05-12 Mon: reviewed Pendle LP script [PR](https://github.com/harmony-one/shadow-scraper/pull/8) from Rika. [Added](https://github.com/harmony-one/portfolio-tracker/commit/5f1c4fb7b3e4b9108c48b89259d556639ad89ac0) Merkl rewards and export to TSV from the last snapshot in the portfolio tracker.

---

2025-05-11 Sun (4.0h): reviewed and tested Euler Re7 vault [PR](https://github.com/harmony-one/shadow-scraper/pull/9) frpm Frank, merged. Portfolio metrics: [added](https://github.com/harmony-one/portfolio-tracker/commit/447dc0efabcfa32fc616c2be65988627fd4d1ad7) support of Euler Re7 vault, [added](https://github.com/harmony-one/portfolio-tracker/commit/b5d95313852ec83b941e0d80e49f9cddd24b4ef7) full portfolio into into snapshot, updated the app.

2025-05-09 Fri: portfolio metrics: added Magpie vault stats, updated the app. Testing portfolio apr scripts, found that Re7 vault not supported, synced with Frank to work on this.

2025-05-08 Thu: portfolio metrics: [prepared](https://github.com/harmony-one/portfolio-tracker/blob/main/api/src/app.service.ts) cron job for Euler, Beefy and Pendle PT data for selected wallet, added performance chart, CAGR and Volatility metric in client.

2025-05-07 Wed: portfolio metrics: [merged](https://github.com/harmony-one/portfolio-tracker/commit/6d8982aadfd6112e84bfb0f995305b230257bbbb) beefy stats and [completed](https://portfolio-tracker-api.fly.dev/portfolioSnapshots?limit=1000&offset=0) first version of backend with cron job to save stats daily. Finalizing calculations of CAGR and MWRR metrics based on portfolio value. [Reviewed](https://github.com/harmony-one/shadow-scraper/pull/6) Frank's PR with Beefy vault stats.

2025-05-06 Tue: tested [DebankChecker](https://github.com/ilyx-dev/DebankChecker/tree/main) script for Debank data, portfolio data is available (script require some configuration with proxy address). Started working on advanced portfolio metrics: CAGR and MWRR.

2025-05-05 Mon: [finished](https://github.com/harmony-one/shadow-scraper/commits/main/) collateral exposure history script and export; found [Merkle rewards page](https://app.merkl.xyz/opportunities/sonic/EULER/0x196F3C7443E940911EE2Bb88e019Fd71400349D9) for MEV USDC.e vault ends May 13; helping Rika with Debank data: checked official API - too expensive, found [workaround](https://github.com/ilyx-dev/DebankChecker/tree/main), started testing.

---

2025-05-04 Sun (3.0h): researched details about MEV Capital Sonic [USDC.e](https://app.euler.finance/vault/0x196F3C7443E940911EE2Bb88e019Fd71400349D9?network=sonic) and prepared [script](https://github.com/harmony-one/shadow-scraper/blob/main/src/portfolio-tracker/euler/history-collateral.ts) to extract total supply (assets, deposited by suppliers) and borrows amount to calculate value utilization over the last 30 days, [export file](https://github.com/harmony-one/shadow-scraper/blob/main/docs/EulerCollateralHistory.md). Checking how to get collateral amounts and ratios (LTV, LLTV) for USDC.e.

2025-05-02 Fri: day-off

2025-05-01 Thu: day-off

2025-04-30 Wed: day-off

2025-04-29 Tue: analysed vaults past gains, prepared full [report](https://github.com/harmony-one/shadow-scraper/blob/main/docs/vaults-performance.md). Sent vaults allocation suggestion to Li. Reviewed recent fixes in Equilibria [pull request](https://github.com/harmony-one/shadow-scraper/pull/5).

2025-04-28 Mon: reviewed Frank's [pull request](https://github.com/harmony-one/shadow-scraper/pull/5) with Equilibria script. Researching [beefy frxUSD-​scUSD](https://app.beefy.com/vault/swapx-ichi-frxusd-scusd) vault to calculate APR. Started drafting 30-days apr estimation for all vaults in our list.

---

2025-04-26 Sat (4.0h): created [script](https://github.com/harmony-one/shadow-scraper/blob/main/src/portfolio-tracker/euler/history.ts) to export historical lending APR for Euler vaults. [Exported](https://github.com/harmony-one/shadow-scraper/blob/main/docs/Euler-USDC.e-apr.md) lending APR for MEV Capital Sonic Cluster USDC.e and Re7 Labs Cluster USDC.e vaults for the last 30 days.

2025-04-25 Fri: [completed](https://portfolio-tracker-api.fly.dev/portfolioSnapshots) simple backend app with cron job to export wallet portfolio on daily basis. Synced with Frank and Rika on Penpie and Equilibria progress. The goal is to complete first version of script next week and compare performance with underlying Pendle LP.

2025-04-24 Thu: looked at [delta neutral strategy](https://yielddev.io/deep-delta-neutral-fixed-pt-yield-on-sonic-with-euler) for wS pool on Euler. [Started](https://github.com/harmony-one/shadow-scraper/commit/d5e1f1b92972eee93e09efb6913fc863820092d7) working on portfolio client with data updated by cron job for specific wallet to track wallet performance over time.

2025-04-23 Wed: prepared reports on [Beefy frxUSD-​scUSD](https://app.beefy.com/vault/swapx-ichi-frxusd-scusd) and [MEV USDC.e](https://app.euler.finance/vault/0x196F3C7443E940911EE2Bb88e019Fd71400349D9?network=sonic), estimated impermanent loss risks for both pools, sent reports to Li. Sync with team.

2025-04-22 Tue: research on Pendle + [Equilibria](https://equilibria.fi/stake) aUSDC pool and [Beefy](https://beets.fi/pools/sonic/v3/0x43026d483f42fb35efe03c20b251142d022783f2) USDC.e/scUSD, sent both reports to Li. Started comparing Equilibria vs Penpie pools. Both pools rewards based on StandardizedYield (SY), asked Frank and Rika to start looked for details about SY on Equilibria and Penpie and then calculate SY rewards apr. Verified Rika's formula for calculating Spectra LP Fees, everything is correct; finalizing some details to add this rewards to our portfolio script.

2025-04-21 Mon: [included](https://github.com/harmony-one/shadow-scraper/commit/c275f9662955cd8cd7993528378c53afddfb2525) Spectra apr into common portfolio script, [merged](https://github.com/harmony-one/shadow-scraper/blob/main/export/portfolio_export.tsv) all stats together into one table, synced with Rika and Frank and prepared new tasks, synced with Li on top candidates for stable pool, discussed next steps.

---

2025-04-20 Sun (1.0h): looked at Sonic scUSD internal structure, core features and potential risks. Checked Pendle PT aUSDC, updated top candidates for stable pool.

2025-04-18 Fri: reviewed and merged Rika's [pull request](https://github.com/harmony-one/shadow-scraper/pull/3) with Spectra apr calculation; the last part of Spectra rewards is the LP fee. Checked Euler script, [added](https://github.com/harmony-one/shadow-scraper/commit/224f87b78538f1b6dcfdd6ca3a2b355548f5b8c1) additional Merkle rewards. [USDC.e Euler vault](https://app.euler.finance/vault/0x196F3C7443E940911EE2Bb88e019Fd71400349D9?network=sonic) APR from script = 4.24%, Euler client = 6.80%.

2025-04-17 Thu: found a way to calculate PT rate on Spectra, using pt price and time to maturity, results similar to the values in Spectra app. Researching [Euler](https://app.euler.finance/positions/0x3D9e5462A940684073EED7e4a13d19AE0Dcd13bc/0xeEb1DC1Ca7ffC5b54aD1cc4c1088Db4E5657Cb6c?network=sonic&tab=multiply) leveraged positions performance. Opened position in [PT-wstkscUSD-29MAY2025](https://app.euler.finance/vault/0xF6E2ddf7a149C171E591C8d58449e371E6dc7570?network=sonic), checking on how to verify displayed rate.


2025-04-16 Wed: [reviewed](https://github.com/harmony-one/shadow-scraper/pull/3#pullrequestreview-2772671910) PR from Rika with Euler LP fees and PT rate script, tested it locally. Sent new tasks for Rika and Frank to complete Aave and Euler research in the next few days. Started researching leveraged position on Euler, opened new position with modest leverage (5x). Synced with Li on current best vaults, started working on the final list.

2025-04-15 Tue: [created](https://github.com/harmony-one/shadow-scraper/commit/a5746ab92e96ea4cc9cf7fa96e6803da4d644eea) script to calculate Spectra Yield Token (YT) rewards and deposits based on on-chain data and Spectra API. This data will be merged with Spectra LP rewards script when it's ready. Synced with the team, defined next tasks about exporting data to tsv.

2025-04-14 Mon: started researching [Spectra](https://app.spectra.finance/pools/sonic:0x167b0951c5d3fb8ff5ab675401e369dd65817801) pool, deposited tokens, calculated Yield token (YT) rewards based on data from the contract: value fully matched with YT rewards in the UI. Synced with Frank and Rika on tasks for this week.

---

2025-04-13 Sun (2.0h): [drafted](https://github.com/harmony-one/shadow-scraper/commit/0585a5b8d56973f91f446f2ddddeda6c4c421706) apr calculation for the entire Euler usdc.e vault for the past x days. Reviewed Rika's report with Euler additional rewards apr, break down the next week tasks in our team with Rika and Frank.

2025-04-12 Sat (2.0h): researching apr calculation over the last X days for the entire Euler usdc.e vault. Monitored vfat usdc.e/scusd position with auto-rebalancing, still in the initial range.

2025-04-11 Fri: [completed](https://github.com/harmony-one/shadow-scraper/commit/85a2953d1bb511fc1b2ccd0a5d703e38ff964cb6) Euler usdc.e vault apr history over the past [x] days for specific wallet. APR calculated for the value at 11:59pm. Results for my wallet varies around 3.05%. Next tasks for Rika and Frank. Details about Pendle PT from Philipp, shared with other devs.

2025-04-10 Thu: started working on Euler apr over the last x days, tested solution with archival node calls to get contract state for each day, started working on implementation. Monitored vfat USDC.e/scUSD position with 0.05% width and enabled auto-reblancing, buffer + cutoff. Sync with Frank and Rika, split the tasks for the devs.

2025-04-09 Wed: [completed](https://github.com/harmony-one/shadow-scraper/commit/05ae63bbd39f21560fc6149bcf8c276af6c24f52) Euler apr calculation for base rewards, my result is 3.1% which is not too far from the dashboard value (3.4%). Defined steps to complete research for all vaults from /farms: Pendle and Aave. Researching how to calculate historical apr over the past x days for Euler vault.

2025-04-08 Tue: completed research and testing of advanced vfat auto-rebalancing feautures that may be helpful for optimizing impermanent loss: buffer and cutoff, shared report with Stephen and Aaron. Started working on Euler portfolio, [implemented](https://github.com/harmony-one/shadow-scraper/commit/15d174a9222ed568d961a0b568bcec88647a1df1) current amount of tokens locked in the pool, started working on total deposited amount to calculate APR.

2025-04-07 Mon: [added](https://github.com/harmony-one/shadow-scraper/commit/16de94a6e9928444d66b9d3367fce293094dfa97) Silo Finance scUSD position stats in portfolio script, APR=4.69% (good performance for stable coin pool). [Exported](https://github.com/harmony-one/shadow-scraper/blob/main/export/portfolio_0x4E430992Db6F3BdDbC6A50d1513845f087E9af4A_1744043032.tsv) Silo position info.

---

2025-04-06 Sun (2.0h): tested vfat auto-rebalancing on volatile wS/USDC.e pool, monitored pool stats, adjusted position width and deposited amount to meet the requirements from vfat [docs](https://docs.vfat.io/automation/rebalance/).

2025-04-05 Sat (1.0h): looking at vfat vaults paramaters + auto-rebalance, deposited funds into [CL5-USDC.e/scUSD](https://vfat.io/farm?chainId=146&farmAddress=0xf8440c989c72751c3a36419e61b6f62dfeb7630e&poolId=0) and [CL50-wS/USDC.e](https://vfat.io/farm?chainId=146&farmAddress=0xe879d0e44e6873cf4ab71686055a4f6817685f02&poolId=0) with narrow ranges, enabled auto-rebalancing with 3% max slippage to check how auto-rebalancing works without restraints. Monitoring vault stats.

2025-04-04 Fri: started researching vfat auto-rebalancing for [USDC.e/scUSD](https://vfat.io/farm?chainId=146&farmAddress=0xf8440c989c72751c3a36419e61b6f62dfeb7630e&poolId=0) vault to compare with other volatility models. Checked vfat and underlying shadow pool contracts, [collected](https://github.com/harmony-one/shadow-scraper/commit/f780cff6e9d49c77dd13aca183487d7876df9af5) methods to track position ticks range and current tick in the pool.

2025-04-03 Thu: [completed](https://github.com/harmony-one/shadow-scraper/commit/30323f03fdff135c5ee99b15a30da48ce8af1811) magpie pendle portfolio [export](https://github.com/harmony-one/shadow-scraper/blob/main/export/portfolio_0x881E625E5C30973b47ceE3a0f3Ef456012F13f7D_1743673030.tsv) (#5 in /farms): base apr is around 3% for aUSDC pool, this number correlates with base reward from the dashboard. Additional rewards, such as SY, wasn't found in reward contracts, continue researching. Started looking at the rest pools from /farms: euler (#2), silo (#3), beefy (#7).

2025-04-02 Wed: [added](https://github.com/harmony-one/shadow-scraper/commit/2e98c1daf071255ec8b19dc9e988a9f6a77c9a39) address transactions history to portfolio [export](https://github.com/harmony-one/shadow-scraper/blob/main/export/portfolio_0x881E625E5C30973b47ceE3a0f3Ef456012F13f7D_1743604632.tsv); data is fetched from Sonicscan API, wallet balance is calculated in USD and S at the time of each transaction.

2025-04-01 Tue: completed manual research of [magpie usdc](https://www.pendle.magpiexyz.io/stake/0x3F5EA53d1160177445B1898afbB16da111182418) pool and calculation of pending rewards based on data from smart contracts, results fully matched with magpie dashboard; started implementation in portfolio script.

---

2025 Q1 Review

In Q1 2025, I focused on advancing DeFi analytics. I started portfolio performance tracking across Sonic-based DeFi protocols like Silo, Shadow, and Aave, depositing funds and looking for APIs for data aggregation. I completed research on ALM (Automated Liquidity Management) protocols, identifying Gamma as optimal for dynamic volatility strategies, and shared findings with Stephen and Li. Created Shadow Exchange scraper, a set of scripts to export pool's deposits and withdrawals events from the Shadow Subgrarph to CSV, and developed scripts for TVL and APY analysis of Beefy and vfat pools. Additionally, I contributed to Pump.ONE’s client and backend updates, improving competition features and launching production services. I also started researching UniswapX, resolved deployment issues with Aaron's help, and started testing contract deployments on Harmony. My work focused on analyzing DeFi liquidity pools, validating the data, and working with the team on the analysis results.

---

2025-03-31 Mon: portfolio script: updated formatting of APR and amount fields, added pool label, deposit link, [exported](https://github.com/harmony-one/shadow-scraper/blob/main/export/portfolio_0x4E430992Db6F3BdDbC6A50d1513845f087E9af4A_1743422366.tsv) new version. Started looking at Silo, Pendle and Beefy pools to collect rewards data in portfolio script. Added [article](https://github.com/harmony-one/shadow-scraper/blob/main/docs/uniswap_liquidity_calculation.md) on Uniswap V3 liquidity calculation with step-by-step explanation, that clarify unproportional token amounts in some edge cases. All formulas found on Uniswap V3 [docs](https://uniswapv3book.com/milestone_1/calculating-liquidity.html) page.

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
