# Weekly Protocol Sync Meeting
`Testing` `Consensus` `Syncing` 

---
## ⏰ Meeting Information
* Date:  2024-04-18

## 📝 Meeting Notes
1. **Testing and Issue Replication on Shard1 Testnet**
    Discussion on testing the Shard1 Testnet to replicate an issue and understanding the lack of conditions in a loop that rejects consensus or status back.
    > 
2. **Consensus Update Issues**
    Exploration of problems related to updating consensus without restarts, particularly during committee changes and view changes, and the reliance on outdated epoch information.
    > 
3. **Epoch Syncing Between Shard1 and Shard0**
    Identifying the problem of epoch syncing between Shard1 and Shard0, and the incorrect use of committee information from an older epoch.
    > 
4. **Potential Solutions for Shard1 Issues**
    Discussion of potential solutions for fixing Shard1 issues, including hard-forking, updating internal voting power, and resetting the database.
    > 
5. **Syncing and Consensus Mode Issues**
    Addressing problems with nodes entering syncing mode and not returning to normal consensus mode, and the lack of checks during view change processes.
    > 
6. **Node Performance and Version Updates**
    Sharing experiences regarding node performance post-upgrade and clarifying the version being used.
    > 
7. **Collaboration and Feedback on Development**
    Encouragement for team members to review pull requests, address issues with Binance, and provide feedback on new single-player demo from Adam.
    > 