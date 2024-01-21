2024-01-21 Sun: I were actively working on fixes and addressing several issues. After the devnet nodes were upgraded, all the new stream functions were added to the nodes as well. The devnet went down due to enabling the stream server on the main devnet nodes, and they were involved in sync tests. Due to the non-existence of a snapshot, this led to crashes. I created a PR to address this issue.

I also worked on improving logs to investigate a case of stuck transactions on one of the clients node. I added a couple of logs and pushed them to the latest log branch. Later, these logs helped identify the issue, and the team created a PR to address it.

Additionally, I fixed another issue in the devnet. The stakedVoteWeight structure didn't support concurrent read and write, which could break the main process if an RPC triggered any write or read from it. I created a PR to address this issue by adding a mutex to make it thread-safe. However, this PR was later closed due to overlap, as we had already implemented thread-safe measures in another PR for consensus and quorum.

---

2024-01-15 Mon: We encountered an issue with the devnet as shard 0 experienced downtime. We conducted an investigation to identify and resolve the problem. Several nodes were stuck while attempting to read shard state. To address this, we implemented a few changes, and ultimately, the team restarted the devnet. Another issue arose concerning one of the RPC nodes dedicated to the Harmony client. Transactions were getting stuck on this node, and the leader node did not receive the first transaction. To investigate further, I created a new branch from the main codebase and added additional logs to track transactions entering the transaction pool and being broadcasted. We are currently working on reproducing the issue to utilize the logs for debugging. Additionally, there was an issue with legacy sync related to known existing blocks. As a quick fix, I submitted a pull request that allows the syncing process to continue for known blocks instead of triggering an error. I have also been ongoing with the testing of state sync to explore and address the stream reset issue that occurs during the process of obtaining account ranges.

---

2024-01-08 Mon: Last week, I continued testing and addressing issues related to state sync. One of the problems involved a potential syncing process disruption due to receiving nil accounts, which has been fixed, and the code has been pushed. Another issue surfaced during the transition to the new sync mode, added to the last stage of state sync. Currently, the primary challenge is the error "stream removed when doing request," which occurs when the node attempts to retrieve a range of accounts. I dedicated several hours to investigating this issue, examining the peer manager and exploring all possible scenarios that could remove a peer outside the sync loop. Unfortunately, the issue remains unresolved. My current focus is to prioritize fixing this problem. It appears that all nodes on the devnet might need to undergo an upgrade to incorporate new changes in stream sync. Successfully addressing this issue marks a significant milestone towards achieving a full state sync, allowing me to finalize the codes.

---

2024-01-01 Mon: My primary focus was on testing the latest fast sync PR (#4594). To check the transition from fast sync to full sync, I adjusted the pivot closer to the genesis. This modification enabled a quicker assessment of the functionality within a shorter timeframe. Additionally, I addressed the local net sync issue and resolved issues related to known blocks and double block insertion. As part of the debug process, I refactored the downloader to return the count of tasks, eliminating the need for individual length checks. Testing will continue into the next week.

---

2023-12-25 Mon: Last week, I primarily focused on a new pull request (PR #4594) that completes the fast sync pull request (PR #4465). This integration involves merging the full state sync stage into stream sync while adjusting parameters for fast sync. The PR enhances the fast sync code and addresses several fast sync issues. Currently drafted, it will be merged once fully tested.

Additionally, I submitted a new PR to enhance the validator code wrapper. This update enables automatic detection of the validator account. Originally intended as a hotfix for the main branch, I later switched it to the development branch as an improvement.

---

2023-12-18 Mon: I refactored the state sync request cap in the full state sync stage and also implemented additional error handling. I refactored the process of requesting states into five steps, and the corresponding code has been added to PR 4465. Subsequently, I rebased this PR with the dev branch, encountering over 60 conflicts. Some required codes were altered or removed by other PRs, and I reinstated them, resolving all conflicts, which took a couple of hours. Although PR 4465 requires further improvements and a full cycle of tests, we merged it with dev to address the potential rebase conflicts. Tests and optimizations will be addressed in a separate PR.

I identified an issue with validator wrappers. Harmony's rawdb employs distinct prefixes for validator wrapper code and contract code. The current code initializes a validator wrapper and attempts to fetch it from the database without using the appropriate prefix. It initializes the validator wrapper without the prefix, but for updating the validator wrapper, it sets the isValidatorWrapper flag to true, causing it to write the code with the prefix. In response, I created PR 4587, which resolves this issue by eliminating the flag and introducing automatic detection for validator code using the IsValidator function. The modified code checks whether it is for a validator, and based on that, it attempts to retrieve or write the code accordingly. BTW, Further discussion and investigation proved that this issue doesn't have any impact on node performance , So, later as an improvement I sent its PR to dev branch. 

---

2023-12-11 Mon: I have successfully implemented the functionalities to request account ranges, storages, byte codes, and to heal trie nodes and byte codes. The downloader is now complete for all these functions. Additionally, I have added the necessary code to handle the results of each request, including functions to manage errors and failed requests, queuing those that failed for later retries.

Moving forward, in the staged state sync, I integrated the downloader and added the relevant code to utilize its functions. As I wrap up this integration, my next steps involve optimizing request sizes and making a few adjustments to P2P communications. This phase would be the final piece of the state sync implementation.

---

2023-11-04 Mon: on leave for a week

---
2023-11-27 Mon: My main focus was on state sync. I needed to refactor the state sync stage to a full version, as it was previously a snap sync version. Switching to the full version required refactoring the state sync downloader. This involved making changes to the stream P2P client and adding a new function in the adapter. I completed this part and am currently working on the state downloader itself. The state downloader comprises five different steps, each involving the addition of new functions:
1- accounts by ranges
2- storages by ranges
3- bytecodes
4- healing trie nodes
5- healing byte codes
I started by addressing account ranges and added the necessary functions for the subsequent steps.

Also, We encountered an issue with block insertion during legacy sync. In the legacy sync process, attempting to insert a block that already exists leads to a complete break in the sync process. To address this issue, I created a pull request that adds an exception for known blocks.

--- 

2023-10-28 Sat: Since last Wednesday, I have been on call, and fortunately, it has been quiet with no major issues.

I completed the tests for my latest PR, #4540, and finalized the code. The team reviewed it, and it has been merged into the dev branch.

Currently, I am working on refactoring the state sync stage to enable the synchronization of all states. This is essential for the node to regenerate Tries. The existing code only syncs the latest leaves of the trie. This part is more complex than the previous implementation, as it requires using the snapshot feature, which we haven't implemented yet. I'm exploring alternative methods that don't rely on snapshots. If these methods do not prove effective, we'll need to prioritize the development of the instant snapshot feature.
