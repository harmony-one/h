2024-03-01 Fri: Spent most of the week looking at the code to try to replicate the issue with the blocked pending delegations, I've developed a couple of theories but nothing conclusive yet. I'll keep looking at it during the weekend as this is an issue of major importance. 

---
2024-02-23 Fri: Ran the devnet externalization test which involved external validator in the process of externalizing devnet and also introducing leader rotation, this concludes the set of tests we wanted to run in devnet.

Also, investigated the issue with the buggy validator, and got a few insights on the unblocked stacking. 

---
2024-02-16 Fri: This week started with a major hurdle: a 26-hour network outage! I organized the validators, and together we coordinated a synchronized restart attempt, achieving 67% voting power. While the initial effort wasn't successful, good news arrived on Monday – the network was back online! However, cross-links still posed a challenge. Teaming up with Soph and Gheis, we identified and fixed the issue, clearing the queue and getting things moving smoothly again.

Now, I've shifted my focus to the leader rotation process. After resetting the devent and applying the latest updates, I'll be reaching out to validators to gauge their interest in participating in the upcoming testing phase. Stay tuned for further updates next week!

---
2024-02-09 Fri: This week, we started by updating the RPC nodes' certificates. I created an automation role and playbook using Ansible to streamline future renewals.

Next, we focused on leader rotation, adding a new node from a different global location to assess latency impacts. We also tested network reliability when a leader node goes offline. The downtime averaged 25 seconds, consistent with our expectations, regardless of the number of BLS keys.

At the week's end, I reset the development network, aligning the leader rotation and externalization epochs to ensure smooth operation. This setup mirrors what we anticipate for the main network. Next week, we plan to engage the validator community in our testing efforts.

---
2024-02-02 Fri: The week began with the observation of a slowdown in block finality on the devnet, where blocks were produced at a rate of 10 seconds. Initially, i suspected that the issue was related to leader rotation, but after an update, the network halted. We discovered that restarting the network multiple times could temporarily resolve the issue. This finding, combined with analysis of the produced logs, led to an investigation together with Soph.

The root cause of the problem was identified as the network operating at a 100% rate, triggering a special code path designed for such scenarios. This path involved old code that had not been executed in any other network scenario because a 100% operation rate was never previously reached. I created a PR to address this issue and deployed it to the devnet, which successfully resolved the problem.

Additionally, towards the end of the week, a minor issue related to the DNS records for the devnet was fixed. This allowed me to proceed with the latest tests concerning leader rotation, such as shutting down the leader and measuring the outage time. 

---

2024-01-26 Fri: This week, we made significant progress in leader rotation. We began by allowing external validators to participate in the rotation on the development network. Initially, this led to block forking and the subsequent failure of nodes. However, after resolving this issue and restarting the development network, we increased the number of external validators. Since then, there have been no instances of node forking, and the network is functioning smoothly as it continues to rotate leaders.

Additionally, we encountered a situation where a leader registered both 'Hoorays' and 'Bingos' for the same block, which warrants further investigation. Towards the end of the week, I implemented a hardfork to enable the development network to operate solely on external nodes. The hardfork was successfully activated, and the chain remained operational. However, a noticeable slowdown in block finality was observed, which is currently under investigation.

I'm also investigating a bug on one of the validators state, nothing to report yet, but I'll update this section once I have more information.

---

2024-01-21 Sun: I came to catch up with the binance tx pool issue that started when I was about to go for PTO and eventually soph took over, also I was looking at our test harness and I'm working towards adding new test to guarantee the from tx hash is set correctly and is not altered after any update.

I'm working with konstantine towards the one second finality, we had to push a few PRs and reset devnet, this week I'll come back to the task of trying to make the whole network external.

---

2024-01-14 Sun: I was off this week.

---
2024-01-7 Sun: This week I kept in the process of debugging a transaction issue related to leader rotation, we replicated the problem in a local environment and began identifying a solution. During this process, we discovered an additional bug concerning block production. This bug could potentially result in the creation of invalid blocks. If a node produces an invalid block, it may cause subsequent nodes to stall, impeding the network's progress. It remains unclear whether this issue is directly connected to the leader rotation mechanism or if it's a consequence of another feature currently being tested on the devnet.

To address these challenges and improve our testing efficiency, I propose the development of multiple devnets. These devnets would allow us to test various features independently, reducing the likelihood of interference between different development activities. The implementation of this system should be straightforward, requiring minimal effort to set up and operate through a few simple commands. This approach will enable us to isolate and resolve issues more efficiently without disrupting the overall workflow.

