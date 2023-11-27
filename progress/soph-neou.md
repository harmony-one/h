2023-11-27 Mon:
I am in active negotiations with five bare metal providers to optimize our server instance pricing. 
Addtionnally, I have proposed options for serving subgraph, and now awaiting feedback from management.

We Addressed two issues on the devnet:
- Restored consensus in s0 by resyncing two validator nodes
- Resolved the processing of the s1 accumulated crosslinks by rotating to a different leader

Reviewed five Protocol PRs [Fix for ShardIDFromKey](https://github.com/harmony-one/harmony/pull/4566), [Fix for last mile block](https://github.com/harmony-one/harmony/pull/4567), [Rollback removes physically block data from db](https://github.com/harmony-one/harmony/pull/4568), [Removed future blocks from blockchain_impl.go](https://github.com/harmony-one/harmony/pull/4569), [ELK Stack for runtime log processing](https://github.com/harmony-one/harmony/pull/4570) and created two OPS PRs [retiring london archival node](https://github.com/harmony-one/elastic-rpc-infra/pull/20), [install teleport client](https://github.com/harmony-one/ansible/pull/87). 

Finally, Protofire completed the testnet s0 blockscout indexing. And there are some challenges ahead. One will be the cross-shard transactions. As it requires customization, this feature will not be included in the initial version

---

2023-11-05 Sun: Explorer service - There have been ongoing discussions regarding the Socialscan explorer initiative, and after much deliberation, we have decided to pause it until next year. Instead, we will focus on R&D work with Protofire on Blockscout, which will be a key focus for Q4. While this work continues, our current mainnet explorer still requires maintenance. To save costs, we have executed a downgrade on the s0 mainnet RDS instance, resulting in savings of $365 per month.

TheGraph service - TheGraph has reached out to us for a grant to support their hosted service. Since they've provided this service for free since June 2022, we are considering having Protofire maintain a dedicated graph node to ensure the continuity of our public dapp service (swap.country). 

Network service - We have initiated work to identify nodes that need to be terminated due to HIP30. The execution of this process is scheduled for the week of November 6. Additionally, I have reviewed and provided comments on Protofire's proposal to take over our snapshot service, which would cost us $2,000 per month, excluding the node infrastructure cost.

HIP30 epoch was successfully implemented on November 2. The multisig address 0xd8194284df879f465ed61dba6fa8300940cacea3 has collected 1.25 million ONE tokens, valued at approximately $17,100 at the current price. As described by Diego earlier, we have identified certain edge cases. Furthermore, several validators are currently competing for election, as they adapt to the new minimum stake requirement, which stands at 7.37 million ONE. The number of active validators has decreased from its peak of 120+ to the current count of 66.

Finally, I have initiated discussions with Huobi and Binance regarding the 0x address format initiative.
