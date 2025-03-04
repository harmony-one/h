2025-02-28 Fri: Following the Ledger integration with the staking dashboard, we identified two issues: "Show on Ledger" functionality and clear signing. The first issue was resolved with [PR #722](https://github.com/harmony-one/staking-dashboard/pull/720).  Clear signing requires further development, potentially involving [ERC7730](https://developers.ledger.com/docs/clear-signing/erc7730/process) implementation with the registration of the precompile staking contract, a new [wallet integration](https://developers.ledger.com/docs/clear-signing/wallets) and Ledger's Generic Parser (WIP on ledger side).

Investigation into inconsistent debug_traceTransaction results continues, with suspected timeout and resource constraint issues. A separate timeout problem is being investigated for single-transaction failures.

I also reviewed numerous PRs to support protocol team feature development.

---

2025-02-21 Fri: This week's focus was integrating the staking dashboard wallet with the latest Harmony Ledger app v1.15.0. All staking transactions are now functional with the new app.
I also reviewed several protocol features and fixes: EOA sender validation (EIP-3607) #4849, the 1-second finality fix (1.05s) requires further testing after discussion with Konstantin, and the p2p gater PR #4841, which will help control non-Harmony P2P nodes on the network.
During on-call duty, I investigated five instances of long block times (15s+) on shard 0 mainnet.  Initial findings suggest slower processing times by Harmony node leaders. These same leaders also exhibited varying block times between 2-6s.

---

2025-02-14 Fri: A workaround for the harmony-test repo's localnet issue has been deployed, reducing the number of spawned nodes from 24 to 8, a resource usage improvement of over 65%. 1-second finality testing in localnet shows promising results with an average block time of 1.05s. Devnet 1-second finality testing with a live network and real transactions is upcoming. [A fix](https://github.com/harmony-one/harmony/pull/4844) for the 2025.0.0 transaction receipt RPC failure for pre-release transactions has been successfully tested. Staking dashboard development for Ledger support is in progress. A demo site showcasing login and address display with the new Ledger app v1.15.0 has been deployed, but significant further development is needed for full dashboard integration.

---

2025-02-07 Fri: Travis CI tests rely on the harmony-test repo's localnet configuration.  This week, we've been working to reduce the number of spawned nodes to optimize Travis CI resource usage. This revealed a corner-case consensus issue in localnet, occurring during the transition from the pre-staking to staking epoch when no external validators are present and all internal BLS keys reside on a single node.  An initial fix is in place, but further work is required.  Development of the staking dashboard's Ledger support continues.

---

2025-01-31 Fri: The network has seen improved performance following validator node upgrades to v2025.0.0. Harmony Ledger v1.15.0 has been delivered; a public announcement will be made after the staking dashboard is updated to support the new ledger application.  Testing and review of the new staking data features for the Harmony Explorer are underway on mainnet, with production deployment expected shortly.

---

2025-01-24 Fri: The v2025.0.0 PR has been reviewed, approved, and successfully merged. This release includes a critical fix addressing consensus loss that occurred when the next leader was assigned to the same machine. Release planned next week.

During latest dev branch protocol testing, a new edge case was identified where consensus failure can occur under specific conditions: when the leader is on the same node during an epoch change. While this issue does not occur consistently, current investigations suggest that the updateConsensus process may disrupt consensus if triggered at a specific moment during the epoch transition. Issue has been significantly improved with the changes introduced in [PR #4837](https://github.com/harmony-one/harmony/pull/4837)

---

2025-01-17 Fri:
**Blockscout Explorer Updates**: After refining and testing features 1, 2, and 3, they were approved for deployment to production, and the community provided positive feedback. The inclusion of the dollar-equivalent ONE value, initially planned within these features, was deferred to a newly designated feature (#5). Additionally, discussions and clarifications were made for Feature 4, which is aimed at displaying a summary of staking accounts, in preparation for its upcoming implementation.

**Ledger Update**: The previously submitted PR did not pass Ledger’s CI tests due to missing information and the icon not adhering to their recommendations. These issues have been addressed, and the updated PR is now pending approval.

**Protocol Update**: The `v2025.0.0` PR has been created and is currently under review. This update includes a critical fix for the dual consensus proposal bug.

---

2025-01-10 Fri:

**Ledger Integration Progress** : This week, I followed up with Ledger regarding the new Harmony Ledger app. During the meeting, Ledger provided an estimated timeline for the release, targeting the end of January or early February 2025. This progress is a critical step since the old app has been removed from the ledger directory.  

**Staking Data Explorer Development** : Significant progress has been made on the staking data explorer features, with 2.5 out of 4 features successfully deployed on the Harmony testnet explorer. The following updates were implemented: 1) The "Collect Reward" staking transactions now display the exact number of ONE tokens collected, offering users better visibility into their staking rewards. 2) Staking precompile transactions currently remain on the "normal" transaction page instead of being moved to the "staking" transaction page. Moving these transactions would require significant resources. As a workaround, a filter has been implemented to improve user navigation. 3) The staking transactions list page now includes the ONE value involved in staking transactions. This feature will also be extended to the "normal" transactions list page to display the ONE value for staking precompile transactions. Feedback on these features has been shared with Protofire for further refinement.  

**Protocol Updates**  
An **Out of Memory (OOM)** problem was identified, which appears to be linked to the recent implementation of the resource manager. The team has been investigating the root cause, and a potential fix has been developed and is currently under testing.  

Additionally, the devnet for Shard 1 experienced a recurring consensus loss at the start of each epoch. This issue was traced to an out-of-sync internal validator node, which was unable to propose blocks. The Harmony protocol prioritizes internal nodes as the initial proposers, and they cannot be removed from the committee. For the mainnet, this specific issue will be mitigated in future releases when internal nodes are removed entirely. In this scenario, the first proposer in the committee will be an external validator. If this validator remains out of sync for the entire epoch, it will be automatically excluded from the next election, resolving similar corner cases. 

---

**2025 Goals:**

In 2025, my focus will be on strengthening Harmony’s network stability, advancing key protocol upgrades, and driving the adoption of new features to improve overall performance and reliability.

Improving Network Stability:
A primary goal is addressing stability issues caused by leader rotation. We’re working on Leader Rotation V2 to refine the protocol, ensuring seamless leadership transitions without impacting consensus or block production.

Achieving 1-Second Finality:
Optimizing staking and consensus mechanisms to achieve 1-second finality will enhance user experience and boost Harmony's competitiveness. This will ensure all systems can handle the faster pace without bottlenecks.

Migrating DNS Sync to StreamSync:
Migrating to StreamSync will improve node synchronization, making it more scalable and resilient. This will reduce downtime and ensure nodes stay aligned with the network state.

