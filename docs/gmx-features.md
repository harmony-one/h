# GMX Features Notes
## Referrals
- Traders receive discounts and affiliates recieve rebates
- For V1, distrubuted as ETH on Arbitrum, AVAX on Avalanche every Wednesday
- For V2, applied/accumulated automatically (claimed in "Claimable Rebates")
- 3 Tiers depending on number of referred users
- Referral code stored on contract when user makes first trade
- [ReferralStorage.sol](https://github.com/gmx-io/gmx-contracts/blob/master/contracts/referrals/ReferralStorage.sol): Manage tiers, referrers, and referral codes
- [ReferralReader.sol](https://github.com/gmx-io/gmx-contracts/blob/master/contracts/referrals/ReferralReader.sol): Provide batch query of owners of mutliple referral codes
- [PositionRouter.sol](https://github.com/gmx-io/gmx-contracts/blob/master/contracts/core/PositionRouter.sol): If the user doesn't already have a referral code, _referralCode is set in createIncreasePosition()
- [scripts/referrals](https://github.com/gmx-io/gmx-contracts/tree/master/scripts/referrals)
  - [distributionData](https://github.com/gmx-io/gmx-contracts/blob/master/scripts/referrals/distributionData.js): Queries referral data from subgraph. Calculates total rebates, referral volumes, esGMX rewards. Saves processed data to JSON file.
  - [referralRewards](https://github.com/gmx-io/gmx-contracts/blob/master/scripts/referrals/referralRewards.js): Reads distribution data from JSON file, calculates and sends rewards
  - [bonusReferralRewards](https://github.com/gmx-io/gmx-contracts/blob/master/scripts/referrals/bonusReferralRewards.js): Uses distributionData to set bonus rewards
- scripts/core
  - [setReferralTier](https://github.com/gmx-io/gmx-contracts/blob/master/scripts/core/setReferralTier.js): Update referral tiers for specific accounts
  - [setReferralCodeOwner](https://github.com/gmx-io/gmx-contracts/blob/master/scripts/core/setReferralCodeOwner.js): Update ownership of code

## Dashboard

## Leaderboard

## Earn