---
2023-12-30 Sat: I was off during the first half of this week. For the second half, my focus was on transitioning devnet to full external validation, aiming to test leader rotation under more realistic conditions before moving to testnet. However, we encountered a blocker: a bug in the latest development branch is affecting how transactions are executed, which currently prevents us from funding new external validators. We are currenlty looking into the bug.

---
2023-12-23 Sat: The week started with work on the aftermath of the hardfork. Our partners reported an issue with the eth_getTransactionReceipt method. Upon investigation, the root cause was identified, leading to a proposed fix and the opening of a PR to address the issue. After this update, the issue was partially resolved, so another fix was proposed. This involved keeping the original `hmy tx` `from` field but allowing the former eth logic to encode the response.

All our internal RPC nodes were updated, and we worked with partners to assist them with their updates and to clarify any inquiries they had.

There was also an investigation into an issue with Soph, where Binance transactions were not included in the pool. It was found that the issue was related to a throttling mechanism that prevents more than 60 transactions per address. While we can whitelist addresses to allow more transactions, this isn't a feasible solution once we go fully decentralized. This matter was brought up during the protocol meeting.

Finally, I worked with Konstantine on the leader rotation feature. An external validator was deployed to the devnet, and the feature was enabled for external testing. The feature is currently being tested and is showing signs of success.

---
2023-12-17 Sun: I started the week aiding Konstantine with the leader rotation feature aiming to enable external validators to participate in the consensus. We successfully tested the feature on the devnet, and I am working on enabling few external validators to test the feature further.

Additionally, I merged a PR to fix the issue with the eth_getTransactionByHash method. I also reviewed and merged a PR to fix the issue with the eth_getTransactionReceipt method.

Towards the middle of the week, I shifted my focus with helping on the most recent hardfork. I reviewed a PR fixing the issue, engaged in discussions with the team and took preventive measures which we will disclose in the near future.

I executed the upgrade in testnet and mainnet internal nodes and coordinated the upgrade with binance.

---
2023-12-10 Sun: This week, I focused on the protocol aspect of our project. I reopened a previously submitted Pull Request (PR) to address a rate-fix issue. This PR aims to correct a bug identified post-HIP30, where under certain circumstances, some delegators were incorrectly set to a 5% rate instead of the minimum 7%.

Additionally, I opened another PR to resolve an inconsistency in the from field in the transaction method responses. This discrepancy was noted between the hmy_ and eth_ responses.

I also initiated research into achieving 1-second finality. In collaboration with Konstantine, we deployed and tested the leader rotation PR on the devnet. While it's currently operational, further testing with external validators on the devnet is planned to evaluate this feature in a more realistic setup. Preliminary results are promising.

Moreover, I worked alongside Ulad to review a significant PR concerning the refactoring and updating process of the watchdog deployment.

---

2023-12-03 Mon: The week kicked off with me migrating two shard 1 validators to a different cloud provider. This move was driven by the need for better cost efficiency and redundancy. I diligently followed the operational checklist, ensuring that monitoring and alerting systems were in place.

Next, I shifted my attention to assisting Adam in setting up a new node for testing state pruning. I cloned the full database and initiated tests. However, we encountered a syncing issue with the node. I took time to address some linting problems in the pull request and had a discussion with Adam about a potential code loss in one of the files during the merge. He agreed to investigate this further.

Towards the week's end, my focus pivoted to researching an issue with the Ethereum JSON RPC, specifically regarding discrepancies in the 'from' field when using the eth_transaction method. I uncovered the root cause: it's related to the method of hash calculation. Armed with this insight, I plan to propose a fix in the coming week.

---

2023-11-05 Sun: Started the week working on a script that would tell us if we had enough validator voting power with the premiage imported before the account migration epoch start, that was important as that could have brought the shards to a halt if case we didn’t. Was in talks with the validators to make sure they have imported the preimage. 

After the initial account migration, worked with Soph in verifying we had imported the balances correctly and worked on a report that would show the affected address along with their balances before and post epoch HIP30-1  the migration went smoothly and was executed correctly.

After the HIP30 epoch worked in fixing the watchdog and created a PR fixing and edge case identified by Soph where validators with the max-rate set to 5% didn’t get the fee upgrade, the fix will have to be part of a future hardfork.
