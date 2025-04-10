2025-04-05 Sat: I completed [PR 4876](https://github.com/harmony-one/harmony/pull/4876), which simplifies the staged stream sync by removing the last-mile blocks stage. Previously, this stage duplicated the work already handled by the helper through a channel that receives blocks directly from consensus. The PR delegates this responsibility entirely to the helper, reducing redundancy and streamlining the sync process. The change was reviewed and successfully merged by the team.

This week, I opened [PR 4877](https://github.com/harmony-one/harmony/pull/4877), which refactors the block body download loop to adopt a pull-based worker model. The previous approach could lead to deadlocks, especially when workers failed during the processing of final batches. The new model allows workers to explicitly request tasks when ready, eliminating coordination issues and busy waiting. It also introduces improved error handling using `gbm`'s retry mechanism, tracks active workers using an atomic counter, and ensures a clean shutdown once all work is complete. This refactor enhances both the reliability and maintainability of the download stage.

---

2025 Q1 Review 

During Q1 2025, I focused on improving Harmony’s P2P layer, stream sync, and network stability through multiple optimizations, bug fixes, and new features. Notable improvements include refining stream sync logic, optimizing reconnections, enhancing block request handling, and reducing memory usage. Several PRs addressed syncing inefficiencies, protocol mismatches, and connectivity issues, significantly improving network performance. 

Key updates include a new reconnection mechanism for streams, adaptive backoff for peer advertisements, and better error handling for block downloads. I also improved macOS development support by introducing cross-platform builds and streamlined setup instructions. Additionally, major updates to the protocol ID system, epoch sync handling, and explorer node connectivity have enhanced overall network resilience. 

Bug fixes included resolving deadlocks, context deadline exceeded errors, and race conditions affecting syncing. With these updates, syncing efficiency, stability, and resource management have greatly improved, making the network more robust and scalable.

---

2025-03-29 Sat: I updated the default devnet configurations through [PR #4874](https://github.com/harmony-one/harmony/pull/4874). In devnet, explorer nodes were often syncing only with each other due to a strict two-connection limit, preventing them from obtaining the actual chain height from validators. This PR increases the minimum number of connections to three, ensuring better connectivity and improving synchronization reliability.  

I also worked on [PR #4876](https://github.com/harmony-one/harmony/pull/4876), which optimizes staged stream sync by removing redundant processing of last-mile blocks. Previously, both the last-mile blocks stage and a helper component handled final block delivery, leading to duplication. This PR eliminates the redundant stage and delegates the task entirely to the helper, streamlining the sync process and reducing unnecessary overhead.  

---

2025-03-22 Sat: PTO (2025-03-18 - 2025-03-21) I continued refining stream sync optimizations and code refactoring. I created and deployed **[PR #4873](https://github.com/harmony-one/harmony/pull/4873)**, addressing a critical issue in epoch sync caused by protocol ID mismatches. Previously, shard nodes relied on a separate protocol ID to discover beacon peers, but stream connections were later rejected due to inconsistencies. 

This PR introduces a dedicated protocol for beacon validators to manage epoch sync independently. The P2P host now supports multiple protocols, each operating with its own stream manager and set of discovered nodes. This resolves the previous discovery issues and ensures stable connections for epoch sync. The PR was reviewed, merged, and successfully deployed to devnet.  


---

2025-03-15 Sat: I completed and deployed **[PR #4866](https://github.com/harmony-one/harmony/pull/4866)** to devnet, introducing significant improvements to Stream Management. This update enhances reconnection logic, optimizes buffer usage, and improves block request handling, leading to better stability and performance. Streams now support a reconnection mechanism that attempts up to three retries with short intervals before failing. Memory usage has been optimized by improving buffer pooling, reducing unnecessary allocations, and enhancing overall efficiency. Block request timeouts have been adjusted to fix context deadline exceeded issues, while unexpected blocks in the database are now properly validated and handled with appropriate head adjustments. Additionally, the block height estimation mechanism has been refined for greater accuracy in long-range syncing.  

The PR was reviewed, merged, and deployed to devnet, and investigations confirm that block request timeouts and context deadline exceeded issues have been resolved. Currently, I am focusing on fixing connection issues between shards. While shard nodes can see and connect to each other, challenges remain in epoch chain synchronization and cross-shard syncing, which are now my primary focus.  

---

2025-03-08 Sat: I continued working on **stability improvements for StreamNet and Explorer nodes**. Several **critical bug fixes and optimizations** were implemented to enhance the syncing process. While **syncing performance has improved**, further investigations are ongoing to resolve remaining issues.  

- **[PR #4846](https://github.com/harmony-one/harmony/pull/4846)** improved the **advertise function** with **dynamic timeout adjustments and adaptive backoff**. Previously, fixed 60s timeouts caused unnecessary delays. Now, timeouts increase incrementally up to 5m, and retries follow a progressive backoff strategy. This ensures **better adaptation to network conditions** while **preventing excessive delays and retries**.  

- **[PR #4865](https://github.com/harmony-one/harmony/pull/4865)** fixed a **deadlock in the downloader loop** by resolving a double-lock issue in **syncMutex**. This also optimizes **downloadC signal handling**, preventing excessive goroutine creation and memory usage.  

These improvements **enhance syncing reliability, reduce delays, and improve network efficiency**. Work is ongoing to further refine the synchronization process.  

---

2025-03-01 Sat: I focused on improving **synchronization efficiency, error handling, and stream stability** in the P2P layer. Several key PRs were merged, bringing **significant performance optimizations** to the syncing process.  

- **[PR #4861](https://github.com/harmony-one/harmony/pull/4861)** refactored the **staged stream sync downloader loop** to enhance concurrency and **eliminate sync overlaps**. Now, new syncs are only triggered if no sync is already in progress, preventing redundant operations.  

- **[PR #4862](https://github.com/harmony-one/harmony/pull/4862)** introduced **robust retry logic, improved stream tracking, and better error handling** for **bad block re-downloads**, ensuring more reliable data recovery.  

- **[PR #4863](https://github.com/harmony-one/harmony/pull/4863)** removed the **staged DNS sync** logic, simplifying sync behavior and improving maintainability.  

- **[PR #4855](https://github.com/harmony-one/harmony/pull/4855)** optimized the **staged stream sync block download process**, resolving a **nil pointer issue**, improving block hash management, and introducing a **dedicated thread for database reads**, significantly **boosting performance and concurrency**.   

---

2025-02-22 Sat: My primary focus remained on improving the **P2P layer, stream managers, and syncing modules** to enhance performance and stability. However, I also introduced two PRs aimed at **macOS users**, significantly simplifying the development process for them.  

**[PR #4851](https://github.com/harmony-one/harmony/pull/4851)** updates the **README.md** with macOS-specific configuration instructions. This change provides **clear, step-by-step guidance** to help macOS developers set up their environment effortlessly. By addressing common setup issues, this update reduces onboarding time and streamlines the workflow for macOS users.  

**[PR #4852](https://github.com/harmony-one/harmony/pull/4852)** introduces a **cross-platform build solution**, allowing macOS users to build **Linux static binaries** for the Harmony project. Since macOS lacks native support for Linux binaries, this PR provides a **Docker-based approach** to generate **fully functional Linux executables**. A new shell script automates the build process inside a **Docker container**, making cross-compilation seamless. Additionally, a **Makefile command** (`linux_static_from_macos`) enables developers to initiate the build with a single command. This change eliminates the need for complex manual setups, making development more efficient across platforms.  

On the **P2P side**, I introduced several crucial improvements to enhance network reliability, reduce resource waste, and improve synchronization stability.  

**[PR #4856](https://github.com/harmony-one/harmony/pull/4856)** fixes an issue where the **stream manager** was operating with an outdated list of streams, causing inefficiencies and missed updates. Now, the system properly signals the stream feed when a new stream is added from the **reserved list**, ensuring the request manager always operates with the latest and most relevant data.  

**[PR #4857](https://github.com/harmony-one/harmony/pull/4857)** introduces **monitorStreamHealth**, a crucial function that **monitors active streams** in the request manager. If no valid peers remain for a certain threshold, the system **automatically cancels pending requests** to prevent overload and unnecessary resource usage. This watchdog mechanism significantly improves **network resilience**, preventing requests from getting stuck when no reachable peers are available.  

**[PR #4853](https://github.com/harmony-one/harmony/pull/4853)** improves the **P2P layer** by introducing a **cooldown mechanism** for removed streams. Previously, if a stream was removed due to failure, the system could **immediately reconnect** to the same stream in the next discovery cycle, leading to potential issues if the peer was still unsynced or invalid. To prevent this, the update introduces a **60-minute cooldown period**, ensuring the system does not reconnect to unreliable streams too soon. Additionally, a new **RemovalInfo** structure tracks removal timestamps and expiration times, enforcing better **stream management** and **sync stability**.  

These **performance improvements** significantly enhance **network reliability**, reduce **resource consumption**, and make the system more **adaptive** to dynamic network conditions.

---

2025-02-15 Sat: I created, reviewed, finalized, and merged multiple PRs.  

- **[PR #4846](https://github.com/harmony-one/harmony/pull/4846) Merged:** This PR addresses the connectivity issue of **explorer nodes** by adding them to the protocol ID, allowing them to discover and connect with other nodes sharing the same protocol ID.  
- **[PR #4839](https://github.com/harmony-one/harmony/pull/4839) Finalized:** Reviewed and updated with a new commit, now ready for merging.  
- **[PR #4845](https://github.com/harmony-one/harmony/pull/4845) Finalized:** Addressed review concerns by adding a few commits, making it ready for merging.  
- **[PR #4847](https://github.com/harmony-one/harmony/pull/4847) Created:** This PR refactors **staged stream sync loggers** by introducing a dedicated **local logger for each stage**. This enhancement improves log traceability, making it easier to debug and filter logs using **Loki** or other monitoring tools.  
- **[PR #4848](https://github.com/harmony-one/harmony/pull/4848) Created:** Updates the **advertisement logic** in the protocol, making it more **reliable and adaptive**. This PR introduces a **retry mechanism, dynamic timeout adjustments, peer discovery tracking, and optimized sleep time adjustments** to enhance peer-to-peer connectivity.  

Additionally, I am focusing on fixing a **race condition** affecting **explorer nodes**. Once resolved, we plan to **upgrade and restart** explorer nodes on **streamnet** to improve stability and performance.  

---

2025-02-08 Sat: I completed and finalized [PR #4841](https://github.com/harmony-one/harmony/pull/4841), addressing issues and refactoring some parts of the code for better integration and performance. This PR introduces a **Connection Manager**, a **Connection Gater**, and an **Extended Peer Store**, enhancing Harmony’s P2P network management.  

We also continued investigating the **stream net** issue affecting explorer nodes, specifically related to block insertion failures. Our deep investigation identified several corner cases:
- **Future Blocks in Explorer Nodes:** Explorer nodes were accepting future blocks that were not the immediate next block during the COMMIT and PREPARE phases. This led to excessive error logs when the sync module was not fully ready. To address this, I created [PR #4845](https://github.com/harmony-one/harmony/pull/4845).
- **Peer Connectivity Issues:** Sometimes, **stream net** nodes fail to discover or connect to each other, and we are still investigating the root cause.
- **Syncing Issue:** In certain scenarios, stream sync nodes stop syncing using the short-range module and are unable to revert to long-range syncing. This issue is under further investigation.  

We are prioritizing these investigations and working on solutions to improve network stability and synchronization consistency.  

---

2025-02-01 Sat:  

We investigated the issue of an unusually high number of known peers. As part of this effort, I created [PR #4839](https://github.com/harmony-one/harmony/pull/4839), which removes streams from the peer store if they fail the sanity check. This change is expected to improve peer management, and we plan to test it on the devnet next week.  

I also conducted a deep study on how other blockchains manage unwanted connections at the P2P layer. Based on this research, I created [PR #4841](https://github.com/harmony-one/harmony/pull/4841), which introduces a **Connection Manager**, a **Connection Gater**, and an **Extended Peer Store**. The base code has been customized and integrated into Harmony’s codebase. While this PR establishes the core functionality, we still need to determine the best way to detect and filter unwanted connections using the Connection Gater.  

Additionally, we encountered an issue on **stream net** affecting explorer nodes. The issue is related to block insertion failures and is currently under investigation. Identifying and resolving this will be a priority moving forward.  

---

2025-01-25 Sat:  

We finalized and released **v2025.0.0**, marking a significant improvement for the project.  

I primarily focused on resolving issues with [PR #4824](https://github.com/harmony-one/harmony/pull/4824). The PR had a fatal error causing tests to fail when one of the localnet nodes restarted. After thorough investigation, I identified and fixed the issue, improving the PR in the process. Following a detailed review by the team, the PR was successfully merged into the dev branch.  

In addition to this, I reviewed several other PRs, closed some older ones, and rebased the latest ones to prepare them for merging. We also had discussions about deploying stream sync on the devnet. The team agreed to start with a limited deployment on "stream net", a subset of nodes in the devnet, to validate its performance and stability.  

During these discussions, we identified another issue at the chain setup level, which is currently under investigation. 

---

2025-01-18 Sat: PTO (2025-01-13 - 2025-01-17: 5 days)

---

2025-01-11 Sat: I finalized [PR #4824](https://github.com/harmony-one/harmony/pull/4824), addressing team feedback, adding tests, and resolving issues. The PR has another small issue; after addressing that, it will be ready to be merged.  

I also introduced a new feature in [PR #4826](https://github.com/harmony-one/harmony/pull/4826), which adds a reserved stream list to the Harmony P2P stream management system. This feature ensures that peer connections can be replaced immediately from a backup pool whenever a stream is removed due to issues like invalid data or connectivity disruptions. By bypassing the traditional peer discovery process, this approach significantly improves recovery times, maintains stable network operations, and enhances resilience, especially in larger networks where delays could disrupt syncing and consensus processes.  

The team identified a RAM usage issue on devnet nodes, where memory consumption kept increasing. After thorough investigation—reviewing node resources, binary flags, peer store, and memdb, it was discovered that the resource manager was disabled. Enabling the resource manager and setting the memory limit to 0 (defaulting to 25% of available RAM) resolved the issue. To further improve this, I created [PR #4827](https://github.com/harmony-one/harmony/pull/4827), which introduces conditional inclusion of the Resource Manager in P2P configurations, ensuring it is added only when explicitly enabled. We are now focused on optimizing resource manager configurations to maintain efficient resource usage.  

---

2025-01-04 Sat: I finalized the staged stream sync code refactor to include a new stage for block hashes, ensuring improved data integrity before downloading block bodies. The changes were submitted as [PR #4824](https://github.com/harmony-one/harmony/pull/4824).  

Additionally, I am exploring an idea to introduce a reserved list of peers for stream sync. This feature would replace disconnected peers instantly with ones from the reserved list whenever connectivity issues or invalid responses occur. Implementing this will enhance the consistency and reliability of stream sync operations.  

---

2024-12-28 Sat: I continued working on stream sync, focusing on the block hash stage. This enhancement introduces a new stage where block hashes are downloaded from all connected nodes before retrieving block bodies. By calculating the correct hash first, this ensures data integrity and reliability in the block download process.  

The progress on this feature is about 60%, and I aim to complete and test it within the next two weeks. Once finalized, it will improve the efficiency and accuracy of stream sync operations.  

---

2024-12-21 Sat: I returned to working on stream sync and investigated an issue affecting one of the devnet nodes. The investigation revealed that the Mdbx database required an upgrade, as newer versions resolved a memory limit issue impacting the Erigon database. I am now focusing on upgrading stream sync and have discussed the deployment plan with the team for devnet implementation.  

Additionally, I created [PR #4818](https://github.com/harmony-one/harmony/pull/4818) to improve debugging for localnet setups with external validators and multi-BLS keys. This PR introduces a new command to the Makefile, allowing terminal logs to be more accessible during local net debug with multi bls keys.  

Work on stream sync upgrades and testing will continue this week, with further collaboration planned for ensuring a smooth deployment.  

---

2024 Q4 Review

This quarter, I tackled several critical areas to improve network stability, performance, and decentralization. A lot of my focus was on addressing **stream disconnectivity issues** and enhancing the **P2P layer**. I optimized the way streams handle connections and refactored parts of the system to make error handling more resilient. Stream concurrency and lock management were improved, along with significant updates to the **Staged Stream Sync module**, making it more reliable and easier to maintain. I also added support for **Trusted Nodes** in the P2P host, enhancing the flexibility and security of the network.  

Another big milestone was the **successful HIP32 hardfork**, which brought the network much closer to full decentralization. It was a proud moment to see the community and the infrastructure align for such a critical upgrade.  

On the consensus side, I conducted an in-depth review of the **leader rotation process**, identified edge cases, and implemented fixes to improve reliability. I also addressed issues with **multi-BLS validators**, such as improving quorum calculations and fixing problems with multiple block proposals. These changes ensure smoother operations for validators and better overall performance.  

Finally, I resolved a resource limitation issue impacting **boot nodes**, making them more efficient at handling traffic. Alongside this, I worked on adding capacity to support concurrent requests across streams and refined the **P2P muxers** for better performance. This quarter was all about solving major pain points and laying the groundwork for a more decentralized and reliable network.

---

2024-12-14 Sat: I worked on resolving an issue with multi-BLS key validators in the consensus module. These validators, when retaining leadership, could create multiple block proposals, leading to potential network crashes. To address this, I made the [PR #4810](https://github.com/harmony-one/harmony/pull/4810) last week, but later I drafted that PR and created a new one [PR #4811](https://github.com/harmony-one/harmony/pull/4811), which targets the root cause and refines the logic to verify if the leader has changed or if the previous leader belongs to the same node in multi-BLS key scenarios. It also ensures the consensus module avoids redundant leadership actions for the same node and updates logs to improve debugging and clarity around leader transitions.  

In addition, I simplified the leader quorum calculation process for the commit and prepare phases with [PR #4813](https://github.com/harmony-one/harmony/pull/4813). The update replaces dynamic quorum checks with a state-based approach, using the `State` structure to store the last quorum-achieved block. This improves the efficiency and reliability of quorum handling, ensuring better consistency across consensus operations.  

Lastly, I worked on resolving a resource limit issue affecting boot nodes. I introduced a resource manager to the P2P configurations through [PR #4815](https://github.com/harmony-one/harmony/pull/4815). This addition helps mitigate the issue by providing better control over resource usage, enhancing the stability and performance of the network.  

---

2025 Goals:

Stream Sync and State Sync:
One of my top goals is to bring Stream Sync to mainnet, enabling validators to communicate directly through streams rather than relying on DNS nodes. By releasing Stream Sync, DNS nodes will only serve as a backup, significantly reducing their load and improving the network's efficiency. This will make Harmony’s network fully decentralized, more resilient, and better equipped to handle scaling challenges.

Leader Rotation V2:
I am committed to completing and deploying Leader Rotation V2, to enhance stability, fairness, and efficiency. This upgrade will not only enhance network reliability but will also reduce potential vulnerabilities and ensure the network operates seamlessly under all conditions. I will also conduct deeper studies on [leader rotation scoring](https://github.com/harmony-one/harmony/issues/4797) to determine the's feasibility of implementatino on Harmony.

Consensus Stability:
Another key priority for me is enhancing the stability of Harmony’s consensus mechanism. A robust, bug-free consensus is essential for ensuring the network's reliability and security. I will focus on identifying and resolving any [remaining issues](https://github.com/harmony-one/harmony/issues/4796) while optimizing performance to meet the needs of a rapidly growing user base.

Supporting Improvement Proposals:
Finally, I aim to actively support and contribute to new improvement proposals. Whether it’s implementing innovative features or refining existing ones, I want to ensure Harmony remains at the forefront of blockchain technology, offering a platform that developers and users can trust and depend on.


---

2024-12-07 Sat: I focused on addressing the issue of multiple block proposals being generated by multi-BLS key validators. This issue can be replicated in the localnet by adding multi-BLS key validators and enabling leader rotation.

To tackle this, I created **[PR #4810](https://github.com/harmony-one/harmony/pull/4810)**, which introduces a fix for the problem where multi-BLS key leaders occasionally triggered multiple block proposals simultaneously. The solution includes a **Proposal Manager** and a **Queue System** to ensure that only one block proposal is processed at a time.

The team and I are still testing this fix and exploring additional solutions to fully resolve the issue. Progress is ongoing, and I look forward to sharing updates as we make further advancements.

---

2024-11-30 Sat: We successfully finalized and merged PR #4789 and PR #4801 into the `dev` branch. I also focused on investigating a persistent issue in the localnet. For multi-BLS key validators, the network gets stuck after a certain number of blocks when leader rotation is enabled. Logs revealed that multiple block proposals were being generated. I documented the entire block proposal logic and shared it with the team for collaborative investigation. The issue appears to occur only when a new leader with multiple BLS keys is selected, and our investigation is ongoing.

During this time, I identified a few inconsistencies in the consensus logic. To address these:

- **[PR #4805](https://github.com/harmony-one/harmony/pull/4805)**: I added a check for the existence of a faucet key before adding a new external leader. This change ensures proper error handling and exits the test with a clear message if the faucet account is missing.
- **[PR #4806](https://github.com/harmony-one/harmony/pull/4806)**: I noticed inconsistencies in quorum checks across different parts of the code, specifically in `IsQuorumAchievedByMask`. This PR introduces a consistent approach but may require a hard fork to implement. For now, I have submitted it as a draft to facilitate team discussion.

Additionally, I created **[PR #4807](https://github.com/harmony-one/harmony/pull/4807)**, which introduces new configurations to adjust the number of blocks per epoch for the localnet. This PR also optimizes the `Makefile` by removing unnecessary pre-external processes.

---

2024-11-23 Sat: I focused on finalizing two critical PRs that address leader rotation and quorom calculation edge cases.

The first one is [PR #4789](https://github.com/harmony-one/harmony/pull/4798), which enhances the leader rotation logic to tackle previously unaddressed edge cases. I updated the logic and also implemented tests to validate the new logic, including scenarios that demonstrated the shortcomings of the old version and confirmed that the new approach resolves these issues. This PR introduces changes that require a hard fork for full network-wide consistency. The hard fork epoch is yet to be determined, pending team discussions.

The second [PR #4799](https://github.com/harmony-one/harmony/pull/4799), focuses on improving consensus logic for validators with multiple BLS keys. It addresses issues where quorum is achieved immediately, causing delays in phase transitions. I added a function to detect and handle immediate quorum during the first batch of signatures or commits, ensuring smoother transitions. I replicated same changes for Prepare phase as well. It is compatibile with both single-BLS and multi-BLS validator setups.

Both PRs are now complete and proper tests have been added and awaiting team review. I look forward to receiving feedback and collaborating with the team to ensure these changes are working as expected. These updates are expected to bring significant improvements to leader selection and consensus processes.

---

2024-11-16 Sat: I conducted an in-depth analysis of the leader rotation logic and identified several corner cases and improvements, which I reported in [Issue #4796](https://github.com/harmony-one/harmony/issues/4796). To address some of these issues, I created [PR #4789](https://github.com/harmony-one/harmony/pull/4798). 

This PR refines the `NthNextValidator` function in the leader rotation logic, ensuring robustness by addressing previously unhandled edge cases:
- **Wrap-around Handling:** The original function risked skipping the first validator when the list wrapped around. The updated logic introduces an `attempts` counter, ensuring that no validator is skipped during wrap-around scenarios.
- **Missing Current Leader Key:** If the current leader's `pubKey` wasn't found in the validator list, the original code could crash. The refactored version logs this error and gracefully falls back to the first validator in the list, maintaining stability.
- **Repetitive Selection Prevention:** The revised function avoids repeatedly selecting the same leader by ensuring the returned validator is distinct. A limit on `attempts` prevents infinite loops, and warnings are logged when no unique validator is found.
These changes require a hard fork (HF) for consistency across the network, as they modify validator selection. The hard fork epoch is currently set to "TBD" to allow for further discussion and coordination.

I proposed a new feature to score leaders based on their performance in a [leader scoring improvement proposal](https://github.com/harmony-one/harmony/issues/4797). This feature would assign higher probabilities for future leader selection to validators with better performance, encouraging fairness and reliability.

I created a new [PR #4799](https://github.com/harmony-one/harmony/pull/4799) to address an issue with consensus quorum calculation for multi-BLS key validators. The PR corrects how quorum is determined, ensuring that multi-BLS validators are accounted for accurately during consensus formation. This PR is currently in draft and will be reviewed by the team. I will continue working on it next week.

I also worked on an issue where leaders experienced delays in block production. Logs revealed that leaders were occasionally announcing blocks multiple times, causing delays. With Soph's assistance, we analyzed the logs, and I created a new PR [PR #4801](https://github.com/harmony-one/harmony/pull/4801) to enhance logging in the `announce` function to trace its invocations. This investigation is ongoing.

I continued working on the stream sync module, focusing on refactoring the block header stage. The refactor ensures that nodes use block hashes rather than block numbers, improving the accuracy of received blocks and enhancing neighbor evaluation for invalid data. This is a significant update to the staged stream sync, and progress is now over 50%.

---

2024-11-09 Sat: Following the successful HIP32 hardfork, we encountered an issue where certain leaders experienced delays in block production, causing brief interruptions on the beacon chain (usually under 15 seconds). To investigate further, I created a [PR #4791](https://github.com/harmony-one/harmony/pull/4791) to enhance log messages, adding the current block hash in `setupForNewConsensus`. This update provides clearer logs, making it easier to distinguish between the consensus block leader and previously produced blocks.

I conducted an in-depth review of the leader rotation code and shared insights with the team, identifying areas for improvement and potential corner cases. For instance, ensuring that leaders are fully synchronized before proposing new blocks is crucial. I am also developing comprehensive documentation on these leader rotation corner cases and improvements, which I will present to the team early next week to facilitate further enhancements.

---

2024-11-02 Sat: The successful HIP32 hardfork enhances the decentralization of the Harmony network by granting complete governance to the community, making the Harmony chain fully decentralized. So far, the chain is performing smoothly, producing blocks as expected. We are closely monitoring the network and working on an issue about low number of to_sign for a few validators. We plan to confirm stability after a few successful epochs.

Another issue was blocks were being produced with a `0x0` hash. After discussions with the team, we identified that state resets were being triggered, potentially due to the syncing modules' `BlocksSynchronized` signal resetting the consensus state. To address this, I created [PR #4787](https://github.com/harmony-one/harmony/pull/4787). With this change, the `BlocksSynchronized` signal now triggers only when new blocks are added to the chain during the syncing process, preventing unnecessary consensus resets and ensuring that resets occur only when truly required. This PR could help to resolve the issue and it is still under tests.

Additionally, I worked on improving block commit logic. I submitted [PR #4786](https://github.com/harmony-one/harmony/pull/4786), which refines the `finalCommit` function in the consensus module. This PR enhances logging and introduces return statements after error checks to halt processing in case of critical errors, ensuring the function exits immediately upon encountering any issues.

---

2024-10-26 Sat: The team reviewed and approved [PR #4762](https://github.com/harmony-one/harmony/pull/4762), which has now been merged into the `dev` branch. Early testing shows improvements in syncing performance.

Additionally, [PR #4772](https://github.com/harmony-one/harmony/pull/4772) was reviewed. After resolving all merge conflicts, it is now ready for merging. Together, these two PRs bring good enhancements to stream handling and stream sync mechanisms.

A significant development was [PR #4777](https://github.com/harmony-one/harmony/pull/4777), which introduces support for Trusted Nodes in the P2P Host. This update addresses stream sync concerns by implementing trusted nodes, allowing the network to prioritize these nodes for more stable and secure connections. By designating certain peers as trusted, we maintain reliable connectivity with critical, verified nodes, reducing the likelihood of interactions with potentially malicious peers. This trusted node list is configurable, allowing network administrators to define it through configuration files. While the PR has passed unit tests, it will be validated further in the dev-net environment with a mix of trusted and regular peers to ensure reliable performance.

Lastly, I worked on [PR #4780](https://github.com/harmony-one/harmony/pull/4780), which adds capacity to each stream to support concurrent requests by giving each stream peer its own queue. This enhancement promises significant performance improvements, although it is still in progress and further testing is needed to ensure stability.

---

2024-10-19 Sat: I added a few commits to improve [PR #4762](https://github.com/harmony-one/harmony/pull/4762). The new commits focused on improving concurrency handling and stream shutdowns. The team has started reviewing the PR.

Additionally, I created another [PR #4772](https://github.com/harmony-one/harmony/pull/4772). This PR introduces significant enhancements to the concurrency management and lock handling in the Staged Stream Sync module. By replacing `sync.Mutex` with `sync.RWMutex`, the module now supports concurrent read access, boosting performance for read-heavy operations. The scope of locks has been minimized to reduce contention, especially in high-frequency functions like `Get()` and `List()`. 

To improve the shutdown process, extra checks have been added to prevent double closure of channels, along with new locking mechanisms to ensure state changes are synchronized during shutdown. This results in a smoother shutdown process and helps prevent race conditions when terminating active processes. Clearer documentation and error messages have also been added for better consistency and reduced confusion.

These changes collectively improve the performance, reliability, and maintainability of the Staged Stream Sync module by ensuring more efficient resource management, reducing the likelihood of race conditions, and allowing concurrent operations to proceed more smoothly.

The next focus was the issue with MDBX. After investigation, I found that the issue was common with Erigon DB and was resolved in later versions. After discussions with the team, we concluded that updating the DB requires updating Go to version 1.23. I created another [PR #4773](https://github.com/harmony-one/harmony/pull/4773) to implement this, though it still requires fixing Travis issues. We're currently awaiting the team's decision, as this update may impact other parts of the core.

---

2024-10-12 Sat: I continued working on P2P layer improvements with [PR #4762](https://github.com/harmony-one/harmony/pull/4762). This PR brings several key enhancements to P2P stream handling and Stream Sync, aimed at improving stability, error handling, and optimizing the codebase.

Key improvements include enhanced stream error handling for better visibility, optimizing pickAvailableStream to search for other streams when one fails, and refactoring the stream request manager with a Safe Map for thread safety. I've also improved the logic for switching between short-range and long-range syncing, optimized computeLongestHashChain and its whitelist, and refined countHashMaxVote for accurate vote calculations.

New configurations were added to staged stream sync, along with fixes for Beacon Node and Epoch Chain detection. Metrics were introduced for better monitoring of stream sync, and lock management and concurrency were enhanced. Additionally, node roles are now passed through the stream protocol for better context, and the stream sync short-range helpers were refined. The shutdown and cooldown processes for streams were improved, along with a comprehensive refactor of the stream manager for better readability and maintainability. Finally, I added more meaningful logs while cleaning up unnecessary log entries. 

The PR is now finalized and ready for team review. We'll be testing these changes on devnet this week.

---

2024-10-05 Sat: I continued working on **issue #4789**, which involves addressing stream disconnectivities. A series of tests were conducted to identify the root cause, and several improvements were implemented across key areas which are mentioned on my last week update. Despite the efforts, the issue persisted. I decided to revert recent commits one by one to trace the problem and eventually identified that the update on **P2P Host's Muxers** was the root cause. This led to the creation of [PR #4764](https://github.com/harmony-one/harmony/pull/4764), which removes the use of the **mplex muxer** for localnet and configures it to exclusively use the **Yamux muxer**. This adjustment resolved stream disconnectivity issues in the localnet.

During the tests, I also discovered an issue related to the retrieval of **non-existent crosslinks**. This prompted [PR #4765](https://github.com/harmony-one/harmony/pull/4765), which introduces a validation check for the **Crosslink Epoch** before attempting retrieval, effectively preventing errors from attempting to access non-existent crosslinks.

I am also actively working on [PR #4762](https://github.com/harmony-one/harmony/pull/4762), which focuses on enhancing and refactoring the **P2P stream layer**. Although the changes have been promising, there is still an outstanding issue causing **slowness in Shard 1 block production**, which will be my main focus in the upcoming week.

---

**Q3 Summary – 2024**

This quarter, I worked on a wide range of tasks, from boot node functionality to fixing issues and enhancements. At the start of Q3, we successfully addressed some of the most pressing issues with boot nodes, stabilizing them after dealing with recurring connectivity problems. This early success set the stage for further improvements throughout the quarter. One of the major accomplishments was **PR #4735**, where I introduced an **RPC server for boot nodes**. This was a huge change, bringing significant improvements to our ability to monitor boot nodes. Previously, boot nodes had no way to expose metadata or provide visibility into connected peers, making it difficult to diagnose and optimize their performance. By adding several new APIs, we now have much better tracking and debugging capabilities for boot nodes. Additionally, I refactored the codebase to separate boot node from Harmony node, making the system more modular and maintainable.

For awhile I worked on errors in crosslink processing. We were dealing with race conditions and missing database keys that were causing instability and database lookup failures. By improving error handling and refactoring the process for managing pending crosslinks, I was able to resolve these issues and reduce unnecessary database lookups. Beyond the major features and bug fixes, I took on several refactoring tasks, including removing unused configurations and functions, optimizing test cases, and ensuring that localnet scripts were functioning as expected. I also updated Go version of the Harmony Go-SDK to 1.22.5, making sure it remained compatible with the latest Harmony binary. At the end of Q3 I started investigating the root cause of stream removal issues. We had noticed that streams were being unexpectedly removed whenever the `getCurrentNumber` request failed, which was affecting overall system performance.

---
2024-09-28 Sat: I primarily focused on issue [#4789](https://github.com/harmony-one/harmony/issues/4749), which involves addressing stream disconnectivities. A series of tests were conducted to identify the root cause, and several improvements were implemented:
- I created a safe map to prevent race conditions in the request manager, ensuring smoother operation.
- Refactored the switching logic between long-range and soft-range syncing for better performance and reliability.
- Enhanced error handling for the "context deadline exceeded" issue, which was a recurring problem.
- Worked on improving timeout functions to avoid unnecessary interruptions.
- Increased the context deadlines to provide more leeway for requests.
- Optimized the use of locks and mutexes to eliminate potential bottlenecks.
- Thoroughly double-checked the code to ensure all improvements aligned with the issue at hand.
- Investigated potential P2P layer overloading, which might be caused by new features like broadcasting voting power and epoch blocks, putting additional strain on the P2P client.
- Added P2P channel capacity to help manage load more effectively.
- Introduced additional logs and analyzed the results to better understand the system behavior.

All of these efforts have been packaged into a draft [#PR4762](https://github.com/harmony-one/harmony/pull/4762). Once I successfully test the changes, I will request a review from the team. Until then, my investigation into the root cause of the issue is ongoing.

---

2024-09-21 Sat: I attended the **Token2049 conference** and several side events, gaining valuable insights into the latest trends and technologies in the blockchain space. This allowed me to stay up-to-date with new developments and better understand the direction of the industry.

---

2024-09-14 Sat: We finalized [PR #4735](https://github.com/harmony-one/harmony/pull/4735). After the team reviewed the code, I removed many unused functions and configurations. The `MetData` structure previously relied on the Harmony node metadata format, which included fields irrelevant to boot nodes. Since boot nodes only use specific fields, I refactored the code to separate boot node metadata from Harmony node metadata. I also refactored peer info, and after thorough testing, the code was merged into the dev branch. As a result, we now have three new RPCs for boot nodes.

Additionally, I helped resolve a Crosslink issue where we encountered an `error: leveldb not found`. I fixed several race conditions, added logs for debugging, and refactored the process crosslinks function to handle maximum pending crosslinks. I also added error handling for non-existent pending crosslink keys. These changes were pushed in [PR #4754](https://github.com/harmony-one/harmony/pull/4754).

I further improved the pending crosslinks removal process. Previously, the code attempted to delete pending crosslinks older than 10 epochs. However, if the crosslinks weren't added to the database within the first 10 epochs, it could lead to a `leveldb: not found` error. This issue was resolved by skipping pending crosslink checks during the first 10 epochs, preventing unnecessary database lookups and potential errors.

Lastly, I started investigating [issue #4749](https://github.com/harmony-one/harmony/issues/4749), where P2P streams were being removed. The removal is expected when the `getCurrentNumber` request fails multiple times, triggering stream replacement. The main concern now is determining why the `getCurrentNumber` request is failing in the first place, and I am investigating to identify the root cause.

---

2024-09-07 Sat: The team reviewed [PR #4735](https://github.com/harmony-one/harmony/pull/4735), and I addressed the merge conflicts caused by changes in the dev branch that needed to be replicated in this PR. Additionally, per the team's request, I removed all unused configurations and functions. I also fixed the tests, and the PR is now finalized, with a scheduled merge expected early this week.

I encountered an issue while running localnet, which Soph helped me to resolve it. This took a few days as I tested multiple solutions. It involved updating Golang, rebuilding all dependencies, and ensuring the correct RPC port was used. The localnet were essential for me to continue focusing on peer connectivity issues and further investigations [Issue #4749](https://github.com/harmony-one/harmony/issues/4749).

---

2024-08-31 Sat: I focused on different tasks to improve our project’s alignment with the latest developments. I started by updating the Go version in the go-sdk to 1.22.5, as seen in [PR #304](https://github.com/harmony-one/go-sdk/pull/304). This update ensures that the go-sdk is now compatible with the new Harmony binary. Alongside this, I updated Dr.Harmony to support the same Go version, which you can review in this [commit](https://github.com/GheisMohammadi/Dr.Harmony/commit/b26a898a901771e95dd204d7d25fbc8b9c3df02f)

In addition to these updates, I tackled the conflicts between [PR #4735](https://github.com/harmony-one/harmony/pull/4735) and the dev branch. After resolving these conflicts and rebasing the branch, I pushed the updated code, which is now under team review.

Furthermore, I reviewed some PRs, including the release v2024.2.0 PR [PR #4666](https://github.com/harmony-one/harmony/pull/4666), which is set for deployment next week. During this review, I identified some missing code, prompting me to create [PR #4747](https://github.com/harmony-one/harmony/pull/4747) to add boot node watermark flags, ensuring all main_hotfix changes are covered in the dev branch.

---

2024-08-24 Sat: I resolved build issues, optimized, and finalized [PR4735](https://github.com/harmony-one/harmony/pull/4735). This PR significantly enhances the visibility and monitoring capabilities of boot nodes by introducing an RPC server. Previously, boot nodes lacked RPCs and didn't expose any metadata, limiting our monitoring capabilities. With this update, several new APIs have been added, allowing us to efficiently monitor and track connectivity and peers connected to the boot nodes. In addition to these monitoring enhancements, the PR includes a redefinition of the node and RPC folder structure, leading to a more organized and well-structured codebase. This improvement ensures that adding boot node functions will be easier in the future. 

I also conducted code reviews, provided feedback to the team, and finalized [PR4731](https://github.com/harmony-one/harmony/pull/4731).

---

2024-08-17 Sat: I focused on preparing the [PR #4735](https://github.com/harmony-one/harmony/pull/4735) for the RPC feature for boot nodes and resolving issues with building of the PR. After conducting numerous tests and systematically removing each RPC feature to identify the problematic one, I found the root cause of the build issue. I am currently exploring solutions, and it appears that different configurations may be required for boot RPCs instead of using the same configs as the Harmony node. Once resolved, I will add more endpoints and finalize the tests.

Additionally, I made a small [PR #4737](https://github.com/harmony-one/harmony/pull/4737) to update the Makefile. This update includes several commands that were previously missing from the output of the make help command.

---

2024-08-10 Sat: I worked on improving different parts of the Harmony project. One of the things I tackled was the Network Time Protocol (NTP) functionality. In [PR #4728](https://github.com/harmony-one/harmony/pull/4728), I reworked the NTP setup to support multiple servers, which should make time synchronization more reliable. I also fixed an issue where the NTP queries were timing out in localnet environments by extending the timeout from 10 to 30 seconds. Plus, I made some tweaks to error handling and logging to make troubleshooting easier.

I also fixed an annoying issue where the allowedtxs.txt file would cause errors if it wasn’t in the .hmy directory. In [PR #4731](https://github.com/harmony-one/harmony/pull/4731), I added a simple check to make sure the file exists before moving forward, which should help avoid any unexpected hiccups during setup.

Another important fix was in [PR #4724](https://github.com/harmony-one/harmony/pull/4724), where I addressed a problem with the boot node address parsing. The script would sometimes mess up if there was extra printed info which goes on the same line as the address, leading to boot failures. I adjusted it so that the address is printed on a new line, which should fix the boot process.

I also took some time to clean up the debug scripts in [PR #4729](https://github.com/harmony-one/harmony/pull/4729). Now, unnecessary error messages won’t pop up when trying to delete non-existent directories or files, which should make the debugging process a little less noisy.

Lastly, I made good progress on the boot node RPC feature [boot/rpc](https://github.com/harmony-one/harmony/compare/dev...feature/boot_rpc). It’s about 90% done, though there’s a build issue I’m currently looking into. Once that’s sorted out, this feature will give us a solid RPC interface for boot nodes, making boot node monitoring a lot more efficient.

---

2024-08-02 Sat: My main focus was increasing the visibility of boot nodes. I am working on adding an RPC server to the boot node since it currently lacks any RPC and does not expose any information or metadata. I am addressing this in a pull request, aiming to add at least a few APIs to allow better and more efficient monitoring. This way, we can observe and monitor the connectivity and peers connected to the boot node. This work is in progress, and the code is already in the feature/boot_rpc branch.

The progress is at 70%, with thousands of lines of code added. I will continue working on this next week as well.

---

2024-07-27 Sat: My primary focus this week was to find a final solution to stabilize the boot nodes and fix the crashes on mainnet. While the issues were fixed on devnet, mainnet still had its own instabilities. The investigation led to the following PR: [harmony-one/harmony#4717](https://github.com/harmony-one/harmony/pull/4717).

This PR updates the p2p host configuration to maintain the same values as the current mainnet setup. It ensures that both muxers are supported, making the host fully backward-compatible. The primary goal of this PR is to address mainnet boot node crashes caused by the old muxer and security configurations.

The PR was deployed on two boot nodes on mainnet and showed promising results. The boot nodes have been stable for a few days, indicating that the PR has likely fixed the connectivity issues. Consequently, the team merged it into the `main_hotfix` branch.

My next focus is on improving visibility into boot nodes' performance and connections. Currently, boot nodes do not execute any RPCs and do not expose connection data to monitoring. I am working on adding an RPC server to them, which requires many code additions and tests. I will continue working on this next week as well.

---

2024-07-20 Sat: I investigated the `eth_call` issue and reviewed my findings with Soph. We discovered that a client specific contract was causing the issue. Additionally, we identified the need to upgrade certain functions in the EVM to enhance compatibility and reduce issues with newer versions of smart contracts.

I also performed code checks in stream sync and fixed a small bug. You can find the details of the bug fix in [pull request #4714](https://github.com/harmony-one/harmony/pull/4714). Alongside this, I updated some deprecated code in our code base that was generating warnings, which is documented in [pull request #4715](https://github.com/harmony-one/harmony/pull/4715).

Regarding bootnodes, we found that the main net nodes are using an old version of Yamux. To address this, we need the newest version of libp2p. The team has already upgraded Golang, and the next step is to upgrade libp2p to ensure improved performance and compatibility.

---

2024-07-13 Sat: After several discussions and evaluations of the expected impacts, we finalized the decision to upgrade the boot nodes. Boot nodes 1 and 2, and later boot node 3, were successfully upgraded with [PR #4707](https://github.com/harmony-one/harmony/pull/4707). This PR improves the P2P host connection manager and removes QUIC transporters. The upgrade was successful, carried out without disturbing the network or bringing consensus down. We are closely monitoring the boot nodes post-upgrade. This was a significant step towards upgrading all boot nodes on the mainnet without any disruption. The next step is to upgrade the last boot node and then apply security configurations for the boot nodes in the mainnet.

Next, we addressed the number of connections boot nodes can accept. The current high water mark was set at 192. The team decided to increase this limit for boot node connections. I created [PR #4710](https://github.com/harmony-one/harmony/pull/4710), which adds a new flag to the P2P host for boot nodes to adjust the high water mark, preventing any limit on boot node connections.

I also created [PR #4711](https://github.com/harmony-one/harmony/pull/4711) to replicate a Travis fix for the hotfix branch. This helps resolve build issues and ensures successful builds in the `mainnet_hotfix` branch.

We encountered another issue where only active validators among DNS nodes could participate in syncing. Soph updated the list of DNS nodes, which helped to address the issue, but I am still investigating to find the root cause. My investigation led to the discovery of a few minor bugs (unrelated to the issue), which I fixed in [PR #4713](https://github.com/harmony-one/harmony/pull/4713).

Additionally, there is an issue with `eth_call` that could potentially fail when `gasPrice` is not included in the request. Addressing this will be my next task.

Lastly, I conducted code reviews for several PRs that the team is working on.

---

2024-07-06 Sat: I created a new branch in GitHub ([compare branch](https://github.com/harmony-one/harmony/compare/main...mainnet/bootnode/8717ccf61)), which is the old code from last year. It has the exact same HEAD commit as what the old boot nodes are using. The idea of this branch is to check the QUIC protocol removal without touching anything else.

Later, I created PR [#4705](https://github.com/harmony-one/harmony/pull/4705). This PR enables security by default. The reason is that we are trying to avoid a mainnet split or consensus downtime. So, we want to have as much of the same P2P configurations as we have in the mainnet. This PR has already been merged into the dev branch.

We agreed on an upgrade plan for bootnodes, which will proceed as follows:
1. Upgrade mainnet bootnodes 01/02/03 to the latest dev version with PR #4705.
2. Test the latest dev version on 1 or 2 mainnet nodes first (we will also ask a few validators in the community with backup nodes to test as well).
3. Upgrade devnet/testnet bootnodes and validator nodes with the latest dev version.
4. Deploy the dev release to all mainnet nodes.

This plan should ensure a smooth upgrade process.

Next, I created another PR [#4707](https://github.com/harmony-one/harmony/pull/4707) to remove QUIC from the current mainnet for testing. This PR improves the P2P host connection manager and removes QUIC transporters from the P2P host. We will test this on 2 or 3 boot nodes first next week.

I also created PR [#4704](https://github.com/harmony-one/harmony/pull/4704). This pull request introduces a new command in the Makefile to create a Linux executable more quickly by only building the main binary without recompiling dependencies. The existing `linux_static` command remains unchanged and continues to perform a full build, including all dependencies (mcl & bls). The new command is named `linux_static_quick`.

---

2024-06-29 Sat: After a successful hard fork, we shifted our focus back to the HIP32 requirements, moving towards the necessary enhancements and improvements. Some old boot nodes couldn't get enough peers after the upgrade, and I am already addressing that issue. The first solution I tried involved testing different P2P configurations that are compatible with both old and new versions. I am also incorporating some code from older versions and working on the TLS and security aspects. The investigation is still ongoing, and I will continue working on it.

---

2024 Q2 Review: Throughout this quarter, I implemented major PRs, contributing significantly to network improvements. Moving towards HIP-32, I focused on critical improvements to enhance our network's stability and performance. One major achievement was addressing P2P stream discovery issues, ensuring stable operation of devnet nodes, and resolving high storage usage and syncing problems PR[#4676](https://github.com/harmony-one/harmony/pull/4676). I also refactored the stream sync block storage, significantly improving stability PR[#4660](https://github.com/harmony-one/harmony/pull/4660) and logging capabilities PR[#4667](https://github.com/harmony-one/harmony/pull/4667), aiding in more effective debugging processes.

Resolving persistent boot node issues was another highlight. This issue was getting a big impact on validators. By upgrading to the latest version of libp2p, refactoring code, and meticulously testing various configurations, I managed to stabilize the boot nodes PR[#4674](https://github.com/harmony-one/harmony/pull/4674). The implemented changes, encapsulated in key pull requests such as PR[#4682](https://github.com/harmony-one/harmony/pull/4682) and PR[#4679](https://github.com/harmony-one/harmony/pull/4679) to add support for multiple muxers, ensured seamless network operation. Additionally, I enhanced P2P connection monitoring by implementing logger flags and the environment variables, providing the team with better visibility.

A major problem with pending undelegations on the mainnet required thorough analysis and collaboration. I shared theories, conducted code reviews, and investigated various scenarios, which helped guide the team towards a successful resolution. My insights and collaborative approach and a great team work were helped in fixing this critical issue, which was later resolved by a team PR.

---

2024-06-15 Sat: We focused on resolving the undelegation issue, with the entire team actively working and discussing it. We have been thoroughly investigating the problem and reviewing various parts of the code. We have nearly identified the root cause or, at the very least, have developed a few hot fixes.

The primary issue was related to validator validation and the validator max rate. Specifically, some validators already have invalid max rates, causing their validations to fail in the codebase. Although this issue was previously fixed, it wasn't applied to the main branch and will be included in the next hard fork (HF). So far, the team has implemented a max rate hard fork and selected the appropriate epoch for mainnet, testnet, and devnet.

---

2024-06-08 Sat: I replicated the same changes on P2P configurations and muxers for the main net. I pushed the PR to the bootnode_fix branch, which is cloned from the main branch, and it is currently under review by the team.

We conducted a study to make decisions about security configurations, and it is under investigation by the DevOps team using the visibility provided by the P2P trace file.

We had a delegation issue reported by validators. The team has initiated an in-depth study of this problem. I also started investigating the code and working on a solution for it.

---

2024-06-01 Sat: We successfully resolved the boot node issue. The corresponding PR was reviewed and approved by the team, then deployed to the devnet boot nodes. All tests were successful. However, a significant challenge was that these changes required bringing main-net consensus down, and all validators had to use the latest version of the binary with the same P2P configurations. We worked on identifying configurations that were not backward compatible and found two key ones: Muxer and Security.

Initially, I realized that the flags were not properly set on the devnet boot node. I added the muxer flag for the boot node, which resolved the issue and brought it back online. After an in-depth study of the muxer, I discovered that the P2P host could support multiple muxers. This discovery led to a permanent fix for challenges related to different muxers. I then submitted the PR[#4682](https://github.com/harmony-one/harmony/pull/4682) to add support for multiple muxers.
Initially, I realized that the flags were not properly set on the devnet boot node. I added the muxer flag for the boot node PR[#4679](https://github.com/harmony-one/harmony/pull/4679), which resolved the issue and brought it back online. After an in-depth study of the muxer, I discovered that the P2P host could support multiple muxers. This discovery led to a permanent fix for challenges related to different muxers. I then submitted the PR to add support for multiple muxers.

To further investigate issues and improve migration to the new binary version, we needed better visibility into P2P connections. We previously lacked insight into the lower layers of P2P, which was necessary for monitoring connections. After extensive research, I suggested four approaches:

1- Clone the KDM repository and add all required functionalities: This would be a temporary solution and would require significant effort to maintain and keep the repository updated with the latest KDM changes.

2- Use the Host Peer Store: This approach requires a deeper study of P2P host connections and DHT data.

3- Use the logger flag along with other boot parameters

4- Use the TRACE_FILE environment variable and pass it to libp2p

We tested options 3 and 4, and the team is currently using them to monitor connections. The next task will be to further implement option 3 for enhanced monitoring capabilities.

---

2024-05-25 Sat: I finalized the PR[#4674](https://github.com/harmony-one/harmony/pull/4674) to address the bootnode issue. This PR includes the following changes:

- Removed QUIC, an unnecessary feature, and switched to TCP transport.
- Made TLS/Noise, relays, and NAT optional features that can be disabled via configuration.
- Added a dial timeout for the connection manager.
- Allowed the use of the MPlex muxer in addition to Yamux.

This PR was approved and successfully tested on two bootnodes on the mainnet, effectively resolving the issue. Subsequently, I implemented the same changes[#4676](https://github.com/harmony-one/harmony/pull/4676) for the dev branch. We hoped this PR would also help with the syncing issue, but it did not. The new P2P host configurations need to be carefully planned for mainnet deployment to ensure all nodes use consistent P2P protocol configurations. The team is working on a phased approach for this rollout.

I reviewed a few PRs related to crosslink issues. These PRs have been updated, approved, and are ready for merging.

We are still working on the OUT OF SYNC issue. This issue persists on devnet, and devnet shard 1 was down for a few hours as a result.

---

2024-05-18 Sat: My main focus was on resolving the boot node issue. The boot nodes kept restarting with several debug logs related to the lower layers of libp2p, such as the QUIC protocol, p2p multiplexers, and session failures. The upgrade of the mainnet boot nodes caused these problems, which stemmed from the lower layers, limiting our immediate control.

Upon investigation, I discovered that several issues were addressed in newer versions of libp2p. I upgraded the main branch to the latest version of libp2p, refactored parts of the code, resolved all conflicts, and built a new binary. Testing this on the boot node improved stability, but some vague logs persisted.

I then noticed that the QUIC protocol could be disabled. After disabling it and conducting further tests, the boot nodes remained unstable. 

To address the boot node issue, I tested several solutions:

- Added a few flags for the connection manager.
- Used the default connection manager.
- Tested only the TCP transporter and removed UDP.
- Used default values for Kademlia (KDM).
- Changed the multiplexer.
- Disabled the libp2p host relayers
- Disabled the firewall.
- Readjusted log flags.
- Updated the boot node service file.

Despite these efforts, the instability persisted. Each test required updating the code, building the binary, deploying to the boot node, and waiting for results, which took a few hours each time.

Ultimately, I disabled all libp2p features on the boot nodes, which resulted in stability. We monitored the stable system for a while, and things looked promising. Subsequently, I re-enabled the features one by one. This incremental approach proved successful, and the tests confirmed that the issue was resolved.

I am now preparing the final PR to upgrade all boot nodes this week.

---

2024-05-11 Sat: Our primary focus was on resolving the boot node issues. We conducted several investigations into the matter, and although progress has been made, we are still actively working on it. Personally, I dedicated time to addressing the out-of-sync issue by meticulously reviewing logs and eliminating any unnecessary ones.

---

2024-05-04 Sat: I finalized [#4660](https://github.com/harmony-one/harmony/pull/4660), which was reviewed and merged by the team to dev branch. We investigated a connection issue and observed that two peers could connect and successfully complete the handshake. However, when they started syncing blocks, the connection broke instantly. We thoroughly checked the stream logs, the handshake process, the stream client, the database layer for fetching blocks, context timeout, block size, and double-checked with RPC, and all of them appeared to be working fine. Our next theory focused on the rate limiter, but upon examination, it also seemed to be functioning properly. This issue is still under investigation.

Additionally, there was an incident involving all boot nodes that, after upgrading, were unable to sync the peers list. Many validators reported this issue, prompting us to prioritize its resolution. Eventually, we disabled pprof, after which all boot nodes came back online, and the main net was successfully recovered.

---

2024-04-27 Sat: Our primary focus revolved around investigating why nodes switched to syncing mode despite being fully synchronized. Additionally, I delved into resolving NTP and local net block production issues. Furthermore, efforts were directed towards addressing the build issue encountered in my latest pull request.

---

2024-04-19 Sat: My focus was on enhancing the stream sync code and block storage functionality. I submitted a pull request [#4660](https://github.com/harmony-one/harmony/pull/4660) aimed at improving and refactoring the stream sync block storage. Currently, this PR is undergoing team review. It is expected to enhance the stream sync's stability, provide more useful logs, and serve as a valuable step towards debugging.

---

2024-04-13 Sat: As we move towards achieving a fully decentralized network and implementing HIP32, effective communication between nodes becomes crucial. This necessitates having a reliable and operational stream sync, which is of utmost importance. Over the past few months, we've implemented numerous changes to both the stream codes and consensus module. However, these alterations have led to instability in the sync protocol and communication between the sync and consensus modules. Currently, my main focus is on addressing these issues. I'm working on a couple of code fixes and conducting tests to ensure that everything functions as expected.

---

2024 Q1 Review
In Q1, my focus was on enhancing the functionality and stability of Harmony network. Throughout the quarter, I dedicated considerable efforts to resolving various issues including known blocks, stuck transactions, p2p client crashes, race conditions, configurations and logs, syncing issues and so on. These efforts were instrumental in maintaining the stability and reliability of our networks.

I worked on many new features that each of them could be a separate project: 
- p2p client: implementation of numerous new functions in the p2p client, significantly enhancing its capabilities. Now, nodes can seamlessly request accounts, storages, and state sharing from each other
- state synchronization: I completed the necessary code and resolved numerous issues, followed by a significant refactor of the state sync stage, accounting for approximately 40% of the changes. It is in the final stages and requires an operational snapshot database.
- state pruning: I made substantial progress by addressing numerous issues and conducting extensive testing across different network databases. This one also is in the final stages and requires an operational snapshot database.
- snapshot database: I spearheaded efforts to optimize our snapshot database, refactoring the codebase and resolving numerous issues to ensure its successful operation. Despite encountering some remaining challenges, our progress in this area has been promising.
- eth database upgrade: upgrading the eth database has been initiated to support snapshot functionality. The PR would be thousands lines of codes.

Furthermore, we successfully addressed an unexpected Mainnet Shard 0 outage and Crosslink stuck situation, requiring intensive effort over several days and the implementation of multiple PRs. 

The outage on shard 0 highlighted significant technical challenges, including the inclusion of outdated crosslink data within block proposals and issues with the deployment of snapDB. To address these challenges, We added many new logs, developed and deployed hotfixes, alongside with grafana alerts, to bypass the validation failures and node stagnation. Process improvements focused on enhancing crosslinks processing, new deployment procedures for critical updates, ensuring synchronization of components, and bolstering monitoring and alerting capabilities. These measures aim to mitigate the risk of future outages, enhance network stability, and improve overall reliability.

In parallel, I made several enhancements to our network configuration file, introducing new configurations and segregating cache configurations for improved manageability. 

Overall, Q1 was marked by significant progress, with numerous issues addressed and a couple of new features has been developed and are in their final stages.

---

2024-04-06 Sat: We addressed the p2p stream discoveries issue and successfully resolved it in the devnet node However, two other issues persist: high storage usage by stream sync and the transition from Syncing mode to Normal mode. After many discussions with the team and thorough code base analysis, we are actively addressing these priorities. Additionally, we continue to prioritize the recovery of devnet shard1, exploring the most efficient approach for its restoration.

---

2024-03-30 Sat: We encountered a storage issue where the team identified that the stream cache was consuming excessive storage. I conducted tests on the sync in the local network, and everything appeared to be fine, with storage usage within normal limits. However, we later observed that the stream service kept restarting, and the cleanup process wasn't triggered for unknown reasons. Currently, I am working on a pull request (PR) to address this cleanup issue.

Additionally, we faced problems with p2p stream discoveries as the node couldn't connect to other nodes, which were rejecting it. It seems the node was being blocked by others. We are actively working on resolving this issue as well.

---

2024-03-15 Fri: We encountered a simple configuration issue. All devnet nodes were upgraded to the latest release, and snapshot generation was inadvertently enabled by default, causing several nodes to go down. To address this, I created a pull request and set the Snapshots Limit to zero by default for all networks. This effectively disabled snapshots permanently and resolved the issue.

Subsequently, we encountered another issue where two nodes became stuck due to an increasing view ID, resulting in different block hashes. We investigated this issue and considered two theories: one related to the snapshot root hash and the other to potential root causes within stream sync. Upon investigation, I confirmed that stream sync could not be the issue, as it does not manipulate or increase view IDs. However, there remained a possibility of indirect conflicts with consensus. Our investigation revealed that one node had somehow received the wrong view ID from another node. We temporarily resolved this issue by disabling snapshots and resyncing the affected node using the snapshot database.

Additionally, upgrading ETHdb is another ongoing task, which is nearly complete. This involves adding a few thousand new lines of code, necessitating thorough and precise testing.

---

2024-03-09 Sat: I continued working on upgrading the database layer. It will involve significant changes and will require extensive testing. I have already resolved 90% of the upgrade issues and am aiming to finalize the code by the end of next week

---

2024-03-02 Sat: I started refactoring snapshot database. This would fix a couple of issues on old versions of database

---

2024-02-24 Sat: I resumed working on the snapshot database. I completed several tests and thoroughly examined the codes of ethdb. During this process, I identified an issue with the validator wrapper code prefix that could potentially lead to failures in snapshot creation. I promptly addressed this by adding the new prefix and proceeded to conduct additional tests on the mainnet database. These tests have been ongoing for the past 40 hours, and we are currently awaiting the results. If successful, this update would mark a significant advancement in snapshot creation.

---

2024-02-16 Sat: My main focus of this week was on the unexpected Mainnet Shard 0 outage and Crosslink stuck. We had several meetings, calls, and discussions during both the weekend and weekdays. After extensive team collaboration and testing, I created several PRs to address the crosslink issues [#4629](https://github.com/harmony-one/harmony/pull/4629) , [#4630](https://github.com/harmony-one/harmony/pull/4630) and delete pending crosslinks [this commit](https://github.com/harmony-one/harmony/commit/d0261f8ef5360e05ee964b034afd83b10de34615). Through collaborative efforts and rigorous code review, we successfully resolved the issue.

Additionally, I conducted several code reviews and provided comments on other PRs that addressed race conditions.

Another challenge we faced was a devnet stuck on Shard 0. I investigated this issue as well. After thorough investigation, we discovered that it may be related to some new configurations for snapshots. The team assisted in adding these new configurations to all nodes and subsequently disabled them.

---

2024-02-10 Sat: I focused on fixing snapshot DB creation. I refactored the snapshot codes, addressed several race conditions, and made some improvements to the code. Later, I tested snapshot creation again on the mainnet DB, which had a size of 32TB. It took around 42 hours to complete, and no errors were reported during generation. However, the issue arose afterward when the node became stuck and couldn't continue syncing. We attempted to identify the problem and tested several possible scenarios. We are still working on resolving this issue, and once it is fixed, we can proceed with the final pruning test.

---

2024-02-02 Sat: I focused on the state pruning feature. During this time, I addressed a few issues, successfully fixed them, and rebased the branch, which is now ready for merge. To test the pruning functionality, I performed tests on the devnet. However, the database size did not significantly decrease due to the recent devnet restart, resulting in a lack of transactions. Consequently, there were not many intermediary states to remove.

For a more comprehensive test, I conducted state pruning on the test-net database. Here are the results for shard 0:

Before: 26,758,097,053 bytes
After: 26,734,477,304 bytes
Difference: 23,619,749 bytes

The pruning operation reduced the size by approximately 23MB (out of 25 GB), albeit a modest reduction. The limited decrease is attributed to the test-net database also lacking a substantial number of intermediary states. To overcome this, the devops team assisted in deploying a main net node, and I commenced testing pruning on the main net. Results for this test will be shared once the testing is complete.

Additionally, I addressed a user-reported issue regarding transaction sending. Upon investigation, we identified a logic flaw in the allowed list, allowing multiple entries for the same "from" address. The current code only retains the latest entry, disregarding the previous ones. To rectify this, I submitted a pull request that resolves the issue by establishing a map of allowed transactions to an array of transaction data, rather than a map of "from" to a single transaction data.

---

2024-01-26 Fri: We encountered an issue that could lead to panic errors on devnet nodes due to a null snapshot. This problem was triggered by fast sync tests in StreamNet and was affecting the decoupled nodes. I addressed this issue on the P2P client side by validating the snapshot creation result.

Subsequently, I resolved the snapshot creation issue, which was a blocker for state pruning as well. The snapshot creation was broken because of an incorrect root hash. The PR addresses that issue and also adds a new section in the configuration file for cache settings. It moves old cache settings under this new section as well. All the changes have been tested successfully and are ready to review and merge by team.

Once these two PRs are merged to the dev branch, the devnet nodes will be able to create or load a snapshot db once they get restarted. I will continue my tests to complete the last step of sync development.


---

2024-01-21 Sun: I was actively working on fixes and addressing several issues. After the devnet nodes were upgraded, all the new stream functions were added to the nodes as well. The devnet went down due to enabling the stream server on the main devnet nodes, and they were involved in sync tests. Due to the non-existence of a snapshot, this led to crashes. I created a PR to address this issue.

I also worked on improving logs to investigate a case of stuck transactions on one of the clients node. I added a couple of logs and pushed them to the latest log branch. Later, these logs helped identify the issue, and the team created a PR to address it.

Additionally, I fixed another issue in the devnet. The stakedVoteWeight structure didn't support concurrent read and write, which could break the main process if an RPC triggered any write or read from it. I created a PR to address this issue by adding a mutex to make it thread-safe. However, this PR was later closed due to overlap, as we had already implemented thread-safe measures in another PR for consensus and quorum.

---

2024-01-15 Mon: We encountered an issue with the devnet as shard 0 experienced downtime. We conducted an investigation to identify and resolve the problem. Several nodes were stuck while attempting to read shard state. To address this, we implemented a few changes, and ultimately, the team restarted the devnet. Another issue arose concerning one of the RPC nodes dedicated to the Harmony client. Transactions were getting stuck on this node, and the leader node did not receive the first transaction. To investigate further, I created a new branch from the main codebase and added additional logs to track transactions entering the transaction pool and being broadcasted. We are currently working on reproducing the issue to utilize the logs for debugging. Additionally, there was an issue with legacy sync related to known existing blocks. As a quick fix, I submitted a pull request that allows the syncing process to continue for known blocks instead of triggering an error. I have also been ongoing with the testing of state sync to explore and address the stream reset issue that occurs during the process of obtaining account ranges.

---

2024-01-08 Mon: I continued testing and addressing issues related to state sync. One of the problems involved a potential syncing process disruption due to receiving nil accounts, which has been fixed, and the code has been pushed. Another issue surfaced during the transition to the new sync mode, added to the last stage of state sync. Currently, the primary challenge is the error "stream removed when doing request," which occurs when the node attempts to retrieve a range of accounts. I dedicated several hours to investigating this issue, examining the peer manager and exploring all possible scenarios that could remove a peer outside the sync loop. Unfortunately, the issue remains unresolved. My current focus is to prioritize fixing this problem. It appears that all nodes on the devnet might need to undergo an upgrade to incorporate new changes in stream sync. Successfully addressing this issue marks a significant milestone towards achieving a full state sync, allowing me to finalize the codes.

---

2024-01-01 Mon: My primary focus was on testing the latest fast sync PR (#4594). To check the transition from fast sync to full sync, I adjusted the pivot closer to the genesis. This modification enabled a quicker assessment of the functionality within a shorter timeframe. Additionally, I addressed the local net sync issue and resolved issues related to known blocks and double block insertion. As part of the debug process, I refactored the downloader to return the count of tasks, eliminating the need for individual length checks. Testing will continue into the next week.

---

2023-12-25 Mon: I primarily focused on a new pull request (PR #4594) that completes the fast sync pull request (PR #4465). This integration involves merging the full state sync stage into stream sync while adjusting parameters for fast sync. The PR enhances the fast sync code and addresses several fast sync issues. Currently drafted, it will be merged once fully tested.

Additionally, I submitted a new PR to enhance the validator code wrapper. This update enables automatic detection of the validator account. Originally intended as a hotfix for the main branch, I later switched it to the development branch as an improvement.

---

2023-12-18 Mon: I refactored the state sync request cap in the full state sync stage and also implemented additional error handling. I refactored the process of requesting states into five steps, and the corresponding code has been added to PR 4465. Subsequently, I rebased this PR with the dev branch, encountering over 60 conflicts. Some required codes were altered or removed by other PRs, and I reinstated them, resolving all conflicts, which took a couple of hours. Although PR 4465 requires further improvements and a full cycle of tests, we merged it with dev to address the potential rebase conflicts. Tests and optimizations will be addressed in a separate PR.

I identified an issue with validator wrappers. Harmony's rawdb employs distinct prefixes for validator wrapper code and contract code. The current code initializes a validator wrapper and attempts to fetch it from the database without using the appropriate prefix. It initializes the validator wrapper without the prefix, but for updating the validator wrapper, it sets the isValidatorWrapper flag to true, causing it to write the code with the prefix. In response, I created PR 4587, which resolves this issue by eliminating the flag and introducing automatic detection for validator code using the IsValidator function. The modified code checks whether it is for a validator, and based on that, it attempts to retrieve or write the code accordingly. BTW, Further discussion and investigation proved that this issue doesn't have any impact on node performance , So, later as an improvement I sent its PR to dev branch. 

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
