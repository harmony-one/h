GMX v1 contracts deploy
==============

Original gmx contracts repo: https://github.com/gmx-io/gmx-contracts

Docs at https://gmxio.gitbook.io/gmx/contracts

**Harmony fork: https://github.com/harmony-one/h-gmx-contracts**

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
Then you need to copy paste all deployed addresses to json config to use it with frontend app

Example: 
```
{
  "Vault": "0x70b08Bb9911420457eaaeaE768c5Bc6bE5Bb0360",
  "USDG": "0xF3815a049bEcF828B5001211e30DC5186CF08af8",
  "Reader": "0x32B0634B40B6Eb0F0613B493425855e0cFece7b8",
  "RewardReader": "0xBC7E09D3E88Ec310C6F7ddb7E725c30619628DA3",
  "VaultReader": "0x32B0634B40B6Eb0F0613B493425855e0cFece7b8",
  "Router": "0x253aB47bE6E7cFb0C83F53750DA8Bf0fa28624F6",
  "VaultPriceFeed": "0x0bD1202Cb43d85E85aF51e4FF47f830CD2c09aeF",
  "GLP": "0x4Ac24573d684CC7e675a3C3917f522b875148bC0",
  "ShortsTracker": "0x111BB36Dc1C2122d5071B8D0c6FbAda77AC44978",
  "GlpManager": "0x57d5a0d3c997635632aec378516A0ca568da9454",
  "VaultErrorController": "0xD3b30E0001AeA297D37E45413Aa0C76A238420c4",
  "VaultUtils": "0xA3B711Ea7309dcF990cD83356b842c6B4E1C4252",
  "bnGMX": "0x85F4700553e64d67CacA2AFf02D6B973C775EB2D",
  "esGMX": "0x96d749565091cDCD724930C65Bb3ACEbA847860D",
  "GMX": "0xa43bf71007A0AD33b790E48cB4eE9784A1FC2cad",
  "sGMX": "0x7c0DC0091e239deDe3897CAdB7B0318240A29274",
  "sGMXDistributor": "0xCbE578973Ac14E869Ff0043C216487c8Dc9fac7c",
  "sbfGMX": "0x803Ace9aD2960b4D41f6a2C9c5fd5Ed7CD28319b",
  "sbfGMXDistributor": "0x1A9873264fA3478901B7f8eB0Ce2Da3f3551a725",
  "RewardRouter": "0x1A9873264fA3478901B7f8eB0Ce2Da3f3551a725",
  "VesterGMX": "0xc85F06dbfb7155a8439F1F3D6A6C51090F595184",
  "VestedGLP": "0x51B0411d5F97f6062121A895E1C0bE9c3748B449"
}
```

