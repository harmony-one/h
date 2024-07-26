2024-07-08 Mon: Today I researched and fixed the cause of the exploit. I also added a Foundry PoC which showed the exploit and verified that the bug is no longer present. Some tweaking of the repo was needed to make it work with Foundry.

2024-07-09 Tue: I continued with the work on Euler V1, running all tests to make sure the addressed bug did not break anything. I continued investigating the deploy scripts, checking which modules can be omitted, what configurations are needed, and is Chainlink a must-have dependency. I ran the development deploy script to a local node.

2024-07-10 Wed:
I deployed Euler V1 to the testnet and set up the Hardhat configuration. I forked all GitHub repos (Panoptic, Euler V1, Opyn Squeeth, WETH9, deploy-v3), made necessary config changes, and added Makefiles for Harmony testnet deployment.

2024-07-11 Thu:
I added Foundry scripts to Euler V1 for activating USDC and WETH markets. I redeployed Opyn Squeeth, deployed the Zen Bull Strategy and Zen Bull Netting contracts with new Euler dependencies, and created Makefiles and notes.md for the new deployments.

2024-07-12 Fri: I tested the Zen Bull Strategy and Zen Bull Netting contracts on the testnet.

2024-07-22 Mon: I tested Panoptic core contracts on the testnet. They failed due to dependencies on existing Uniswap pools, which required mocking them.

2024-07-23 Tue: I tested Panoptic core contracts on a forked mainnet. I started creating CLI scripts for interacting with the Panoptic contracts.

2024-07-24 Wed: I started testing Opyn Squeeth on a forked mainnet. I started creating CLI scripts for interacting with the core contracts.

2024-07-25 Thu: I created and tested a CLI script for opening a position in Opyn Squeeth. Additionally, I pushed work in progress repositories for [panoptic](https://github.com/0x73696d616f/panoptic-v1-core), [squeeth](https://github.com/0x73696d616f/squeeth-monorepo), [euler](https://github.com/0x73696d616f/euler-contracts) and helpers uniswap deployer [deploy-v3](https://github.com/0x73696d616f/deploy-v3), [canonical-weth](https://github.com/0x73696d616f/canonical-weth).

2024-07-26 Thu: I created and tested a CLI script for liquidating a position in Opyn Squeeth.