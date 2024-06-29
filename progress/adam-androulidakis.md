2024-6-28 Fri: <br>
Weekly summary <br>
-Attended general engineering and devops discussions (Tuesday/Thursday) <br>
-Performed code reviews/approvals and other general protocol duties <br>
-We are still trying to deploy some Gains network contracts, there still seem to be some resources missing such as a storage contract we are unable to locate. I am uncertain if we are going to proceed with this one. I have scheduled some time to coordinate with other members of the team and the custodians of the platform to bring this task to a close <br>
-Reviewed some of the most recent contracts that were published in Harmony's repositories such as gmx_contracts <br>
-I reviewed several of our publications and reports to maintain sychronization with our teams progress and goals <br>

---

2024-6-21 Fri: <br>

-Early in the week the team was making many preparations for a hard fork release. <br>
-This week I concluded dev-ops on-call duties for the month of June <br>
-I have been focused on research into potential security pitfalls with perpetual futures contracts, and understanding risks and recovery procedures and previous incidents with relative protocols <br>
-Sorted out several issues with dependencies and understanding unknowns during pre-deployment verification <br>
-Out Wednesday for personal day <br>
-Attended code review sessions with other protocol engineers throughout the week, leading to review and approval of a few essential pull requests awaiting merge <br>

---

2024-6-14 Fri: <br>
<br>

-Code reviews and approval of hotfixes <br>
-Carried out devops on-call duties: https://docs.google.com/document/d/1m_tMXh0K5fCmuCeXV-tJSmwDUFkcH2tvJzUAmXgAbvA/ <br>
-Continued to work on deploying a set of perp contracts. I am still sorting out the dependencies and working on the ground work <br>
-Attended a review meeting with Li <br>
-We have been looking into an issue with undelegation and are now waiting to coordinate deploying the fix <br>
-Attended discussions on HIP-32 issues with the devops team <br>

---

**2024 Q2 Review**

