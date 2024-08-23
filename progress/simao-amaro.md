2024-08-22 Thu: I added a profitable trades script for Vertex repo, including a forked test showing the profitable trades. I am currently debugging a CALL_EXCEPTION error in the script. 

2024-08-21 Wed: I [added](https://github.com/harmony-one/synthetix/pull/1) a profitable trades script for Synthetix repo, including a forked test showing the profitable trades.

2024-08-20 Tue: I could not figure out why transactions stay pending on Foundry. I started working on the profitable trades script for the synthetix codebase.

2024-08-19 Mon: I [fixed](https://github.com/0x73696d616f/squeeth-monorepo/commit/69256a6f8c302f544e7ee0c2424685ba634b04af) the profitable trades script by using the `msg.sender` to provide liquidity. I continued debugging why transactions are showing as pending when initiated from Foundry.

---

2024-08-16 Fri: I [fixed](https://github.com/0x73696d616f/squeeth-monorepo/commit/329c9ebc127edcc35de33a49371144dcf7adc96b) the withdraw-lp script by explicitly specifiying `msg.sender` to all scripts. I continued debugging why transactions are showing as pending when initiated from Foundry.

2024-08-15 Thu: I added deposit and withdraw CLI (Command Line Interface) [scripts](https://github.com/0x73696d616f/squeeth-monorepo/commit/65b92ceb5eab89636fe577218c279d7a5e32b15a) for the Zen Bull Vault strategy.

2024-08-14 Wed: I added withdraw and burn LP (Liquidity Provision) CLI (Command Line Interface) [script](https://github.com/0x73696d616f/squeeth-monorepo/commit/9e5c304636d17d3c9e284df6a419628fcae4762f).

2024-08-13 Tue: I added a profitable trades Command Line Interface (CLI) script. I added a forked test showing the profitable trades. [Link](https://github.com/0x73696d616f/squeeth-monorepo/commit/4fe8aaefd311d1daf1b97feb97e07ee7fe577bb9).

2024-08-12 Mon: I added Crab StrategyV2 deposit and withdraw Command Line Interface (CLI) scripts. I [resolved](https://github.com/0x73696d616f/squeeth-monorepo/commit/ac6e577c0485ca80966b7db9e6747206097d1214) the Uniswap Quoter issue.

---

2024-08-09 Fri: I added and tested Close Long, Close Short Command Line Interface (CLI) [scripts](https://github.com/0x73696d616f/squeeth-monorepo/commit/a7bdcc5a82720bb156c2546329c8b2b9450b05cf). I investigated a present issue with the Uniswap Quoter.

2024-08-08 Thu: I added and tested Mint and Short, Mint and Liquidity Provision and Open Long Command Line Interface (CLI) scripts [1](https://github.com/0x73696d616f/squeeth-monorepo/commit/fa1a72a7c7a8c769338d71142a50a950a21c5b08), [2](https://github.com/0x73696d616f/squeeth-monorepo/commit/70f04330b8f9c7bb59159a346525b058cf36b040) and [3](https://github.com/0x73696d616f/squeeth-monorepo/commit/2b3f6297739cb414bbd3aadf55cd441235a2032b).

2024-08-07 Wed: I resolved the Uniswap Swap Router issue by deploying a new contract [1](https://github.com/0x73696d616f/squeeth-monorepo/commit/00ace5892eb765f81492ef27a24f329283667e37), [2](https://github.com/0x73696d616f/squeeth-monorepo/commit/0288a5703295964321ccf66982e9e21e28b037ef) and [3](https://github.com/0x73696d616f/squeeth-monorepo/commit/fe389753340d0e5a59f350821b81d71b1baed437). I enhanced the guide.md and scripts, replacing parameters with more descriptive ones and adding NatSpec for clarity.

2024-08-06 Tue: I continued developing the automated tests. I focused on resolving a persistent [issue](https://github.com/0x73696d616f/squeeth-monorepo/commit/28b5b88363f62d0096dc715bfe32f3d5f153ce90) with the Uniswap Swap Router.

2024-08-05 Mon: I [worked](https://github.com/harmony-one/squeeth-monorepo/commit/65b92ceb5eab89636fe577218c279d7a5e32b15a) on automated tests and scripts for profitable long trades.

---

2024-08-02 Fri: I worked on doing a profitable liquidation (Opyn Squeeth). The [Euler](https://github.com/harmony-one/euler-contracts) and [Opyn](https://github.com/harmony-one/squeeth-monorepo) repositories were moved from my profile to the Harmony Organization.

2024-08-01 Thu: I continued enhancing [opyn-squeeth-trading.md](https://github.com/harmony-one/h/blob/main/docs/opyn-squeeth-trading.md) (previously [guide.md](https://github.com/0x73696d616f/squeeth-monorepo/blob/main/guide.md)) for executing profitable trades on Opyn Squeeth. I worked on manipulating the oracle price to test the trading strategies.

2024-07-31 Wed: I started writing [guide.md](https://github.com/0x73696d616f/squeeth-monorepo/blob/main/guide.md) for executing profitable trades on Opyn Squeeth.

2024-07-30 Tue: I deployed and tested Opyn Squeeth core contracts and strategies to mainnet. I improved the folder structure, [Core](https://github.com/0x73696d616f/squeeth-monorepo/blob/main/packages/hardhat/Makefile), [Zen-Bull-Vault](https://github.com/0x73696d616f/squeeth-monorepo/blob/main/packages/zen-bull-vault/Makefile) and [Zen-Bull-Netting](https://github.com/0x73696d616f/squeeth-monorepo/blob/main/packages/zen-bull-netting/Makefile) Makefiles, deployment scripts, and [notes](https://github.com/0x73696d616f/squeeth-monorepo/blob/main/notes.md).

2024-07-29 Mon: I created and tested withdraw, deposit, and burn command line interface (CLI) [scripts](https://github.com/0x73696d616f/squeeth-monorepo/blob/main/packages/cli/Makefile) for Opyn Squeeth. I cleaned up the Opyn Squeeth repository and Euler V1 [repository](https://github.com/0x73696d616f/euler-contracts/commit/98ae2ae4346f94777ea7cab9a790d5db4516fc5a).

---

2024-07-26 Fri: I created and tested a command line interface (CLI) script for liquidating a position in Opyn Squeeth.

2024-07-25 Thu: I created and tested a command line interface (CLI) script for opening a position in Opyn Squeeth. Additionally, I pushed work in progress repositories for [panoptic](https://github.com/0x73696d616f/panoptic-v1-core), [squeeth](https://github.com/0x73696d616f/squeeth-monorepo), [euler](https://github.com/0x73696d616f/euler-contracts) and helpers uniswap deployer [deploy-v3](https://github.com/0x73696d616f/deploy-v3), [canonical-weth](https://github.com/0x73696d616f/canonical-weth).

2024-07-24 Wed: I started testing Opyn Squeeth on a forked mainnet. I started creating command line interface (CLI) scripts for interacting with the core contracts.

2024-07-23 Tue: I tested Panoptic core contracts on a forked mainnet. I started creating command line interface (CLI) scripts for interacting with the Panoptic contracts.

2024-07-22 Mon: I tested Panoptic core contracts on the testnet. They failed due to dependencies on existing Uniswap pools, which required mocking them.

---

2024-07-12 Fri: I tested the Zen Bull Strategy and Zen Bull Netting contracts on the testnet.

2024-07-11 Thu:
I added Foundry scripts to Euler V1 for activating USDC and WETH markets. I redeployed Opyn Squeeth, deployed the Zen Bull Strategy and Zen Bull Netting contracts with new Euler dependencies, and created Makefiles and notes.md for the new deployments.

2024-07-10 Wed:
I deployed Euler V1 to the testnet and set up the Hardhat configuration. I forked all GitHub repositories (Panoptic, Euler V1, Opyn Squeeth, WETH9, deploy-v3), made necessary config changes, and added Makefiles for Harmony testnet deployment.

2024-07-09 Tue: I continued with the work on Euler V1, running all tests to make sure the addressed bug did not break anything. I continued investigating the deploy scripts, checking which modules can be omitted, what configurations are needed, and is Chainlink a must-have dependency. I ran the development deploy script to a local node.

2024-07-08 Mon: Today I researched and fixed the cause of the exploit. I also added a Foundry proof of concept which showed the exploit and verified that the bug is no longer present. Some tweaking of the repository was needed to make it work with Foundry.
