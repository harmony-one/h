I wanted to take a moment to express my sincere gratitude for the opportunity to work with Harmony. For almost 2 years, I have had the privilege of collaborating with an incredibly talented and dedicated team. The experiences and knowledge I have gained during my time here have been invaluable.

I am proud of the work we have accomplished together, particularly our recent advancements with HIP-30 and the successful resolution of several critical issues. The support and camaraderie I have experienced at Harmony have been truly remarkable. I am grateful for the friendships and professional relationships I have built with both the remote team and the SF team.

While I am saddened to leave, I am optimistic about the future and excited about the new opportunities that lie ahead. I will always cherish my time at Harmony and look forward to seeing the team and project continue to succeed.

___
### Weekly Progress Update: 2024-07-30

#### HIP-30 Development

- **HIP-30 Progress:**
  - Continued work on HIP-30, including forking code changes and various testing improvements.
  - Focused on broadcasting vote power and P2P host configurations.

#### Code Review and Testing

- **Golang Upgrade:**
  - Tested and reviewed code changes for the upgrade to Golang 1.22.

- **MaxRate Issue:**
  - Completed a post-bug report on the latest MaxRate issue. The full report can be found [here](https://talk.harmony.one/t/harmony-protocol-bug-report-hard-fork-v2024-1-0/24761/4).

- **Zero Division Panic Fix:**
  - Reviewed and tested the fix for the zero division panic issue (#4720). The details can be found [here](https://github.com/harmony-one/harmony/pull/4720).

#### Upcoming On-Call Responsibilities

- **On-Call Duties:**
  - Will be on-call next week, handling all DevOps operations during the US timezone.

This week focused on advancing HIP-30, upgrading to Golang 1.22, addressing recent issues, and preparing for on-call responsibilities next week.
___
### Weekly Progress Update: 2024-07-16

#### Conference Success and Networking

- **ETHcc Conference:**
  - Attended the main ETHcc conference and over 27 side events, including ETH Brussels, L2 Day, Open Finance Day, Chainlink Day, and multiple Gitcoin Passport events.
  - Met with multiple partners of Harmony, including validators and ecosystem projects.
  - Participated in two closed-door roundtable sessions with Ethereum Foundation Geth L2 growth teams.
  - Promoted Harmony to more than 100 individuals, discussing current projects and future growth steps.
  - Attended a private dinner with Vitalik and several industry leaders.
  - Enjoyed the best rave in Web3, rAAVE!
  - Met with multiple meme coins to promote Harmony's features and attract them to our chain.

#### Protocol Development and Issue Investigation

- **Lending Platform Issue:**
  - Investigating an issue with the lending platform and beginning an after-action report.
  - Considering a possible migration to v3.

- **HIP-32 Release:**
  - Continuing to support the team in the release of HIP-32.
  - Getting caught up with the latest issues and reviewing Pull Requests.

#### Team Management

- **Team Changes:**
  - Adam has exited the protocol team, resulting in only 2 engineers on the on-call schedule.
  - Working with other team members to fill in the gaps and manage the on-call schedule effectively.

This week marked significant progress through successful networking at the ETHcc conference, addressing issues within the lending platform, and continuing support for the HIP-32 release despite team changes.

___
### Weekly Progress Update: 2024-06-28

#### Protocol Investigation

- **Maxrate Issue Investigation:**
  - Investigated the impact of the MaxRate issue identified in previous reports.
  - Communicated with involved wallets and their clients to discuss the next steps and provide guidance.

#### Conference Preparation

- **ETH.CC Conference:**
  - Departed for ETH.CC in Brussels, preparing for the conference events and engagements.

This week was focused on investigating the maxrate issue, communicating with stakeholders, and preparing for and traveling to the ETH.CC conference in Brussels.

___
### Weekly Progress Update: 2024-06-21

#### Protocol Upgrade and Bug Resolution

- **Hard Fork Update / Emergency Upgrade:**
  - Focused on resolving the critical issue identified last week.
  - Ensured the successful deployment of the emergency upgrade (v2024.1.0) for mainnet activation.
  - Coordinated with partners to confirm the upgrade and monitored the process to ensure a smooth transition.

- **Validation of ONE Token Mints:**
  - Began the process of validating any potentially bad ONE token mints post-upgrade.

#### Research and Development

- **Derivatives Smart Contracts:**
  - Minimal progress this week due to the primary focus on the bug resolution and hard fork upgrade.

This week was dedicated to addressing the critical protocol issue, ensuring the successful deployment of the hard fork upgrade, and beginning the validation process for ONE token mints.

___
### Weekly Progress Update: 2024-06-14

#### Protocol Upgrade and Bug Resolution

- **Hard Fork Update / Emergency Upgrade:**
  - Focused on resolving a critical issue requiring a hard fork update.
  - Collaborated with the team to push out the emergency upgrade (v2024.1.0) for mainnet activation around June 20th.
  - Coordinated with partners to confirm the upgrade and ensure smooth deployment.

- **Report Publication:**
  - Wrote and published a detailed report on the bug and the hard fork upgrade. The full report can be found [here](https://talk.harmony.one/t/harmony-protocol-bug-report-hard-fork-v2024-1-0/24761).

#### Conference Preparation

- **ETH.CC Conference:**
  - Started preparations for the ETH.CC conference in Brussels on July 5th.
  - Signed up for events and planned the trip.

#### Research and Development

- **Derivatives Smart Contracts:**
  - Continued working on derivatives smart contracts, although progress was limited due to the focus on the bug and emergency upgrade.

This week was primarily dedicated to addressing the critical protocol issue and ensuring the successful deployment of the emergency upgrade. Preparations for the upcoming ETH.CC conference and some continued work on derivatives smart contracts.

___
### Weekly Progress Update: 2024-06-07

#### HIP-32 Monitoring and Development

- **HIP-32:**
  - Continued monitoring and coordination of HIP-32 development.
  - Maintained stable devnet and testnet environments.
  - Managed and reviewed multiple PRs to ensure smooth progress.

#### Bug Investigation

- **Critical Issue with Pending Undelegations:**
  - **Issue Summary:**
    - Discovered a critical bug where funds were released but the pending undelegation object was not cleared.
    - This posed a risk of a second release of pending undelegations and potential abuse to mint new ONE tokens.

  - **Actions Taken:**
    - Analyzed protocol behavior and confirmed the bug.
    - Researched fixes to ensure proper clearing of pending undelegation objects.
    - Report will be released shortly.

#### Code Review and PR Management

- **Reviewed PRs:**
  - **Removed Threshold for 10 Epochs (#4671):**
    - Fixed the threshold issue for devnet crosslinks.
  - **Fix for Race Condition in New Block Post-Consensus (#4677):**
    - Addressed potential race conditions during new block post-consensus processing.
  - **Crosslink Heartbeat Verification (#4673):**
    - Ensured crosslink heartbeats are signed and verified correctly across epochs.

#### Research and Development

- **Derivatives Smart Contracts:**
  - Researched, optimized, and deployed derivatives smart contracts using Panoptic.
  
- **Superchain Research:**
  - Investigated the decentralized shared sequencer approach used by Superchain.
  
- **Options and Derivatives Market:**
  - Conducted extensive research on developments in the options and derivatives market.

#### Partnerships and Collaborations

- **Engagements:**
  - Engaged with potential partners, including Partie, DelphiDigital, Coinbase, and Circle.

- **Notable Meetings:**
  - Had a productive sync with Li and discussed potential Web3 game development on Harmony.

This week has been focused on ensuring the stability and progress of HIP-32, addressing critical bugs, and advancing research and development in derivatives smart contracts. Engaging with potential partners and preparing for upcoming initiatives are also key highlights.

___

**Weekly Progress Update: 2024-05-24**<br>
**Leadership and Project Management**<br>

- **HIP-32 Development:**
  - Continued testing and coordination efforts for HIP-32.
  - Reviewed PRs related to HIP-32:
    - **Removed Threshold 10 Epochs #4671:**
      - Removed threshold for 10 blocks to fix devnet crosslinks.
    - **Fix for Possible Race for New Block Post-Consensus Processing #4677:**
      - Addressed potential race conditions during new block post-consensus processing.
    - **Crosslink Heartbeat Verification Through Current Committee #4673:**
      - Ensured crosslink heartbeats are signed by the current leader private key and verified correctly across epochs.

- **Validator Operations:**
  - Improved and implemented changes and configurations for devnode validators.
  - Coordinated and audited new explorer changes to enhance user experience, working closely with Frank.

#### Research and Development

- **Research Paper:**
  - Began writing a new research paper to explore and document innovative developments and strategic insights for Harmony Protocol.

#### Community Engagement and Outreach

- **Event Coordination:**
  - Continued planning and coordination for upcoming community events and engagements during devcon in November.

#### Upcoming Plans

- **Rest and Relaxation:**
  - Scheduled a few days of rest and relaxation next week to recharge and prepare for future tasks.

This week has been focused on advancing HIP-32 development, enhancing validator operations, and starting new research initiatives. Coordination efforts with team members and the community continue to ensure smooth progress and prepare for upcoming events and projects.

___

**Weekly Progress Update: 2024-05-17**<br>
**On-Call Responsibilities:**
* Managed multiple issues related to testnet and mainnet.
* Coordinated the release of the Blockscan Explorer with the Protofire team.
* Primary focus on managing, testing, and fixing issues related to HIP-32 development.

**Crosslink Boot Node Service File**<br>
Troubleshooting Boot Node Issues:
* Addressed Crosslink and Boot Node issues, with a PR from Konstantin focusing on fixes.
* Identified the boot node issue as potentially stemming from the libP2P layer.
* Tested QUIC protocol, various transporters, connection manager, and firewall settings without resolution.
* Investigated metrics to understand the load and connections better, considering limiting boot node connections.
* Planned to test the boot node on a different provider like AWS.
* Discussed proper service file configuration for the boot node.
* Ensured restart configurations were correct, with Soph double-checking for any other triggers.

**Crosslink Validation and Processing:**
* Addressed three crosslink validation issues: using the current committer to sign, forcing crosslinks due to no new blocks, and outdated thresholds.
* Fixed the first two issues and continued work on the third.
* Reviewed pending crosslinks during the snapshot DB restoration to mainnet.

**Technical Discussions:**
* Reviewed PRs and discussed ongoing updates for testnet and partner networks.
* Analyzed the process costing heartbeat message and its functionality.
* Monitored progress on boot nodes and reviewed pull requests.
* Discussed the testnet explorer running on Blockscout and plans for Mainnet.

**Research and Development**
    
**Coinbase Rosetta:**
* Updated and tested Coinbase Rosetta documentation and integration (https://docs.cdp.coinbase.com/rosetta/docs/welcome/).
* Worked on the Coinbase listing application with team members.

**Validator Operations:**
* Conducted extensive testing on current validator build operations.
* Coordinated the update and upgrade of multiple modules and libraries to address ongoing issues.

**Community Engagement and Outreach**

**Event Planning:**
* Researched possible venues and locations in Bangkok for Devcon in November to support the Harmony community.<br>

This week has been marked by significant troubleshooting and coordination efforts, particularly related to HIP-32 development and validator operations. Focusing on technical configurations and community planning ensures ongoing progress and readiness for upcoming events and network updates.

___
**Harmony Protocol Q1 2024 Performance Report**

Q1 of 2024 has been a period of significant advancements and solid growth for the Harmony Protocol, underpinned by strategic technical leadership, robust research initiatives, and active community engagement. As the Lead Protocol Engineer and Researcher, my contributions spanned various critical aspects of our project's development, from leading protocol discussions to conducting vital research that will shape the future of our network. This report outlines the essential areas of my involvement and their impact on the Harmony ecosystem.

**Leadership and Project Management**<br>
My leadership was instrumental in steering the protocol's development and ensuring alignment with our strategic goals:
* **Lead Protocol Meetings:** Regular protocol discussions are convened to align development priorities, tackle technical challenges, and foster a cohesive engineering culture.
* **Code Reviews and Branch Management:** Spearheaded code review sessions and managed multiple development branches, significantly improving our codebase quality and facilitating smoother future development.
* **Jira Progress Boards Organization:** Implemented SCRUM-based Jira boards to streamline our engineering efforts, enhancing team productivity and project tracking.

**Research and Development**<br>
Research forms the backbone of our protocol's innovation:
* **Research Reports:** Delivered comprehensive research reports on upcoming incentives, guiding our strategic planning and decision-making processes.
* **Network Incident Reports and HIP-32 Proposal:** Authored detailed incident reports and reformed the HIP-32 proposal, contributing to our network's resilience and governance model refinement.
* **Smart Contract Audits:** Conducted extensive audits on key smart contracts (Lend, Swap, Liquidity), providing critical insights to fortify our network's security and reliability.

**Community Engagement and Outreach**<br>
Actively engaged with the blockchain community, reinforcing Harmony's presence and fostering partnerships:
* **Global Blockchain Events:** Participated in leading blockchain events (DevConnect, ETHDenver, ETHLondon, ETHTaipei, ETHSeoul), representing Harmony and engaging with community members and partners.
* **Mentorship:** I have served as a mentor at various events, onboarding new engineers to Harmony and broader EVM chains and strengthening our developer community.
* **Project Outreach:** Led outreach for stealth projects considering building on Harmony, notably Partie/AWS, broadening our ecosystem and fostering innovation.

**Incentive Management and Gaming Initiatives**<br>
Managed vital initiatives to drive protocol adoption and engagement:
* **Protofire Incentives Management:** Oversaw the Protofire incentives, ensuring their effective execution and alignment with our lending and swapping mechanisms.
* **Web3 Gaming Research:** Conducted research to support the development of a Web3 game, aiming to combine fun with functional engagement to attract more users to our network.

Q1 2024 has been marked by concerted efforts to enhance Harmony Protocol's technical foundation, governance, and community engagement. My leadership across these domains has driven progress and laid a robust foundation for our ecosystem's continued growth and evolution. As we look ahead, I am committed to sustaining this momentum, fostering innovation, and further solidifying Harmony's position as a leading blockchain platform.

---

**2024-02-07 Wed:** Most of my time has been spent auditing, testing, and reviewing our lending initiatives, as well as supporting the protocol team on our upcoming release. Due to some of our governance changes and Oracle providers on Harmony, there have been many improvements to our compound fork in the last few weeks. Besides that, I've continued to support our gaming efforts and assist Adam, but most of my workload this month will be ETHDenver related. 

**2024-01-16 Tue:** The holidays are over, and it's been a busy and productive period for the team. We're gearing up for the much-anticipated 2024.1.0 forking update, which promises to introduce leader rotation alongside many enhancements to the blockchain. This update, encapsulated in pull request #4546, culminates extensive development efforts, including fixes for memory leaks, dead code, data races, and numerous optimizations and cleanups across various issues from #4539 to #4611. These improvements refine the existing functionalities and lay the groundwork for more robust and efficient operations.

This release phase, however, hasn't been without its challenges. Rigorous testing has highlighted areas needing further improvement, driving us to enhance the codebase for increased security and bug-free performance. My contributions have been centered on conducting multiple code reviews and validator tests, ensuring that each update aspect is thoroughly vetted and optimized.

In addition to these technical endeavors, I have also been revising the paper I mentioned. Though demanding, the revision process is paving the way for the release of a technical paper that will outline our ambitious plans for 2024. This paper will detail the upcoming protocol enhancements and highlight the exciting developments we have in store for the Harmony ecosystem.

**2023-12-18 Mon:** At Palo Alto Office last week. Besides meetings on upcoming improvements and the potential development of a game, the week primarily consisted of working on fixing a bug during the protocols undelegation process. The Hard Fork update was released last Friday, and the fork happened Sunday. A full report will be released in the coming days.

---
2023-12-13 Wed: Engaged in office-based meetings and synchronization sessions, focusing on technical improvements and potential enhancements to the blockchain. This involved collaborative discussions with the team, aiming to identify and plan for future advancements.

Addressed and researched several protocol issues, with updates poised for release shortly. The nature of these fixes suggests the possibility of a hardfork, with more details to be disclosed in the near future.

Progressed with the audit of the compound fork, completing code development and initiating comprehensive testing and review. Collaborating closely with the Protofire team to ensure thorough verification of the code.

Continued development of the 1-second finality code, successfully pushing the branch and commencing testing on localnet. This marks a significant step towards enhancing transaction finality speeds.

Initiated leader rotation testing on the devnet, a critical phase in ensuring the robustness and reliability of this feature within the network.

Conducted multiple code reviews, focusing on resolving inconsistencies in hash calculation across different API versions and activating leader rotation on devnet. Notably reviewed and contributed to the Initial Version of Fast Sync #4465, a significant update aimed at reducing validator syncing time.

Authored and published a comprehensive guide for users affected by hacked wallets, providing crucial assistance and information to the community. The guide is available at Harmony GitHub Issue #4585.

Continued to develop the research paper mentioned in the last update, dedicating time and effort to this ongoing project.

---
2023-12-1 Fri: Progressed on a utilization and technical paper slated for mid-December release, focusing on current initiatives and potential future enhancements to the Harmony protocol. This involves in-depth analysis and planning for both existing and prospective protocol developments.

Conducted a code review and successfully removed an outdated check, enhancing the Harmony codebase's efficiency and reliability. The specific update can be found in pull request #4574.

Served as the on-call engineer, addressing and resolving various DevOps outages and issues promptly, ensuring uninterrupted operations and system reliability.

Advanced the development of 1-second finality code, which is still in progress and not yet committed. Collaborated with colleague Adam during an in-person workday, acknowledging the need for further research and development.

Participated in weekly developer syncs and private meetings, focusing on addressing stage sync and leader rotation issues, along with other protocol improvements and bug fixes. These sessions were critical for identifying and solving current challenges in the Harmony protocol.

---

2023-11-20 Mon: Attended Ethereum Foundation's Devconnect in Istanbul, actively participating in panel discussions and fireside chats alongside notable figures like Vitalik Buterin. Engaged in insightful roundtables with Geth, zk, and Consensus teams. I established valuable connections with former Harmony colleagues Suede and Qi from EthStorage, Bay Area's Foresight Ventures members, and engineers from potential partner organizations Socialscan and DIA.

Completed a detailed preliminary audit of Compound's smart contracts, revealing critical issues stemming from removing the cONE token. This removal has caused significant problems across all markets, including a division by zero error, leading to market crashes. The findings and subsequent recommendations were thoroughly documented, aiming to address and rectify these issues.

Reviewed and provided feedback on several key pull requests for the Harmony blockchain. These PRs focused on vital fixes and enhancements, such as resolving last mile block issues, improving block data removal processes during rollbacks, and correcting block insertion in legacy sync. The PRs reviewed include: Fix for last mile block #4567, Rollback removes physically block data from db #4568, and Fix the block insertion in legacy sync for existing block #4565.