Achieving 100% External Vote Power:
Reaching 100% external vote power, aided by StreamSync, will mark a significant step for decentralization and governance, ensuring all nodes can reliably connect to validators.

By focusing on stability, finality, synchronization, and decentralization, I aim to help Harmony build a secure, efficient, and decentralized blockchain ecosystem through collaboration, testing, and iterative improvements.

---

2024 Q4 Review:

In Q4, I focused on enhancing staking functionality and addressing critical protocol challenges. A significant part of my efforts was dedicated to investigating consensus-related issues, particularly a bug causing multiple block proposals. While the final resolution is still in progress, my thorough analysis clarified the problem's scope and outlined actionable next steps for resolving it.

To strengthen protocol stability, I rigorously tested and reviewed pull requests addressing post-HIP32 challenges. This included refining leader rotation logic and optimizing multi-BLS validator consensus mechanisms. Additionally, I updated the localnet to replicate mainnet conditions, uncovering critical edge cases such as consensus failures during single-node quorum scenarios.

Operationally, I worked on improving the network by developing and implementing scripts to identify anomalies in block production. My proactive collaboration with the validator community was instrumental in mitigating these issues, including a significant 12-minute shard 0 consensus loss. Detailed incident reporting and follow-up ensured transparency and informed future improvements.

---


2024-12-06 Fri: This week, I focused on improving staking-related features and functionality. I investigated issues related to the staking "collect reward" amount and collaborated with Artem for assistance. Additionally, I submitted new feature requests to Protofire aimed at enhancing the staking experience on the explorer: 1) Support for displaying `claimed reward amounts` 2) `Relocating account staking precompile transaction history` from the normal transaction page to the dedicated staking transaction page  3) `Displaying CollectReward, Delegate, and Undelegate amounts` on the staking transaction page

Additionally, I spent time testing and reviewing PRs aimed at resolving the multiple consensus proposal bug. However, despite these efforts, the issue remains unresolved and will require further investigation and refinements.  

---

