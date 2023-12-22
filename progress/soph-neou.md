**2023-12-25 Mon** (edited Friday Dec 22 as I will be OOO Dec 23 to Jan 7):

Jumped into action during my holiday to contribute to resolving the Staking Logic Vulnerability Incident. The Mainnet Hard Fork v2023.3.0 took place on Sunday, the 17th, with exceptional assistance from the validator community. However, a transaction hash bug surfaced as we tried to conceal the fix, leading us to release v2023.4.2 and support various partners, including thegraph, layerzero, chainstack, synapse, and SimplyVC.

Simultaneously, Binance.com encountered issues, leading to the suspension of withdrawals due to a surge in transactions hitting the 64-transaction limit per account in the pending transaction pool. We collaborated to analyze and resolve the problem, and withdrawals resumed on 12-22-2023 at 01:29 UTC, following an outage that began on 12/19/2023, 21:47 UTC.

Additionally, I received reports of five more drained wallets related to the use of Harmony's deprecated extension. One of them belongs to a validator who still has a portion of their funds staked. I assisted him in running a custom script to programmatically transfer the undelegated funds.

---
**2023-12-11 Mon** (edited Friday Dec 8 as I will be OOO Dec 11 to Dec 18):

November cloud costs are down to $12.88k from $14.91k. The decrease in costs is a result of various measures undertaken by the devops team, including cleaning up the S3 storage space, terminating, downgrading, and migrating instances (RDS/EC2) to other cloud providers, and optimizing our mainnet node architecture.

There's been a recent surge in victims of drained wallets, with many cases pointing to stolen funds landing in the KuCoin hot wallet. Some confusion arose due to the use of this address as an example by a Harmony dev on Discord. Let's note that victims were using the deprecated Harmony wallet extension and hadn't created new accounts, as suggested in [this article published in 2022](https://harmonyone.notion.site/Wallet-Security-and-Your-Assets-665171c3857a4510abedc44f3b929bd1) I recommend another round of communication/tweets to encourage users to migrate to a new wallet at their earliest convenience.

I've initiated the investigation and implementation of leader metric export. While a demo was built, the data received proved inconsistent. A proposed solution is to focus on the last voting power instead of the constantly changing ongoing vote power during the vote collection.

Additionally, I've reviewed and commented on multiple PRs, including [the automation of watchdog installation](https://github.com/harmony-one/ansible/pull/90), a fix for the [ETH JSON method source address issue](https://github.com/harmony-one/harmony/pull/4575). I also provided guidance to the team for the leader rotation hardfork.

Finally, I investigated the shard 1 signature loss reported by the validator community, tracing it back to the migration of our s1 leader node from Latitude. A workaround to swap the bls keys was suggested and doing further test with VPS could be beneficial as we move towards leader rotation to identify the correct VPS specs

---
**2023-12-4 Mon**:
Management has approved a 1-year long-term contract for essential Harmony Base services, such as the archival node, aimed at cost savings. The November cloud cost report is pending finalization, awaiting GCP invoices.

0% internal voting power discussions started on our social and internally, Validators are showing enthusiasm to embrace this challenge. Validator community will be engaged for testing in testnet. The hardfork is targeted for 1Q, and two technical challenges are in focus: 1) leader rotation with external validators and 2) leader consensus metrics (the proposed solution involves sending metrics to our Prometheus push gateway)

One famous exchange partner received funds via a multisig transaction and have expressed the need for a more robust explorer. It faced challenges with the internal transaction tab lacking the necessary data for confirmation. A temporary manual and empirical process has been communicated to address this concern. Improving our explorer is imperative.

Protofire is actively working on migrating their testnet blockscout local environment to a more robust one. It's essential to note that Protofire allocates approximately 0.5 Full-Time Equivalent (FTE) per month for projects like Safe, Swap, Compound, and Blockscout. Currently, Blockscout has the lowest priority in this allocation.
 
---
**2023-11-27 Mon**:
I am in active negotiations with five bare metal providers to optimize our server instance pricing. 
Addtionnally, I have proposed options for serving subgraph, and now awaiting feedback from management.

We addressed two issues on the devnet: 1. restored consensus in s0 by resyncing two validator nodes; 2. resolved the processing of the s1 accumulated crosslinks by rotating to a different leader.

Reviewed five Protocol PRs [Fix for ShardIDFromKey](https://github.com/harmony-one/harmony/pull/4566), [Fix for last mile block](https://github.com/harmony-one/harmony/pull/4567), [Rollback removes physically block data from db](https://github.com/harmony-one/harmony/pull/4568), [Removed future blocks from blockchain_impl.go](https://github.com/harmony-one/harmony/pull/4569), [ELK Stack for runtime log processing](https://github.com/harmony-one/harmony/pull/4570) and created two OPS PRs [retiring london archival node](https://github.com/harmony-one/elastic-rpc-infra/pull/20), [install teleport client](https://github.com/harmony-one/ansible/pull/87). 

Finally, Protofire completed the testnet s0 blockscout indexing. And there are some challenges ahead. One will be the cross-shard transactions. As it requires customization, this feature will not be included in the initial version.

---

**2023-11-05 Sun**: Explorer service - There have been ongoing discussions regarding the Socialscan explorer initiative, and after much deliberation, we have decided to pause it until next year. Instead, we will focus on R&D work with Protofire on Blockscout, which will be a key focus for Q4. While this work continues, our current mainnet explorer still requires maintenance. To save costs, we have executed a downgrade on the s0 mainnet RDS instance, resulting in savings of $365 per month.

TheGraph service - TheGraph has reached out to us for a grant to support their hosted service. Since they've provided this service for free since June 2022, we are considering having Protofire maintain a dedicated graph node to ensure the continuity of our public dapp service (swap.country). 

Network service - We have initiated work to identify nodes that need to be terminated due to HIP30. The execution of this process is scheduled for the week of November 6. Additionally, I have reviewed and provided comments on Protofire's proposal to take over our snapshot service, which would cost us $2,000 per month, excluding the node infrastructure cost.

HIP30 epoch was successfully implemented on November 2. The multisig address 0xd8194284df879f465ed61dba6fa8300940cacea3 has collected 1.25 million ONE tokens, valued at approximately $17,100 at the current price. As described by Diego earlier, we have identified certain edge cases. Furthermore, several validators are currently competing for election, as they adapt to the new minimum stake requirement, which stands at 7.37 million ONE. The number of active validators has decreased from its peak of 120+ to the current count of 66.

Finally, I have initiated discussions with Huobi and Binance regarding the 0x address format initiative.
