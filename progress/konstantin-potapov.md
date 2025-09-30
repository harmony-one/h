Q4 plans:
1) Launch release with transient storage (EIP-1153) on mainnet.
2) Improve metrics coverage for the block proposing process, including more precise block proposal timings under 1-second finality.

---

2025 Q3 Review:
During Q3, I tested the London and Berlin fork release compatibility. The release passed validation on devnet and testnet and was partially deployed on mainnet.
    It introduced more than 15k lines of code changes and revised EVM internals by replacing `big.Int` with `uint256.Int`, updating Harmony smart contracts to align with EVM rules, adding the BASEFEE opcode, and adjusting gas computation for several built-in functions.
I also implemented transient storage (EIP-1153) and confirmed its execution on devnet.
    This feature requires additional modifications introduced in the 1.11 fork (Shanghai), including a writable data location with transaction-scoped lifetime, load and save functions integrated into state transition, and new opcodes supporting transient semantics. 

---

2025-09-19 Fri:
Implemented transient storage as specified in EIP-1153, adding new VM opcodes. Launched the London fork on testnet. Completed a 2-week devnet test run successfully.

---

2025-09-12 Fri:
Branch 1.10 with the London fork was launched on devnet. I started investigating the issue with the low block production rate under 1-second finality mode. During the analysis, I found several cases of duplicate block proposals and implemented a workaround to prevent duplicate emissions. However, after testing, the solution caused significant block production degradation, so I decided not to proceed with this workaround. 

---

2025-09-05 Fri:
Branch 1.10 has one failing test and is ready for devnet integration. Branches 1.9 and 1.10 were rebased with the latest dev.
The 1-second finality mode produces fewer than 60 blocks per minute, so I am investigating the issue. Current progress is about 20%.
Reviewed several PRs.

---

2025-08-22 Fri:
Branch 1.10 now compiles successfully and passes about 99% of the tests. An issue in branch 1.9 was identified and fixed. Revived several Pull Requests

---

2025-08-08 Fri:
Rebased 1.10 branch onto 1.9, reaching ~90% completion. Reviewed multiple PRs.

---

2025-08-01 Fri:
Finalized 1.9 version update, it's on review and ready to be merged. Started rebase 1.10 version update, current progress is 70%. Reviewed several PRs.    

---

2025-07-25 Fri:
This week, I rebased the 1.9 branch with the latest dev code and resolved all issues related to the 1.9 update. Ulad and I also launched nodes on the devnet to test the new changes.

---

2025-07-18 Fri (3 days off):
I fixed a failing test caused by the execution of validator-assigned code, which should be avoided in the Harmony codebase.
Additionally, I reviewed the pull request introducing the new BLS12-381 precompiles.

---

2025-07-11 Fri: I fixed several failing tests to support the London and Berlin upgrades, updating the test suite to reflect recent code changes. Overall progress is around 90%, with only a few remaining test failures that I couldn’t reproduce on macOS.

Additionally, Ulad and I have been working on collecting block production statistics to analyze proposal timing and improve metrics coverage for the block proposing process.   

---

Q3 Plans:
-	Successfully launch the London upgrade on testnet.
-	Improve metrics coverage for the block proposing process.
-	Analyze and optimize block proposal timing to achieve consistent 1-second intervals under the 1-second finality model.

---

2025-07-04 Fri: I focused on fixing and updating the test codebase to support the London and Berlin upgrades. The test suite was adapted to recent code changes, with overall progress at approximately 70%.

Additionally, I revived several team pull requests and handled on-call issues related to bootnode stability. 

---

2025-06-27 Fri: I focused on improving cross-platform test reliability. While working with the 1.9 and 1.10 branches, I identified macOS-specific issues and addressed them by creating a Docker-based, platform-independent testing setup. It currently supports the go-test command and is designed to be extensible to other test commands.

I also handled on-call responsibilities and reviewed multiple pull requests.

---

2025 Q2 Review

