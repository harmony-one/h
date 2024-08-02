2024-08-02 Fri: [updated](https://github.com/ArtemKolodko/synthetix/blob/d8eeb652f434add77d8180f768f813c5a5666bf1/v2-harmony-deployment.md) Synthetix V2 deployment instructions with information about oracle feeds. Tested [band-oracle-updater](https://github.com/harmony-one/band-oracle-updater) bot locally. Continue testing [https://sy.country/](https://sy.country/) client. Scheduled call to discuss Synthetix launch with Pablo from ThreeSigma on Monday (Aug 05).

2024-08-01 Thu: created a bot [band-oracle-updater](https://github.com/ArtemKolodko/band-oracle-updater) that trigger [BandOracleReader](https://github.com/ArtemKolodko/band-oracle-reader) contract update. Bot will be used in Synthetix and GMX releases as a part of the oracles system.

2024-07-31 Wed: replaced all Synthetix to SY in the client; added Harmony logo to the network select. Deployed client update: [https://sy.country/](https://sy.country/).

2024-07-30 Tue: [updated](https://github.com/ArtemKolodko/synthetix/blob/0d9262e1af01a9fb0cecd6ab6ae836209006d5be/v2-harmony-deployment.md) complete guide how to deploy Synthetix on Harmony and run client. Helped Aaron with DNS records for sy.country domain. Testing Synthetix [client](https://harmony-synthetix.netlify.app/).

2024-07-29 Mon: [fixed](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/a5d1c2957538ec2a4fbc3ad75de25e6b139879e0) Burn transaction call in Synthetix client; fixed Explorer links, deployed client update: [https://harmony-synthetix.netlify.app](https://harmony-synthetix.netlify.app/). Checking Synthetix [litepaper](https://developer.synthetix.io/litepaper/).

---

2024-07-26 Fri: created new Synthetix deployment on Harmony with increased SNX supply (100 mil tokens) for testing purposes, updated contract addresses in client, deployed [client](https://harmony-synthetix.netlify.app/) update. Had a great progress, because finally I was able to borrow sUSD token for SNX. The only missing thing is oracles data for SNX token: it's not available in BAND oracles. currently I'm using BTC price for testing.

2024-07-25 Thu: investigated and [fixed](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/36369d88664f857eaf3442dbbccee14c55d6c79a) error in Mint operation in Synthetix client. Deployed client update: [https://harmony-synthetix.netlify.app](https://harmony-synthetix.netlify.app). Working on new contracts deployment with increased SNX supply.

2024-07-24 Wed: Synthetix deployment process on Harmony with updated scripts and docs. Discussed creation of SNX-like token with Aaron, we need to have similar token with real price to use it in client. Working on adding token supply in deployment scripts to have some SNX on balance to test.

2024-07-23 Tue: working on different bugs in Synthetix client: "current network does not support EIP-1559" on minting attempt and minting initial [SNX token](https://explorer.harmony.one/address/one1gj68vrrcdnkklcv2240lu7uann27u9dghsuk2l) supply to use in staking. Deployed BandOracleReader [contract](https://explorer.harmony.one/address/one1dj60qgw3v0fcwehfq56tyxn3kgy9kcdg25nfuy?tab=txs&shard=0) with ONE token price.

2024-07-22 Mon: Aaron fixed a bug in BandOracle proxy, and I updated Harmony  Synthetix deployment. Price quote on Mint page is working now!  Deployed client update: [https://harmony-synthetix.netlify.app/staking/mint](https://harmony-synthetix.netlify.app/staking/mint). To test price estimate, select Harmony in the top right network selector, connect wallet and type something in stake or borrow inputs on Mint page, quotes will be fetched from the contract. Currently it's using only Bitcoin price, later I'll update the feeds accordingly to the actual token (ETH, SNX, BTC).

---

2024-07-19 Fri: got an error while adding custom oracles aggregator to ExchangeRates contract. While debugging the problem, [created](https://github.com/ArtemKolodko/synthetix/pull/2/commits/e0d4bdaf371e935e66ba01245aab0a5402da9033) a script to test previously deployed BandOracleReader contract, and found a bug in BandOracleReader contract: latestRound method return error, which maybe caused the original error. Sent all information to Aaron (he is an author of BandOracleReader contract).
 
2024-07-18 Thu: deployed BandOracleReader with BTC and ETH currencies; [re-runned](https://github.com/ArtemKolodko/synthetix/pull/2/commits/e251ec352ac6050b856f51c5f6efd3e36b82ddba) harmony deploy with new aggregator addresses, started testing

2024-07-17 Wed: reviewed Aaron's [PR](https://github.com/ArtemKolodko/synthetix/pull/3), started integration of Band oracles with Synthetix deployment script

2024-07-16 Tue: sick time-off

2024-07-15 Mon: fixes in Synthetix v2 client: [included](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/bff8c0d148f37cdd3c74b92bf27caf27abb723ec) Reward contract, [disabled](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/418f6ed32098a49acea2f02ff2f16623e45a55af) some optional features. Debugging error in Mint quote: "No aggregator for asset".

---

2024-07-12 Fri: [Fixed](https://github.com/ArtemKolodko/synthetix-js-monorepo/pull/1/commits/3647a79e508dd72904e49b4085b477b7ceb0f5d1) runtime errors, related to contract imports and number conversions, deployed synthetix client to [https://harmony-synthetix.netlify.app/](https://harmony-synthetix.netlify.app/). Minting is not working right now, need prepare new contracts with no mocks and real oracles support.

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

