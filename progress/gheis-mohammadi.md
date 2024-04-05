**2024-04-06 Saturday:** Last week, we could address the p2p stream discoveries issue and successfully resolved it in the devnet node However, two other issues persist: high storage usage by stream sync and the transition from Syncing mode to Normal mode. After many discussions with the team and thorough code base analysis, we are actively addressing these priorities. Additionally, we continue to prioritize the recovery of devnet shard1, exploring the most efficient approach for its restoration.

**2024-03-30 Saturday:** Last week, we encountered a storage issue where the team identified that the stream cache was consuming excessive storage. I conducted tests on the sync in the local network, and everything appeared to be fine, with storage usage within normal limits. However, we later observed that the stream service kept restarting, and the cleanup process wasn't triggered for unknown reasons. Currently, I am working on a pull request (PR) to address this cleanup issue.

Additionally, we faced problems with p2p stream discoveries as the node couldn't connect to other nodes, which were rejecting it. It seems the node was being blocked by others. We are actively working on resolving this issue as well.

---

**2024-03-15 Friday:** Last week, we encountered a simple configuration issue. All devnet nodes were upgraded to the latest release, and snapshot generation was inadvertently enabled by default, causing several nodes to go down. To address this, I created a pull request and set the Snapshots Limit to zero by default for all networks. This effectively disabled snapshots permanently and resolved the issue.

Subsequently, we encountered another issue where two nodes became stuck due to an increasing view ID, resulting in different block hashes. We investigated this issue and considered two theories: one related to the snapshot root hash and the other to potential root causes within stream sync. Upon investigation, I confirmed that stream sync could not be the issue, as it does not manipulate or increase view IDs. However, there remained a possibility of indirect conflicts with consensus. Our investigation revealed that one node had somehow received the wrong view ID from another node. We temporarily resolved this issue by disabling snapshots and resyncing the affected node using the snapshot database.

Additionally, upgrading ETHdb is another ongoing task, which is nearly complete. This involves adding a few thousand new lines of code, necessitating thorough and precise testing.

---

**2024-03-09 Sat:** Last week, I continued working on upgrading the database layer. It will involve significant changes and will require extensive testing. I have already resolved 90% of the upgrade issues and am aiming to finalize the code by the end of next week

---

**2024-03-02 Sat:** Last week, I started refactoring snapshot database. This would fix a couple of issues on old versions of database

---

**2024-02-24 Sat:** Last week, I resumed working on the snapshot database. I completed several tests and thoroughly examined the codes of ethdb. During this process, I identified an issue with the validator wrapper code prefix that could potentially lead to failures in snapshot creation. I promptly addressed this by adding the new prefix and proceeded to conduct additional tests on the mainnet database. These tests have been ongoing for the past 40 hours, and we are currently awaiting the results. If successful, this update would mark a significant advancement in snapshot creation.

---

