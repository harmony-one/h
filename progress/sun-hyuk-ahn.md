2024-03-11 Mon: Yuriy and I decided on [Sovereign SDK](https://github.com/Sovereign-Labs/sovereign-sdk) in order to implement the sovereign rollup on our Shard 1. Started the architecture and technical roadmap, as well as writing up and dividing up tasks to be completed along with Yuriy. Tomorrow morning, we will discuss on the ETAs for the features and provide an initial write up for review.

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
