# **Add Bridge support for ERC20**

## **What you need to know before deploying**

1. **Have metamask account on the target chain with a sufficient number of native tokens for deployment**
2. Read how to deploy contracts via Remix here https://docs.linea.build/build-on-linea/quickstart/deploy-smart-contract/remix
3. Read how to verify contracts in explorer
4. Add target chain configs to backend and frontend [**Add Bridge support for new chain**](https://www.notion.so/Add-Bridge-support-for-new-chain-5748fc212a6d4909b64bf2d26802f2e6?pvs=21) 
5. Prepare target chain and token links:
    1. Target chain explorer: for example linea https://lineascan.build/
    2. Target Original ERC20 token address: for example (USDC): https://lineascan.build/token/0x176211869ca2b568f2a7d4ee941e073a821ee1ff

## Deploy Steps:

1. **Deploy HRC20 token wrapper to Harmony**
    1. Generate sources here https://wizard.openzeppelin.com/ (Mint, Burn, Pause, Roles) (name: chain prefix + Original name)
    2. Go to [https://remix.ethereum.org](https://remix.ethereum.org/), create new file and paste sources
    3. Add custom decimals if needed 
    
    ```solidity
    function decimals() public pure override returns (uint8) {
    		return 6;
    }
    ```
    
    1. Build without optimisation with latest solidity version
    2. Deploy to Harmony
2. **Deploy HRC20Proxy contract**
    1. Get ERC20Proxy flattened sources from here https://github.com/harmony-one/solidity-examples/blob/78c650cfb83325dc1681de145c203a47b848428c/flattened-contracts/proxyERC20WithMint.sol
    2. Go to [https://remix.ethereum.org](https://remix.ethereum.org/), create new file and paste sources
    3. Build without optimisation with latest solidity version (also check evm version for target chain)
    4. Deploy to Harmony Network
        1. ProxyToken address: token address from 1 step
        2. lzEndpoint: address from here https://layerzero.gitbook.io/docs/technical-reference/mainnet/supported-chain-ids
3. **Deploy ERC20Proxy contract**
    1. Get ERC20Proxy flattened sources from here https://github.com/harmony-one/solidity-examples/blob/78c650cfb83325dc1681de145c203a47b848428c/flattened-contracts/proxyERC20.sol
    2. Go to [https://remix.ethereum.org](https://remix.ethereum.org/), create new file and paste sources
    3. Build without optimisation with latest solidity version (also check evm version for target chain)
    4. Deploy to External Network (Linea)
        1. ProxyToken address: original token address
        2. lzEndpoint: address from here https://layerzero.gitbook.io/docs/technical-reference/mainnet/supported-chain-ids

## Contracts configuring:

You can read more about Proxy configuring here: 

[](https://github.com/harmony-one/solidity-examples/tree/main/contracts/token/oft/extension)

1. Set Mint Role for ProxyHRC20 contract from **HRC20 token**
2. Set Trusted remote (**setTrustedRemoteAddress**) for Harmony ProxyHRC20
3. Set Trusted remote (**setTrustedRemoteAddress**) for External ProxyERC20

## Update backend & frontend configurations:

1. Create Token Configuration
    
    ```jsx
    {
        hrc20Address: '0x9c5C877DB2A5a37733Fe1a0bdcae8411Cdc8c5B3',
        erc20Address: '0x176211869ca2b568f2a7d4ee941e073a821ee1ff',
        proxyERC20: '0x8a0167fC1Ef2E9492a1Eb978A9dA9137Ba25BB1B',
        proxyHRC20: '0xbA21f99d1067B8aE09f4f162e0528cB3FDb4FeD2',
        name: 'USD Coin (Linea)',
        symbol: 'USDC',
        decimals: '6',
        totalLocked: '0',
        totalSupply: '0',
        totalLockedNormal: '0',
        totalLockedUSD: '0',
        token: TOKEN.ERC20,
        type: TOKEN.ERC20,
        network: NETWORK_TYPE.LINEA,
        image: '/usdc.svg',
        adapterParams: '0x',
      },
    ```
    
2. Add config to Frontend 

https://github.com/harmony-one/layerzero-bridge.frontend/commit/abedb14b9e73ae9d124ca04e66eda06b8fa4cdb3

1. Add config to Backend 

https://github.com/harmony-one/layerzero-bridge.appengine/commit/04ca61f993411644d8e9d69e73dac15bba0bbae6

1. Redeploy all services

## **Verify all contracts:**

1. Verify HRC20 Wrapper (from step 1.1) on Harmony side
2. Verify ProxyHrc20 (from step 1.2) on Harmony side
3. Verify ProxyErc20 (from step 1.3) on external chain side

## Transfer ownership of contracts to Harmony Multisig**:**

1. Change roles for HRC20 Wrapper (from step 1.1) on Harmony side
2. Use method **transferOwnership for Proxy contracts**
