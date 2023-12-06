2023-12-04 Mon: 

---

2023-11-27 Mon: on leave for a week

---
2023-11-20 Mon: My main focus was on state sync. I needed to refactor the state sync stage to a full version, as it was previously a snap sync version. Switching to the full version required refactoring the state sync downloader. This involved making changes to the stream P2P client and adding a new function in the adapter. I completed this part and am currently working on the state downloader itself. The state downloader comprises five different steps, each involving the addition of new functions:
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
