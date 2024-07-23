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

Result example: 
```
{
  PositionRouter: '0x7372f0e13d631cd7F970D97369dFB099916922C9',
  PositionManager: '0x53C44698e6c7A76101B15B8C04ce1b6aF93bb7d3',
  Vault: '0x78cD8463Ff91e3E7f2AC6fdd0d0d0e3124B50bCa',
  Router: '0x6b72AA81d45fE13a09a5f00C25E6B9FA18E98b88',
  VaultReader: '0x96aabeF07cF417b951c94a5c1492099c45334B79',
  Reader: '0xCe9417cCC1EC7cB8BD10ECC6ADf0c30F26D03fc5',
  GlpManager: '0xF3c3AC1D89360e2a0B18b3a062987f028F0728c5',
  RewardRouter: '0x13e8a04a9f76c144D4dC45Ebe3B3184CE8603Ae4',
  GlpRewardRouter: '0x13e8a04a9f76c144D4dC45Ebe3B3184CE8603Ae4',
  GovToken: '0x1347d869D8dF70bCe6b82d140b6761e0A12B92bb',
  NATIVE_TOKEN: '0xcF664087a5bB0237a0BAd6742852ec6c8d69A27a',
  GLP: '0x7C54F8d25F224DeE7A0FA7583f621E9AebE24DfE',
  GMX: '0x9D609c2c561e31dC0B9664F060590de7953a215A',
  ES_GMX: '0x7945a75839636E10F2833d3758A5fE0e52B3EEB6',
  BN_GMX: '0x6b71a8D43CE48B43BBfe7F9BF41A42FE0cc74F8b',
  USDG: '0xe6941777F5c64272Dd17469c69C774d94B68d27F',
  StakedGmxTracker: '0xE5097230e7e33F205Ba2dF6a5155c605C3F0Fc68',
  BonusGmxTracker: '0xFF606BdE1895994C1E7a6eaa21776250F4439318',
  FeeGmxTracker: '0xB4Ba30A130E66A95D7C90Be58F172B854a46F7a4',
  StakedGlpTracker: '0x69F9B87b7de99A2ec6D5BCA690357957fE8752CC',
  FeeGlpTracker: '0x5Ba5371d1fC76502eea14391bF4200A5fC668eE9',
  OrderBook: '0xDEDF0bB00a482810b55065582cE3066D0E3B4E11',
  OrderBookReader: '0x77976FF62dd78242Cb0386cd4c88406f146c8b09',
  TokenManager: '0x61c5D6645f4EFa7165760Ef779C4AA498e1D7379',
  FastPriceEvents: '0xEd1a6A1557fef646f5beB2206cD10412a69C1345',
  FastPriceFeed: '0xC5A123C9F98cb21859F49Df6AD3f57E428607C8E',
  VaultPriceFeed: '0x447BD0BB67F40a4ceeF14BC0945e440d5858F443',
  VaultErrorController: '0x9d4125F148faF341a41D637B152942E4bBDE1543',
  VaultUtils: '0xD4A07901fe938a2cEC88d99a01D9c30Bc2bF9936',
  Timelock: '0xda4f51e95A003cC430C11bE97A286A2428eafC23',
  PriceFeedTimelock: '0x8826C1C9ff560656C05Cf58dFF685020B5401E34',
  ShortsTrackerTimelock: '0xb295A7204f5742189E08Cdf59D158c8bcE21B67c'
}
```

***Next steps:***

1) Copy - paste result JSON to interface contracts config [here](https://github.com/harmony-one/gmx-interface/blob/master/src/config/contracts.ts#L15) until the Synthetics zone
2) Copy - paste result JSON to keeper service contracts config [here](https://github.com/harmony-one/gmx-price-keeper/blob/main/src/contracts.config.ts)
