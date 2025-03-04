### UniswapX on Harmony

UniswapX is a permissionless, open-source protocol developed by Uniswap Labs for trading cryptocurrencies across automated market makers (AMMs) and other liquidity sources.

It enhances onchain trading by offering gas-free swaps, better pricing, and protection against maximal extractable value (MEV).

The protocol aggregates liquidity from various onchain and offchain sources, using an auction-based system to optimize trade execution.

[Official docs](https://docs.uniswap.org/contracts/uniswapx/overview)

[Github repository](https://github.com/Uniswap/UniswapX)

Core Components:
- **Signed Orders**: Swappers create offchain orders specifying trade intents (e.g., token amounts and limits), signed via Permit2 for secure token transfers.
- **Fillers**: Competitive agents who execute orders by sourcing liquidity, paying gas on behalf of swappers, and batching transactions for efficiency.
- **Order Reactors**: Smart contracts that validate, resolve, and settle orders, coordinating with fillers’ strategies for onchain execution.
- **Dutch Auction Mechanism**: Orders decay over time (e.g., via Exclusive Dutch Orders), incentivizing fillers to compete for the best execution prices.

### Deployment Steps

Deployment for the MVP can be divided by 3 steps:
1) Creating Dutch Order: [source code](https://github.com/ArtemKolodko/uniswapx-demo/blob/main/backend/src/index.ts)
2) Deploying [Dutch Order Reactor](https://github.com/Uniswap/UniswapX/blob/main/src/reactors/V2DutchOrderReactor.sol) contract
3) Creating a [Filler](https://docs.uniswap.org/contracts/uniswapx/guides/createfiller) and [integration](https://hackernoon.com/technical-overview-of-the-uniswapx-protocol-architecture-integration-methods-and-order-execution) with Uniswap V3 (swap.country)

#### Creating Dutch Order
```
const createDutchOrder = () => {
  const permit2Address = '0xC5f4c7C1C20532CdCB84dcf9A2B4FfB8F431246C';
  const reactorAddress = '0x6000da47483062a0d734ba3dc7576ce6a0b645c4';

  const orderInfo: OrderInfo = {
    reactor: reactorAddress,
    swapper: wallet.address,
    nonce: BigNumber.from(Date.now()),
    deadline: Math.floor(Date.now() / 1000) + 3600,
    additionalValidationContract: '0x0000000000000000000000000000000000000000',
    additionalValidationData: '0x',
  };

  const now = Math.floor(Date.now() / 1000);
  const decayStartTime = now + 60; // Starts in 1 minute
  const decayEndTime = now + 600; // Ends in 10 minutes

  const exclusiveFiller = '0xFILLER_ADDRESS'; // Replace with actual filler address
  const exclusivityOverrideBps = BigNumber.from(50); // 0.5% override

  const input = {
    token: '0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2', // WETH on Mainnet
    startAmount: BigNumber.from('10'),
    endAmount: BigNumber.from('1'),
  };

  // Output Token (e.g., USDC)
  const outputs = [
    {
      token: '0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48',
      startAmount: BigNumber.from('3100'),
      endAmount: BigNumber.from('300'),
      recipient: wallet.address,
    },
  ];

  const dutchOrderInfo: DutchOrderInfo = {
    ...orderInfo,
    decayStartTime,
    decayEndTime,
    exclusiveFiller,
    exclusivityOverrideBps,
    input,
    outputs
  }

  const dutchOrder = new DutchOrder(dutchOrderInfo, chainId, permit2Address)
  const orderBuilder = DutchOrderBuilder.fromOrder(dutchOrder)
  const order = orderBuilder.build();
  return order
}
```

#### Deploying Dutch Order reactor

Create2 deployer address: 0xA769Ee082Dd5ed0912f81f58C4Ee15b8C300a6aa

1. Deploy permit2 contract:
```
forge script --broadcast --rpc-url https://api.harmony.one  --private-key 0x12345 --create2-deployer 0xA769Ee082Dd5ed0912f81f58C4Ee15b8C300a6aa --verify script/DeployPermit2.s.sol:DeployPermit2 --legacy
```

Permit2 address: 0xC5f4c7C1C20532CdCB84dcf9A2B4FfB8F431246C

2. Change permit2 address and deploy Dutch order Reactor
```
forge script --broadcast --rpc-url https://a.api.s0.t.hmny.io  --private-key 0x12345 --create2-deployer 0xA769Ee082Dd5ed0912f81f58C4Ee15b8C300a6aa script/DeployDutchV2.s.sol:DeployDutchV2 --legacy
```

Test deployment in Arbitrum Sepolia:
```
forge script --broadcast --rpc-url https://sepolia-rollup.arbitrum.io/rpc  --private-key 0x12345 script/DeployDutchV2.s.sol:DeployDutchV2 --legacy -vvvvv
```

Transaction in Sepolia Explorer: https://sepolia.arbiscan.io/tx/0x444c1b432254aa02dae019d887d59146e52bbf49f8cc42a66ed9be0f0769ab66
Contract address: https://sepolia.arbiscan.io/address/0x744aA5638e503E73957f07087745684E0aFc2b9F
