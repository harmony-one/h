**Q2 devops and service roadmap**

In the upcoming quarter, our DevOps roadmap prioritizes three key initiatives aimed at enhancing the efficiency and reliability of our infrastructure. Foremost, we will focus on implementing the Blockscout Explorer for the Harmony Mainnet. This initiative aims to provide users with an intuitive interface to explore on-chain data comprehensively. By integrating Blockscout, we anticipate improved transparency and accessibility within our ecosystem, ultimately empowering users with better insights and decision-making capabilities.

Simultaneously, we are committed to implementing rate limits on Harmony RPCs to optimize performance and ensure service reliability. By regulating incoming traffic, this initiative aims to prevent overload and maintain the responsiveness of our RPC infrastructure. By proactively managing traffic flow, we anticipate enhancing the overall user experience for developers and validators, aligning with our goal of delivering seamless and efficient services. Additionally, we are preparing for the imminent replacement of RPC nodes facing disk full issues, prioritizing the stability and availability of our RPC services. Through these initiatives, we aim to uphold our commitment to providing a robust and dependable platform for our community.

---
**2024-4-26: Weekly update**

This week, I've been diving deep into some critical tasks. First off, I've been helping test and review the latest feature addition to the Blockscout explorer currently being deeloped by Protofire, focusing on cross-shard and shard 1 support.

Additionally, I've been heavily involved in resolving the shard 1 consensus loss issue. After successfully replicating the problem and testing a fix in the localnet, I've outlined the steps for resolution. This includes creating a hard fork to reinstate internal node voting power, reverting the shard 1 last block, and allowing shard 1 to propose and add a new block with the latest shard state. However, while tackling this issue, I encountered some new challenges. Firstly and originally the devnet went down with internal nodes losing their voting power, requiring me to shift focus to the external nodes' current voting power. Furthermore, despite the leader being able to add the new last block, the final commit isn't being received by other nodes in the network. Unfortunately, attempts to restore consensus through block download via syncing have been unsuccessful, as we're currently encountering block nil errors. 

In addition to these tasks, I've also been assisting Gheis with testing PR 4660 for a Travis CI bug. We identified that the issue stems from the latest commit using short-range sync instead of long-range sync, causing localnet to stop producing block. We're currently investigating why the consensus mode switches to sync when short-range sync is used in a new network.

---
**2024-4-19: Weekly update**

AWay 3 days from Mon to Wed. In the last two days, I continued the investigation into the Harmony code base in order to address the consensus issue affecting shard 1 on the testnet and devnet.

---
**2024-4-12: Weekly update**

Throughout the week, my focus has been on addressing the critical issue of the shard 1 testnet/devnet no committee problem, which resulted in a network without consensus. My goal has been to identify a solution to prevent this issue from recurring and to mitigate potential risks on the mainnet. While I was able to replicate the issue in localnet by Friday, finding a definitive fix remains uncertain. The challenge lies in shard 1 using the last epoch committee when it becomes stuck, rather than the latest committee. I've identified the root cause as the shard 1 crosslink not being sent or processed by shard 0. As a long-term solution applicable to the mainnet, we're exploring options to ensure that validators are not excluded from the new committee when their signature performance metrics are not being updated, resulting in having 0 "signed" out of 0 "to sign".

---
**2024-4-5 Fri: Weekly update**

During the week, we encountered issues with Shard 0 devnet, where the consensus went down twice. However, a simple restart of the cluster effectively resolved the problem on both occasions. Upon conducting a root cause analysis, I identified that a validator had mistakenly switched its consensus mode to "syncing" preventing its participation in the consensus process. Further analysis is still pending.

