2024-08-23 Fri:
- Lock-Free Consensus Methods for Message Validation: The current consensus mechanism involves sending messages from methods that are under `mutex.Lock`, which in turn call libp2p. Since libp2p also uses `mutex.Lock` internally, this can lead to potential deadlocks. To prevent this, we need to call such methods asynchronously. However, executing these methods asynchronously introduces unpredictability in their behavior.
- Investigating the Zero Sign Power Issue on Local Watchdog: I was unable to identify the cause of the zero sign power issue on the local watchdog. This problem requires further investigation on the devnet. I will continue working on this with Ulad next week.
- Reviewing Pull Requests.

2024-08-16 Fri:
- Working on branch with 1 second finality and 67% signers count. It passed 75% of tests
- Was investigating the `context deadline` issue occurring on the localnet with Streamsync. During the investigation, I discovered duplicated connections. When a connection is replaced with a new one, any requests in progress on the old connection are discarded, leading to the deadline error. However, I have yet to determine the root cause of the connection duplication.
- Fixed an issue with `legacysync` where incorrect ports were being used, causing shard 0 to receive information intended for shard 1. This miscommunication forced unnecessary synchronization, disrupting consensus and preventing the proposal of new blocks. 
- Reviewing and merging pull requests.  

---

2024-08-09 Fri:
- Collaborated with Ulad to update harmony-test repo. Even it flexible to run various branches and not the default one, it's impossible to configure to run certain golang version instead of default. We were working on additional arguments which could be provided on start.  
- Created new version of commission split, where necessary to sign only 67% of the validators. It allows to skip waiting time for the rest of the validators, but requires code changes in the network and the signing layers, and i working to achieve it being stable.  
- Created new fix for the theoretical zero division issue, it does not happen, but when harmony nodes count will be zero, it will. Issue was provided by Soph.
- Was reviewing Pull Requests, merging and providing feedback.

2024-08-02 Fri: Updated golang to 1.22. With Ulad tested made additional tests golang 1.22. Version 1.22 does not have incompatibility or stability issues. Results can be found https://github.com/harmony-one/harmony/pull/4722/#discussion_r1702049235

**Research on 1-Second Finality and Validator Rewards in Block Signing**

In the context of Byzantine Fault Tolerance (BFT) protocols, achieving consensus requires collecting 67% of the votes. To optimize our protocol for validator rewards and block signing without significant changes, i have identified two potential approaches:

*Reward Splitting Among Validators Who Sign the Block*:

In this approach, rewards are distributed among the validators who successfully sign a block. This method encourages competition among validators, potentially increasing operational costs and leading to greater centralization within our network. Networking efficiency will become crucial, as a single high-performance server will be more profitable than multiple lower-performance servers. As a result, servers may be concentrated in the same data center to minimize latency.

*Reward Splitting Independent of Block Signing*:
Here, rewards are split among all validators regardless of whether they sign the block. This makes block signing optional for individual validators, yet incentivizes collective action, as the total reward increases when all validators sign the block as quickly as possible. This approach simplifies the reward distribution process and enhances performance.

Currently, our protocol does not support identifying a block proposer. While theoretically, we could distribute rewards between the block proposer and the validators, implementing this would necessitate significant protocol modifications. These changes would include updates to block proposing, consensus mechanisms, reward calculation, crosslinks, and the introduction of a new block version.   

---

2024-07-26 Fri:
- Fixed issue with zero division
- Tested new golang version and the latest go-lib-p2p version on devnet in different combinations with bootnode. 
- Found and fixed issue with security incompatibility.
- Found and fixed issue with multiplexer incompatibility.
- Tested new code in testnet environment, it was successful.
- Tested mainnet compatibility, contains differences in security parameter. Will continue on Monday.  

---

