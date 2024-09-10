How to add new token to GMX

1) Add new token address to contracts - Vault, VaultPriceFeed, FastPriceFeed - change and call this script:
https://github.com/harmony-one/h-gmx-contracts/blob/test_price_feeds/scripts/harmony/add-new-token.js

2) Add new token config to interface
https://github.com/harmony-one/gmx-interface/blob/master/src/config/tokens.ts#L8

3) Add new token config to price keeper
https://github.com/harmony-one/gmx-price-keeper/blob/main/src/configs/tokens.ts

4) Add new token config to stats service (for charts support)
https://github.com/harmony-one/gmx-stats/blob/harmony/src/addresses.js#L30
