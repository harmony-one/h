Panoptic SwapUSDC test

1) clone repository:
```
git clone https://github.com/polymorpher/panoptic-v1-core.git
cd panoptic-v1-core
```

2) create `.env.swap-usdc` in the root directory

3) add environmental variables to this file:
```
DEPLOYER_PRIVATE_KEY=<your_private_key>
USDC_ADDRESS=0xBC594CABd205bD993e7FfA6F3e9ceA75c1110da5
WETH_ADDRESS=0xcF664087a5bB0237a0BAd6742852ec6c8d69A27a
POOL_ADDRESS=0x6e543b707693492a2d14d729ac10a9d03b4c9383
TARGET=0x98f0c3D42b8DaFB1f73d8F105344C6a4434a0109
ETH_AMOUNT=1
```

4) create a new file: swap-usdc.sh
it's a modified version of the original swap-usdc-local.sh script to use on Harmony mainnet:
```
#!/bin/zsh

export $(grep -v '^#' .env.swap-usdc | xargs)

forge script deploy/SwapUSDC.s.sol --rpc-url https://api.harmony.one \
  --tc SwapUSDC \
  --chain-id 1666600000 \
  --broadcast \
  --private-key ${DEPLOYER_PRIVATE_KEY} \
  -vvvv \
  --legacy
```
5) run script:

```./swap-usdc.sh```