**2024-02-16 Sat:** My main focus of this week was on the unexpected Mainnet Shard 0 outage and Crosslink stuck. We had several meetings, calls, and discussions during both the weekend and weekdays. After extensive team collaboration and testing, I created several PRs to address the crosslink issues [#4629](https://github.com/harmony-one/harmony/pull/4629) , [#4630](https://github.com/harmony-one/harmony/pull/4630) and delete pending crosslinks [this commit](https://github.com/harmony-one/harmony/commit/d0261f8ef5360e05ee964b034afd83b10de34615). Through collaborative efforts and rigorous code review, we successfully resolved the issue.

Additionally, I conducted several code reviews and provided comments on other PRs that addressed race conditions.

Another challenge we faced was a devnet stuck on Shard 0. I investigated this issue as well. After thorough investigation, we discovered that it may be related to some new configurations for snapshots. The team assisted in adding these new configurations to all nodes and subsequently disabled them.

---

**2024-02-10 Sat:** Last week, I focused on fixing snapshot DB creation. I refactored the snapshot codes, addressed several race conditions, and made some improvements to the code. Later, I tested snapshot creation again on the mainnet DB, which had a size of 32TB. It took around 42 hours to complete, and no errors were reported during generation. However, the issue arose afterward when the node became stuck and couldn't continue syncing. We attempted to identify the problem and tested several possible scenarios. We are still working on resolving this issue, and once it is fixed, we can proceed with the final pruning test.

---

**2024-02-02 Sat:** Last week, I focused on the state pruning feature. During this time, I addressed a few issues, successfully fixed them, and rebased the branch, which is now ready for merge. To test the pruning functionality, I performed tests on the devnet. However, the database size did not significantly decrease due to the recent devnet restart, resulting in a lack of transactions. Consequently, there were not many intermediary states to remove.

For a more comprehensive test, I conducted state pruning on the test-net database. Here are the results for shard 0:

Before: 26,758,097,053 bytes
After: 26,734,477,304 bytes
Difference: 23,619,749 bytes

The pruning operation reduced the size by approximately 23MB (out of 25 GB), albeit a modest reduction. The limited decrease is attributed to the test-net database also lacking a substantial number of intermediary states. To overcome this, the devops team assisted in deploying a main net node, and I commenced testing pruning on the main net. Results for this test will be shared once the testing is complete.

Additionally, I addressed a user-reported issue regarding transaction sending. Upon investigation, we identified a logic flaw in the allowed list, allowing multiple entries for the same "from" address. The current code only retains the latest entry, disregarding the previous ones. To rectify this, I submitted a pull request that resolves the issue by establishing a map of allowed transactions to an array of transaction data, rather than a map of "from" to a single transaction data.

---

**2024-01-26 Friday:** We encountered an issue that could lead to panic errors on devnet nodes due to a null snapshot. This problem was triggered by fast sync tests in StreamNet and was affecting the decoupled nodes. I addressed this issue on the P2P client side by validating the snapshot creation result.

Subsequently, I resolved the snapshot creation issue, which was a blocker for state pruning as well. The snapshot creation was broken because of an incorrect root hash. The PR addresses that issue and also adds a new section in the configuration file for cache settings. It moves old cache settings under this new section as well. All the changes have been tested successfully and are ready to review and merge by team.

Once these two PRs are merged to the dev branch, the devnet nodes will be able to create or load a snapshot db once they get restarted. I will continue my tests to complete the last step of sync development.


---

**2024-01-21 Sun:** I were actively working on fixes and addressing several issues. After the devnet nodes were upgraded, all the new stream functions were added to the nodes as well. The devnet went down due to enabling the stream server on the main devnet nodes, and they were involved in sync tests. Due to the non-existence of a snapshot, this led to crashes. I created a PR to address this issue.

I also worked on improving logs to investigate a case of stuck transactions on one of the clients node. I added a couple of logs and pushed them to the latest log branch. Later, these logs helped identify the issue, and the team created a PR to address it.

Additionally, I fixed another issue in the devnet. The stakedVoteWeight structure didn't support concurrent read and write, which could break the main process if an RPC triggered any write or read from it. I created a PR to address this issue by adding a mutex to make it thread-safe. However, this PR was later closed due to overlap, as we had already implemented thread-safe measures in another PR for consensus and quorum.

---

**2024-01-15 Mon:** We encountered an issue with the devnet as shard 0 experienced downtime. We conducted an investigation to identify and resolve the problem. Several nodes were stuck while attempting to read shard state. To address this, we implemented a few changes, and ultimately, the team restarted the devnet. Another issue arose concerning one of the RPC nodes dedicated to the Harmony client. Transactions were getting stuck on this node, and the leader node did not receive the first transaction. To investigate further, I created a new branch from the main codebase and added additional logs to track transactions entering the transaction pool and being broadcasted. We are currently working on reproducing the issue to utilize the logs for debugging. Additionally, there was an issue with legacy sync related to known existing blocks. As a quick fix, I submitted a pull request that allows the syncing process to continue for known blocks instead of triggering an error. I have also been ongoing with the testing of state sync to explore and address the stream reset issue that occurs during the process of obtaining account ranges.

---

**2024-01-08 Mon:** Last week, I continued testing and addressing issues related to state sync. One of the problems involved a potential syncing process disruption due to receiving nil accounts, which has been fixed, and the code has been pushed. Another issue surfaced during the transition to the new sync mode, added to the last stage of state sync. Currently, the primary challenge is the error "stream removed when doing request," which occurs when the node attempts to retrieve a range of accounts. I dedicated several hours to investigating this issue, examining the peer manager and exploring all possible scenarios that could remove a peer outside the sync loop. Unfortunately, the issue remains unresolved. My current focus is to prioritize fixing this problem. It appears that all nodes on the devnet might need to undergo an upgrade to incorporate new changes in stream sync. Successfully addressing this issue marks a significant milestone towards achieving a full state sync, allowing me to finalize the codes.

---

**2024-01-01 Mon:** My primary focus was on testing the latest fast sync PR (#4594). To check the transition from fast sync to full sync, I adjusted the pivot closer to the genesis. This modification enabled a quicker assessment of the functionality within a shorter timeframe. Additionally, I addressed the local net sync issue and resolved issues related to known blocks and double block insertion. As part of the debug process, I refactored the downloader to return the count of tasks, eliminating the need for individual length checks. Testing will continue into the next week.

---

**2023-12-25 Mon:** Last week, I primarily focused on a new pull request (PR #4594) that completes the fast sync pull request (PR #4465). This integration involves merging the full state sync stage into stream sync while adjusting parameters for fast sync. The PR enhances the fast sync code and addresses several fast sync issues. Currently drafted, it will be merged once fully tested.

Additionally, I submitted a new PR to enhance the validator code wrapper. This update enables automatic detection of the validator account. Originally intended as a hotfix for the main branch, I later switched it to the development branch as an improvement.

---

**2023-12-18 Mon:** I refactored the state sync request cap in the full state sync stage and also implemented additional error handling. I refactored the process of requesting states into five steps, and the corresponding code has been added to PR 4465. Subsequently, I rebased this PR with the dev branch, encountering over 60 conflicts. Some required codes were altered or removed by other PRs, and I reinstated them, resolving all conflicts, which took a couple of hours. Although PR 4465 requires further improvements and a full cycle of tests, we merged it with dev to address the potential rebase conflicts. Tests and optimizations will be addressed in a separate PR.

I identified an issue with validator wrappers. Harmony's rawdb employs distinct prefixes for validator wrapper code and contract code. The current code initializes a validator wrapper and attempts to fetch it from the database without using the appropriate prefix. It initializes the validator wrapper without the prefix, but for updating the validator wrapper, it sets the isValidatorWrapper flag to true, causing it to write the code with the prefix. In response, I created PR 4587, which resolves this issue by eliminating the flag and introducing automatic detection for validator code using the IsValidator function. The modified code checks whether it is for a validator, and based on that, it attempts to retrieve or write the code accordingly. BTW, Further discussion and investigation proved that this issue doesn't have any impact on node performance , So, later as an improvement I sent its PR to dev branch. 

---

**2023-12-11 Mon:** I have successfully implemented the functionalities to request account ranges, storages, byte codes, and to heal trie nodes and byte codes. The downloader is now complete for all these functions. Additionally, I have added the necessary code to handle the results of each request, including functions to manage errors and failed requests, queuing those that failed for later retries.

Moving forward, in the staged state sync, I integrated the downloader and added the relevant code to utilize its functions. As I wrap up this integration, my next steps involve optimizing request sizes and making a few adjustments to P2P communications. This phase would be the final piece of the state sync implementation.

---

**2023-11-04 Mon:** on leave for a week

---
**2023-11-27 Mon:** My main focus was on state sync. I needed to refactor the state sync stage to a full version, as it was previously a snap sync version. Switching to the full version required refactoring the state sync downloader. This involved making changes to the stream P2P client and adding a new function in the adapter. I completed this part and am currently working on the state downloader itself. The state downloader comprises five different steps, each involving the addition of new functions:
1- accounts by ranges
2- storages by ranges
3- bytecodes
4- healing trie nodes
5- healing byte codes
I started by addressing account ranges and added the necessary functions for the subsequent steps.

Also, We encountered an issue with block insertion during legacy sync. In the legacy sync process, attempting to insert a block that already exists leads to a complete break in the sync process. To address this issue, I created a pull request that adds an exception for known blocks.

--- 

**2023-10-28 Sat:** Since last Wednesday, I have been on call, and fortunately, it has been quiet with no major issues.

I completed the tests for my latest PR, #4540, and finalized the code. The team reviewed it, and it has been merged into the dev branch.

Currently, I am working on refactoring the state sync stage to enable the synchronization of all states. This is essential for the node to regenerate Tries. The existing code only syncs the latest leaves of the trie. This part is more complex than the previous implementation, as it requires using the snapshot feature, which we haven't implemented yet. I'm exploring alternative methods that don't rely on snapshots. If these methods do not prove effective, we'll need to prioritize the development of the instant snapshot feature.