Shard 1 testnet and devnet are currently experiencing downtime, posing a significant challenge for HIP32. The issue, outlined in detail in [https://github.com/harmony-one/harmony/issues/4651](https://github.com/harmony-one/harmony/issues/4651), revolves around the handling of crosslinks within our consensus protocol.

In response to the security vulnerability CVE-2024-3094, I diligently conducted a comprehensive security check on all Harmony nodes and explorer backends. I'm pleased to confirm that none of our systems were running the vulnerable version, ensuring the security and integrity of our infrastructure.

Furthermore, I meticulously tested and reviewed the [isbackup PR fix](https://github.com/harmony-one/harmony/pull/4644), confirming the correct operation and readiness for merging. However, I recommended the removal of BINGO messages from the logs to prevent confusion for node operators.

Lastly, I provided comprehensive assistance to joskins, offering technical guidance and addressing issues related to contract deployment using Remix for an upcoming token pre-sale. 

---
**Q1 Impact and Performance Summary**:

Throughout Q1, I've played a pivotal role in addressing technical challenges and advancing key initiatives within our project. Notably, I collaborated with team members on resolving issues such as testnet leader rotation activation hurdles and enhancing our mainnet oracle integration with Band. Moreover, my efforts in troubleshooting and providing support for various development tasks, including HIP30 state verification failures and devnet consensus loss investigations, have contributed to the overall progress and stability of our ecosystem.

In addition to technical contributions, I actively participated in community engagement and internal operations improvements. I facilitated the progress of HIP32 through validator coordination, while also enhancing our internal operations and security through the development and updating of multiple playbooks. Furthermore, my involvement in addressing user-reported issues and providing support to exchange partners underscores my commitment to ensuring a seamless experience for all stakeholders.

Detailing more the DevOps area, in the first quarter, I spearheaded several initiatives aimed at enhancing our technical capabilities, optimizing processes, and fortifying our security posture. I automated the renewal of SSL certificates for non .country domains name linked to harmony.one subdomains, empowering our DevOps team to efficiently manage certificate renewals. Additionally, I took the lead in updating our internal operations playbook for Goteleport, significantly reducing manual interventions required for adding, updating, or installing new teleport nodes. Moreover, I developed a 'bad-delegation' script to detect addresses that received an excessive amount of ONE, ensuring the integrity of our network and implementing processes to swiftly address any issues encountered. These initiatives underscore my commitment to leveraging technology and process improvements to drive efficiency and enhance our overall operational resilience.

Additionnaly, the devops team has made significant strides in advancing our technical capabilities and improving operational efficiency. Under my guidance and supervision, Ulad executed several key initiatives, including the establishment of two snapshot nodes for shard 0 and shard 1 in the testnet, which have already been embraced by users. We also focused on optimizing system performance by updating the Push-gateway runbook and creating RPC/nginx runbooks to streamline the process of updating our RPC. Additionally, we developed scripts to detect backup nodes in preparation for HIP32. These efforts align with our overarching objective of maintaining a secure, efficient, and resilient technical infrastructure.

---
**2024-3-29 Fri**:

This week kicked off with Amanda and me diving into the intricacies of updating billing information on mission control. In addition to that, I lent a hand to community users grappling with blacklist address and wallet issues.

Unfortunately, our testnet leader rotation activation hit a snag. While Shard 0 smoothly integrated the new feature, Shard 1 encountered a hitch. A stuck crosslink resulted in lost consensus, leaving Shard 1 without both internal and external validators. In collaboration with Diego, we explored a potential solution, considering another hard fork to temporarily reinstate the internal validator.

On a brighter note, Band's recent update to their [network blockchain page](https://docs.bandchain.org/develop/supported-blockchains/) now includes our mainnet standard reference price address, enhancing the legitimacy of our mainnet oracle integration with Band.

---
**2024-3-22 Fri**:

Throughout the week, I provided support for band/QiDAO and conducted checks for stuck blocks in devnet s1, while also assisting with investigations into validator s1 signature loss. Additionally, I troubleshooted issues related to Buggy validator state #4605 and pending undelegation not released with inactive validator #4632, uncovering corner cases with HIP30 that caused state verification failures. Towards the end of the week, I investigated shard 1 devnet consensus loss and identified a block verification failure at the prepare phase of block 1140307. 

---
**2024-3-15 Fri**:

I've been quite busy this week! First off, I've kept in touch with validators to ensure the progress of HIP32, which is currently approved and awaiting the final decision on March 19th, check out the latest update the [HIP32 Vote dashboard] (https://vstats.fortune-validator.pro/proposals/0x2c862da1cc9036a13d0505cba3aeb44f99ae5b7b7c1ef011aa147f73be9022f0) thanks to David Fortune

Furthermore, I troubleshooted devnet node problem concerning streamsync, alongside Gheis. It emerged that the faulty node had an incorrect viewID, leading to a divergence in hash values and subsequently causing a local node fork. Upon initial investigation, it was suggested that the snapshot feature might be updating the viewID, or that a node with a DB containing incorrect information was used for syncing.

On another front, I worked with Artem on testing a new endpoint that enables us to query the details of an HRC20 transaction (check out: [HRC20 Transaction Detail](http://api1.explorer.t.hmny.io:3001/?query=getERC20TransferInfo%200%200xdce285759c3d3a1e6b66b57f064cc6b9399e5eb744ccb2b96414b3ff1ab1bd94)). We've been investigating a bug related to the circulation supply of depegged assets. Unfortunately, we won't be able to fix it until the mainnet blockscout is available.

Lastly, I've been enhancing our internal operations and security by writing and updating multiple playbooks. You can find the latest changes and improvements in the following pull requests: [#139](https://github.com/harmony-one/ansible/pull/139), [#138](https://github.com/harmony-one/ansible/pull/138), [#137](https://github.com/harmony-one/ansible/pull/137), [#136](https://github.com/harmony-one/ansible/pull/136)

---
**2024-3-8 Fri**:

This week, we released v2024.4.0 to facilitate testing without activating the HIP32 leader rotation. This decision aims to reduce potential errors and streamline troubleshooting processes if any issues arise.

Snapshot voting for HIP32 is underway, with unanimous support thus far. However, we still need another 883M ONE votes to reach the required 51% total stake for the vote to be valid. You can track the progress here: [Snapshot Voting Details.](https://vstats.fortune-validator.pro/proposals/0x2c862da1cc9036a13d0505cba3aeb44f99ae5b7b7c1ef011aa147f73be9022f0) Thanks David Fortune

Addressing the need for incident response guidance within the validator community, I've drafted a [General instruction doc](https://docs.google.com/document/d/12n0-z7WRtJXBBJcphdl7-pGONGW7gRqCDurMsI_x5_8/edit) outlining procedures during such events. This document is currently under review and includes tooling suggestions for future development.

---
**2024-3-1 Fri**:

I've assisted Protofire with the migration of Blockscout contracts and created the infra required for docs.lend.harmony.one.
I then contributed to our playbook by adding gcloud cert map creation to help future subdomain ssl linked to dot country.

For the leader rotation, the isbackup feature was tested with the validator community. It has been confirmed not working and Konstantin is leading the effort to address this. With the devnet leader rotation test, we highlighted the need of a 1% internal voting power to be used as DNS node. And we finally coordinated with validators to halt their backup nodes in preparation for full decentralization. We are now left with 21 validators out of the original 31.

On the commnunity side, I helped with bridge users issue, including one user losing 2000 BSC-USDT during the bridge transfer. Yuriy is investigating, and I'm awaiting feedback. And I assisted two other blacklisted users with their inquiries for burning and unblacklisting their ONE account.

---
**2024-2-23 Fri**:
I focused on analyzing content hosted on dot country domains using harmony.one SSL. To streamline the process, I developed automation for certificate creation, which you can find here: https://github.com/harmony-one/ansible/pull/126. Additionally, we provided support to several users encountering stuck transactions, particularly those using ledger and exchange platforms. Some of these issues are still tied to the blacklist implemented on the network.

---
**2024-2-16 Fri**:
The focal point of this week was the unexpected Mainnet Shard 0 Outage and Crosslink stuck. Through collaborative efforts and rigorous code review, we successfully resolved the issue. For those interested, a detailed post-mortem report has been published here : https://talk.harmony.one/t/harmony-mainnet-stuck-incident-report-feb-10-2024/24087

I dedicated time to enhancing our developer documentation by reorganizing and restructuring it for improved accessibility and usability. You can explore the latest updates at https://docs.harmony.one/home/developers.

In regards of the Harmony Cloud Accounting, I compiled and analyzed the costs incurred for December 2023 and January 2024. The findings will be shared with the team via internal channels on Monday.

Lastly, I reviewed, researched, and tested automation processes for SSL certificate issuance. This initiative aimed to streamline security measures, particularly for non .country domains hosted on our .country infrastructure.

---
**2024-2-9 Fri**:

The long release for v2024.0.0, detailed in [PR 4546](https://github.com/harmony-one/harmony/pull/4546), has undergone review. Testing will commence next week, with an anticipated release by the end of the following week, barring any unforeseen issues. This release will be non-mandatory.

Regarding the upcoming [HIP32 hardfork](https://talk.harmony.one/t/hip32-complete-decentralization-of-validator-network), the initial estimate of March 13th may be postponed to the end of March. This adjustment is due to underestimating the time required for coordination with our validator community. Discussion are still ongoing.

---
**2024-2-2 Fri**:

This week, progress was made in unblocking the leader rotation testing by addressing a corner case related to fast signature collection and achieving 100% vote before meeting the 67% quorum. The corresponding  [PR4626](https://github.com/harmony-one/harmony/pull/4625) has been created and confirmed working by Diego.

Addressing user-reported issues (3), a [fix](https://github.com/harmony-one/harmony/pull/4624) was implemented for the allowedtx feature, allowing users to successfully burn a total of 1,562,914 $ONE this week.

In addition, support was provided to two exchange partners facing challenges with stuck transactions, and coordination for state pruning testing was facilitated.

More details on my github profile https://github.com/sophoah

---
**2024-1-26 Fri**:

Devnet leader rotation testing is underway, and we've identified issues that are currently under investigation (refer to Diego's update for details). Two migration tests are planned: 1) a temporary transition involving rotation with internal nodes, followed by rotation with no internal nodes (currently at this stage), and 2) a direct transaction to external leader rotation only (no internal). 

Additionally, I've reviewed, commented on, and approved 9 PRs across 2 GitHub repositories. A new issue (issue [4616](https://github.com/harmony-one/harmony/issues/4616)) surfaced in the v2023.4.0 release, requiring attention, but our protocol engineers are currently occupied with other issues and testing. 

Lastly, the ongoing work on the harmony revert function, which introduced the 'block already exists' issue, is progressin. First [PR](https://github.com/harmony-one/harmony/pull/4608) test triggered [a panic error](https://github.com/harmony-one/harmony/issues/4616) and the [latest PR](https://github.com/harmony-one/harmony/pull/4617) is currently being tested.

---
**2024-1-21 Sun**:

Our oneinscription partner sought our support for a successful launch on Friday at 13 UTC, and it was indeed a success. 1919 wallet addresses were sold out within a remarkable 13 minutes of the public release, generating 2817 transactions. 

During the oncall mainnet s0 validator crashed twice and hit the infamous `block known already` error which prevent the node to sync. A fix is currently being tested on devnet.

The root cause of the pending transaction stuck issues reported by two major exchanges has been identified. When an exchange user sends a transaction to a blacklisted address, this transaction is discarded, preventing other transactions from going through. A simple fix is for the exchanges to send themselves a transaction to cancel the problematic one.

Regarding the pending delegation bug, after two updates to the allowed transactions list, blacklisted addresses can now 1) burn excess ONE and 2) send a transaction to themselves to cancel pending transactions. A [post on the forum](https://talk.harmony.one/t/technical-incident-report-staking-logic-vulnerability-and-exploitation/23660/15?u=sophoah) informed users of the need to burn, and a [script](https://github.com/harmony-one/ansible/pull/102) to identify cleaned accounts has been developed. Blacklisted addresses will be updated weekly to minimize leader restarts.

---
**2024-1-15 Mon**:

Last week, Binance's transaction queue experienced three instances of getting stuck due to a missing transaction. Extensive troubleshooting was conducted, but there was no apparent reason for the transaction not being added to the chain. We suspect either the transaction was never added to a block and silently discarded or it never reached the leader node. To enhance visibility, we are incorporating additional logs and troubleshooting is continuing this week.

Protofire has released a testnet version of the Blockscout explorer, which currently indexes only s0 and does not support cross-shard transactions yet: [Blockscout Testnet](https://bs-harmony-testnet.protofire.io/). I welcome any feedback via DM.

During my holiday, the devnet encountered issues and was reset to v8307-v2023.4.2-111-g2927929ef last week. However, the recurring problem of a block already being inserted persists. It's crucial to address this issue before the next release, as it is currently causing a delay in the leader rotation testing.

---
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
