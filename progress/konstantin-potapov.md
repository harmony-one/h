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