2024-11-29 Fri: The issue of consensus loss caused by two validators running on the same node is closely tied to the multiple block proposal bug. In the latest development branch, within a multi-BLS key setup where the next leader resides on the same node, multiple block proposals are generated for the same height. This results in a signature verification failure because the second proposal has a different block hash compared to the first. This bug currently obstructs testing of the [next validator view change PR](https://github.com/harmony-one/harmony/pull/4802).

---

2024-11-22 Fri: On the protocol side, I reviewed several PRs aimed at addressing the HIP32 aftermath issues, including : [PR 4801](https://github.com/harmony-one/harmony/pull/4801): "Add Logging to ReadySignal Method for New Block Proposals, [PR 4785](https://github.com/harmony-one/harmony/pull/4785): "Additional Logs for Consensus", [PR 4798](https://github.com/harmony-one/harmony/pull/4798): "Enhance Leader Rotation Logic to Address Edge Cases in Leader Selection", [PR 4799](https://github.com/harmony-one/harmony/pull/4799): "Improve Consensus Logic for Multi-BLS Validators with Quorum", [PR 4802](https://github.com/harmony-one/harmony/pull/4802): "View Change: Support for Checking if Validators Belong to the Same Key"

Each of these PRs was reviewed to ensure they effectively address edge cases and enhance the protocol's stability post-HIP32.

Additionally, an offline test specifically designed for evaluating new hire candidates has been developped thanks to a team effort. This test aims to streamline the hiring process by effectively filtering and assessing technical skills. 

---

2024-11-15 Fri: To address the aftermath of the HIP32 issues, setting up a localnet with a multi-BLS key configuration became essential. For this purpose, a PR was created: [#4793](https://github.com/harmony-one/harmony/pull/4793). During testing, an unexpected corner case was encountered where the consensus became stuck because the leader achieved quorum solely with its own BLS keys. After implementing a workaround to progress with the replication of the HIP32 issue, another complication arose: the leader is generating two concurrent proposals for the same block height, leading to signature verification failures.

---

2024-11-08 Fri: This week, much of my time was dedicated to investigating and addressing issues related to consensus and block production.

Early in the week, I improved the validator uptime metric displayed on the staking explorer at staking.harmony.one. Additionally, I developed a script to detect unusual block times, aimed at identifying anomalies in block production. This new script proved valuable in analyzing a recent short consensus loss on shard 0, where it uncovered multiple instances of blocks taking three to four times longer than expected to produce. These prolonged block times contributed to a reduction in overall block production and were linked to [low "tosign" counts issue](https://github.com/harmony-one/harmony/issues/4789).

Midweek, I conducted a more in-depth investigation into the shard 0 consensus loss by collaborating with one of our validators. Through this analysis, I discovered that the validator was running two validator instances on the same server. This setup caused complications when leader rotation assigned the next leadership role to a key on the same machine, resulting in delays in consensus restoration.  After advising the validator to add an additional key to avoid leadership transfer issues on the same server, we were able to resolve this specific problem. In parallel, I worked on replicating mainnet conditions in our localnet environment. However, I encountered a different type of consensus loss when the network hit a staking epoch, underscoring the need for further refinement in localnet to better mirror mainnet behavior. 

Toward the end of the week, I conducted a thorough investigation, troubleshooting, and reporting on [the 12-minute consensus loss incident on shard 0](https://talk.harmony.one/t/mainnet-shard-0-12-minute-downtime-on-november-8-2024/25161) that occurred on November 8. This report will serve as a key resource in identifying preventive measures and refining our response strategies going forward.

---

2024-11-01 Fri: This week was dedicated to final preparations for the HIP32 hardfork, which successfully occurred on Thursday, October 31, at 13:18 UTC without major incidents. However, there was an issue at the end of the epoch where the block height reported by the [staking protocol for signing was lower than expected](https://github.com/harmony-one/harmony/issues/4789). The focus for the upcoming week will be on analyzing and troubleshooting this issue.

Additionally, I reviewed and approved several pull requests aimed at improving streamsync, which should help address the ongoing 0x0 block hash issue. I was able to replicate this issue in localnet by intensively running a CPU stress tester and tuning the setup. However, replication is challenging, as it requires multiple attempts to achieve the right conditions.

---

2024-10-25 Fri: This week, I reviewed and tested multiple PRs. For the [0x0 hash bug fix PR](https://github.com/harmony-one/harmony/pull/4778), the PR only addressed the streamsync syncing method, while the issue also impacts the DNS sync method. Additionally, I tested the [1-second finality PR](https://github.com/harmony-one/harmony/pull/4771) in localnet, which revealed issues with signature collection as soon as the 1-second epoch block occurs. Lastly, I reviewed and tested two streamsync improvement PRs([1](https://github.com/harmony-one/harmony/pull/4762) and [2](https://github.com/harmony-one/harmony/pull/4772)), which have shown positive outcomes in localnet, including a faster start to the sync process when nodes initialize.

---

2024-10-17 Thu: The Harmony Ledger app testing is currently in progress, with some environment issues identified that we're working to resolve. In the meantime, the repository has been prepped and is available here: [Harmony Ledger App](https://github.com/harmony-one/harmony-ledger-app/tree/harmony).

On the protocol side, I identified and troubleshooted a fork issue affecting both devnet and testnet. The problem seems to be caused by the leader committing a block hash but broadcasting a 0x0 hash to the network. We're continuing with further investigation and testing to fully confirm and resolve the issue.

Lastly, the planned v2024.3.0 release has been updated to [v2024.3.1](https://github.com/harmony-one/harmony/releases/tag/v2024.3.1) due to a deprecated GitHub action in our CI pipeline.

---

2024-10-11 Fri: This week, I participated in a technical discussion with the validator community regarding HIP32 and backup node configurations. The hardfork scheduled for 31st October is still on track. Additionally, I've been involved to help with the rescue of DaVinci.

September cloud costs saw a slight decrease of $200, but there's room for further reduction by migrating the RPC used by Hiddenstate on GCP to a bare metal server. 

The total supply script is still running, with an estimated completion time of 2 weeks. 

Finally, during my on-call duties, I handled two incident RCAs: 1) a shard 0 node fork, which will need further analysis and team review, and 2) a false positive alert related to a consensus loss on mainnet shards 0 and 1, caused by Watchdog.

---

2024-10-04 Fri: This week, I refined the total supply script after discussions regarding how bridge-locked or wrapped of ONE Token are handled. I also fixed a bug that caused certain blocks to be skipped during indexing. Additionally, staked ONE tokens are now included in the calculation. The script is running again, although it’s taking longer to complete due to these updates.

I also spent time reviewing and testing PRs aimed at progressing toward the HIP32 release. As a result, we've adjusted the planned HIP32 release date to October 31st, set to occur at epoch 2152 at 13:02 UTC.

---

Q3 Review:

During Q3, my work primarily focused on addressing critical technical issues and preparing key protocol upgrades for Harmony. A major part of my efforts revolved around the HIP32 leader rotation feature, which was deployed on both devnet and testnet but surfaced issues when tested with external validators. This led to a significant shift in focus towards troubleshooting, reviewing, and testing multiple pull requests to replicate the instability, alongside improving internal logging and monitoring for better issue detection. The challenges encountered pushed back the HIP32 hard fork timeline, with the release now tentatively scheduled for mid-October.

Additionally, I managed several releases, including the [mainnet stable v2024.2.0](https://github.com/harmony-one/harmony/releases/tag/v2024.2.0), which introduced P2P improvements and the Go 1.22.5 update. I played a pivotal role in troubleshooting node issues during deployment and ensuring the stability of our localnet with external validators. Beyond technical work, I collaborated with the team to outline objectives for upcoming quarters and supported key community engagements, including facilitating the reopening of BEP2 ONE deposits with Binance and assisting users with staking and node operation issues.

---
2024-09-27 Fri:
The Harmony Ledger app has been an ongoing topic of discussion internally, as work is required to ensure the app becomes available on Ledger Live. This week, Ledger reached out to me with a deadline for its removal unless code refactoring, testing, and auditing are completed by December 31st. While users can still access their wallets through Metamask and Harmony's EVM equivalence, the primary remaining challenge is addressing the legacy HD derivation path. I am considering developing a Metamask snap to resolve this. We've expedited internal discussions to finalize our approach moving forward.

On the technical side, two key pull requests — [Vote Power](https://github.com/harmony-one/harmony/pull/4748) and [Epoch Block Broadcast](https://github.com/harmony-one/harmony/pull/4756) — were fully reviewed, tested, and merged. The Epoch Block broadcast demonstrated promising results, with significantly improved stability on the localnet with external validators. We plan to test this further on the devnet for a week, after which we should have a clearer timeline for the upcoming HIP32 release. 

Additionally, I developed and initiated a script to identify the total ONE in circulation, which is expected to take several days to complete.

---

2024-09-20 Fri: 
I spent the week in Singapore attending Token 2049 meeting with Partners and Harmony community users.

---

2024-09-13 Fri: 
This week, protocol testing on the localnet with external validators revealed an issue with the HIP32 leader rotation feature. Although the feature had been deployed on both devnet and testnet, the problem went unnoticed due to overly lenient monitoring rules on our part.

I’ve since shifted my focus to reviewing and testing pull requests ([#4735](https://github.com/harmony-one/harmony/pull/4735), [#4748](https://github.com/harmony-one/harmony/pull/4748), [#4750](https://github.com/harmony-one/harmony/pull/4750), [#4751](https://github.com/harmony-one/harmony/pull/4751)) on localnet with external validators to replicate and understand the current instability. In parallel, I’m collaborating with Ulad to improve our internal logging system, aiming to streamline troubleshooting within Harmony node logs and enhance our monitoring to detect this issue more accurately.

As a result of these findings, I’m postponing the HIP32 release to October 17th, or potentially later, depending on the stability fixes on both devnet and testnet.

---

2024-09-06 Fri:
The v2024.2.0 release is out, and several discussions have taken place regarding the necessity of removing backup nodes. However, new issues surfaced this week: 1. A new Harmony testnet node encountered the error: `bootnode could not bootstrap consensuscontext deadline exceeded`. This was resolved after multiple restarts. 2. The v2024.2.0 update has introduced challenges in starting and maintaining a stable localnet with external validators due to crosslinks not being processed. Although Konstantin has created a PR to address the issue, it’s clear that a change in protocol behavior occurred with the v2024.2.0 release.

Due to these challenges, the tentative date for the HIP32 hardfork has been pushed back by a week, now set for 3rd October 2024.

---

2024-08-30 Fri:
This week has been focused on ensuring that the mainnet stable release v2024.2.0 is ready for rollout on Monday, September 2, 2024. So far, everything is on track, with Devnet, Testnet, and Mainnet all successfully upgraded. This release is a critical step towards HIP32, incorporating a new stable Harmony version featuring P2P improvements and the Go 1.22.5 update. The final few PRs for the HIP32 hard fork are currently in progress, with the fork tentatively scheduled for September 26, 2024.

During the deployment of the new release on Devnet, we encountered an issue where four nodes went offline due to streamsync not finding nodes with a higher block height to sync with. This was resolved by enabling DNS sync on one of those four nodes. Additionally, the team and I successfully upgraded Golang to version 1.22.5 across all our projects (watchdog, harmony-test, go-sdk) with multiple PR reviews for the upcoming v2024.3.0 Hardfork.

On another note, I also assisted the team in drafting their objectives for Q4 2024 and Q1 2025, which will be finalized after a review with Steven.

---

2024-08-23 Fri: Having been out of the office for the past two weeks, I've been catching up on all the updates. After getting up to speed, I focused on planning for the HIP32 hard fork, which involves an intermediary release using Go 1.22. The current plan is to release v2024.2.0 in early September, with the HIP32 hard fork scheduled for the end of September. A significant portion of my time has been dedicated to coordinating and assisting with PR reviews for the upcoming v2024.2.0 release.

Additionally, I've completed the cost reporting for July. We managed to save approximately $1.3k compared to June, primarily due to overlapping costs from transitioning between the old and new explorers. The old explorer was fully decommissioned in July, so we should see the final, adjusted monthly costs reflected in August.

---

2024-08-01 Thu: This week, I coordinated closely with Harmony management and Binance to facilitate the reopening of BEP2 ONE deposit, ensuring that users who were previously stuck could regain access to their assets. Additionally, I assisted Frank with the restoration of the Harmony ONE bot's PostgreSQL database cluster, ensuring the system's functionality was restored. I also completed the offboarding process for Casey, ensuring that his access was removed from all relevant systems and platforms.

---

2024-07-26 Fri: I worked on the BEP2 ONE sunset, investigating the sunset procedure, tech documentation, and researching/coordinating the different accounts related to it. This effort led to the recovery of 50 BNB (equivalent to $30,000) back to the Harmony treasury. However, I have yet to find a solution for users who still have ONE on the BEP2 network. I am actively working with management and exchanges to determine the best course of action for these users.

Additionally, I assisted three community members with staking issues, supported two community node operators, and helped one exchange partner with their node operation. We also made a significant breakthrough with the mainnet bootnode issue. Thanks to Gheis' latest PR 4717, the bootnode service was successfully installed on two of the four mainnet bootnodes, resulting in improved stability.

---

2024-07-19 Fri: This week has been focused on troubleshooting, support, and addressing critical issues. I continued troubleshooting the Sushi revert issue, which could only be replicated under the exact conditions experienced by the Sushi team. During testing, I used `eth_call` with `gasPrice` while calling `totalSupply` on the WONE contract without any issues. Additionally, I provided support for Blockscout users who reported several issues: the search bar couldn't find addresses that had never been used on-chain, account and block information used by other dashboards contained a "#" that prevented direct access, and staking data were no longer available. For the staking data issue, I suggested linking to the staking dashboard showing the portfolio page which is currently pending implementation.

I implemented playbook and security fixes on the monitoring server and managed the transition of the AWS account for Harmony Lend staging and production under the Harmony AWS account. I also completed the June cloud accounting, which revealed a slight decrease in our overall cloud costs.

---

2024-07-12 Fri: This week has been productive with a strong focus on resolving key technical issues and maintaining our infrastructure. I tested multiple bootnode setups and identified overlooked settings, which led to the review of Gheis' PRs [4707 - improve p2p connection manager](https://github.com/harmony-one/harmony/pull/4707) and [4710 - add connection manager high water mark flag to boot node](https://github.com/harmony-one/harmony/pull/4710). During the bootnode version upgrade, I also upgraded their operating systems to address last week's SSH CVE regression vulnerability.

In parallel, I assisted the Sushi team in troubleshooting swap issues involving ONE as the output and investigated a shard 0 RPC node stuck issue. This issue is assumed to be caused by heavy computation during the epoch change, which subsequently triggered a corner case in the current DNS sync protocol. I also reviewed watchdog [PR #97](https://github.com/harmony-one/watchdog/pull/97), which aims to support a localnet version to facilitate protocol engineering work. 

Finally, we successfully launched the new explorer, [https://explorer.harmony.one](https://explorer.harmony.one), on Tuesday marking a significant milestone for the network

---

2024-07-05 Fri: Script was finalized this week and the impact of the pending undelegation bug has been relatively minor. Additionally, remediation efforts for the [SSH regression](https://blog.qualys.com/vulnerabilities-threat-research/2024/07/01/regresshion-remote-unauthenticated-code-execution-vulnerability-in-openssh-server#detect-and-remediate-cve-2024-6387-with-qualys-totalcloud-container-security) have been ongoing, with 90% of the internal servers upgraded with the assistance of Ulad. However, a few servers will still require a software/OS reinstallation. Finally, Shard 1 mainnet RPC has been under maintenance since Tuesday due to a `block already known` issue. We have restarted the synchronization of the archival data and are planning to set up a new snapshot node to expedite future restorations.

---

**2024 Q2 Review**

Throughout Q2 2024, significant strides were made in enhancing the stability and reliability of our network environments, particularly in the devnet and testnet. In April, our efforts focused on resolving critical consensus issues in shard 1, improving security, and developing the new Blockscout explorer. We addressed downtime issues in Shard 0 and ensured the integrity of our infrastructure through comprehensive security checks. In May, we stabilized the devnet consensus by switching to DNS Sync, launched the [testnet Blockscout Explorer](https://explorer.testnet.harmony.one/), and continued refining crosslink logic to improve network reliability. Intensive troubleshooting and collaboration with team members led to effective solutions for connectivity issues caused by old P2P configuration.

June's efforts culminated in the successful execution of the [v2024.1.0](https://github.com/harmony-one/harmony/releases/tag/v2024.1.) hard fork release on June 20th. This release involved meticulous preparation and collaboration with the validator community and partners to resolve issues before the deadline. We also restored and updated snapshot nodes to ensure the stability of the latest development code, paving the way for future protocol upgrades and reinforcing the security and reliability of our network infrastructure.

---
2024-06-28 Fri: This entire week has been mostly dedicated to writing the script. Identifying the problematic pending undelegations has been challenging. The delay stems from our initial assumption that all validators with a 100% max rate would be impacted by the bug, which proved to be incorrect. Analyzing the staking data state at each epoch showed otherwise. As a result, I've had to review all the staking transactions made by each delegator account and develop new logic to update the state of all undelegations.

---
2024-06-21 Fri: This week has been hectic as we prepared for the successful execution of the v2024.1.0 hard fork release, which took place on June 20th, 2024, at around 00:09 AM UTC. I've been working closely with the validator community and our partners to resolve any issues before the deadline. Additionally, I have spent the remainder of my time identifying the extent of the bug.

---
2024-06-14 Fri: We spent several days thoroughly analyzing the staking bug and understanding how the validator max rate affects pending undelegation. After gaining a clear understanding, I began leading the v2024.1.0 release, which includes planning for a hard fork scheduled to occur at epoch 1976.

---

2024-06-07 Fri: This week's focus was on stabilizing our devnet and testnet environments by restoring and updating snapshot nodes. The objective is to ensure that the latest code in the development branch is stable and functioning correctly.

---

2024-05-31 Fri: As anticipated last week during our investigation of the consensus loss in devnet, switching to DNS Sync has resulted in a stable consensus. Our next step is to enable streamsync on shard 1 while maintaining DNS Sync on shard 0 and continuing our troubleshooting efforts.

Following the previous week's crosslink fix, Shard 1 testnet has been revived. However, upon revival, all nodes except the internal node are currently stuck.

During the switch to DNS Sync, the latest P2P configuration code prevented communication between nodes, indicating a potential impact on the mainnet. Multiple tests have been conducted, but the lack of P2P logging has hindered our ability to pinpoint the issue. Gheis has proposed four different options to enhance visibility, and two of them are currently being tested.

---

2024-05-24 Fri: I've continued working on crosslinks, spending significant time analyzing the overall logic for improvements and fixes in Konstantin's PR. The bootnode issue has been thoroughly tested on mainnet, resulting in confirmed improvements in service stability. Testing on devnet revealed connectivity issues with network nodes until all nodes were upgraded to the same version, suggesting a potential discrepancy in the new P2P configuration.

Furthermore, devnet consensus has not remained stable for more than 48 hours. Multiple troubleshooting sessions indicated that nodes go out of sync even when they appear fully synced. To address this, we plan to test DNS sync to rule out a possible streamsync bug.

---

2024-05-17 Fri: This week, I set up a new log collection server utilizing our Grafana/Loki/Promtail stack, which is now actively logging data from all the devnet nodes. User testing is currently in progress. Additionally, the testnet Blockscout Explorer was launched on Wednesday and accessible https://explorer.testnet.harmony.one

On the protocol side, I collaborated with Gheis to address the mainnet bootnode issue, which a fix currently being tested without issue. Concurrently, I worked with Konstantin on resolving the crosslink issue in testnet/devnet, with multiple leads being pursued and 2 PRs ([4669](https://github.com/harmony-one/harmony/pull/4669) and [4671](https://github.com/harmony-one/harmony/pull/4671)) currently under review.

--- 

2024-05-10 Fri: This week, I've been actively involved in a new explorer project that resembles etherscan. We've developed a demo for mainnet shard 0, focusing solely on EVM indexing, which is currently undergoing indexing. Additionally, discussions are underway to obtain a quote that encompasses Harmony-specific features such as support for two shards, cross-shard transactions, and staking transactions. With the mainnet infrastructure cost approval, progress continues on the Blockscout explorer with plans to launch testnet launch in the coming days and mainnet next.

Despite our efforts, several ongoing issues across our network are hindering our progress with HIP32 implementation: 1) Mainnet bootnodes are experiencing panics, 2) There are pending crosslinks in the devnet, and 3) We're encountering streamsync issues. While the latter is not necessarily a blocker at the moment, achieving 0% internal vote power and complete decentralization remains a crucial goal for our future endeavors.

---

2024-05-03 Fri: 1. The mainnet bootnode experienced higher-than-usual traffic this week, leading to elevated CPU and memory usage. Consequently, we upgraded all four instances to accommodate the increased load efficiently.

2. We successfully restored consensus on shard 1 devnet after encountering obstacles with our streamsync code, which hindered node synchronization to the latest block and hindered consensus restoration. Multiple restarts were necessary to achieve full synchronization across all nodes. During troubleshooting sessions, we identified potential issues with streamsync and deployed PR 4660 to enhance code performance and improve log visibility. However, the root cause of the issue remains unidentified.

3. I coordinated the update of the explorer dashboard client to minimize the number of requests to CoinGecko, reducing the volume from 7.8 million calls to less than 10,000 per month. Special thanks to Artem for implementing a cache at the API layer, which significantly optimized the process.

4. I conducted a cost analysis comparing our current explorer expenses with Protofire's estimation for the upcoming Blockscout deployment focusing on the infrastructure cost. While Protofire's estimate appeared cheaper in April, my earlier projections suggested our costs were lower earlier this year. It's essential to note that our expenses are subject to fluctuations based on traffic and resource utilization, while Protofire cost should not while ensuring the retention of the entire transaction history.

---

2024-04-26 Fri: This week, I've been diving deep into some critical tasks. First off, I've been helping test and review the latest feature addition to the Blockscout explorer currently being deeloped by Protofire, focusing on cross-shard and shard 1 support.

Additionally, I've been heavily involved in resolving the shard 1 consensus loss issue. After successfully replicating the problem and testing a fix in the localnet, I've outlined the steps for resolution. This includes creating a hard fork to reinstate internal node voting power, reverting the shard 1 last block, and allowing shard 1 to propose and add a new block with the latest shard state. However, while tackling this issue, I encountered some new challenges. Firstly and originally the devnet went down with internal nodes losing their voting power, requiring me to shift focus to the external nodes' current voting power. Furthermore, despite the leader being able to add the new last block, the final commit isn't being received by other nodes in the network. Unfortunately, attempts to restore consensus through block download via syncing have been unsuccessful, as we're currently encountering block nil errors. 

In addition to these tasks, I've also been assisting Gheis with testing PR 4660 for a Travis CI bug. We identified that the issue stems from the latest commit using short-range sync instead of long-range sync, causing localnet to stop producing block. We're currently investigating why the consensus mode switches to sync when short-range sync is used in a new network.

---

2024-04-19 Fri: Away 3 days from Mon to Wed. In the last two days, I continued the investigation into the Harmony code base in order to address the consensus issue affecting shard 1 on the testnet and devnet.

---

2024-04-12 Fri: Throughout the week, my focus has been on addressing the critical issue of the shard 1 testnet/devnet no committee problem, which resulted in a network without consensus. My goal has been to identify a solution to prevent this issue from recurring and to mitigate potential risks on the mainnet. While I was able to replicate the issue in localnet by Friday, finding a definitive fix remains uncertain. The challenge lies in shard 1 using the last epoch committee when it becomes stuck, rather than the latest committee. I've identified the root cause as the shard 1 crosslink not being sent or processed by shard 0. As a long-term solution applicable to the mainnet, we're exploring options to ensure that validators are not excluded from the new committee when their signature performance metrics are not being updated, resulting in having 0 "signed" out of 0 "to sign".

---

2024-04-05 Fri: During the week, we encountered issues with Shard 0 devnet, where the consensus went down twice. However, a simple restart of the cluster effectively resolved the problem on both occasions. Upon conducting a root cause analysis, I identified that a validator had mistakenly switched its consensus mode to "syncing" preventing its participation in the consensus process. Further analysis is still pending.

Shard 1 testnet and devnet are currently experiencing downtime, posing a significant challenge for HIP32. The issue, outlined in detail in [https://github.com/harmony-one/harmony/issues/4651](https://github.com/harmony-one/harmony/issues/4651), revolves around the handling of crosslinks within our consensus protocol.

In response to the security vulnerability CVE-2024-3094, I diligently conducted a comprehensive security check on all Harmony nodes and explorer backends. I'm pleased to confirm that none of our systems were running the vulnerable version, ensuring the security and integrity of our infrastructure.

Furthermore, I meticulously tested and reviewed the [isbackup PR fix](https://github.com/harmony-one/harmony/pull/4644), confirming the correct operation and readiness for merging. However, I recommended the removal of BINGO messages from the logs to prevent confusion for node operators.

Lastly, I provided comprehensive assistance to joskins, offering technical guidance and addressing issues related to contract deployment using Remix for an upcoming token pre-sale. 

---

Q2 devops and service roadmap

In the upcoming quarter, our DevOps roadmap prioritizes three key initiatives aimed at enhancing the efficiency and reliability of our infrastructure. Foremost, we will focus on implementing the Blockscout Explorer for the Harmony Mainnet. This initiative aims to provide users with an intuitive interface to explore on-chain data comprehensively. By integrating Blockscout, we anticipate improved transparency and accessibility within our ecosystem, ultimately empowering users with better insights and decision-making capabilities.

Simultaneously, we are committed to implementing rate limits on Harmony RPCs to optimize performance and ensure service reliability. By regulating incoming traffic, this initiative aims to prevent overload and maintain the responsiveness of our RPC infrastructure. By proactively managing traffic flow, we anticipate enhancing the overall user experience for developers and validators, aligning with our goal of delivering seamless and efficient services. Additionally, we are preparing for the imminent replacement of RPC nodes facing disk full issues, prioritizing the stability and availability of our RPC services. Through these initiatives, we aim to uphold our commitment to providing a robust and dependable platform for our community.

---

Q1 Impact and Performance Summary:

Throughout Q1, I've played a pivotal role in addressing technical challenges and advancing key initiatives within our project. Notably, I collaborated with team members on resolving issues such as testnet leader rotation activation hurdles and enhancing our mainnet oracle integration with Band. Moreover, my efforts in troubleshooting and providing support for various development tasks, including HIP30 state verification failures and devnet consensus loss investigations, have contributed to the overall progress and stability of our ecosystem.

In addition to technical contributions, I actively participated in community engagement and internal operations improvements. I facilitated the progress of HIP32 through validator coordination, while also enhancing our internal operations and security through the development and updating of multiple playbooks. Furthermore, my involvement in addressing user-reported issues and providing support to exchange partners underscores my commitment to ensuring a seamless experience for all stakeholders.

Detailing more the DevOps area, in the first quarter, I spearheaded several initiatives aimed at enhancing our technical capabilities, optimizing processes, and fortifying our security posture. I automated the renewal of SSL certificates for non .country domains name linked to harmony.one subdomains, empowering our DevOps team to efficiently manage certificate renewals. Additionally, I took the lead in updating our internal operations playbook for Goteleport, significantly reducing manual interventions required for adding, updating, or installing new teleport nodes. Moreover, I developed a 'bad-delegation' script to detect addresses that received an excessive amount of ONE, ensuring the integrity of our network and implementing processes to swiftly address any issues encountered. These initiatives underscore my commitment to leveraging technology and process improvements to drive efficiency and enhance our overall operational resilience.

Additionnaly, the devops team has made significant strides in advancing our technical capabilities and improving operational efficiency. Under my guidance and supervision, Ulad executed several key initiatives, including the establishment of two snapshot nodes for shard 0 and shard 1 in the testnet, which have already been embraced by users. We also focused on optimizing system performance by updating the Push-gateway runbook and creating RPC/nginx runbooks to streamline the process of updating our RPC. Additionally, we developed scripts to detect backup nodes in preparation for HIP32. These efforts align with our overarching objective of maintaining a secure, efficient, and resilient technical infrastructure.

---

2024-03-29 Fri: This week kicked off with Amanda and me diving into the intricacies of updating billing information on mission control. In addition to that, I lent a hand to community users grappling with blacklist address and wallet issues.

Unfortunately, our testnet leader rotation activation hit a snag. While Shard 0 smoothly integrated the new feature, Shard 1 encountered a hitch. A stuck crosslink resulted in lost consensus, leaving Shard 1 without both internal and external validators. In collaboration with Diego, we explored a potential solution, considering another hard fork to temporarily reinstate the internal validator.

On a brighter note, Band's recent update to their [network blockchain page](https://docs.bandchain.org/develop/supported-blockchains/) now includes our mainnet standard reference price address, enhancing the legitimacy of our mainnet oracle integration with Band.

---

2024-03-22 Fri: Throughout the week, I provided support for band/QiDAO and conducted checks for stuck blocks in devnet s1, while also assisting with investigations into validator s1 signature loss. Additionally, I troubleshooted issues related to Buggy validator state #4605 and pending undelegation not released with inactive validator #4632, uncovering corner cases with HIP30 that caused state verification failures. Towards the end of the week, I investigated shard 1 devnet consensus loss and identified a block verification failure at the prepare phase of block 1140307. 

---

2024-03-15 Fri: I've been quite busy this week! First off, I've kept in touch with validators to ensure the progress of HIP32, which is currently approved and awaiting the final decision on March 19th, check out the latest update the [HIP32 Vote dashboard] (https://vstats.fortune-validator.pro/proposals/0x2c862da1cc9036a13d0505cba3aeb44f99ae5b7b7c1ef011aa147f73be9022f0) thanks to David Fortune

Furthermore, I troubleshooted devnet node problem concerning streamsync, alongside Gheis. It emerged that the faulty node had an incorrect viewID, leading to a divergence in hash values and subsequently causing a local node fork. Upon initial investigation, it was suggested that the snapshot feature might be updating the viewID, or that a node with a DB containing incorrect information was used for syncing.

On another front, I worked with Artem on testing a new endpoint that enables us to query the details of an HRC20 transaction (check out: [HRC20 Transaction Detail](http://api1.explorer.t.hmny.io:3001/?query=getERC20TransferInfo%200%200xdce285759c3d3a1e6b66b57f064cc6b9399e5eb744ccb2b96414b3ff1ab1bd94)). We've been investigating a bug related to the circulation supply of depegged assets. Unfortunately, we won't be able to fix it until the mainnet blockscout is available.

Lastly, I've been enhancing our internal operations and security by writing and updating multiple playbooks. You can find the latest changes and improvements in the following pull requests: [#139](https://github.com/harmony-one/ansible/pull/139), [#138](https://github.com/harmony-one/ansible/pull/138), [#137](https://github.com/harmony-one/ansible/pull/137), [#136](https://github.com/harmony-one/ansible/pull/136)

---

2024-03-08 Fri: This week, we released v2024.4.0 to facilitate testing without activating the HIP32 leader rotation. This decision aims to reduce potential errors and streamline troubleshooting processes if any issues arise.

Snapshot voting for HIP32 is underway, with unanimous support thus far. However, we still need another 883M ONE votes to reach the required 51% total stake for the vote to be valid. You can track the progress here: [Snapshot Voting Details.](https://vstats.fortune-validator.pro/proposals/0x2c862da1cc9036a13d0505cba3aeb44f99ae5b7b7c1ef011aa147f73be9022f0) Thanks David Fortune

Addressing the need for incident response guidance within the validator community, I've drafted a [General instruction doc](https://docs.google.com/document/d/12n0-z7WRtJXBBJcphdl7-pGONGW7gRqCDurMsI_x5_8/edit) outlining procedures during such events. This document is currently under review and includes tooling suggestions for future development.

---

2024-03-01 Fri: I've assisted Protofire with the migration of Blockscout contracts and created the infra required for docs.lend.harmony.one.
I then contributed to our playbook by adding gcloud cert map creation to help future subdomain ssl linked to dot country.

For the leader rotation, the isbackup feature was tested with the validator community. It has been confirmed not working and Konstantin is leading the effort to address this. With the devnet leader rotation test, we highlighted the need of a 1% internal voting power to be used as DNS node. And we finally coordinated with validators to halt their backup nodes in preparation for full decentralization. We are now left with 21 validators out of the original 31.

On the commnunity side, I helped with bridge users issue, including one user losing 2000 BSC-USDT during the bridge transfer. Yuriy is investigating, and I'm awaiting feedback. And I assisted two other blacklisted users with their inquiries for burning and unblacklisting their ONE account.

---

2024-02-23 Fri: I focused on analyzing content hosted on dot country domains using harmony.one SSL. To streamline the process, I developed automation for certificate creation, which you can find here: https://github.com/harmony-one/ansible/pull/126. Additionally, we provided support to several users encountering stuck transactions, particularly those using ledger and exchange platforms. Some of these issues are still tied to the blacklist implemented on the network.

---

2024-02-16 Fri: The focal point of this week was the unexpected Mainnet Shard 0 Outage and Crosslink stuck. Through collaborative efforts and rigorous code review, we successfully resolved the issue. For those interested, a detailed post-mortem report has been published here : https://talk.harmony.one/t/harmony-mainnet-stuck-incident-report-feb-10-2024/24087

I dedicated time to enhancing our developer documentation by reorganizing and restructuring it for improved accessibility and usability. You can explore the latest updates at https://docs.harmony.one/home/developers.

In regards of the Harmony Cloud Accounting, I compiled and analyzed the costs incurred for December 2023 and January 2024. The findings will be shared with the team via internal channels on Monday.

Lastly, I reviewed, researched, and tested automation processes for SSL certificate issuance. This initiative aimed to streamline security measures, particularly for non .country domains hosted on our .country infrastructure.

---

2024-02-09 Fri: The long release for v2024.0.0, detailed in [PR 4546](https://github.com/harmony-one/harmony/pull/4546), has undergone review. Testing will commence next week, with an anticipated release by the end of the following week, barring any unforeseen issues. This release will be non-mandatory.

Regarding the upcoming [HIP32 hardfork](https://talk.harmony.one/t/hip32-complete-decentralization-of-validator-network), the initial estimate of March 13th may be postponed to the end of March. This adjustment is due to underestimating the time required for coordination with our validator community. Discussion are still ongoing.

---

2024-02-02 Fri: This week, progress was made in unblocking the leader rotation testing by addressing a corner case related to fast signature collection and achieving 100% vote before meeting the 67% quorum. The corresponding  [PR4626](https://github.com/harmony-one/harmony/pull/4625) has been created and confirmed working by Diego.

Addressing user-reported issues (3), a [fix](https://github.com/harmony-one/harmony/pull/4624) was implemented for the allowedtx feature, allowing users to successfully burn a total of 1,562,914 $ONE this week.

In addition, support was provided to two exchange partners facing challenges with stuck transactions, and coordination for state pruning testing was facilitated.

More details on my github profile https://github.com/sophoah

---

2024-01-26 Fri: Devnet leader rotation testing is underway, and we've identified issues that are currently under investigation (refer to Diego's update for details). Two migration tests are planned: 1) a temporary transition involving rotation with internal nodes, followed by rotation with no internal nodes (currently at this stage), and 2) a direct transaction to external leader rotation only (no internal). 

Additionally, I've reviewed, commented on, and approved 9 PRs across 2 GitHub repositories. A new issue (issue [4616](https://github.com/harmony-one/harmony/issues/4616)) surfaced in the v2023.4.0 release, requiring attention, but our protocol engineers are currently occupied with other issues and testing. 

Lastly, the ongoing work on the harmony revert function, which introduced the 'block already exists' issue, is progressin. First [PR](https://github.com/harmony-one/harmony/pull/4608) test triggered [a panic error](https://github.com/harmony-one/harmony/issues/4616) and the [latest PR](https://github.com/harmony-one/harmony/pull/4617) is currently being tested.

---

2024-01-21 Sun: Our oneinscription partner sought our support for a successful launch on Friday at 13 UTC, and it was indeed a success. 1919 wallet addresses were sold out within a remarkable 13 minutes of the public release, generating 2817 transactions. 

During the oncall mainnet s0 validator crashed twice and hit the infamous `block known already` error which prevent the node to sync. A fix is currently being tested on devnet.

The root cause of the pending transaction stuck issues reported by two major exchanges has been identified. When an exchange user sends a transaction to a blacklisted address, this transaction is discarded, preventing other transactions from going through. A simple fix is for the exchanges to send themselves a transaction to cancel the problematic one.

Regarding the pending delegation bug, after two updates to the allowed transactions list, blacklisted addresses can now 1) burn excess ONE and 2) send a transaction to themselves to cancel pending transactions. A [post on the forum](https://talk.harmony.one/t/technical-incident-report-staking-logic-vulnerability-and-exploitation/23660/15?u=sophoah) informed users of the need to burn, and a [script](https://github.com/harmony-one/ansible/pull/102) to identify cleaned accounts has been developed. Blacklisted addresses will be updated weekly to minimize leader restarts.

---

2024-01-15 Mon: Last week, Binance's transaction queue experienced three instances of getting stuck due to a missing transaction. Extensive troubleshooting was conducted, but there was no apparent reason for the transaction not being added to the chain. We suspect either the transaction was never added to a block and silently discarded or it never reached the leader node. To enhance visibility, we are incorporating additional logs and troubleshooting is continuing this week.

Protofire has released a testnet version of the Blockscout explorer, which currently indexes only s0 and does not support cross-shard transactions yet: [Blockscout Testnet](https://bs-harmony-testnet.protofire.io/). I welcome any feedback via DM.

During my holiday, the devnet encountered issues and was reset to v8307-v2023.4.2-111-g2927929ef last week. However, the recurring problem of a block already being inserted persists. It's crucial to address this issue before the next release, as it is currently causing a delay in the leader rotation testing.

---

2023-12-25 Mon: (edited Friday Dec 22 as I will be OOO Dec 23 to Jan 7): Jumped into action during my holiday to contribute to resolving the Staking Logic Vulnerability Incident. The Mainnet Hard Fork v2023.3.0 took place on Sunday, the 17th, with exceptional assistance from the validator community. However, a transaction hash bug surfaced as we tried to conceal the fix, leading us to release v2023.4.2 and support various partners, including thegraph, layerzero, chainstack, synapse, and SimplyVC.

Simultaneously, Binance.com encountered issues, leading to the suspension of withdrawals due to a surge in transactions hitting the 64-transaction limit per account in the pending transaction pool. We collaborated to analyze and resolve the problem, and withdrawals resumed on 12-22-2023 at 01:29 UTC, following an outage that began on 12/19/2023, 21:47 UTC.

Additionally, I received reports of five more drained wallets related to the use of Harmony's deprecated extension. One of them belongs to a validator who still has a portion of their funds staked. I assisted him in running a custom script to programmatically transfer the undelegated funds.

---

2023-12-11 Mon: (edited Friday Dec 8 as I will be OOO Dec 11 to Dec 18): November cloud costs are down to $12.88k from $14.91k. The decrease in costs is a result of various measures undertaken by the devops team, including cleaning up the S3 storage space, terminating, downgrading, and migrating instances (RDS/EC2) to other cloud providers, and optimizing our mainnet node architecture.

There's been a recent surge in victims of drained wallets, with many cases pointing to stolen funds landing in the KuCoin hot wallet. Some confusion arose due to the use of this address as an example by a Harmony dev on Discord. Let's note that victims were using the deprecated Harmony wallet extension and hadn't created new accounts, as suggested in [this article published in 2022](https://harmonyone.notion.site/Wallet-Security-and-Your-Assets-665171c3857a4510abedc44f3b929bd1) I recommend another round of communication/tweets to encourage users to migrate to a new wallet at their earliest convenience.

I've initiated the investigation and implementation of leader metric export. While a demo was built, the data received proved inconsistent. A proposed solution is to focus on the last voting power instead of the constantly changing ongoing vote power during the vote collection.

Additionally, I've reviewed and commented on multiple PRs, including [the automation of watchdog installation](https://github.com/harmony-one/ansible/pull/90), a fix for the [ETH JSON method source address issue](https://github.com/harmony-one/harmony/pull/4575). I also provided guidance to the team for the leader rotation hardfork.

Finally, I investigated the shard 1 signature loss reported by the validator community, tracing it back to the migration of our s1 leader node from Latitude. A workaround to swap the bls keys was suggested and doing further test with VPS could be beneficial as we move towards leader rotation to identify the correct VPS specs

---

2023-12-04 Mon:
Management has approved a 1-year long-term contract for essential Harmony Base services, such as the archival node, aimed at cost savings. The November cloud cost report is pending finalization, awaiting GCP invoices.

0% internal voting power discussions started on our social and internally, Validators are showing enthusiasm to embrace this challenge. Validator community will be engaged for testing in testnet. The hardfork is targeted for 1Q, and two technical challenges are in focus: 1) leader rotation with external validators and 2) leader consensus metrics (the proposed solution involves sending metrics to our Prometheus push gateway)

One famous exchange partner received funds via a multisig transaction and have expressed the need for a more robust explorer. It faced challenges with the internal transaction tab lacking the necessary data for confirmation. A temporary manual and empirical process has been communicated to address this concern. Improving our explorer is imperative.

Protofire is actively working on migrating their testnet blockscout local environment to a more robust one. It's essential to note that Protofire allocates approximately 0.5 Full-Time Equivalent (FTE) per month for projects like Safe, Swap, Compound, and Blockscout. Currently, Blockscout has the lowest priority in this allocation.
 
---

2023-11-27 Mon:
I am in active negotiations with five bare metal providers to optimize our server instance pricing. 
Addtionnally, I have proposed options for serving subgraph, and now awaiting feedback from management.

We addressed two issues on the devnet: 1. restored consensus in s0 by resyncing two validator nodes; 2. resolved the processing of the s1 accumulated crosslinks by rotating to a different leader.

Reviewed five Protocol PRs [Fix for ShardIDFromKey](https://github.com/harmony-one/harmony/pull/4566), [Fix for last mile block](https://github.com/harmony-one/harmony/pull/4567), [Rollback removes physically block data from db](https://github.com/harmony-one/harmony/pull/4568), [Removed future blocks from blockchain_impl.go](https://github.com/harmony-one/harmony/pull/4569), [ELK Stack for runtime log processing](https://github.com/harmony-one/harmony/pull/4570) and created two OPS PRs [retiring london archival node](https://github.com/harmony-one/elastic-rpc-infra/pull/20), [install teleport client](https://github.com/harmony-one/ansible/pull/87). 

Finally, Protofire completed the testnet s0 blockscout indexing. And there are some challenges ahead. One will be the cross-shard transactions. As it requires customization, this feature will not be included in the initial version.

---

2023-11-05 Sun: Explorer service - There have been ongoing discussions regarding the Socialscan explorer initiative, and after much deliberation, we have decided to pause it until next year. Instead, we will focus on R&D work with Protofire on Blockscout, which will be a key focus for Q4. While this work continues, our current mainnet explorer still requires maintenance. To save costs, we have executed a downgrade on the s0 mainnet RDS instance, resulting in savings of $365 per month.

TheGraph service - TheGraph has reached out to us for a grant to support their hosted service. Since they've provided this service for free since June 2022, we are considering having Protofire maintain a dedicated graph node to ensure the continuity of our public dapp service (swap.country). 

Network service - We have initiated work to identify nodes that need to be terminated due to HIP30. The execution of this process is scheduled for the week of November 6. Additionally, I have reviewed and provided comments on Protofire's proposal to take over our snapshot service, which would cost us $2,000 per month, excluding the node infrastructure cost.

HIP30 epoch was successfully implemented on November 2. The multisig address 0xd8194284df879f465ed61dba6fa8300940cacea3 has collected 1.25 million ONE tokens, valued at approximately $17,100 at the current price. As described by Diego earlier, we have identified certain edge cases. Furthermore, several validators are currently competing for election, as they adapt to the new minimum stake requirement, which stands at 7.37 million ONE. The number of active validators has decreased from its peak of 120+ to the current count of 66.

Finally, I have initiated discussions with Huobi and Binance regarding the 0x address format initiative.
