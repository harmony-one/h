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

***How to deploy:***

1) Clone and build repo
```
git clone git@github.com:harmony-one/h-gmx-contracts.git
npm install -g npx
npx hardhat compile
```

2) Set deploy ENV to env.json (MAINNET_DEPLOY_KEY and DEPLOYER_PK may be the same)
```
{
    "MAINNET_DEPLOY_KEY": "",
    "DEPLOYER_PK": "",
    "MAINNET_URL": "https://api.harmony.one"
}
```

3) Run deploy script
```
npx hardhat run ./scripts/harmony/deployAll.js --network mainnet
```

***Next steps:***
Then you need to copy paste all deployed addresses to json config to use it with frontend app and keeper service

