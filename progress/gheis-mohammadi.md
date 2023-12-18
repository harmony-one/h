2023-12-18 Mon: I refactored the state sync request cap in the full state sync stage and also implemented additional error handling. I refactored the process of requesting states into five steps, and the corresponding code has been added to PR 4465. Subsequently, I rebased this PR with the dev branch, encountering over 60 conflicts. Some required codes were altered or removed by other PRs, and I reinstated them, resolving all conflicts, which took a couple of hours. Although PR 4465 requires further improvements and a full cycle of tests, we merged it with dev to address the potential rebase conflicts. Tests and optimizations will be addressed in a separate PR.

A critical issue arose with undelegation on the mainnet, prompting us to prioritize it. Additionally, I identified an issue with validator wrappers. Harmony's rawdb employs distinct prefixes for validator wrapper code and contract code. The current code initializes a validator wrapper and attempts to fetch it from the database without using the appropriate prefix. It initializes the validator wrapper without the prefix, but for updating the validator wrapper, it sets the isValidatorWrapper flag to true, causing it to write the code with the prefix. In response, I created PR 4587, which resolves this issue by eliminating the flag and introducing automatic detection for validator code using the IsValidator function. The modified code checks whether it is for a validator, and based on that, it attempts to retrieve or write the code accordingly. BTW, Further discussion and investigation proved that this issue wasn't related to undelegation issue. Later We fixed the undelegation by refactoring the validator fee calculations.

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
