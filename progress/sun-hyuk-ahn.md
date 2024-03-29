**2-week Deliverables**

Deploy a rollup on shard 1 that utilizes Celestia for data availability. Specifically, need to change the existing Rollkit SDK so that 1) interaction with Celestia for data avilability occurs, 2) settlement happens in Harmony Shard 1, and 3) deploy smart contract (and necessary features) in order to handle settlement.

---
2023-03-22 Fri:

2023-03-21 Thu: Continued implementation for the wrapper. Discussed with Diego regarding the metrics. We realized that throughput for Shard 1 is near 0 currently. In order to get the precise metrics, we need to create a tool to traverse throughout all the nodes. Attended Nvidia GTC after meetup. Diego would be working on the costs.

2023-03-20 Wed: Began implementing wrapper for Harmony nodes to be used for Rollkit. Divided the task with Yuriy so that Yuriy would be working on the intial approach of deploying a rollup on Celestia as the data availability layer with Shard 1 as the proof storage and I would work on a rollup with Shard 1 as both data availability layer and proof storage. Attended Nvidia GTC.

2023-03-19 Tue: Discussed with Stephen that we want a sovereign one instead. Began looking at Polaris implementation for Rollkit, which allows for EVM execution environment with Cosmos based chains and rollups. Realized that we would need a wrapper around our Harmony nodes, in order for it to work as a data availability layer.

2023-03-18 Mon: Began deployment for Op Stack rollup. Deployed smart contracts as well as op-geth, the execution engine for the rollup.

---

2023-03-17 Sun: Discussed with Yuriy on possible progression with Op Stack. Began looking at the documents as well as the smart contracts required for deployment.

2023-03-16 Sat: Began looking at smart contract rollups via Op Stack as an alternative. One problem with Rollkit (Cosmos SDK) is that they do not yet have a connection with EVM chains, thus unable to utilize EVMs as data availability layer. 

2023-03-15 Fri: Continued studying Rollkit and Cosmos SDK. Launched rollups on Celestia, without shard 1 interaction. One concern is that there is no EVM chain used as the data availability layer. Also, it seem that Polaris is the only option for enabling EVM execution environment in Cosmos based chains / rollups. Looking into alternatives, possibly Op Stack.

2023-03-14 Thu: Deployed Celestia node on a local network. Will continue tomorrow on learning the Cosmos SDK. Discussed with Ivan and Yuriy in terms of the LayerZero bridge audit.

2023-03-13 Wed: Started exploring Celestia and the Cosmos SDK. Since Rollkit is based on the Cosmos SDK, they offer the required resources for understanding the SDK. 