[I upgraded the Harmony codebase to include Ethereum Berlin and London updates](https://github.com/harmony-one/harmony/pull/4915)

During Q2 2025, I focused on improving Harmony’s P2P consensus, EVM execution, gas calculation, and precompiled contract infrastructure. 

I launched a new release that completely removed redundant view-change logic, eliminated overhead from the heavily used getLogger method, redesigned the validator uptime calculation to account for mined blocks, and improved localnet testing to be more portable across platforms.

Validator uptime calculation to account for mined blocks.
Ulad and I found a major discrepancy between validator uptime on the staking platform and internal Grafana. The platform only counts signed blocks, ignoring produced ones, which leads to inaccurate metrics-especially when a validator produces blocks slower than the expected 1 block every 2 seconds (e.g. 1 block in 6 seconds). We’re exploring updates to the API or staking logic to include produced blocks and calculate uptime based on actual block rate over time.

---

2025-06-13 Fri: I completed the EVM 1.9 update. I refactored the precompiled contract handling by removing hardcoded logic and extending Ethereum interfaces to support additional parameters, such as EVM and Contract.   

I created an issue proposing a new algorithm for calculating validator uptime. The current approach only accounts for signing power, while the new method will also consider blocks produced by validators. I reviewed, approved and merged several pull requests into dev branch.

---

2025-06-06 Fri: I reviewed and merged the dev branch into master. We agreed to announce the changes on Monday morning to have a full week of support and oversight for validators. 

I identified portions of the EVM code that were not updated in the 1.9 branch. These sections include conflicts that require manual resolution. I estimate the work is currently about 50% complete and will continue next week. I reviewed, approved and merged several pull requests into dev branch.

---

2025-05-30 Fri: I focused on integrating the new VM opcodes introduced in the Ethereum 1.10 update. I estimate we’re approximately 80% through the full 1.10 integration. We also continued testing the upcoming release to ensure stability and compatibility across our codebase. So far, results have been promising, with no major issues detected.

In parallel, I began working on the implementation of transient storage as specified in EIP-1153. While not part of the 1.10 update itself, it is a feature that will enhance our compatibility with the Ethereum ecosystem.

---

2025-05-23 Fri: I identified and resolved an issue in the tests repository related to an invalid library version. The bug was blocking progress across all branches, and fixing it has unblocked further development and testing workflows. I continued making progress on the Ethereum 1.10 integration into our blockchain codebase. I estimate around 50% through the overall update.

We also continued testing the upcoming release in coordination with mainnet validators. Assuming no critical issues arise during this phase, we are on track to prepare the final release within the next two weeks. 

---

2025-05-16 Fri: I continued progressing with the Ethereum 1.10 integration into our blockchain codebase. Based on the current status, I estimate we are approximately 30% through the update process. During release testing, Ulad encountered an issue related to node startup. The problem appears to be minor and is not expected to impact the current release timeline. Gheis investigating the issue and expect to have a fix by monday.

---

2025-05-09 Fri: Our efforts were centered around validating the upcoming release. During testing, we identified an issue related to the bootnode. While the impact appears to be limited and not a blocker, I proactively submitted a PR with a potential fix involving targeted code changes. After further in-depth testing, it became clear that the fix did not fully resolve the issue. Still, we kept things moving and continued with the testing process.

We are now updating mainnet validators with the new release to assess compatibility in a live environment and ensure readiness for deployment.

---

2025-05-02 Fri: After a series of updates, Gheis, Ulad, and I successfully resolved an issue that caused unintended view change activation on the first block of a new epoch. This fix enhances consensus stability and ensures smoother epoch transitions. In addition, I reviewed, approved, and merged several small pull requests, including changes to the release branch. These updates contribute to improved logging performance, more robust error handling, and increased test coverage.

---

2025-04-25 Fri:  I focused on integrating the consensus module with the Loki logging system. I enhanced the consensus logging infrastructure to produce structured logs, significantly improving the experience when analyzing data in Grafana. In addition, I refactored the logger to populate consensus-related fields without requiring a lock. Previously, acquiring locks for logging was a delicate task that demanded careful handling to avoid deadlocks or performance degradation. The updated implementation eliminates the need for locks entirely, simplifying the system and reducing the risk of misuse within the consensus logging logic.

---

2025-04-18 Fri: This week, I implemented a fix for the view change issue that occurred during the updateConsensusInformation function call. Previously, this call could interrupt the leader’s signature collection process, leading to an unintended view change. The patch ensures smoother consensus updates without disrupting the leader’s operation. Additionally, I refactored the interaction between the consensus and synchronization processes.
  
The synchronization logic now supports applying multiple blocks at once and invokes updateConsensusInformation automatically after block insertion. This streamlines the update flow and reduces the interface complexity needed to propagate consensus changes.  

---

2025-04-11 Fri: This week, progress on the upgrade to version 1.10 reached approximately 50%. Key updates include the addition of the BASEFEE opcode, implementation of Access List support, and integration of several PRs adjusting opcode pricing. These changes are essential steps toward aligning with upcoming protocol specifications and improving overall performance. Additionally, enhanced logging was introduced to improve visibility into the view change process during epoch transitions. Although I haven’t been able to reproduce the reported issue locally, the added logs should provide better diagnostics and help track down the root cause if it reappears.

--- 

2025-04-04 Fri: Launched devnet testing for the update to Ethereum source code version 1.9. Devnet and testnet have been updated to the latest development version. The release branch has been tagged. Currently preparing the release build.
Upgraded the Ethereum codebase to version 1.10, affecting approximately 25% of the total codebase. This update includes the Berlin and London network upgrades.

---

2025 Q1 Review

I upgraded the Harmony codebase from Ethereum source version 1.8 to the 1.9 major release, improving EVM internals—including stack management, function handling, and initialization. This PR aligns our codebase with Ethereum, resolving key discrepancies.

I also fixed leader rotation stability in block production, launched 1-second finality on devnet, implemented the BaseFee field in the block header and integrated Ethereum’s EIP-2565 update, upgraded Golang to version 1.24, and improved CI testing for PRs on Travis.

---


2025-03-21 Fri:
- Updated 1-second finality feature based on review comments and additional improvements. Passed the review and is expected to be deployed to devnet next week.
- Updated effective gas price to return a default value of 100 GWEI, preventing potential null values.
- Reviewed 25% of the PR for the 1.9.25 update, which includes modifications across more than 40 files.

---

2025-03-14 Fri:
- Updated Ethereum version in source code to 1.9.25; all unit tests passed, integration tests expected to pass as well.
- Discussed details of 1-second launch with Ulad; scheduled launch for next week, working on necessary preparations.
- Coordinated with Sun on upcoming code updates and implementation details.
- Reviewed pull requests.

---

2025-03-07 Fri:
- Updated the Ethereum version in our source code to 1.9.25. This update includes EIP-2929 and a VM update to stack uint256.Int. However, it requires test modifications, which I am currently working on.
- Upgraded the Go version to 1.24, the latest available at the moment.

--- 

2025-02-28 Fri:
- Implemented EIP-2929: Increased gas costs for state access opcodes, such as SSTORE. This PR is the second of four required for the Berlin update.
- Finalized EIP-2565: Adjusted ModExp gas costs and resolved issues with failed Travis CI tests.
- Fixed effective gas price calculation to return the GasUsed value instead of nil.
- Reviewed multiple pull requests.

---

2025-02-21 Fri:
- Created branches to track progress on the Berlin and London updates.
- Implemented EIP-2565: ModExp Gas Cost, which reduced the gas price for the modexp operation, reaching approximately 25% completion for the Berlin update.
- Collected EIPs required for implementation as part of the London and Berlin upgrades.

---

2025-02-14 Fri:
- Reduced block production time from 1 second to 0.950 seconds in the 1-second-finality branch to mitigate network latency.
- Implemented a new block version following EIP-1559 and EIP-3198. This branch incorporates changes introduced in these two Ethereum EIPs as part of the London hardfork.
- Updated the BLS library with the latest changes from upstream. This branch includes over 100 modified files, incorporating the latest security updates. 

---

2025-02-07 Fri:
- Investigated and resolved an issue with the effective gas price. Developed tests to validate the creation of transaction receipts and block receipts across a range of 0% to 15%.
- Collaborated with Sun on the EIP-1153 transition storage, gathering and refining implementation requirements.
- Updated old pull requests with the latest changes from the development branch.

---

2025-01-31 Fri:
- Identified the cause of the view change issue and am actively working on a fix. The issue occurred because a node was left mining alone, with no other nodes triggering block processing mechanisms like prepare and commit.
- Reviewed and merged multiple PRs.
- Collaborated closely with Sun on EIP-3607: Reject transactions from senders with deployed code.

--- 

2025-01-24 Fri:
- Resolved the issue with duplicated proposal messages, which could potentially trigger the view change mechanism.
- Enhanced the make debug-kill command to ensure all processes are properly terminated, addressing an issue where some processes were left running.
- Reviewed several PRs, particularly those related to the release branch.
- Made approximately 50% progress on the view change issue.

---

2025-01-17 Fri:
- I, Ulad and Soph devised and implemented an approach to repository testing that eliminates the need to explicitly specify the test branch in the main repository. This avoids hardcoding and significantly enhances development flexibility.
- Together with Ulad and Soph, I participated in discussions about potential additional testing scenarios. The current approach no longer meets our needs as it tests an outdated model. In its current state, we need to validate scenarios where a node has multiple keys and/or multiple validators running on the same node. Brute-forcing all possible combinations would exponentially increase test execution time or make it impractical. At this stage, we are exploring optimal solutions.
- Ulad and I discussed potential additional testing scenarios for the view change mechanism, such as disabling a random node and verifying the network’s operability under such conditions. Currently, we have agreed to start with disabling a specific node, with the long-term goal of transitioning to random node selection.
- My main focus this week has been on fixing an issue in the view change mechanism. The situation is complicated by the large number of possible configurations. I estimate my current progress at 30%.

--- 

2025-01-10 Fri:
- Updated the Message struct to ensure alignment with Ethereum code standards.
- Enhanced test scripts to automatically download the required branch, leveraging the TRAVIS_PULL_REQUEST_BRANCH variable. This eliminates the need for hardcoded branch names in the scripts.
- Resolved an issue with effectiveGasPrice for staking transactions.
- Continued work on implementing EIP-3607, which marks the initial phase of sponsored transactions.

---

2025-01-03 Fri:
- Refactored the consensus module by splitting it into smaller, modular structs to enhance testability and maintainability. Increased test coverage for consensus statements from 15% to 18%. 
- Initiated the implementation of EIP-3607, enabling rejection of transactions from senders with deployed code. This progress represents one-third of the required work for full support of EIP-3074-sponsored transactions. 

---

2024-12-20 Fri:
- This week, I resolved the issue of excess signals in the consensus, which addressed several problems. However, while working on achieving 1-second finality, I identified additional issues that I plan to fix this week.
- Fixed an issue with the view id, which could remain unchanged when the syncNotReadyChan method was called. Although the method updated the block number, it did not update the view id, potentially causing the node to get stuck.
- I worked on 1-second finality, which successfully operated for 96 epochs without any major issues.

---

2024-12-13 Fri:
- This week, Gheis and I worked on a fix for the leader rotation issue that could cause an unintended view change. 
The issue occurs only in nodes with multiple BLS keys. In these cases, the node fails to receive the required block proposal notification. 
As a result, after a certain period, the view change process initiates and switches leadership to another node. 
- Ulad and I are working to enable testing under different conditions, focusing on evaluating nodes with both single and multiple keys.


---

2024 Q4 Review

Successfully [completed](https://github.com/harmony-one/harmony/pull/4769) the leader rotation process, ensuring a smooth mainnet launch by enhancing synchronization mechanisms to guarantee [uninterrupted](https://github.com/harmony-one/harmony/pull/4804) block production. Introduced a bypass for [inactive leaders](https://github.com/harmony-one/harmony/pull/4802), significantly reducing potential downtime and improving network resilience.

Additionally, I worked on improving local network [development](https://github.com/harmony-one/harmony/pull/4753), enhancing network [insights](https://github.com/harmony-one/harmony/pull/4785), and refining proposal signals to optimize block production for [multi-BLS](https://github.com/harmony-one/harmony/pull/4816) nodes.



---

2025 Goals:

Achieving 1-Second Finality:
My primary goal is to achieve 1-second finality. I’ve encountered challenges with block proposing when using multiple keys on the same node, particularly during leader rotation. Eliminating these delays is essential, as they significantly impact the consistency of achieving 1-second finality.

Launching Stream+Stage Sync:
My second goal is to deploy the Stream+Stage synchronization mechanism. Stream sync offers a more efficient synchronization process, which will significantly enhance overall network performance.

Support for EIP-3074 Sponsored Transactions:
EIP-3074 introduces sponsored transactions, allowing third parties to cover gas fees on behalf of users. This feature will enable users to interact with decentralized applications (dApps) without needing ETH for gas, improving accessibility and enhancing the overall user experience.

---

2024-11-29 Fri:
- I added additional checks to the synchronization mechanism to ensure that nodes do not update their consensus information during the block construction process. The consensus now ignores BlockSynchronized events while acting as the leader.
As leaders responsible for producing blocks, we must prevent any steps that could disrupt the process. Synchronization should instead be deferred and executed later when the system is idle.
- I made additional changes and minor improvements. The method WaitForConsensusReadyV2 was moved out of the consensus module since it was not being used within the consensus logic itself.
 
---

2024-11-22 Fri:
- This week, I finalized the team's suggestions for handling view change validators' skipping. Gheis and I agreed to use the same interfaces for our respective features to streamline future integration. I implemented the viewChangeNextValidator function, which contains the core logic and is backed by nearly 100% test coverage.
- I'm currently working on removing the update synchronization call. This call triggers a consensus information update, which can disrupt the cycle of block production. 
- I’m actively participating in PR reviews. Most of the changes impact the consensus part of the codebase, so I’m focusing on analyzing the consensus logic and evaluating how these changes affect network stability.

---

2024-11-15 Fri:
- This week, I identified an issue with view changes. Unlike leader rotation, a view change doesn’t alter the leader, so the offset from the last leader remains unchanged. As a result, the mechanism used for leader rotation doesn’t work the same way for view changes.
To address this, I implemented additional logic to verify the consistency of validator addresses. Currently, I’m working toward achieving 100% test coverage for this critical functionality. The codebase has strong interdependencies, so my primary focus is to break it down into smaller, independent components to simplify testing and improve maintainability.  

---

2024-11-08 Fri:
- This week, we received several notifications while on call. There was approximately 12 minutes of downtime during which I actively participated in the recovery and investigation process. Most of the other notifications were resolved quickly or turned out to be false alarms.
- I am working on resolving an issue causing additional delays in average block production. The problem may involve redundant view change processes triggered by an issue that prevents the local network from running with multiple keys on a single node. Initially, I confirmed that the issue is not related to the previous block overriding the state, as we can observe multiple blocks being sent simultaneously. However, this behavior should be canceled by the didReachPrepareQuorum method, which fails to execute due to insufficient signatures being collected.  

---

2024-11-01 Fri:
- I completed the final preparations for the HIP-32 update, which was successfully activated at epoch 2152 without major incidents. Following the update, my focus shifted to analyzing and troubleshooting issues reported by validators.
- The `UpdateConsensusInformation` method has been removed. Previously, calling this method before the finalCommit method could have resulted in undefined behavior or even a hard fork. Its removal reduces the likelihood of inadvertently triggering a clean state.

---

2024-10-25 Fri:
- Developed a workaround for an empty hash issue, incorporating a fix that prevents empty hashes from being processed and sent to other nodes. The root cause lies in the `UpdateConsensusInformation` method, which is triggered without any changes in the blockchain, resulting in the hash being cleared while awaiting the `finalCommit` method call.  
- Additionally implemented a fix to reduce the call count to `UpdateConsensusInformation`. This solution includes extra checks and periodic block collection to prevent consecutive, redundant calls.
- Added logging within `LegacySync` to trace the call stack of `UpdateConsensusInformation`.

---

2024-10-18 Fri:
- Investigating with Ulad an issue where a zero hash is being transferred across the network. The issue is reproducible on the local network with external validators and results in a node fork. To resolve the issue, the node must be reverted by 1 block after the fork.
- Created an issue for the make debug-ext command, which fails to run on Mac due to differences in command syntax.

---

2024-10-11 Fri:
- 1-second finality: Removed all related block signing and commission split changes. Submitted a new PR with no modifications. The 1-second finality will proceed without any commission split modification.
- Added `effectiveGasPrice` to ETH transaction version for `GetTransactionReceipt` and `GetBlockReceipts` API methods.
- Fixed the branch with lock acquisition to ensure it passes all tests.
- Reviewed release branch.

---

2024-10-04 Fri:
- Resolved conflicts between the latest development branch and the 1-second-finality feature.
- Reviewed a PR from the community regarding slice initialization. The issue arises from mixing different initialization methods, which can lead to undefined behavior. Fortunately, this seems to occur in unused or dead code.
- Updated configurations for the HIP-32 update, including the epoch fork and chain configuration. 

---

2024 Q3 Review

Added the `effectiveGasPrice` [field](https://github.com/harmony-one/harmony/pull/4759) to the `getTransactionReceipt` method to maintain compatibility with Ethereum. Completed the implementation of 1-second block [finality](https://github.com/harmony-one/harmony/pull/4738), significantly improving transaction confirmation speeds. [Finalized](https://github.com/harmony-one/harmony/pull/4738) a new commission split mechanism to support 1-second finality and a 67% vote power threshold.

With Ulad and Soph, updated to Go version 1.22. Go [1.22](https://github.com/harmony-one/harmony/pull/4736) provides improvements in the crypto package, updates to the latest package versions and enhanced performance. Enabled the epoch chain to [broadcast](https://github.com/harmony-one/harmony/pull/4756) the epoch block, reducing other shards' epoch block synchronization time to up to 2 seconds. Implemented broadcasting of [vote power](https://github.com/harmony-one/harmony/pull/4748) along with view change signature info, improving observability of nodes. 

---

2024-09-20 Fri:
- Implemented `effectiveGasPrice` Calculation: The `getTransactionReceipt` method now includes the `effectiveGasPrice` parameter. Even without the `baseFee` in the block, our transactions can still support `effectiveGasPrice`. This enhancement ensures accurate transaction fee calculations and maintains compatibility with the Ethereum specification.
- Fixed Peer Selection Bug in LocalSyncingPeerProvider: Addressed an issue where the previous implementation prevented correct peer selection for syncing in the localnet. This fix improves the efficiency and stability of the local network.
- Disabled Stream Sync on Localnet: Due to issue #4749, stream sync has been temporarily disabled on the localnet to prevent potential testing complications associated with this issue.

---

2024-09-13 Fri:
- Implemented broadcasting for the epoch block. The previous epoch sync updated every minute, which was excessive and could trigger unnecessary view change activations. The new implementation reduces the delay to approximately 2 seconds, significantly improving efficiency.
- Fixed an issue with the legacy sync port. When the number of shards was reduced from 4 to 2, the algorithm incorrectly mixed ports for shard 0 and shard 1, breaking consensus and initiating the sync process. The fix resolves this issue and ensures stable operation. 
- Worked on the EIP-1559 upgrade. This update introduced the effectiveGasPrice and its calculation, along with a new block version, a Base Fee field in the block, and additional transaction fields.

---

2024-09-06 Fri:
- Fixed an issue with crosslink processing identified by Soph. Recent commits included additional error checks, which inadvertently prevented crosslink processing on the local network.
- Addressed an issue reported by Ulad related to vote power broadcasting. The previous implementation did not broadcast view change values, so I added an additional broadcasting mechanism. However, this mechanism may still have some limitations and has not yet passed all tests.
- Began work on the `effectiveGasPrice` parameter for the `getTransactionReceipt` method. The current implementation is outdated and no longer conforms to the Ethereum specification.

---

2024-08-30 Fri:
- Finalized "Broadcast Vote Power": Our network monitoring systems rely on the "sign power" API method from the leader node. However, with leader rotation enabled, the leader is often unreachable. To address this, we implemented a feature that allows the broadcast of this value, making it accessible from any node in the network. 
- Completed Crosslinks Feature for HIP32: This feature enables committees to continue operating even if no crosslinks are sent. We have encountered situations where this occurred, and the feature aims to prevent such issues in the future.
- Enhanced Watchdog for Localnet Nodes with Ulad: While testing vote power broadcasting, we discovered unpredictable node assignments within localnet and watchdog. Additionally we reactivated a previously disabled API for localnet that was disabled by default.   
- Made `getLastSigningPower` API Method Public: The getLastSigningPower method, which does not contain any private information, has been moved from the private debug API to the public API. 

---

2024-08-23 Fri:
- Lock-Free Consensus Methods for Message Validation: The current consensus mechanism involves sending messages from methods that are under `mutex.Lock`, which in turn call libp2p. Since libp2p also uses `mutex.Lock` internally, this can lead to potential deadlocks. To prevent this, we need to call such methods asynchronously. However, executing these methods asynchronously introduces unpredictability in their behavior.
- Investigating the Zero Sign Power Issue on Local Watchdog: I was unable to identify the cause of the zero sign power issue on the local watchdog. This problem requires further investigation on the devnet. I will continue working on this with Ulad next week.
- Reviewing Pull Requests.

---

2024-08-16 Fri:
- Working on branch with 1 second finality and 67% signers count. It passed 75% of tests
- Was investigating the `context deadline` issue occurring on the localnet with Streamsync. During the investigation, I discovered duplicated connections. When a connection is replaced with a new one, any requests in progress on the old connection are discarded, leading to the deadline error. However, I have yet to determine the root cause of the connection duplication.
- Fixed an issue with `legacysync` where incorrect ports were being used, causing shard 0 to receive information intended for shard 1. This miscommunication forced unnecessary synchronization, disrupting consensus and preventing the proposal of new blocks. 
- Reviewing and merging pull requests.  

---

2024-08-09 Fri:
- Collaborated with Ulad to update harmony-test repo. Even it flexible to run various branches and not the default one, it's impossible to configure to run certain golang version instead of default. We were working on additional arguments which could be provided on start.  
- Created new version of commission split, where necessary to sign only 67% of the validators. It allows to skip waiting time for the rest of the validators, but requires code changes in the network and the signing layers, and i working to achieve it being stable.  
- Created new fix for the theoretical zero division issue, it does not happen, but when harmony nodes count will be zero, it will. Issue was provided by Soph.
- Was reviewing Pull Requests, merging and providing feedback.

2024-08-02 Fri: Updated golang to 1.22. With Ulad tested made additional tests golang 1.22. Version 1.22 does not have incompatibility or stability issues. Results can be found https://github.com/harmony-one/harmony/pull/4722/#discussion_r1702049235

**Research on 1-Second Finality and Validator Rewards in Block Signing**

In the context of Byzantine Fault Tolerance (BFT) protocols, achieving consensus requires collecting 67% of the votes. To optimize our protocol for validator rewards and block signing without significant changes, i have identified two potential approaches:

*Reward Splitting Among Validators Who Sign the Block*:

In this approach, rewards are distributed among the validators who successfully sign a block. This method encourages competition among validators, potentially increasing operational costs and leading to greater centralization within our network. Networking efficiency will become crucial, as a single high-performance server will be more profitable than multiple lower-performance servers. As a result, servers may be concentrated in the same data center to minimize latency.

*Reward Splitting Independent of Block Signing*:
Here, rewards are split among all validators regardless of whether they sign the block. This makes block signing optional for individual validators, yet incentivizes collective action, as the total reward increases when all validators sign the block as quickly as possible. This approach simplifies the reward distribution process and enhances performance.

Currently, our protocol does not support identifying a block proposer. While theoretically, we could distribute rewards between the block proposer and the validators, implementing this would necessitate significant protocol modifications. These changes would include updates to block proposing, consensus mechanisms, reward calculation, crosslinks, and the introduction of a new block version.   

---

2024-07-26 Fri:
- Fixed issue with zero division
- Tested new golang version and the latest go-lib-p2p version on devnet in different combinations with bootnode. 
- Found and fixed issue with security incompatibility.
- Found and fixed issue with multiplexer incompatibility.
- Tested new code in testnet environment, it was successful.
- Tested mainnet compatibility, contains differences in security parameter. Will continue on Monday.  

---

2024-07-19 Fri:
- Updated golang version to 1.21 version, it passed all tests, total progress 100%. 
- Investigated and fixed issue with different hashes for the same genesis block. Go@1.21 provides different dots on the curve for the same input, so i hardcoded exact dots.
- Tested and merged PR with fix for the peer storage. Improved getting connected peers method from linear complexity to constant.
- Finalized watchdog integration with the localnet. Collaborated with Ulad. Merged.
- Created new issue and started investigation of the watchdog crushes. 
- Collaborated with Ulad for the go@1.21 devnet testing. Test results showed that the node has problems connecting to other nodes. We will continue investigation on monday. 

---

2024-07-12 Fri: Investigated the issue with the hash generation in localnet testing. Go@1.21 changed behavior of the ecdsa key generation function, so it can provide different private keys for the same input. Described [here](https://github.com/golang/go/blob/release-branch.go1.21/src/crypto/ecdsa/ecdsa.go#L153). Updated hotstuff description and commit messages. It can be found [here](https://github.com/Frozen/gohotstuffimpl)

---

2024-07-05 Fri:
- `UpdateMaxCommissionFee` function covered with tests. 
- Provided fix for the node bootstrap process, which was using incorrect method to calculate connected peers. 
- Fixed the `PeerConnectivity` method, which was using iteration over 20k elements in the worst case, now it has no iteration at all.
- Removed trailing zeros from the Decimal.String method.
- Resolved connection issues in the tests package of the Harmony p2p library. 
- Golang version update: passed 50% of tests, current progress is 80%.

---

2024-06-28 Fri:
- Updated go-lib-p2p to the latest version, which can potentially fix issue with bootnode. 
- Updated golang version to the latest, it passed 25% tests, total progress about 70%. 
- Moved tests from separate repository to the project. Having additional repo gives only disadvantages for the small team, forcing us to support 2 different repos aimed to the same goal. 

2024-06-21 Fri: 
- The current status of 1-second finality is approximately 40%. 
- I refactored block proposing, because current implementation does not allow to propose blocks from consensus, it fails with cyclic dependencies. 
- I improved reward calculation frequency, which made our tests execution 2x times faster.
- I implemented minor improvements for the consensus, which were found during the investigation of the undeletions issue and the hotstuff consensus research.

---

**2024 Q2 Review**

Soph and I identified the root cause and implemented a solution for the undeletions issue; I investigated the crosslinks bug and implemented a fix for crosslink processing. I developed a new consensus message for broadcasting vote power across the network. 
I implemented unpredictable leader switch using the verifiable random function. I implemented a prototype for the HotStuff chained protocol, available [here](https://github.com/Frozen/gohotstuffimpl).
HotStuff involves block proposing by the validator who is the future presumptive leader. However, this approach is only partially applicable for us, as it implies rollbacks in the worst-case scenario, which the Harmony blockchain does not support. By applying block proposing within the prepared stage, we can save one network communication without causing a rollback in the worst-case scenario.

---

2024-06-14 Fri: This week we were investigating the issue with undeletations. I created 1 pr with fix, and 4 with different activation for mainnet and devnet. Additionally created PR that fixes race error, and another one for minor improvements which was found during the investigation.

---

2024-06-07 Fri: This week, I completed the task of broadcasting vote power across the network. I also resolved a panic issue during unsuccessful node termination that could potentially lead to state corruption. Additionally, I implemented a PoC for the HotStuff chained protocol, aiming to understand the differences between Harmony's implementation and HotStuff's approach.

---

2024-05-31 Fri: This week, Soph and I have been testing the crosslink fix on the devnet. It successfully synchronized all missing crosslinks, so we have moved further testing to the testnet. Additionally, I am continuing to work on leader broadcasting vote power through the network. This will enable us to debug the network even when we lack information about the leader.          

---

2024-05-24 Fri: This week, Soph discovered another way to sign crosslink. I implemented a new version that not only improves the sender side (as the previous version did) but also enhances the receiver side, making it more suitable for our needs. Additionally, I worked on asynchronous code, specifically on two functions that execute in an unpredictable order. The pull request for this is completed but is dependent on the functionality of another unmerged PR.        

---

2024-05-17 Fri: This week, I fixed three issues with crosslinks. Additionally, I removed the NthNextHmyExt method, which had a bug in its implementation but was not used in the production code.      

---

2024-05-10 Fri: This week I have reviewed the dev branch and investigated issues with the bootnode. I've merged the pprof PR into the dev and created an issue with the dump for further investigation, which seems to be deeply rooted in the libp2p implementation. Additionally, I've been reading about the HotStuff consensus protocol and its rust implementation.    

---

2024-05-03 Fri: This week i implemented unpredictable leader rotation by VRF function. Additionally, i was working with Uladzislau on bootnodes update, they consumed too much resources, we increased limits and added profiling information for future debugging. And i was collaborating with Adam on harmony smart contract development. 

---

2024-04-26 Fri: This week i was working on block proposing code. I provided additional logging, and refactored code, for feature seamless integration 1 second finality. Also, i'm collaborating with Adam on groth16 solidity part, i asked him to help me integrate web3 frameworks with local harmony development.   

---

2024-04-19 Fri: This week, I provided a feature for checking the synchronization state while a node is in the view change process. This prevents the node from possibly getting stuck. Additionally, I published several PRs to improve node logging.   

---

2024-04-12 Fri: This week i provided additional logging for consensus, block proposing and synchronization. Additionally, i created a PR without periodic synchronization calls. This was a drawback for a stuck node to force sync process, but calls for the method may cause consensus loss.

---

2024 Q1 Summary<br>

Protocol Engineering:<br>
During Q1, my primary focus has revolved around leader rotation testing and activation. This involved rigorous testing across various scenarios, including sequential deactivation of internal nodes, fail tolerance, and performance measurements from remote regions. We successfully conducted tests on the devnet and anticipate further activation on the testnet.
In addition to leader rotation, I've also explored a feature that allows skipping keys when they belong to a single address, enhancing recovery by redirecting to another validator instead of attempting keys of an already inactive one individually.
I dedicated effort to resolving issues following HIP-30 activation, particularly concerning coincidences and a significant number of consensus losses.
Furthermore, in my research endeavors, I delved deeper into the Groth16 native EVM implementation. Native implementation requires precompiled contract, which one i've already implemented. Currently it required Solidity wrapper on the low level code, but i faced with total lack of utilities for local development. Groth16 is zero-knowledge, which allows a prover to convince a verifier of the truthfulness of a statement without revealing any additional information about the underlying data.  

---

2024-04-05 Fri: This week, I'm with Diego and Soph investigating the issue with external validator, which not being elected by the consensus. Additionally, i provided several PRs which increase the stability of the network. 

---

2024-03-29 Fri: This week i was working with Ulad and Diego on devnet shard 1 recovering. Additionally, i'm working on the implementation of Groth16 in Solidity, with a specific focus on creating a reproducible working example. 

---

2024-03-22 Fri: This week, i was investigating an issue preventing progress on devnet. I've found that the issue was originally caused by out of space error. We are working with Gheis on a fix. 

---

2024-03-15 Fri: This week, I concentrated on integrating Groth16 into Solidity. I've been working on the decoding and encoding aspects of Solidity contracts to enable calling precompiled functions. Additionally, I've implemented several fixes for the backup functionality.

---

2024-03-08 Fri: This week, i was working on internal functionality for Groth16. I've implemented integration between evm and groth16 library through precompiled contract. 

---

2024-03-01 Fri: This week, I addressed the problem with the backup feature and incorporated new Prometheus logs to monitor the count of signatures.

---

2024-02-23 Fri: This week, we made updates to the devnet by integrating external community validators and updated the testnet with the leader branch. Additionally, I focused on improving view change processes, refactoring code, and implementing additional checks for view change block processing.  

---

2024-02-16 Fri:  This week, I focused on addressing the mainnet downtime issue. I've been working on a feature aimed at preventing the processing of invalid blocks during the view change process. I've submitted multiple pull requests to enhance the view change logic and implemented additional validations. Furthermore, I successfully updated our libp2p dependencies, which was blocking us from updating the Go version.       

---

2024-02-09 Fri: I collaborated with Diego to test network performance. It passed successfully. Additionally, I updated my previous PRs. I've updated libraries, which prevented compilation with new golang versions. And I added additional code for the leader to detect sign power during network downtimes.

---

2024-02-02 Fri: During the first half of the week, I collaborated with Soph and Diego to investigate a devnet hardfork. We successfully identified the root cause and implemented a hotfix, incorporating additional performance improvements. In the second half of the week, I worked with Diego on testing network performance. This involved assessments on both our internal network and external validators located at a distance, ensuring that the new code wouldn't lead to downtimes or performance issues.

---

2024-01-26 Fri: Testing `revert` command functionality found that it can cause panic under certain circumstances, so now we don't try to restore state from the partially valid data, only remove it. It was already tested and merged by Soph. Currently devnet is fully decentrialized, and doesn't contain internal validators, but it still require small improvements like additional logs and fixes for the issues.    

---

2024-01-22 Mon: This week i fixed bugs on devnet with concurrent map access and block insertion. In collaboration with Diego, we successfully launched the devnet with external validators.   

---

2024-01-15 Mon: This week, I fixed the "block exists" issue which no more leads to a node stuck on the devnet. Additionally i am investigating an issue related to a buggy validator state on the mainnet node. 

---

2024-01-08 Mon: This week, i was investigating the issue with balance transferring on devnet with activated rotation. I was collaborating with Diego, finally, we decided to reset devnet. 

---

2024-01-01 Mon: This week, i was investigating the issue with the validator code wrapper while undelegation process. Additionally, i was collaborating with Diego on the leader rotation on the devnet.

---

2023-12-25 Mon: This week we activated external rotation on devnet. Additionally, i started research on SNARKS, advantages/vulnerabilities/implementations, and how it can be integrated into the blockchain.

---

2023-12-18 Mon: This week, I developed a new API method for calculating sigh power without a leader. This feature will become relevant once leader rotation is activated. Furthermore, I addressed an issue related to counting the minimum block count for leader rotation, ensuring smoother functionality. 

---

2023-12-11 Mon: This week, I conducted internal leader rotation testing on the devnet and focused on external rotation. Moreover, I incorporated necessary information into the watchdog system, as external validators do not provide signing power.

---

2023-12-04 Mon: This week, I addressed all the issues discovered by Soph regarding leader rotation. Furthermore, I resolved an issue introduced after the last merge, prevented the code from passing tests, and fixed an infinite loop that could occur during stream synchronization.

---

2023-11-27 Mon: This week, I enhanced epoch chain synchronization and improved the efficiency of test execution. We no longer encounter floating tests, and the test execution time has been significantly reduced. Furthermore, I eliminated outdated code related to block insertion, resulting in lower memory consumption and improved processing speed.

---

2023-11-20 Mon: I investigated an incident that occurred with two nodes in the devnet. Following thorough research, I submitted several pull requests (PRs) to enhance stability and performance. Furthermore, I implemented integration with the ELK Stack (Elasticsearch, Logstash, and Kibana) for local development, facilitating real-time log analysis.

---

2023-11-13 Mon: I addressed an issue occurring during node initialization that was preventing nodes from starting. Additionally, I resolved an issue preventing nodes from passing tests. Furthermore, I investigated an issue with leader rotation, identified by Soph, which was slowing down the epoch change mechanism.

---

2023-11-05 Sun: I conducted testing on leader rotation, addressing various bugs associated with the network stack. Additionally, I am currently investigating an issue concerning duplicated events in the context of block proposing.