2024-07-19 Fri:
- Updated golang version to 1.21 version, it passed all tests, total progress 100%. 
- Investigated and fixed issue with different hashes for the same genesis block. Go@1.21 provides different dots on the curve for the same input, so i hardcoded exact dots.
- Tested and merged PR with fix for the peer storage. Improved getting connected peers method from linear complexity to constant.
- Finalized watchdog integration with the localnet. Collaborated with Ulad. Merged.
- Created new issue and started investigation of the watchdog crushes. 
- Collaborated with Ulad for the go@1.21 devnet testing. Test results showed that the node has problems connecting to other nodes. We will continue investigation on monday. 

---

2024-07-12 Fri: Investigated the issue with the hash generation in localnet testing. Go@1.21 changed behavior of the ecdsa key generation function, so it can provide different private keys for the same input. Described [here](https://github.com/golang/go/blob/release-branch.go1.21/src/crypto/ecdsa/ecdsa.go#L153). Updated hotstuff description and commit messages. It can be found [here](https://github.com/Frozen/gohotstuffimpl)

---

2024-07-05 Fri:
- `UpdateMaxCommissionFee` function covered with tests. 
- Provided fix for the node bootstrap process, which was using incorrect method to calculate connected peers. 
- Fixed the `PeerConnectivity` method, which was using iteration over 20k elements in the worst case, now it has no iteration at all.
- Removed trailing zeros from the Decimal.String method.
- Resolved connection issues in the tests package of the Harmony p2p library. 
- Golang version update: passed 50% of tests, current progress is 80%.

---

2024-06-28 Fri:
- Updated go-lib-p2p to the latest version, which can potentially fix issue with bootnode. 
- Updated golang version to the latest, it passed 25% tests, total progress about 70%. 
- Moved tests from separate repository to the project. Having additional repo gives only disadvantages for the small team, forcing us to support 2 different repos aimed to the same goal. 

2024-06-21 Fri: 
- The current status of 1-second finality is approximately 40%. 
- I refactored block proposing, because current implementation does not allow to propose blocks from consensus, it fails with cyclic dependencies. 
- I improved reward calculation frequency, which made our tests execution 2x times faster.
- I implemented minor improvements for the consensus, which were found during the investigation of the undeletions issue and the hotstuff consensus research.

---

**2024 Q2 Review**

Soph and I identified the root cause and implemented a solution for the undeletions issue; I investigated the crosslinks bug and implemented a fix for crosslink processing. I developed a new consensus message for broadcasting vote power across the network. 
I implemented unpredictable leader switch using the verifiable random function. I implemented a prototype for the HotStuff chained protocol, available [here](https://github.com/Frozen/gohotstuffimpl).
HotStuff involves block proposing by the validator who is the future presumptive leader. However, this approach is only partially applicable for us, as it implies rollbacks in the worst-case scenario, which the Harmony blockchain does not support. By applying block proposing within the prepared stage, we can save one network communication without causing a rollback in the worst-case scenario.

---

2024-06-14 Fri: This week we were investigating the issue with undeletations. I created 1 pr with fix, and 4 with different activation for mainnet and devnet. Additionally created PR that fixes race error, and another one for minor improvements which was found during the investigation.

---

2024-06-07 Fri: This week, I completed the task of broadcasting vote power across the network. I also resolved a panic issue during unsuccessful node termination that could potentially lead to state corruption. Additionally, I implemented a PoC for the HotStuff chained protocol, aiming to understand the differences between Harmony's implementation and HotStuff's approach.

---

2024-05-31 Fri: This week, Soph and I have been testing the crosslink fix on the devnet. It successfully synchronized all missing crosslinks, so we have moved further testing to the testnet. Additionally, I am continuing to work on leader broadcasting vote power through the network. This will enable us to debug the network even when we lack information about the leader.          

---

2024-05-24 Fri: This week, Soph discovered another way to sign crosslink. I implemented a new version that not only improves the sender side (as the previous version did) but also enhances the receiver side, making it more suitable for our needs. Additionally, I worked on asynchronous code, specifically on two functions that execute in an unpredictable order. The pull request for this is completed but is dependent on the functionality of another unmerged PR.        

---

2024-05-17 Fri: This week, I fixed three issues with crosslinks. Additionally, I removed the NthNextHmyExt method, which had a bug in its implementation but was not used in the production code.      

---

2024-05-10 Fri: This week I have reviewed the dev branch and investigated issues with the bootnode. I've merged the pprof PR into the dev and created an issue with the dump for further investigation, which seems to be deeply rooted in the libp2p implementation. Additionally, I've been reading about the HotStuff consensus protocol and its rust implementation.    

---

2024-05-03 Fri: This week i implemented unpredictable leader rotation by VRF function. Additionally, i was working with Uladzislau on bootnodes update, they consumed too much resources, we increased limits and added profiling information for future debugging. And i was collaborating with Adam on harmony smart contract development. 

---

2024-04-26 Fri: This week i was working on block proposing code. I provided additional logging, and refactored code, for feature seamless integration 1 second finality. Also, i'm collaborating with Adam on groth16 solidity part, i asked him to help me integrate web3 frameworks with local harmony development.   

---

2024-04-19 Fri: This week, I provided a feature for checking the synchronization state while a node is in the view change process. This prevents the node from possibly getting stuck. Additionally, I published several PRs to improve node logging.   

---

2024-04-12 Fri: This week i provided additional logging for consensus, block proposing and synchronization. Additionally, i created a PR without periodic synchronization calls. This was a drawback for a stuck node to force sync process, but calls for the method may cause consensus loss.

---

2024 Q1 Summary<br>

Protocol Engineering:<br>
During Q1, my primary focus has revolved around leader rotation testing and activation. This involved rigorous testing across various scenarios, including sequential deactivation of internal nodes, fail tolerance, and performance measurements from remote regions. We successfully conducted tests on the devnet and anticipate further activation on the testnet.
In addition to leader rotation, I've also explored a feature that allows skipping keys when they belong to a single address, enhancing recovery by redirecting to another validator instead of attempting keys of an already inactive one individually.
I dedicated effort to resolving issues following HIP-30 activation, particularly concerning coincidences and a significant number of consensus losses.
Furthermore, in my research endeavors, I delved deeper into the Groth16 native EVM implementation. Native implementation requires precompiled contract, which one i've already implemented. Currently it required Solidity wrapper on the low level code, but i faced with total lack of utilities for local development. Groth16 is zero-knowledge, which allows a prover to convince a verifier of the truthfulness of a statement without revealing any additional information about the underlying data.  

---

2024-04-05 Fri: This week, I'm with Diego and Soph investigating the issue with external validator, which not being elected by the consensus. Additionally, i provided several PRs which increase the stability of the network. 

---

2024-03-29 Fri: This week i was working with Ulad and Diego on devnet shard 1 recovering. Additionally, i'm working on the implementation of Groth16 in Solidity, with a specific focus on creating a reproducible working example. 

---

2024-03-22 Fri: This week, i was investigating an issue preventing progress on devnet. I've found that the issue was originally caused by out of space error. We are working with Gheis on a fix. 

---

2024-03-15 Fri: This week, I concentrated on integrating Groth16 into Solidity. I've been working on the decoding and encoding aspects of Solidity contracts to enable calling precompiled functions. Additionally, I've implemented several fixes for the backup functionality.

---

2024-03-08 Fri: This week, i was working on internal functionality for Groth16. I've implemented integration between evm and groth16 library through precompiled contract. 

---

2024-03-01 Fri: This week, I addressed the problem with the backup feature and incorporated new Prometheus logs to monitor the count of signatures.

---

2024-02-23 Fri: This week, we made updates to the devnet by integrating external community validators and updated the testnet with the leader branch. Additionally, I focused on improving view change processes, refactoring code, and implementing additional checks for view change block processing.  

---

2024-02-16 Fri:  This week, I focused on addressing the mainnet downtime issue. I've been working on a feature aimed at preventing the processing of invalid blocks during the view change process. I've submitted multiple pull requests to enhance the view change logic and implemented additional validations. Furthermore, I successfully updated our libp2p dependencies, which was blocking us from updating the Go version.       

---

2024-02-09 Fri: I collaborated with Diego to test network performance. It passed successfully. Additionally, I updated my previous PRs. I've updated libraries, which prevented compilation with new golang versions. And I added additional code for the leader to detect sign power during network downtimes.

---

2024-02-02 Fri: During the first half of the week, I collaborated with Soph and Diego to investigate a devnet hardfork. We successfully identified the root cause and implemented a hotfix, incorporating additional performance improvements. In the second half of the week, I worked with Diego on testing network performance. This involved assessments on both our internal network and external validators located at a distance, ensuring that the new code wouldn't lead to downtimes or performance issues.

---

2024-01-26 Fri: Testing `revert` command functionality found that it can cause panic under certain circumstances, so now we don't try to restore state from the partially valid data, only remove it. It was already tested and merged by Soph. Currently devnet is fully decentrialized, and doesn't contain internal validators, but it still require small improvements like additional logs and fixes for the issues.    

---

2024-01-22 Mon: This week i fixed bugs on devnet with concurrent map access and block insertion. In collaboration with Diego, we successfully launched the devnet with external validators.   

---

2024-01-15 Mon: This week, I fixed the "block exists" issue which no more leads to a node stuck on the devnet. Additionally i am investigating an issue related to a buggy validator state on the mainnet node. 

---

2024-01-08 Mon: This week, i was investigating the issue with balance transferring on devnet with activated rotation. I was collaborating with Diego, finally, we decided to reset devnet. 

---

2024-01-01 Mon: This week, i was investigating the issue with the validator code wrapper while undelegation process. Additionally, i was collaborating with Diego on the leader rotation on the devnet.

---

2023-12-25 Mon: This week we activated external rotation on devnet. Additionally, i started research on SNARKS, advantages/vulnerabilities/implementations, and how it can be integrated into the blockchain.

---

2023-12-18 Mon: This week, I developed a new API method for calculating sigh power without a leader. This feature will become relevant once leader rotation is activated. Furthermore, I addressed an issue related to counting the minimum block count for leader rotation, ensuring smoother functionality. 

---

2023-12-11 Mon: This week, I conducted internal leader rotation testing on the devnet and focused on external rotation. Moreover, I incorporated necessary information into the watchdog system, as external validators do not provide signing power.

---

2023-12-04 Mon: This week, I addressed all the issues discovered by Soph regarding leader rotation. Furthermore, I resolved an issue introduced after the last merge, prevented the code from passing tests, and fixed an infinite loop that could occur during stream synchronization.

---

2023-11-27 Mon: This week, I enhanced epoch chain synchronization and improved the efficiency of test execution. We no longer encounter floating tests, and the test execution time has been significantly reduced. Furthermore, I eliminated outdated code related to block insertion, resulting in lower memory consumption and improved processing speed.

---

2023-11-20 Mon: I investigated an incident that occurred with two nodes in the devnet. Following thorough research, I submitted several pull requests (PRs) to enhance stability and performance. Furthermore, I implemented integration with the ELK Stack (Elasticsearch, Logstash, and Kibana) for local development, facilitating real-time log analysis.

---

2023-11-13 Mon: I addressed an issue occurring during node initialization that was preventing nodes from starting. Additionally, I resolved an issue preventing nodes from passing tests. Furthermore, I investigated an issue with leader rotation, identified by Soph, which was slowing down the epoch change mechanism.

---

2023-11-05 Sun: I conducted testing on leader rotation, addressing various bugs associated with the network stack. Additionally, I am currently investigating an issue concerning duplicated events in the context of block proposing.

