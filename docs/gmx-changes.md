GMX v1 changes
==============

Original gmx contracts repo: https://github.com/gmx-io/gmx-contracts

Docs at https://gmxio.gitbook.io/gmx/contracts

**Harmony fork: https://github.com/harmony-one/h-gmx-contracts**

**All changes PR: https://github.com/harmony-one/h-gmx-contracts/pull/1/files**

***Changes:***

We did not change the original contracts - we just added a deployAll script for deploying and configuring contracts.
Also corrected several errors in the deployment scripts. 

Details:
1) Commented unused variables in hardhat.config [commit](https://github.com/harmony-one/h-gmx-contracts/commit/76c80848f6967cf2eff0f1567fff3446f4c5d7d9)
2) Fixed getContractFactory options issue [commit](https://github.com/harmony-one/h-gmx-contracts/commit/a71a92a291f484199639199a15936d254c4265b3)
3) Rename GLP to GXP [commit](https://github.com/harmony-one/h-gmx-contracts/commit/c5e3f2075bda68576b8e19c352ff7c56a236fbc3)
4) **Added deployAll script and configs** [commit](https://github.com/harmony-one/h-gmx-contracts/commit/3edccd0ffeedf8b44e471b7bdacb97d73bc19a33) - In fact, this is a major update that requires careful checking, because when deploying and setting up contracts, many parameters and access settings are used

Important files:
1) tokens.js - here is a list of tokens connected to gmx Vault
2) config.js - here is a config with addresses that will have access to contact management
3) deployAll.js - deployment script and settings

***How to deploy:***

https://github.com/harmony-one/h/blob/main/docs/gmx-v1-deploy.md

Gmx Price Keeper
==============

Also, to update prices and execute positions, we have developed a separate Price Keeper Service - which downloads prices from various open APIs and saves them in the secondPriceFeed contract.

Repo: https://github.com/harmony-one/gmx-price-keeper

API: https://gmx-keeper.fly.dev/api

