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
