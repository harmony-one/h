2024-09-18 Fri (on call):

2024-09-17 Thu (on call): Observed a tracer that allowed `debug_traceCall` within our [codebase](https://github.com/harmony-one/harmony/blob/787fc7b7bb48fec6ff0f23d8e58f3165bf20d882/rpc/tracer.go#L180). It is not listed in the developer document but the call is enabled throught setting the method `debug_traceCall` and at the moment the parameters seems to comply with Stackup's requirement. However, proper testing will be required. Began configuring a testnet validator node and a bundler node in order to ascertain the requirements for the `debug_traceCall` as well as other configurations.

2024-09-16 Wed (on call): Further analyzed Harmony's tracer in order to observe the results. Began adding a tracer in Harmony's protocol in order to provide the results required for the validation process.

2024-09-15 Tue: Analyzed Harmony's tracer as it is required in order for bundlers to validate user operations prior to them being sent to the chain. Harmony does have a method `trace_transaction` and `trace_block` but does not comply with `debug_traceCall` ([specs](https://geth.ethereum.org/docs/interacting-with-geth/rpc/ns-debug)).

2024-09-14 Mon: Tested out the whole flow with the [Stackup CLI](https://docs.stackup.sh/docs/getting-started). Now that the process is familiar, began the deployment process on our chain.

---

2024-09-13 Sun (4 hr): Interacting with bundlers set up on [other chains](https://docs.stackup.sh/docs/entity-addresses). Working with paymasters and entry points to test out the whole process.

2024-09-12 Sat (3 hr): Examined the installation process and continued the configuration procedure.

2024-09-12 Fri: Began the deployment process. Finding the correct configuration according to [this](https://docs.stackup.sh/docs/erc-4337-bundler-configuration) specification.

2024-09-11 Thu: Examining installation and configuration for the bundler deployment. 

2024-09-10 Wed: Finalized comparisons of the various bundler implementations ([comparison](https://www.stackup.sh/blog/a-guide-to-the-top-erc-4337-bundlers-features-performance-and-more) and [test results](https://www.erc4337.io/bundlers)). It only makes sense to move forward with Infinitism and Stackup's implementation of the bundlers, which are the only two with 100% test pass rate. Being more familiar with Golang and the performance advantage Stackup has over Infinitism (Infinitism does have ERC 4337 compliance advantage), will go forward with Stackup and began the process tomorrow.

2024-09-09 Tue (on call): Went through the most recent changes in our protocol in order to be aware of the on call situations. Continued to look into Stackup implementation.

2024-09-09 Mon (on call): Examined Stackup's Go implementation of the [bundler](https://docs.stackup.sh/docs/erc-4337-overview). Brushing up on Docker and containers in order to began the [deployment process](https://docs.stackup.sh/docs/erc-4337-bundler-installation).

---

2024-09-08 Sun (3 hr; on call): Completed research on Coinbase smart wallet. Fixed DNS configurations for h.country. 

2024-09-07 Sat (10 hr; on call): Continued Coinbase smart wallet research. Deep dived into their deployment criteria. This will be deployed only once ERC-4337 contracts are deployed. Examined bundler [implementations](https://www.erc4337.io/resources) with focus on the Typescript implementation by [eth-infinitism](https://github.com/eth-infinitism/bundler). Will continue look into other implementations listed on the resources.

2024-09-06 Fri (on call): Completed deep dive into ERC-4337 whitepaper. Began researching [Coinbase smart wallet](https://github.com/coinbase/smart-wallet).

2024-09-05 Thu (on call): [Deep dived](https://brazen-need-a0a.notion.site/ERC-4337-Account-Abstraction-Using-Alt-Mempool-8dcd5d9b769842f0acbf095e8f9680f1) into [ERC-4337 whitepaper](https://eips.ethereum.org/EIPS/eip-4337) in order to understand all components and criteria required for deployment in Harmony. Inspected Aaron's [commits](https://github.com/panoptic-labs/panoptic-v1-core/compare/main...polymorpher:panoptic-v1-core:main) on the the Panoptic command line interface, wrapping up all deployment process and scripts.

2024-09-04 Wed (on call): [Fixing](https://github.com/harmony-one/panoptic-v1-core-cli/commit/66694ce69b197e6393fd4c1b2207b1c968f82163) a bug related to the collateral trackers for the tokens during the mint token operation. Works for the actual tokens but for minted test tokens, not working at the moment. Analyzing the cause.

2024-09-03 Tue (on call): Connected the core componentes of Panoptic to the [command line interface](https://github.com/harmony-one/panoptic-v1-core-cli/commit/8432bf400e12c83753b1635ce25039f8185db999) component. Troubleshooted problem related to deploying pools if it's already deployed with a different fee.

2024-09-02 Mon: Holiday

---

2024-09-01 Sun (5 hr): Wrote scripts to enable client interface commands to interact with deployed smart contracts and to simplify building smart contract abis.

2024-08-31 Sat (11 hr): Writing tests for the key functionalities. Factoring code in order to modularize the functionalities. Simplifying [core functionalities](https://github.com/sunwavesun/panoptics-cli/commit/69fbba06c58d86492ce14a6b36d4c655ee171c0e) in order to interact less with the chain itself in order to improve performance.

2024-08-30 Fri: Began going through the public demo workflow. Pool creation and option mint working as expected, will test more tomorrow.

2024-08-29 Thu: Finalized the multiple leg configuration.

2024-08-28 Wed: Continued the multiple leg configuration. [Reimplemented](https://github.com/sunwavesun/pcli/commit/c00e54f985b0e42aa29687da82c950029004db35) the option mint logic. Public demo ETA 09-05 (Fri).

2024-08-27 Tue (on call): Began reworking option logic to include multiple leg configuration.

2024-08-26 Mon (on call): Users are required to first [approve and deposit](https://deeznuts.panoptic.xyz/new-position) the amount of assets in order to mint an option. However, if there is not sufficient collateral, the option would not be minted. The deposits are not reverted, rather the users receive Panoptics versions of these tokens. This is the same case for the current Panoptics beta version (official version not yet released). Working on to see if it is possible to first check if the collateral are sufficient prior to the deposits.

---

2024-08-25 Sun (12 hr; on call): Continued and completed the code review for [PR 4735](https://github.com/harmony-one/harmony/pull/4735). Inspecting the developments necessary for account abstraction and smart contract in order to coordinate with Konstantin.

2024-08-24 Sat (5 hr; on call): Finalized option minting logic.

2024-08-23 Fri (on call): Analyzing the recently added [RPCs](https://github.com/harmony-one/harmony/pull/4735) for boot nodes. Continued the reimplementation.

2024-08-22 Thu (on call): Familiarizing rollback methods for validators with the newest upgrades. [Reimplemented]() option minting logic in order to improve gas usage.

2024-08-21 Wed (on call): [Implemented](https://github.com/sunwavesun/pcli/commit/f53c6d5e58971912db574b9978f06409463c0fbf) Uniswap V3 and Panoptic pool core functionality. It was previously implemented but had to be rewritten due to bug related to token transfer and pool creation. Will work on reimplementing option logic tomorrow.

2024-08-20 Tue: Fixed the bug. The transactions must be sent using `legacy` mode. If not, the transactions will be processed in ununiformed order. Will make the repo public tomorrow.

2024-08-19 Mon: Continued working on fixing the continuous bug. Seems to be problem with legacy and / or slow mode. Will continue tomorrow on fixing the cause.

---

2024-08-17 Sat (4 hr): Continued the debugging process.

2024-08-16 Fri: Preparing demo to share with teammates. Noticed a bug when continuously creating pool and options. Working on debugging the cause.

2024-08-15 Thu: Finalizing crab and bull strategy development. Continued cleaning up repo.

2024-08-14 Wed: Continued working on strategy creation. Working on different calculation that will allow for the strategy creation once user inputs the required values when creating options. Also, cleaning up repo in order to be made for public.

2024-08-13 Tue (on call): Studied how different strategies are minted (crab and bull). Working to incorporate the strategies so that they can be auto configured for the users. One caveat is that from just command line interface, it is difficult to visualize the strategies.

2024-08-12 Mon (on call): Command line interface completion ETA 08/14 (Wed).

---

2024-08-09 Fri (on call): Continued to implement default strategy creation. Logic not working as expected and options not always created as expected.

2024-08-08 Thu (on call): Updating command line interface option creation logic to support default strategies such as crab, bull, and bear. Studying the differences between the option strategies. For any other options manual input is to be provided.

2024-08-07 Wed (on call): Changing the `geth` version seems to have fixed the issue. Using a version that is too low or too high introduces many issues. Rewriting tests to cover functionality for the changed `geth` versions.

2024-08-06 Tue (on call): Running into out of gas error and working to fix it. Transactions receipts show as successful and the explorer shows successful but running into `out of gas` error for the internal transactions.

2024-08-05 Mon (on call): Fixed the repeated transaction bug. Configuring the transactions to be sent in [`legacy` mode](https://eips.ethereum.org/EIPS/eip-1559) allows for batch as well as multiple transactions to work now. `geth` version downgraded in order to accomplish this as the newer versions have inner methods called that are not supported by Harmony.

---

2024-08-04 Sun (7 hr): Noticed another bug despite the wait time. Seems that sending the transactions in batches does not work as they aren't able to be simultaneously processed. Despite it being slightly slower, broadcasting and processing each transactions individually is fixing the issue.

2024-08-03 Sat (12 hr): Continued working on the repeated transaction bug. Setting wait time after sending a transaction seems to resolve the issue but do not know the exact cause at the moment.

2024-08-02 Fri: Working on repeated transaction sending. At the moment, first two to three transactions are working but the ones sent after sometimes result in failures. 

2024-08-01 Thu: Testing and developing option transferring functionality.

2024-07-31 Wed: Finalizing the command line interface gas estimation issue. Began to work on transferring options.

2024-07-30 Tue: Continued to work on the gas estimation when sending transactions. The method for retrieving gas estimation called from `geth` seems to not be compatible for Harmony (worked for other networks for different chains). Currently using an arbitrary value for gas estimation but will attempt to solve this tomorrow. 

2024-07-29 Mon: Continued development for option creation. Noticed an increase in gas when using the command line interface rather than the script. Attempting to decrease optimize the gas usage.

---

2024-07-27 Fri: command line interface now accepting user inputs for the option creation (ETA 08/01 Thu).

2024-07-26 Thu: During option creation, there are various arguments that need to be supplemented by the user. Finding the optimal way to do so without visualization.

2024-07-25 Wed: Worked on debugging and configuring options for the various option creation.

2024-07-24 Tue: Worked on fixing the configuration for `geth`. The more recent versions support RPC methods that is called when interacting with contracts. These are not support in our network. Had to change configurations in order for the command line interface to properly interact with smart contracts. command line interface now properly creating liquidity pools for both Uniswap V3 and Panoptics.

2024-07-23 Mon: Fixed the bug and now able to create options repeatedly. Encountered several bugs (UniswapV3 interaction when creating a pool, option creation) and began to debug them.

---

2024-07-21 Sat (9 hr): Fixing a bug where an option is unable to created repeatedly, analyzing the cause.

2024-07-20 Fri: Decided to input numbers rather than visualization when minting options, as the whole flow will be done using command line interface. Development on transferring and burning options.

2024-07-19 Thu: Continuing the minting options development. Noticing a problem where it makes users hard to visualize the price points without a visual graph.

2024-07-18 Wed: Continued working on the mint functionality. Attempting to simplify the process of minting various options.

2024-07-17 Tue: Completed deploying the WONE and USDC pool. Continued working on the command line interface functionality to mint options.

2024-07-16 Mon: Completed the fix and made a fork. Deployed the smart contracts.

---

2024-07-13 Sat (12 hr): Began looking at [Ink](https://github.com/vadimdemedes/ink), which provides the same component-based UI building experience that React offers in the browser, but for command-line apps.

2024-07-12 Fri: Analyzed the fix for the failing test with Aaron. USDC uses the highest 1 bit in the balance for blacklist status, but the tests set initial balance to be max uint256, which sets all bits to 1. All tests are passing now. Will redeploy the fixed smart contract.

2024-07-11 Thu: Noticed that some tests were failing for the core smart contracts. Began implementing a fix.

2024-07-10 Wed: Continuing the core functionalities (pool and positions) and implementing mobile wallet connection.

2024-07-09 Tue: Working on functionality for opening pools and positions.

2024-07-08 Mon: Began implementing the built in server mentioned below.

---

2024-07-07 Sun (12 hr): Discussed with Aaron on updating the Panoptics flow. Better idea than the script - command line interface implementation would be to create a simple built-in server that serves an empty-looking web page, which the command line interface program opens in the browser when users need to sign. The page interacts with MetaMask using dynamically rendered JavaScript, and upon transaction completion or rejection, it calls another API on the server to inform the command line interface program to proceed with the next step.

2024-07-06 Sat (8 hr): Continued updating the scripts and asking peers for the script optimization.

2024-07-05 Fri: Continuing the walkthrough as well as debugging the script on closing the pool (technically selling / transferring the option to another user).

2024-07-03 Wed: Creating scripts for the command line interface usage. Starting the pool, depositing the collateral, then minting options are quite complicated solely through command line interface. Thus, created scripts that can be used in the command line interface to perform the mentioned functioned ([walkthrough](https://brazen-need-a0a.notion.site/Panoptics-Guide-9e2897891a61485bb34c81c27a71aaaf)).

2024-07-02 Tue: Learning to use command line interface to create options. Creating a walkthrough to guide others as well.

2024-07-01 Mon: Writing scripts to create various option calls. Searching through ways to trigger to command line interface.

---

**2024 Q2 Review (62 Hours)**

I focused on launching data availability rollup on shard 1. Researched into how Harmony's Shard 1 compares to Celestia and NEAR as data availability layer. Deployed sovereign rollup using [Rollkit](https://rollkit.dev/blog/sovereign-rollups-on-bitcoin) and launched Polaris in order for it to be Ethereum Virtual Machine compatible. Also deployed [Optimistic rollup](https://ethereum.org/en/developers/docs/scaling/optimistic-rollups/), a smart contract rollup, as it was more suitable for Harmony.

Researched and deployed Panoptics protocol, a perpetual options trading protocol utilizing Uniswap v3. Continuing the work by making the protocol accessible through command line interface.

---
2024-06-30 Sun: Able to create pools through scripts. Working on creating option calls through scripts.

2024-06-29 Sat: Testing out Panoptics and replicating the strategies through command line.

2024-06-28 Fri: Panoptics app finally up. Referencing the frontend to replicate. Continued frontend work.

2024-06-27 Thu: Panoptics app has been down since yesterday. Reached out to the team again to get access. Began working on frontend to interact with the smart contracts.

2024-06-26 Wed: Began to work on the frontend for Panoptics. Reached out to their core team to see if their interface is open sourced.

2024-06-25 Tue: Deployed a new pool for the Sepolia Panoptic ([transactions](https://sepolia.etherscan.io/address/0x6fb20da8f132a4849dc1b20bf25b74c1c2a94126)). Successfully deployed the protocol on Harmony Mainnet. Here are addresses of the contracts: [SemiFungiblePositionManager](https://explorer.harmony.one/address/0xdc76db9ea5436cb59ad5ea9d39acb44f29f05602), [PanopticPool](https://explorer.harmony.one/address/0x59a885B64FA250EF87D28274FC254D9E45665786), [CollateralTracker](https://explorer.harmony.one/address/0xdc9C08a86B142E48ddDa4432BE7B3795C65A45d0), and [PanopticFactory](https://explorer.harmony.one/address/0x4AE81fd45e6bdb8c009DcCA13648691E04d40ca2).

2024-06-24 Mon: Deployed Panoptic to Sepolia network. Comparing the variables used for Sepolia and the required ones for Harmony to properly deploy. Need to find the WONE in order to deploy the `PanopticFactory.sol`.

---

2024-06-22 Sat: Continued Uniswap v3 Testnet and Panoptic smart contract deployment.

2024-06-21 Fri: Continued Uniswap v3 Testnet deployment. Also, continued the progress left on 06/19 (Wed) on `PanopticFactory.sol` to coordinate with Uniswap v3.

2024-06-20 Thu: Researched into at Uniswap v3 developer documentation. Began to deploy Uniswap v3 to Testnet.

2024-06-19 Wed: Went over capital efficiency section of Panoptics. Began deploying `PanopticFactory.sol` and configuring variables specific to Harmony so that it interacts with Uniswap. Currently Harmony only has Uniswap on Mainnet so looking for a way to deploy and play around using Testnet.

2024-06-18 Tue: Spent time going over `PanopticFactory.sol` and `PanopticPool.sol` which deploys an options market on top of an existing Uniswap v3 pool and manages positions, collateral, liquidations and forced exercises, respectively. Also, spent time going over `UniswapV3Pool.sol`, a dependency, and how it acts as a "short put" in Panoptics term.

2024-06-17 Mon: Continued Streamia research and overview. Spent time going over `SemiFungiblePositionManager.sol` contract that manages liquidity pool position.

---

2024-06-15 Sat (6): Spent time overviewing Streamia (Streaming Premia) especially on how it completes fee tracking in Uniswap, and fee and liquidity tracking Panoptics. Will continue tomorrow and work to see if I can work fork off and deploy.

2024-06-14 Fri: Researched uniswap v3, especially how it interacts with Panoptics as the main pool. Dived into Uniswap v3 smart contracts as well.

2024-06-13 Thu: Went deeper into general options trading, realized I lack deep understanding options in order to fully understand the protocol logic.

2024-06-12 Wed: Continued research for protocol design and began overviewing smart contracts.

2024-06-11 Tue: Continued Panoptics protocol overview and began researching protocol design and roles. 

2024-06-10 Mon: Studied options basics and Panoptics protocol overview.

---

2024-04-25 - 2024-06-07: Paid time off (32 days)

---

2024-04-24 Wed: Reviewing the draft with Julia and Theo.

2024-04-23 Tue: Worked on a script for calculating the cost. Discussed with Diego on the script accuracy as well as the provided price data.

2024-04-22 Mon: Discussed with Theo on the resume matching service. Looking through system engineer resumes.

---

2024-04-19 Fri: Continued throughput calculation and difference for Near and Celestia.

2024-04-18 Thu: Calculated throughput for our chain. Cleaned and packed boxes at the office for move out day.

2024-04-17 Wed: Started benchmarking process, more into how Near and Celestia calculated the costs. Will talk to Soph on how to calculate our costs.

2024-04-16 Tue: Started looking into resume matching for system engineers of 4 or more years. Discussed with Theo on the ongoing process and progress.

2024-04-15 Mon: Continued working on the data availability article, as well as calculating costs. Trying to make a correlation with each block produced to the cost.

---

2024-04-13 Sat (x.xh): Began looking into the cost metrics for our shard 1 and how other chains calculate their costs.

2024-04-12 Fri: Continued working on the article for data availability. Calculated throughput for our Shard 1, which is nearly 0 due to the lack of user activity.

2024-04-11 Thu: Began writing the article for data availability.

2024-04-10 Wed: Bug fix regarding sending transaction to the rollup contract.

2024-04-09 Tue: Completed deploying rollup.

2024-04-08 Mon: Removing features in order to disable Create2 deploy as our chain does not support it.

---

2024-04-07 Sun (x.xh):

2024-04-06 Sat (x.xh): Continuing on working with different configurations as it is not fully working in terms of deployment.

2024-04-05 Fri: Realized we need to disable block validation and add default baseFee in order to work with our chain.

2024-04-04 Thu: Explored configuration used for the OP stack to work with Etheruem. Working with different configurations in order to accomodate Harmony.

2024-04-03 Wed: Realized the problem with contract deployments. Harmony is EIP-155 protected, requiring chainId to be part of transactions, whereas the OP stack contracts are not. Figuring out alternative solution to bypass this.

2024-04-02 Tue: Continued writing the article. Focused on the Celestia core concepts as well as sovereign vs smart contract rollup explanation. Continued to work on the contract debugging process. Implemented scripts to determine throughput and block sizes for Shard 1.

2024-04-01 Mon: Working on OP Stack deployment, especially the core L1 contract. Trying to debug deployment failure for few contracts.

---

**2-Week Deliverables by 2024-03-31:**

Deploy a rollup on shard 1 that utilizes Celestia for data availability. Specifically, need to change the existing Rollkit SDK so that 1) interaction with Celestia for data avilability occurs, 2) settlement happens in Harmony Shard 1, and 3) deploy smart contract (and necessary features) in order to handle settlement.

---

**2024 Q1 Review (62 hours)**

I implemented a minimal on chain flip service that handled cross chain asset bridging. The services has handled around ~300 transactions for Base and BSC combined. I've also implemented BTC-EVM wallet which allows for users to use command line interface in order to manage accounts in both Bitcoin and EVM based chains derived from the same keypair.

Prototyped human protocol using various tools and frameworks, and eventually implemented the Firestore based h.country. Specifically implemented keypair management, path commands using "/", as well as OAuth flow. At ETH Denver, introduced the application to ~30 users. Recently, I have deployed the Polaris EVM execution layer on Rollkit, a Cosmos SDK fork, and worked with Yuriy in launching Op Stack based, smart contract rollup on Celestia.


---

2024-03-29 Fri: Figuring out the synchronization problem with Shard 1 nodes. Handed off the task to Yuriy.

2024-03-28 Thu: Began deploying node for OP Stack. Running into trouble with Shard 1 interaction.

2024-03-27 Wed: Began drafting the rough draft for the article to be released next Friday. Will include the research, implementations so far (Polaris and OP Stack), as well as ongoing implementations.

2024-03-26 Tue: Read the Celestia Whitepaper on Fraud and Data Availability Proofs.

2024-03-25 Mon: Meeting with Stephen regarding sovereign rollups and explored different possibilities. Continued Polaris implementation. Looked into the wrapper implementation.

---

2024-03-23 Sat (4.0h): Began working on the Polaris rollup with Yuriy.

2024-03-22 Fri: Reviewed Polaris implementation on Cosmost SDK. Attended Nvidia GTC meetups.

2024-03-21 Thu: Continued implementation for the wrapper. Discussed with Diego regarding the metrics. We realized that throughput for Shard 1 is near 0 currently. In order to get the precise metrics, we need to create a tool to traverse throughout all the nodes. Attended Nvidia GTC after meetup. Diego would be working on the costs.

2024-03-20 Wed: Began implementing wrapper for Harmony nodes to be used for Rollkit. Divided the task with Yuriy so that Yuriy would be working on the intial approach of deploying a rollup on Celestia as the data availability layer with Shard 1 as the proof storage and I would work on a rollup with Shard 1 as both data availability layer and proof storage. Attended Nvidia GTC.

2024-03-19 Tue: Discussed with Stephen that we want a sovereign one instead. Began looking at Polaris implementation for Rollkit, which allows for EVM execution environment with Cosmos based chains and rollups. Realized that we would need a wrapper around our Harmony nodes, in order for it to work as a data availability layer.

2024-03-18 Mon: Began deployment for Op Stack rollup. Deployed smart contracts as well as op-geth, the execution engine for the rollup.

---

2024-03-17 Sun (3.0h): Discussed with Yuriy on possible progression with Op Stack. Began looking at the documents as well as the smart contracts required for deployment.

2024-03-16 Sat (4.0h): Began looking at smart contract rollups via Op Stack as an alternative. One problem with Rollkit (Cosmos SDK) is that they do not yet have a connection with EVM chains, thus unable to utilize EVMs as data availability layer. 

2024-03-15 Fri: Continued studying Rollkit and Cosmos SDK. Launched rollups on Celestia, without shard 1 interaction. One concern is that there is no EVM chain used as the data availability layer. Also, it seem that Polaris is the only option for enabling EVM execution environment in Cosmos based chains / rollups. Looking into alternatives, possibly Op Stack.

2024-03-14 Thu: Deployed Celestia node on a local network. Will continue tomorrow on learning the Cosmos SDK. Discussed with Ivan and Yuriy in terms of the LayerZero bridge audit.

2024-03-13 Wed: Started exploring Celestia and the Cosmos SDK. Since Rollkit is based on the Cosmos SDK, they offer the required resources for understanding the SDK. 

2024-03-12 Tue: Yuriy and I decided to look into 2 different SDks with Yuriy diving into Sovereign SDK and me into [Rollkit](https://rollkit.dev/). Both support modular, sovereign rollups but they are in different languages, Rust and Golang, respectively. The current solution is for us to fork the SDKs and change the settlement logic so that it occurs through Harmony rather than Celestia. Smart contract on the Harmony level in order to accept the proofs provided from the rollup (and possibly Celestia) will be required. This part will be handled by Yuriy.

2024-03-11 Mon: Yuriy and I decided on [Sovereign SDK](https://github.com/Sovereign-Labs/sovereign-sdk) in order to implement the sovereign rollup on our Shard 1. Started the architecture and technical roadmap, as well as writing up and dividing up tasks to be completed along with Yuriy. Tomorrow morning, we will discuss on the ETAs for the features and provide an initial write up for review.

2024-03-10 Sun (8.0h): Researched into Celestia and rollups, specifically sovereign rollups. Used Sovereign SDK in order to launch a basic rollup on Celestia. This basic rollup handles the data availability and settlement through Celestia. Looked into how we can integrate Harmony's Shard 1. The most viable solution seems to be handling just the settlement in Shard 1.

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

2024-02-18 Sun (2.0h): Worked on setting up shortcuts for quick testing.

2024-02-17 Sat (5.0h): Restructured the application to fit the restructured data format. Documented the new data structure.

2024-02-16 Fri: Implemented multiple tasks required for the application. Form data structure related to various "actions" within the application.

2024-02-15 Thu: Implemented hash power.

2024-02-14 Wed: Out of office.

2024-02-13 Tue: Out of office.

2024-02-12 Mon: Finalized the h.country merge. Handed off tasks to Julia and Theo to coordinate with Artem and Yuriy. Also, OAuth related tasks to Rika.

---

2024-02-11 Sun (2.0h): Worked on the h.country merge. 

2024-02-10 Sat (4.0h): Implemented neo4js in order to find connections between users.

2024-02-09 Fri: Looked into graph database and sorting algorithms for connections. Decided move forward with and implement the graph method. 

2024-02-08 Thu: Initial implementation of Firebase OAuth with 4 providers (Google, Github, Twitter, and Facebook).

2024-02-07 Wed: Migrated to Firebase datastore in order to utilize offline data availability.

2024-02-06 Tue: Implemented KV store data scheme. Implemented workers to interact with the given data. Handed off the rest of taks to Artem and Yuriy.

2024-02-05 Mon: Implemented counter demo utilizing pages, workers, and kv store from Cloudflare.

---

2024-02-04 Sun (3.0h): Researched into Cloudflare Pages and Workers. Created a simple interaction between pages and workers.

2024-02-03 Sat (4.0h): Researched into ElastiCache Redis. Configured the initial settings for ElastiCache and implemented Typescript interaction with ElastiCache. (2 hours)

2024-02-02 Fri: Implemented BTC command line interface wallet. Discussed new initiative. Benchmarked Redis performance.

2024-02-01 Thu: Fixed q.country lottery endpoints to reflect Telegram entries. Dived into certificate renewals for dotcountry. Attended Sui event and showcased Flip and BTC wallet.

2024-01-31 Wed: Implemented Telegram embeds for 02/01 lottery. Manually implemented cross shard transactions for Flip (had to find a workaround as all the libraries were outdated).

2024-01-30 Tue: Updated 1.country frontend command line interfaceent to host Notion and Substack embed on inscription. Notion is working as expected but have to find a fix for Substack.

2024-01-29 Mon: Launched 01/30 Lottery. Implemented dotcountry redirect logic.

---

2024-01-28 Sun (4.0h): Coordinated with community members to assit in setting up [Flip](https://github.com/harmony-one/flip). [Updated](https://github.com/harmony-one/s/tree/one-server) Flip code to simplify deployment process (containerization setup & configuration for indexers and db into a single server).

2024-01-27 Sat (2.0h): Continued working on the lottery.

2024-01-26 Fri: Dotcountry inscription to work with Telegram inscriptions. Started preparing for next week's lottery.

2024-01-25 Thu: Started dotcountry inscription to allow single domain owners to have user access. Assigned tasks to Yuriy and Artem related to dotcountry inscription.

2024-01-24 Wed: q.country configuration and setup. Implemented lottery logic along with Yuriy. Flip configuration for user deployment.

2024-01-23 Tue: Implemented lottery filtering logic for valid Twitter URL.

2024-01-22 Mon: Updated set up so that a single indexer is deployed for each chain (previously, 2 indexers for each service). No need for overlapping indexers.

---
2024-01-21 Sun (5.0h): Refactor flip backend and frontend code for easier deployment. 

2024-01-20 Sat (4.0h): Set up configuration for for fly.io.

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

2023-11-26 Tue: Benchmarked latencies for head vs subsequent, which came out to 1.6s vs 1.3s (1hr session). The cause is due to the initial setup on the command line interfaceent (audio buffers and sockets) and server-side (authorization). Fixed expiration update [bug](https://github.com/harmony-one/x/commit/51c175aaa66b0e460e555d39972b74db1254732a).

2023-11-25 Mon: Fixed color switch bug on a new context. Implemented perceived latency on the command line interfaceent side. Measured latency to be an average of 1.4 seconds. Testing different chunking sizes to improve latency. 

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