Finalizing all requirements to deliver HIP-32, focusing on peer-to-peer issues impacting network synchronization and undelegating from validators. I am now focused on deploying a set of contracts that match up with our goal of releasing useful perpetuals trading tools. I am outlining the requirements and writing/preparing the necessary contracts and getting Hardhat and other frameworks working correctly on the Harmony localnets to properly deploy/test/use [Uniswap v3](https://github.com/harmony-one/harmony_uniswapv3) router contracts.

Delivered gameplay concept for [Chain Force](https://github.com/harmony-one/Project-G/releases/tag/1a) with [music track](https://github.com/harmony-one/Project-G/commit/25a06052816313c3e9a7e9e66be4faa2f29fbe5e). Along with the relative written godot SDKs, it is now being handled by an [external developer](https://github.com/harmony-one/Project-G/blob/main/log) I coordinate with. Lastly, I'm finalizing my write-up that ties together Harmony blockchain, gaming, AI goals.

---

2024-6-7 Fri:
-Watched a bunch of videos while recovering from my illness, research, etc: https://github.com/adsorptionenthalpy/perp_resources<br>
-There were problems with hardhat deploying contracts onto harmony local (debug) and mainnet. This should be fixed now. https://github.com/adsorptionenthalpy/harmony_hardhat. This hardhat scaffold contains two original FIO smart contracts for an erc20 and erc721 token with built in elected oracles and operating custodians that may prove useful in wrapping/unwrapping tokens securely.<br>
-A note about deploying locally: some Harmony staff have reported issues with insufficient funds while deploying using a .env key for hardhat projects. The debug environment stores the keystore for prefunded accounts in /harmony/.hmy/keystore. Import these keys with `hmy keys import-ks`, and then `hmy keys export-private-key keyname` will provide a 32 bit key that can be easily be used in hardhat as `process.env.THE_PRIVATE_KEY` (saved in `.env` as `THE_PRIVATE_KEY=123456789KEY`) <br>
-Deployed gain locally https://github.com/adsorptionenthalpy/harmony_gain, this requires a Uniswapv2 router which I am working on streamlining deployment on Harmony. The sweepstakes code will need to be stripped out if we want to use this as the contract doesn't seem available, this also involves removing references to some of the formulas within the solidity source. <br>
-There is another set of contracts for GainsNetwork which may be preferable to the GainProtocol https://github.com/adsorptionenthalpy/gTrade-v6.1 these I have roughly deployed on Harmony locally but they also require interfaces to be initialized <br>
-Performed code reviews with members of the protocol team <br>
-I am currently investigating problems with undelegation on protocol side of things <br>

2024-5-31 Fri: <br>
-Out sick most of the week <br> 

2024-05-24 Fri: <br>
-Spent a good chunk of my week getting some of these validator nodes in order. Configured a new bare metal server from scratch using recovered keys and new hardware including 8TB Raid1. <br>
-devops on-call duties (part 1) https://docs.google.com/document/d/1SQwAozqyNJBTbcX18YStZqQtMYyde46Nb-Z9jhgWrvs <br>
-Review PRs fixing bootnode instability issues (w/ Gheis) <br>
-Research on econ and finance topics and anything pertaining to "perpetuals/futures contracts" <br>

---

2024-05-17 Fri: <br>

-Exploring further into 3rd party defi protocols (dydx, gains, oasis)<br>
-Analysis of GainsNetwork gTrade-v6 contracts https://github.com/GainsNetwork/gTrade-v6/tree/main/contracts and test deployments to local testnet <br>
-exercise: liquid staking of stONE <> wstETH<br>
-wrapping up writeup (WIP)<br>
-investigate issues with devsnode validator. OS will not boot. Rebuilt OS and SSD appears to have read issues. <br>I went and physically bought a replacement drive and new drive should be up shortly<br>
<br>

---

2024-05-10 Fri: <br>
-come up with an in-game beat, not too repetitive, too long or too short, and implement in uninterrupted loop <br>
https://github.com/adsorptionenthalpy/Project-G/commit/25a06052816313c3e9a7e9e66be4faa2f29fbe5e <br>
-analyze 3rd party defi contracts for port to harmony <br>
-devops: investigate problems with bootnode <br>
-review fixes to boot node <br>
-migrate devsnode validator to new network <br>
-work on write-up: Harmony goals <br>
<br>

---

2024-05-03 Fri: <br>
-Communication w/ Konstantin and Rika on contract deployment issues
Looking into simplifying harmony contract deployment https://github.com/adsorptionenthalpy/harmony_contracts <br>
I then discovered https://github.com/harmony-one/hardhat-starter-pack that hasn't been updated for some time and relayed to members of the team to look into <br>
-Work on ChainForce network, multiplayer and blockchain components <br>
  - Implemented high score feature so there is data to upload chain data to local harmony instance <br>
    - contract implementation: leaderboard contract only invoked when a player's score has surpassed any score in the leaderboard <br>
    - Challenges: best method to retain achievement info offchain for later onchain push<br>

---

2024-04-26 Fri: <br>
-time-off<br>
-Interviewed some devs in Boulder over lunch<br>
-Protocol PR reviews: Improve staged stream sync, log and cleanup, devnet vote power update https://github.com/harmony-one/harmony/pull/4660<br>
https://github.com/harmony-one/harmony/pull/4656<br>
https://github.com/harmony-one/harmony/pull/4662<br>
-Devops on-call - https://docs.google.com/document/d/1GtkLBK7tP1-nJ3xxaSMBawwVO3oOL_5rd-QyN9nk5aM<br>

---

2024-05-19 Weekly Update<br>
-Wrapped up development for single-player offline demo release Chain Force https://github.com/harmony-one/Project-G/releases/tag/1a<br>

---

2024 Q1 Summary<br>

Protocol Engineering:<br>
For the duration of Q1, my primary focus has been on the harmony gaming initiative. On the protocol side my time has been applied to working with the team in security and outage incidents, and research. I have not made any new advancements in Harmony's ERC4337 account abstraction implementation at this time. 

In research, I have dug further into various abstract security topics, such as formal verification of smart contracts, smart contract security, and deep diving into active Ethereum proposals such as EIP-4844 (protodanksharding), EIP-6780 (Restrict SELFDESTRUCT), EIP-5656 (MCOPY opcode), EIP-4788 (Beacon block root commits), EIP-1153 (transient storage opcodes). 

Devops:<br>
Performed code reviews on many pull requests, looking mostly for issues that could lead to consensus loss and new problems with delegators. I have also collaborated with our team on occasion working to identify and resolve various reoccurring issues with Harmony Mainnet, testnet and devnets. 

Harmony Gaming:<br>
Spent a lot of time researching several different gaming projects, sampling code from them and communicating with developers. I linked with developers and artists at Ethereum Denver and referred those that could be a valuable addition to the Harmony team. 
I completed a rather lengthy update of a formerly released Web3 plugin for the Godot engine written in c++ to support the latest engine updates to 4.x. The plugin is now available to the community as an important component of the sdk. In addition to the Godot web3 plugin upgrade, I have been working to deliver a suitable interface to use common api frameworks within the game sdk. 

---

2024-04-05 Fri: <br>
Week Summary<br>
-I was out on 4/4 using the time for tax preperation<br>
-I attended some discussions with the team over Partie partnership opportunity<br>
-March devops on-call duties concluded on Tuesday<br>
-assist the team in analyzing the cause of Shard0 Devnet and shard1 testnet and devnet failures<br>
-work on the project-g demo continues

---
2024-03-29 Fri: <br>
Week Summary<br>
-devops on call: Review log https://docs.google.com/document/d/18faRFgN16IC_qyAUGUdSn0ZWv3JgEiR5Afm1xul1H6U<br>
 -carried out standard protocol duties, code reviews, meetings, etc<br>
 -progress on project-g: fine tuning player movement controls, playing with some plasma effects<br> (settled on neon colors), camera interactions (player camera movement threshold, controller/mouse scrolling)<br>
 -Researching ways to put ai into crypto games. I am experimenting with components that will be useful for<br> in-game interactions, scripting, events, etc, using apis that are accessible within our framework<br>

---

2024-03-15 Fri: 
Week summary<br>
Focused on web3 gaming iniative, completing code port of web3 plugin originally built for godot 3.5 to godot 4.x. This can now be built with godot 4.2/4.3 source code on osx and linux (tested on Ubuntu 22) https://github.com/adsorptionenthalpy/godot-web3-plugin/tree/main-4.2. Currently building out a web3 game demo toward playable state to demonstrate the capabilities of framework. This is taking a little more time than initially estimated. 
Reviewed incoming bugfixes and updates coming into Harmony dev, and some other housekeeping for some fixes that have been going stale. 
 
---

2024-03-12 Tue: Reviewed PR #4642 that modifies the node to retrieve an address from BLS keys (Konstantin). Continued developing Chain Force demo concepts. Reached out to coinmonstore to arrange Harmony product listing. 

---

2024-03-11 Mon: Branch feature/clear-stale-staking-data fell several months behind dev, updated to prevent future merge conflicts

---

2024-03-06 Wed: Reviewed team pull requests

https://github.com/harmony-one/harmony/pull/4636

https://github.com/harmony-one/harmony/pull/4638

https://github.com/harmony-one/harmony/pull/4639

---

2024-02-23 Fri to 2024-03-02 Sat:
Out for Ethereum Denver Conference

---
2024-02-20 Tue: Review of big pull request dev->main https://github.com/harmony-one/harmony/pull/4633

2024-01-30 Tue: Reviewed snapshot fixes and merged PR# 4618 to dev https://github.com/harmony-one/harmony/pull/4618
The last few weeks I have been shifting focus from protocol development to exploring Harmony's other initiatives involving gaming, account abstraction and security. 

Project-G repository created on the 17th (currently private) https://github.com/harmony-one/Project-G tracks the early development efforts for some games being developed to showcase Harmony's technology stack.

---
 
2024-01-17 Wed: Review of decider changes in PR# 4610 https://github.com/harmony-one/harmony/pull/4610

---

2024-01-09 Tues: WIP PR on pruning stale delegation data has been updated reflecting changes into main->dev and fixing missing code/logic in engine_test.go. Notified Diego, this is in his queue now.
https://github.com/harmony-one/harmony/pull/4505
Review of PR# 4602 https://github.com/harmony-one/harmony/pull/4602

---

2024-01-1 Fri: Happy new year! Work on Harmony's Blockchain gaming initiatives have begun. I am currently updating and testing AA code changes from upstream before deployment

---

2023-12-21 Thu: 
Merge of main -> dev - Concluding my week on-site there was a lot of movement into the harmony/harmony-one main branch to carry out a security and api bug, and some other small fixes. This PR was opened to bring dev into sync and there were a few conflicts needing resolving. https://github.com/harmony-one/harmony/pull/4595 and https://github.com/harmony-one/harmony/pull/4600

Attended weekly developer sync

---

2023-12-15 Fri:  Attended whiteboard discussions on formal verification, smart contract security, coq, blockchain gaming. Had some collaboration with the protocol team on core issues.
Concluded the day with Harmony holiday dinner!

---

2023-12-14 Thu:
Full review of PR https://github.com/harmony-one/harmony/pull/4588 authored by max mustermann. This PR would undo some of the my logical changes to getTransactionReceipt, recently merged into dev.

---

2023-12-13 Wed:
Arrived on-site in Palo Alto. Throughout the week we brainstormed on potential protocol improvements and blockchain security.

---

2023-12-07 Thu:

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