***Deploy logs example:***
```
No need to generate any newer typings.
Deploying Reader:Reader 0x32B0634B40B6Eb0F0613B493425855e0cFece7b8 
... Completed!
Sending Reader.setConfig...
... Sent! 0x5647700d48eaed18f97ffbd176bec924b29eaef22c5a129276085439e6280611
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Deploying RewardReader:RewardReader 0xBC7E09D3E88Ec310C6F7ddb7E725c30619628DA3 
... Completed!
Sleeping for 1 seconds
END
Deploying VaultReader:VaultReader 0xCe0cA9d05BAD33F3978d77D44996FCD29a6acE97 
... Completed!
Sleeping for 1 seconds
END
Deploying Vault 0x70b08Bb9911420457eaaeaE768c5Bc6bE5Bb0360 
... Completed!
Sleeping for 1 seconds
END
Deploying USDG 0x02E0FF03E50f4CaD606d3Ed52e63448F05cDCeB4 "0x70b08Bb9911420457eaaeaE768c5Bc6bE5Bb0360"
... Completed!
Sleeping for 1 seconds
END
Deploying Router 0x253aB47bE6E7cFb0C83F53750DA8Bf0fa28624F6 "0x70b08Bb9911420457eaaeaE768c5Bc6bE5Bb0360" "0x02E0FF03E50f4CaD606d3Ed52e63448F05cDCeB4" "0xcf664087a5bb0237a0bad6742852ec6c8d69a27a"
... Completed!
Sleeping for 1 seconds
END
Deploying VaultPriceFeed 0xe2f7d947dF9770a3D41EC6e508bDF3E520ab7c70 
... Completed!
Sleeping for 1 seconds
END
Sending vaultPriceFeed.setMaxStrictPriceDeviation...
... Sent! 0x8f04765ede09ef3d3aeacd239512f8290fc8f1997316f04c8eb9eaa2356479f0
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending vaultPriceFeed.setPriceSampleSpace...
... Sent! 0x295dcd6bee4a9cdcfe63de92aded0a10b51717c6338ac3dc7b3b5762bc9f60c4
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending vaultPriceFeed.setIsAmmEnabled...
... Sent! 0x468b1b8076b1e5866b961682d8c27c64f0d2798fb6158c624dfa726d3001331d
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Deploying GLP 0x4Ac24573d684CC7e675a3C3917f522b875148bC0 
... Completed!
Sleeping for 1 seconds
END
Sending glp.setInPrivateTransferMode...
... Sent! 0xd62e87fbaf9da706a12c0aadc0bad19869a34ea2e636e0fde2ed1d99ea86a790
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Deploying ShortsTracker:ShortsTracker 0xab078ed601a116AA8bdF847cA08D91E4B8d74251 "0x70b08Bb9911420457eaaeaE768c5Bc6bE5Bb0360"
... Completed!
Sending shortsTracker.setGov...
... Sent! 0xccfbb36c3fa598a60b24560c0e144ea66bebab21a4ff068eca5b279f7eaa7d1c
Sleeping for 2 seconds
END
Deploying GlpManager 0x57d5a0d3c997635632aec378516A0ca568da9454 "0x70b08Bb9911420457eaaeaE768c5Bc6bE5Bb0360" "0x02E0FF03E50f4CaD606d3Ed52e63448F05cDCeB4" "0x4Ac24573d684CC7e675a3C3917f522b875148bC0" "0xab078ed601a116AA8bdF847cA08D91E4B8d74251" "900"
... Completed!
Sleeping for 1 seconds
END
Sending glpManager.setInPrivateMode...
... Sent! 0x909b1b212c9bf6989b09703a49055ba46cbf5f0a822d9a4f128c8db666534811
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending glp.setMinter...
... Sent! 0x798b2b07a903652339d685ed10dc847c2ca3afd6157f4476c0dcc9ff771577a1
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending usdg.addVault(glpManager)...
... Sent! 0x23de738e78fdebe8511fb5f15d8a636cc9228e824213d3b9a94ad15b2b3d0968
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending vault.initialize...
... Sent! 0x39f23ff8bd37d4947bc4816f54127a02cba361312170a7ba991ce43be6c09788
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending vault.setFundingRate...
... Sent! 0xb3853f9f322f16eabb133a578df06c6668956e65460f8f23d888b29818d43781
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending vault.setInManagerMode...
... Sent! 0x3311e123bdafbb4bcbe5366b6ca3a4eed06821e8d00c107849869794d793f0a9
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending vault.setManager...
... Sent! 0x63d57b87181f82d30166220f7890c310db03569d9c4d162d850b4de9e6cee271
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending vault.setFees...
... Sent! 0x95cdaa4c9ac9cc1e61ff30d568ecf1c68dfba81ad0f4d8f9baf7ab0f9d356621
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Deploying VaultErrorController 0xE27DD0d20465101b84f29f1225d1B109Fc17335A 
... Completed!
Sleeping for 1 seconds
END
Sending vault.setErrorController...
... Sent! 0x3b6cafc8d0896f2e59e503e6c9506d85f69ee305090282b7ce2c522235659c1b
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending vaultErrorController.setErrors...
... Sent! 0x66056d377ab596ac76a6731f60c78843591e556b9bef4e412831ce6dd8317815
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Deploying VaultUtils 0x4A9711FDB1905d5191F092697Ce7875387D2e8d3 "0x70b08Bb9911420457eaaeaE768c5Bc6bE5Bb0360"
... Completed!
Sleeping for 1 seconds
END
Sending vault.setVaultUtils...
... Sent! 0x307b48601c4853876ffbb0f12930412ce3095a56bb51a56c5352cf35c8a8967b
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Deploying MintableBaseToken 0x76Ffc81599c5438A163123dCd56B130766e0aE30 "Bonus GMX" "bnGMX" "0"
... Completed!
Sleeping for 1 seconds
END
Deploying EsGMX 0x9E3325AB80fe07a81bfD8bF285BCDC81E3e65C07 
... Completed!
Sleeping for 1 seconds
END
Deploying GMX 0x740940D7A3CB94A32ac8dDc92484F078fa04F5c3 
... Completed!
Sleeping for 1 seconds
END
Deploying RewardTracker 0x5e82CD4c23422083F2CFd0652DF856E94Ac8E685 "Staked GMX" "sGMX"
... Completed!
Sleeping for 1 seconds
END
Deploying RewardDistributor 0xbF702B56F6880d87f80bce0DEF79154B7049568a "0x9E3325AB80fe07a81bfD8bF285BCDC81E3e65C07" "0x5e82CD4c23422083F2CFd0652DF856E94Ac8E685"
... Completed!
Sleeping for 1 seconds
END
Sending stakedGmxTracker.initialize...
... Sent! 0xbc219761fa72cbf34fb5a611459d4c1d7bad33313ae6c05233b974cfcb654c85
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending stakedGmxDistributor.updateLastDistributionTime...
... Sent! 0x3a77dff59603084d3631dfc4fb7905532fbfeece2840c3f1cc96b5d2855f8118
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Deploying RewardTracker 0x327aD9788a8763AE56a723fCB6eEBD4Da3a275bA "Staked + Bonus GMX" "sbGMX"
... Completed!
Deploying BonusDistributor 0xfF04B056C58208a485aE69785119f19bd5fa8b45 "0x76Ffc81599c5438A163123dCd56B130766e0aE30" "0x327aD9788a8763AE56a723fCB6eEBD4Da3a275bA"
... Completed!
Sending bonusGmxTracker.initialize...
... Sent! 0xc38ccce063cfb8123e1c4a38718fa79aa877578a16c60de4731bdeca528fab68
Sleeping for 2 seconds
END
Sending bonusGmxDistributor.updateLastDistributionTime...
... Sent! 0xbdb88dc72187c4a6ad7f8ea37aa1b718cb8e30b00ad21cec2449410c8719f3c1
Sleeping for 2 seconds
END
Deploying RewardTracker 0xd345222B956Af3c4b6eC136de6754Dfb062ca4A1 "Staked + Bonus + Fee GMX" "sbfGMX"
... Completed!
Sleeping for 1 seconds
END
Deploying RewardDistributor 0x1EB40A9D59c0b080dc775675c9F2f3ddF1E6Cd1F "0xC360D44d9021E0d9D2781a6c5c269D209F43dAa7" "0xd345222B956Af3c4b6eC136de6754Dfb062ca4A1"
... Completed!
Sleeping for 1 seconds
END
Sending feeGmxTracker.initialize...
... Sent! 0x5b6536baff951e91db4c42dac4375ff525e5144c08895a4a9ce1c3481043a4b4
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending feeGmxDistributor.updateLastDistributionTime...
... Sent! 0x2f8293ee2de7667fbef9ca28de7e5e7c133c723781657e6c74d2ad723f2d7b5b
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending stakedGmxTracker.setInPrivateTransferMode...
... Sent! 0xc09faede2140bcb2021e6732e3f354c4767010d505fafa80e82a1fc7047d6e63
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending stakedGmxTracker.setInPrivateStakingMode...
... Sent! 0x4d29b22918ee2c192834dedc3b798be21a02d4094bc86b721c281741f402259a
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending bonusGmxTracker.setInPrivateTransferMode...
... Sent! 0x8437e15cc660fef352766538e8407ec290c724b1cf106ab9c1d2496056462eb4
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending bonusGmxTracker.setInPrivateStakingMode...
... Sent! 0xf378a904ea79562b9a98cb9e1230774bbc801a4e222325c1c521e11b0266a7db
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending bonusGmxTracker.setInPrivateClaimingMode...
... Sent! 0xcb77419fce922528af7d01132d230946ac9243ef751773185e0fcd72bcf74d83
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending feeGmxTracker.setInPrivateTransferMode...
... Sent! 0x6583c12130c67d57dd6bf0ff23b9a0bf9724e65d13b3ddfcdf9d4ee740acc718
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending feeGmxTracker.setInPrivateStakingMode...
... Sent! 0x22cee54743252f6e42de62174e61001b194eec5df30eeb4b8e2be5c5b1051545
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Deploying Vester 0xc219BBEed38A78b12A33fd4DD5e2B27516D9c16b "Vested GMX" "vGMX" "31536000" "0x9E3325AB80fe07a81bfD8bF285BCDC81E3e65C07" "0xd345222B956Af3c4b6eC136de6754Dfb062ca4A1" "0x740940D7A3CB94A32ac8dDc92484F078fa04F5c3" "0x5e82CD4c23422083F2CFd0652DF856E94Ac8E685"
... Completed!
Deploying Vester 0x40Cc11d1Df5F9578248C0E9386D22E22FCCaA9Ec "Vested GLP" "vGLP" "31536000" "0x9E3325AB80fe07a81bfD8bF285BCDC81E3e65C07" "0x0000000000000000000000000000000000000000" "0x740940D7A3CB94A32ac8dDc92484F078fa04F5c3" "0x0000000000000000000000000000000000000000"
... Completed!
Deploying RewardRouterV2 0xF33F30625a6E15b7F57FEfFe7d92cF93CD5723df 
... Completed!
Sleeping for 1 seconds
END
Sending rewardRouter.initialize...
... Sent! 0xcbd2fd531f5a075e4ed4b2648113c00bd8e0df23a3b004922f4c1852f6873c96
Sleeping for 2 seconds
END
Sending stakedGmxTracker.setHandler(rewardRouter)...
... Sent! 0x949ff7d55e03f4b2a8f2536f27a984e7c1b2455d6a43f3fc67834f68d8766975
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending stakedGmxTracker.setHandler(bonusGmxTracker)...
... Sent! 0x58628db56e302d1556248234aae2742a2de4329e8931a9fc947b7a21185c263d
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending bonusGmxTracker.setHandler(rewardRouter)...
... Sent! 0x4a6d6a9292f9a98596de862266566e006c2a85dce51d311044050e4530a94695
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending bonusGmxTracker.setHandler(feeGmxTracker)...
... Sent! 0x2bfeaca034d71f6a1250db0e02a595d95cd3d437ff3e93aa40d731d4619becef
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending bonusGmxDistributor.setBonusMultiplier...
... Sent! 0x7f27f169c2ce500a677b2e85fe825de7bea66327fcb2087f23b8711273132d62
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending feeGmxTracker.setHandler(rewardRouter)...
... Sent! 0x26638fdf04178b5cd44338d63e0ad2b9c2d7031d8e94cc0253ce46fda554d2a4
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending esGmx.setHandler(stakedGmxTracker)...
... Sent! 0xf5f001c322e6e3fdd81d6f8f287e783a1b4b7caaec194637b40692e327edfed8
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending bnGmx.setHandler(feeGmxTracker...
... Sent! 0xc03749c9143adedc33edca948530ef06885c02d125a898527f10a05d4342fb55
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending bnGmx.setMinter(rewardRouter...
... Sent! 0xf00545a89857b7275010893e09e46a1412215827fd0757d4a8acb221eaa1e51d
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending esGmx.setMinter(wallet)...
... Sent! 0xe66ee92777f7dcd44e9462f8b4b64da47cb3aa2ba387e32e4eda4b5079dd72d6
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending esGmx.mint(stakedGmxDistributor...
... Sent! 0x15d2467f60c78543d8febe1bb19b565e741bb23dbd4dde0351d95f417c1fc071
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending stakedGmxDistributor.setTokensPerInterval...
... Sent! 0xe98461829c2128aa929a42a984bb91a1986b2201ec08ca0d203acf0427a10390
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending bnGmx.setMinter...
... Sent! 0x4e3a36dfb36c5d31b54711dec700da7989fb4471a5119b7dfbb9553cbd3b7e8e
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
Sending bnGmx.mint(bonusGmxDistributor)...
... Sent! 0x78f410ac2b4ee93eb5b4d98a186a81de5760e0b972fba30788576bfa5f74bf9a
Sleeping for 2 seconds
END
Sleeping for 1 seconds
END
```
