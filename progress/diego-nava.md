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
