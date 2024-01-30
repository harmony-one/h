2024-01-30 Tuesday: Reviewed snapshot fixes and merged PR# 4618 to dev https://github.com/harmony-one/harmony/pull/4618
The last few weeks I have been shifting focus from protocol development to exploring Harmony's other initiatives involving gaming, account abstraction and security. 

Project-G repository created on the 17th (currently private) https://github.com/harmony-one/Project-G tracks the early development efforts for some games being developed to showcase Harmony's technology stack.
 
2024-01-17 Wednesday: Review of decider changes in PR# 4610 https://github.com/harmony-one/harmony/pull/4610

2024-01-09 Tuesday: WIP PR on pruning stale delegation data has been updated reflecting changes into main->dev and fixing missing code/logic in engine_test.go. Notified Diego, this is in his queue now.
https://github.com/harmony-one/harmony/pull/4505
Review of PR# 4602 https://github.com/harmony-one/harmony/pull/4602

---

2024-01-1 Friday: Happy new year! Work on Harmony's Blockchain gaming initiatives have begun. I am currently updating and testing AA code changes from upstream before deployment

---

2023-12-21 Thursday: 
Merge of main -> dev - Concluding my week on-site there was a lot of movement into the harmony/harmony-one main branch to carry out a security and api bug, and some other small fixes. This PR was opened to bring dev into sync and there were a few conflicts needing resolving. https://github.com/harmony-one/harmony/pull/4595 and https://github.com/harmony-one/harmony/pull/4600

Attended weekly developer sync

---

2023-12-15 Friday:  Attended whiteboard discussions on formal verification, smart contract security, coq, blockchain gaming. Had some collaboration with the protocol team on core issues.
Concluded the day with Harmony holiday dinner!

---

2023-12-14 Thursday:
Full review of PR https://github.com/harmony-one/harmony/pull/4588 authored by max mustermann. This PR would undo some of the my logical changes to getTransactionReceipt, recently merged into dev.

---

2023-12-13 Wed:
Arrived on-site in Palo Alto. Throughout the week we brainstormed on potential protocol improvements and blockchain security.

---

2023-12-07 Thursday:

Worked on this PR that made a modification to getReceipt to only return details in harmony format. https://github.com/harmony-one/harmony/pull/4582 (This would eventually be redone by alternative logic on a future PR)

---

2023-12-05 Tue:

Worked to identify an issue where the getTransactionHash endpoint would return an incorrect from address. This was due to an eth trx obj conversion that would strip the shardid and testshard from the transaction. Discovered Diego was also working on the issue earlier that day so we cross-examined our findings, I have another update coming in that fixes the same issue for another endpoint. https://github.com/harmony-one/harmony/pull/4581/files Progress: https://harmonyengineering.atlassian.net/jira/core/projects/HET/board?filter=%22assignee%22%20%3D%20%27712020%3Ac5eee807-1c18-47ac-bcd5-b46588527039%27&groupBy=status&selectedIssue=HET-104

Prune stale delegation - PR#4505/HET-83 is in testing. Working on an issue with engine_test.go incompability due to missing or out of date logic https://harmonyengineering.atlassian.net/jira/core/projects/HET/board?filter=%22assignee%22%20%3D%20%27712020%3Ac5eee807-1c18-47ac-bcd5-b46588527039%27&groupBy=status&selectedIssue=HET-83

Reviewing literature: - LLVM, EVM architecture

---

2023-10-02 Mon: Making progress on bringing some stale prs back to life. https://github.com/harmony-one/harmony/pull/4505 has been opened and replaces https://github.com/harmony-one/harmony/pull/4068. Additional notes on progress can be tracked in the jira ticket here: https://harmonyengineering.atlassian.net/jira/core/projects/HET/board?filter=%22assignee%22%20%3D%20%27712020%3Ac5eee807-1c18-47ac-bcd5-b46588527039%27&selectedIssue=HET-83
There were changes required to core/blockchain_stub.go that may be a new requirement or was left out of previous commits.
There are a few more problems to fix in statedb and then it will need tested with alterations to staking then it should be good to roll into dev for a cycle of tests. 

There were problems with the deployment script when trying to get the entrypoint contract deployed. I have written a solution and hope to have the contract deployed out on mainnet and testnet very soon. This is for the bundler Stackup will operate on the Harmony network (entrypoint address 0x5FF137D4b0FDCD49DcA30c7CF57E578a026d2789 and added to this list https://docs.stackup.sh/docs/entity-addresses)

Protofire has rolled out aa on Harmony and I have been in recent communication with their team tracking developments

Recently investigating logs to find any clues on why crosslink keeps failing on devnet
