# Eliza Web3 Plugin Ecosystem

## Plugin Architecture

Each plugin implements independent functionality, with no shared base implementation.

## Plugin Categories

### 1. Chain-Specific Operations

**Core features:** transfers, balances, transactions, smart contracts

- **Layer 1:** Avalanche, Arthera, Flow, Massa, Movement, MultiversX, NEAR, Quai, Sui, TON
- **Layer 2:** Cronos zkEVM, Starknet, zkSync Era
- **Other:** Binance, Cosmos

### 2. DeFi & Trading

**Exchange Integration**

- **Centralized:** Binance (Traditional order book trading)
- **Decentralized Swaps:**
  - [Avalanche](https://github.com/harmony-one/eliza-harmony/blob/develop/packages/plugin-avalanche/README.md) (YAK [swaps](https://github.com/harmony-one/eliza-harmony/blob/develop/packages/plugin-avalanche/src/actions/yakSwap.ts))
  - NEAR ([Ref Finance](https://github.com/harmony-one/eliza-harmony/blob/develop/packages/plugin-near/src/actions/swap.ts): Native DEX enabling token swaps, liquidity provision, and yield farming across NEAR ecosystem)
  - Starknet ([AVNU](https://github.com/harmony-one/eliza-harmony/blob/develop/packages/plugin-starknet/src/actions/swap.ts): DEX aggregator with cross-protocol routing and gas optimization)
  - [Hyperliquid](https://github.com/harmony-one/eliza-harmony/blob/develop/packages/plugin-hyperliquid/README.md) (DEX trading)
- **Analytics:**
- Rabbi Trader (Solana-based token analysis tool with AI-driven market insights, trust scoring, and [trading recommendations](https://github.com/harmony-one/eliza-harmony/blob/develop/packages/plugin-rabbi-trader/src/actions/analyzeTrade.ts))

*Note: Currently no staking functionality is implemented in any plugin*

### 3. Memecoin/Token Creation

- **Starknet:** Unruggable memecoin deployment (agent action that generates [unruggable tokens](https://github.com/harmony-one/eliza-harmony/blob/develop/packages/plugin-starknet/src/actions/unruggable.ts))
- **Avalanche:** Token creation and [market generation](https://github.com/harmony-one/eliza-harmony/blob/develop/packages/plugin-avalanche/src/utils/tokenMill.ts)
- **MultiversX:** ESDT token creation
- **Flow:** NFT collection creation

### 4. Naming services & NFTs

- **Collections:** Solana NFT Generator, Flow, MultiversX
- **Domains:** [Starknet](https://github.com/harmony-one/eliza-harmony/tree/develop/packages/plugin-starknet) (.stark naming, subdomain management)

### 5. Intellectual Property
- **IP Rights:** Story Protocol (Blockchain-based intellectual property rights management)

### 6. Infrastructure

- **Cross-Chain:** Cosmos (Inter-Blockchain Communication)
- **Compute:** Spheron ([Cloud computing infrastructure](https://github.com/harmony-one/eliza-harmony/tree/develop/packages/plugin-spheron), GPU compute resources, supports multiple blockchain tokens)
- **Storage:** Irys (allows agents to store and retrieve data in a [decentralized manner](https://github.com/harmony-one/eliza-harmony/tree/develop/packages/plugin-irys))

### 7. Application Layer

- **Social:** Lens Protocol/Momoka
- **Payments:** Coinbase Commerce

### 8. Trading & Predictive Services


- **Decentralized Exchange:** [Hyperliquid](https://github.com/harmony-one/eliza-harmony/blob/develop/packages/plugin-hyperliquid/README.md) (Spot trading platform with market and limit order capabilities)
- **Machine Learning Inference:** [Allora Network](https://docs.allora.network/devs/get-started/overview)  (Decentralized machine learning network for on-chain predictive intelligence, providing AI-powered inference via smart contract integration)

## Implementation Pattern

Each plugin provides:

- Custom wallet implementation
- Chain-specific transaction handling
- Protocol-unique features