2024-03-12 Tue: Yuriy and I decided to look into 2 different SDks with Yuriy diving into Sovereign SDK and me into [Rollkit](https://rollkit.dev/). Both support modular, sovereign rollups but they are in different languages, Rust and Golang, respectively. The current solution is for us to fork the SDKs and change the settlement logic so that it occurs through Harmony rather than Celestia. Smart contract on the Harmony level in order to accept the proofs provided from the rollup (and possibly Celestia) will be required. This part will be handled by Yuriy.

2024-03-11 Mon: Yuriy and I decided on [Sovereign SDK](https://github.com/Sovereign-Labs/sovereign-sdk) in order to implement the sovereign rollup on our Shard 1. Started the architecture and technical roadmap, as well as writing up and dividing up tasks to be completed along with Yuriy. Tomorrow morning, we will discuss on the ETAs for the features and provide an initial write up for review.

2024-03-10 Sun (8 hours): Researched into Celestia and rollups, specifically sovereign rollups. Used Sovereign SDK in order to launch a basic rollup on Celestia. This basic rollup handles the data availability and settlement through Celestia. Looked into how we can integrate Harmony's Shard 1. The most viable solution seems to be handling just the settlement in Shard 1.

---

## ETH Denver Update:

The rise of Bitcoin Layer 2 technologies presents an opportunity to harness idle Bitcoin assets for enhancing the security and liquidity of networks like Harmony. By integrating these innovations, we can leverage Bitcoin's robustness and value. Babylon Staking Protocol allows for the mentioned properties.

To integrate the Babylon Staking Protocol with Harmony the following specifications need to be developed: IBC (Inter Blockchain Communication) implementation, Babylon smart contract development, timestamping service integration, and finality gadget implementation. The following outlines a detailed approach for each of these components:

### 1. IBC Implementation for Harmony
- Objective: Enable Harmony to communicate with the Babylon chain and other IBC-enabled blockchains for cross-chain interactions, enhancing interoperability within the Cosmos ecosystem.
- Approach: Adapt Harmony's existing infrastructure to support IBC modules, ensuring compatibility with the Cosmos SDK. This may involve developing custom relayer services or adapting existing ones to facilitate communication between Harmony's EVM architecture and the IBC protocol.
- Challenges: Ensuring compatibility with Harmony's EVM and PoS mechanisms, efficient message passing, and maintaining security during cross-chain communications.

### 2. Babylon Smart Contract Development
- Objective: Develop EVM-compatible smart contracts on Harmony that can interact with the Babylon chain for staking, validation, and other protocol-specific functions.
- Approach: Design and deploy smart contracts that can:
  - Handle staking from users, issuing corresponding tokens or receipts as proof of stake.
  - Interact with IBC relayers to send and receive validation information and finality signatures.
  - Ensure secure and efficient execution of protocol operations within the EVM environment.
- Challenges: Maintaining security in a cross-chain environment, optimizing for gas efficiency, and ensuring the contracts are upgradeable to adapt to future protocol changes.

### 3. Timestamping Service Integration
- Objective: Integrate Harmony with the Babylon chain's Bitcoin timestamping service to enable synchronization with the Bitcoin network.
- Approach: Implement a mechanism within Harmony (possibly through smart contracts or protocol-level integration) that:
  - Requests timestamping from the Babylon chain.
  - Verifies and incorporates the timestamps into Harmony's blockchain to maintain accurate time references.
- Challenges: Ensuring the reliability and security of timestamp data, minimizing latency in timestamp retrieval and verification, and handling the potential for discrepancies between blockchain time and real-world time.

### 4. Finality Gadget Implementation 
- Objective: Implement a finality gadget within Harmony's PoS mechanism that is compatible with the Babylon protocol, enabling validators to sign finality signatures.
- Approach: Develop a component within Harmony's consensus mechanism that:
  - Allows validators to generate and sign finality signatures upon reaching consensus.
  - Communicates these signatures to the Babylon chain via IBC, ensuring they are recorded and acknowledged.
- Challenges: Integrating the finality gadget with Harmony's existing consensus protocol without compromising security or performance, ensuring the finality signatures are recognized and processed efficiently by the Babylon chain.

Note that these are brief layout of the specification after the initial research of the Babylon Staking Protocol. Further research into the development and integration will be done in the coming days with the team to continue with the development.

--- 

2024-02-22 Thu: Completed last minute bug fixes and feature implementation for Eth Denver.

2024-02-21 Wed: Completed all "slash" commands listed [here](https://xn--qv9h.s.country/p/human-protocol-social-shard-1-hcountry).

2024-02-20 Tue: Implemented multi tags to allow hash/?. Fixed bugs related to user manual links.

2024-02-19 Mon: Holiday.

---

2024-02-18 Sun: Worked on setting up shortcuts for quick testing.

2024-02-17 Sat: Restructured the application to fit the restructured data format. Documented the new data structure.

2024-02-16 Fri: Implemented multiple tasks required for the application. Form data structure related to various "actions" within the application.

2024-02-15 Thu: Implemented hash power.

2024-02-14 Wed: Out of office.

2024-02-13 Tue: Out of office.

2024-02-12 Mon: Finalized the h.country merge. Handed off tasks to Julia and Theo to coordinate with Artem and Yuriy. Also, OAuth related tasks to Rika.

---

2024-02-11 Sun: Worked on the h.country merge. 

2024-02-10 Sat: Implemented neo4js in order to find connections between users.

2024-02-09 Fri: Looked into graph database and sorting algorithms for connections. Decided move forward with and implement the graph method. 

2024-02-08 Thu: Initial implementation of Firebase OAuth with 4 providers (Google, Github, Twitter, and Facebook).

2024-02-07 Wed: Migrated to Firebase datastore in order to utilize offline data availability.

2024-02-06 Tue: Implemented KV store data scheme. Implemented workers to interact with the given data. Handed off the rest of taks to Artem and Yuriy.

2024-02-05 Mon: Implemented counter demo utilizing pages, workers, and kv store from Cloudflare.

---

2024-02-04 Sun: Researched into Cloudflare Pages and Workers. Created a simple interaction between pages and workers.

2024-02-03 Sat: Researched into ElastiCache Redis. Configured the initial settings for ElastiCache and implemented Typescript interaction with ElastiCache. (2 hours)

2024-02-02 Fri: Implemented BTC CLI wallet. Discussed new initiative. Benchmarked Redis performance.

2024-02-01 Thu: Fixed q.country lottery endpoints to reflect Telegram entries. Dived into certificate renewals for dotcountry. Attended Sui event and showcased Flip and BTC wallet.

2024-01-31 Wed: Implemented Telegram embeds for 02/01 lottery. Manually implemented cross shard transactions for Flip (had to find a workaround as all the libraries were outdated).

2024-01-30 Tue: Updated 1.country frontend client to host Notion and Substack embed on inscription. Notion is working as expected but have to find a fix for Substack.

2024-01-29 Mon: Launched 01/30 Lottery. Implemented dotcountry redirect logic.

---

2024-01-28 Sun: Coordinated with community members to assit in setting up [Flip](https://github.com/harmony-one/flip). [Updated](https://github.com/harmony-one/s/tree/one-server) Flip code to simplify deployment process (containerization setup & configuration for indexers and db into a single server).

2024-01-27 Sat: Continued working on the lottery.

2024-01-26 Fri: Dotcountry inscription to work with Telegram inscriptions. Started preparing for next week's lottery.

2024-01-25 Thu: Started dotcountry inscription to allow single domain owners to have user access. Assigned tasks to Yuriy and Artem related to dotcountry inscription.

2024-01-24 Wed: q.country configuration and setup. Implemented lottery logic along with Yuriy. Flip configuration for user deployment.

2024-01-23 Tue: Implemented lottery filtering logic for valid Twitter URL.

2024-01-22 Mon: Updated set up so that a single indexer is deployed for each chain (previously, 2 indexers for each service). No need for overlapping indexers.

---
2024-01-21 Sun: Refactor flip backend and frontend code for easier deployment. 

2024-01-20 Sat: Set up configuration for for fly.io.

2024-01-19 Fri: Generalize flip to deploy to chains using ChainConfig class.

2024-01-18 Thu: Deployed usdt.country (Binance USDT / Harmony ONE pair).

2024-01-17 Wed: Generalized indexer and transaction manager class to work with any chains.

2024-01-16 Tue: Create and deploy backup indexer for Onescriptions.

2024-01-15 Mon: Holiday

---

2024-01-12 Fri: Deploy frontend for flip.

2024-01-11 Thu: Updated logic to process transaction synchronously.

2024-01-10 Wed: Updated streaming process of transactions. Implemted rate limit of $1 with remainder DB and logic to later process manual refunds.

2024-01-09 Tue: Updated wallet managing logic. Configured Postgres to store transaction data. Deployed the service on moc.usdc.country.

2024-01-08 Mon: Implemented the priced handling logic. Binance API only provides ONE/USDT pair pricing for now so have set that as a placeholder. Will update the logic to utillize ONE/USDC pair once found.

---

2024-01-05 Fri: Generalized logic and refactored classes for it to be utilized for other pairs.

2024-01-04 Thu: Fixed USDC indexer logic to accurately index ERC20 transactions, fixed Harmony indexer because subscribe is not supported (workaround to fetch transactions every 5 seconds), fixed gas estimation, and added error handling for a robust flow ([PR](https://github.com/harmony-one/s/pull/6)). Will work on price estimation and DB implementaion tomorrow.

2024-01-03 Wed: Fixed up /moe to not use smart contract and bridges. Initial implementation finished with transfer from ONE on Harmony to USDC to Base (vice versa). Will work on implementing the price logic and generalizing the logic to implement for Arbitrum.

2024-01-02 Tue: Implemented usdc.country transaction logic outlined in /moe.

---

2023-12-29 Fri: Out of office

2023-12-28 Thu: Fixed monitor logic for the relayer. Subscribe is not supported for Harmony network, also web3js causes problem in abi decoding with hardhat environment, thus changed the logic to poll transactions every 1 second. The monitor is working as expected now.

2023-12-27 Wed: Initiated development for relayer for signature verification. Also, looking at ways to possibly implement Circle's CCTP to the bridge.

2023-12-26 Tue: Researched over Circle's cross chain transfer protocol. Built simple smart contract utilizing the protocol.

---

2023-12-24 Sun: Testnet testing the bridge transacitons. Working as expected.

2023-12-23 Sat: Generalized bridge logic to be deployed on any chains. Generalized Bridge.sol now can deposit and withdraw tokens. In need of Harmony Testnet tokens in order to deploy and test out transactions.

2023-12-22 Fri: [Developed](https://github.com/harmony-one/s/tree/bridge/s-bridge/bridge) smart contracts to facilitate the transfer of assets from Harmony to Arbitrum (ETA: Arbitrum to Harmony 12/23). [Implemented](https://github.com/harmony-one/s/tree/bridge/s-bridge/bridge) verification logic using signatures authenticated by the relayer, ensuring cross chain validation.

2023-12-21 Thu: Researched into bridge implementation and studied solidity to began smart contract development. Also researched for secure ways to authenticate transactions between different chains, mostly [signature proofs vs merkle tree](https://github.com/harmony-one/s/blob/bridge/s-bridge/bridge/README.md). 

---

2023-12-29 Fri: Write from scratch a minimal bridge to/from arbitrium in 500 lines on command line.

---

2023-12-20 Wed: Deployed mint.i.country.

2023-12-19 Tue: Started development for minting tools and indexer required for the inscription tokens.

2023-12-18 Mon: Research into inscription tokens.

---

2023-12-15 Fri: Replaced random facts with the talk to me logic. Set token limits for the context. Currently, looking at a bug that stops the synthesis for Talk to Me (hand over to Yuriy).

2023-12-14 Thu: [Completed](https://github.com/harmony-one/x/commit/8002e4631c372d5f9520fcc386b1079deb5159c2) the updated implementation for the hardcoded news feed, which is fully merged and working with the following sources (soccer, appl, btc, eth, one). Started working on the backend implementation to fetch data from sources based on this [doc](https://github.com/harmony-one/x/blob/main/doc/follows) (hand over to Artem).

2023-12-13 Wed: Completed and refactored logic for fetching from data feed and providing to OpenAI context. Wrote tests for coverage for the DataFeed file. Deployed USDT on the Linea <-> Harmony bridge. 

2023-12-12 Tue: [Implemented](https://github.com/harmony-one/x/pull/370) end-to-end logic for "Talk to ME!" news feed fetching and user profile settings.

---

2023-12-10 Sun: Configured a.country.  

2023-12-09 Sat: Discussed Twitter implementation with Aaron. Will meet up with Yuriy and Artem on Monday.

2023-12-08 Fri: Updated transcript logic handling. There is a known bug in Testflight and Production where some data is transcribed as "private", need to enable the information.

2023-12-07 Thu: Updated speech recognition logic handling to prevent "No Speech Recongition" error (as well as minor "errors") from being reported. Refactored TimeLogger logic measuringa app performance.

2023-12-06 Wed: Implemented enhanced transcription functionality of obtaining [setting information](https://github.com/harmony-one/x/pull/319/commits/32532bec445284f2b9f4d68093873d4f4d03e950) (model identifier, app version, and ios version) and [limiting](https://github.com/harmony-one/x/pull/319/commits/b55eaecd99a866f24903d09f2a0d9da840411c96) the size of transcript to 10MB. Artem will be finishing up the remaining tasks regarding the enchanced transcription. Updated font alignments and icons for the "Pause / Play" to match all other icons.

2023-12-05 Tue: Discussed and assigned tasks, as well as their ETAs to engineers with Theo F. Fixed a bug that threw nil pointer when transcription was empty. Began setting up haptic feedback for "Press & Hold" (handoff to Nagesh).

2023-12-04 Mon: Out of office

---

2023-11-29 Fri - 2023-12-03 Sun: Out of office

2023-11-28 Thu: Fixed user deletion and creation flow bug. Updated context length from 500 to 8000. Updated setting fields to have matching format.

2023-11-27 Wed: Fixed Network manager handling bug. Refactor and cleanup in app purchase process. In app purchase server side bug fix (hand off to Artem).

2023-11-26 Tue: Benchmarked latencies for head vs subsequent, which came out to 1.6s vs 1.3s (1hr session). The cause is due to the initial setup on the client (audio buffers and sockets) and server-side (authorization). Fixed expiration update [bug](https://github.com/harmony-one/x/commit/51c175aaa66b0e460e555d39972b74db1254732a).

2023-11-25 Mon: Fixed color switch bug on a new context. Implemented perceived latency on the client side. Measured latency to be an average of 1.4 seconds. Testing different chunking sizes to improve latency. 

---

2023-11-24 Sun: Going over PRs 261-266. Will be testing them tomorrow and merging them in order.

2023-11-25 Sat: Worked on resolving the linter issue.

2023-11-22 Wed: Fixed "More Action" button [bug](https://github.com/harmony-one/x/commit/d71ba3566c76794378b3492281dab13be132f7c8) and updated the icon. Fixed a [bug](https://github.com/harmony-one/x/commit/9fcde16412d557e0e910a5c081353f46125facd8) that rate-limited users upon new context.

2023-11-21 Tue: Updated asset structure so that they are shareable across different builds. Fixed asset [alignment and sizing](https://github.com/harmony-one/x/commit/fb6fcae7b780ff245abec55cb8b05516091059d4). Refactored [AppConfiguration](https://github.com/harmony-one/x/pull/242) module.

2023-11-20 Mon: Finalized the attestation issue (since we were requesting one from the App Store each time, some users were rate-limited) and solved it using caching from the relayer server. Measured the new perceived [latency](https://imgur.com/a/ExTJbIt) using a proxy server, which is around ~900ms median with up to ~1500ms as max.

---

2023-11-19 Sun: Refactored [OpenAI](https://github.com/harmony-one/x/commit/ef517118beaaa57bdbe9ede53b37072e47f519b5) and [Actions](https://github.com/harmony-one/x/commit/8f7220effd080dbcf01fb73933b302c053f4e4dd) module.

2023-11-18 Sat: Reviewed over updates made for the [relayer](https://github.com/harmony-one/x/tree/main/voice/relay).

2023-11-17 Fri: Resolved relayer issue.

2023-11-16 Thu: Resolved issue with retry API not being canceled. Updated product configuration and improved logic handling to prevent crashes when required data is not provided. Worked on the restore server logic handling to be in accordance with the voice app's new product configuration. 

2023-11-15 Wed: Discussing key auth server infrastructure with Aaron. Fixed custom instruction configuration so that it loads when the app is downloaded and first loaded. Disabled Apple Pay and user authentication. Addressed and fixed (handed over) a bug that crashed the app when user authentication is loaded.

2023-11-14 Tue: Updated chunking size (10 / 50) with exponential backoff of a total 10 min and canned response. Worked with Frank on implementing custom instructions, as well as setting configurations. Fixed voice selection bug. Went over OpenAI's Assistant to see a better implementation of context embedding without having to provide it each time. The current limitation of "assistant" is that streaming is not supported.

2023-11-13 Mon: Fixed a bug that ensures custom instructions are not deleted when cleaning up context for 512 max tokens. User testing with Theo and Alaina to diagnose if there are persistent issues with the current chunking method. Went through the official OpenAI API documentation, as well as various sources to see if there was an optimal way of implementing context embedding rather than providing it every time (result: there does not exist one as of now; Artem / Aaron going over other implementations)

---

2023-11-12 Sun: Reviewed Aaron's PR on the relayer service, as well as the configuration in the cloud service.

2023-11-11 Sat: Configured [Github action and Husky pre-commit hook](https://github.com/harmony-one/x/pull/165) preventing AppConfig.plist from being committed.

2023-11-10 Fri: Debugged time calculation logic that triggers gpt-3.5.

2023-11-09 Thu: Implementing long-press actions for multiple buttons. Fixing various bugs for the launch day. Debugging Aaron's rate limit merge (initially defaulted to 3.5turbo due to date calculation bug).

2023-11-08 Wed: Implemented "Press to Speak & Press to Send" button. Researched different tools we can use to develop the "share" feature. [Branch](https://www.branch.io/) seems to be the most useful SDK. Began looking into the SDK to start implementation.

2023-11-07 Tue: Update streaming to initially flush 5 words then by delimiting punctuations, upperbounded by 20 words. Finished setting up Sentry with Yuriy. Exponential backoff changes to 2, 4, 8 seconds.

2023-11-06 Mon: Fixed a bug that ensures streams that are part of the previous word are appended correctly. Upper bounded buffer to contain 10 words at max so that synthesis occurs at delimiter or 10 words. Implemented retryable methods with exponential backoff.

---

2023-11-06 Sun: Fixed existing conflicts for some PRs and have reviewed/merged them. Began refactoring the code to make it production-ready.

2023-11-04 Sat: Made updates and benchmarked the updated streaming implementation. Observed that the initial stream takes about 2-3 seconds but the latter ones are ~950ms.

2023-11-03 Fri: Updated Random Fact button to return random entries. Discussed with Aaron and Julia different approaches to improving the latency. Introduced initial flush (thinking -> synthesizer) of x (currently 5 words) words that increase the perceived latency.

2023-11-02 Thu: Fixed repeat button bug. Previously, it was only repeating the final streamed portion. Now it repeats the whole response. Demoed Voice AI at the Voice AI meetup.

2023-11-01 Wed: Fixed streaming interruption bug. Fixed the Press to Speak button functionality and color change bug. Discussed major persisting bugs and handed them over to the remote engineers.

2023-10-31 Tue: Spent time debugging a bug crashing the app during the "Press to Speak" interruption. Realized that when the streaming is completed, during synthesis, interruption is being handled correctly. However, while streaming, starting a new recognition will crash the application. Fixed bugs preventing Pause / Play button from working.

2023-10-30 Mon: Fixed bugs preventing ChatGPT streaming from working. Fixed another bug preventing interruption during synthesis.

---

2023-10-29 Sun: Cleaning up Yuriy's PR so that the "Press to Speak" button is working. Will wrap up tomorrow.

2023-10-28 Sat: Reviewed Yuriy's PR on streaming implementation for OpenAI.

2023-10-27 Fri: Fixed "Press to Speak" so that it does not crash from silence anymore. Bug fix regarding interruption has been fixed, "Press to Speak" in the middle of generation and synthesis is working as expected. There is a known bug where a user rapidly spamming "Press to Speak" button will the audio functionality to crash (will continue working on this). ChatGPT4 context has been enabled.

2023-10-26 Thu: Redeployed with another bug fix where "Press to Speak" button ends only when user lets go of the hold (previously 1.5 second silence would stop the recording). Implemented interruptibility where recognition task and audio response now stops when user holds the "Press to Speak" button, starting a new recognition task. Implemented OpenAI call with custom instruction embedded.


2023-10-25 Wed: Fixed another bug preventing "Press to Speak" button from working. Fixed the bug and refactored code so that any layout and / or design change will be separated from the logic implementation. Began implementing OpenAI streaming functionality based on Aaron's build.

2023-10-24 Tue: Fixed a bug preventing "Press Speak" button on the press build from working. Deployed the fix on "Voice AI" and "Sun". Began polishing the repo so that it is production ready. Will implement CI/CD pipeline, add linting rules, and other components that will make the repo more robust.

2023-10-23 Mon: Wrapped up user perceived latency for web app which is 15%, 45%, and 40% for transcription, knowledge base, and synthesis respectively (Deepgram, GPT4, and Azure / Google). I also deployed "sun" as a fork of FissionLab's Voice AI. There are many bugs to fix, mainly "Speak" button not working, and I will continue on fixing the bugs with Julia tomorrow. I have also set up another machine for Ivan to test out multiple LLM models.

---

2023-10-22 Sun: Measured latencies for Google. Can test out the latencies [here](https://yuriy.x.country/). Continued studying xcode to participate in iOS development and measure latencies.

2023-10-19 Thu: Continued working on calculating individual latencies for the API to use. Tested Azure, Google, and began to a look at Play.ht.

2023-10-18 Wed: Calculated end to end and user perceived latencies for sam.x.country. This [document](https://www.notion.so/harmonyone/API-Percentage-b44ce9c347f5474fb0f0a36c02dc6e55?pvs=4) contains detailed information. Started learning Xcode in order to benchmark and make improvements to ths X iOS application.

2023-10-17 Tue: Benchmarked latencies for various speech to text API. Deepgram [outperforms](https://www.notion.so/harmonyone/API-Benchmark-f3bee005a3aa4e4eb302ad02647a3d8b?pvs=4) others by far. Fixed ElevenLabs issue "webapp" was having. Had a meeting with Ivan to prioritize tasks, we will work on benchmarking latency percentage for the end-to-end flow.

2023-10-16 Mon: Updated the app to support iOS compatibility on Safari, which will become the main browser for /sam. Began setting up Prometheus to measure time lapsed on key components of the app (DeepGram, ChatGPT, and ElevenLabs).

---

2023-10-13 Fri: Deployed voice-webapp on [sun.x.country](sun.x.country). Working on integrating with Ivan's Acapela to the voice-webapp. Looking for various areas of optimization.

2023-10-12 Thu: Studying and going over Hugging Face [Quantization](https://huggingface.co/docs/transformers/main_classes/quantization); Wrestling [GPTQ](https://arxiv.org/pdf/2210.17323.pdf) paper (still need time to fully digest the material); Building demo 8-bit GTPQ (referenced from this [repo](https://github.com/IST-DASLab/gptq)); will continue working on this tomorrow

2023-10-11 Wed: Set up access and permission to supercomputing infrastructure with GPUs (for Ivan); Set up access and permission to Picovoice Rhino benchmark testing; Benchmarked the following NLU models: Picovoice Rhino, Google Dialogflow, Amazon Lex; Picovoice Rhino outperforms the other mentioned models by ~30% average
