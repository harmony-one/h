2024-05-03 Fri: This week, i implemented unpredictable leader rotation by VRF function. Additionally, i was working with Uladzislau on bootnodes update, they consumed too much resources, we increased limits and added profiling information for future debugging.

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

