# Eliza Web3 Plugin Ecosystem

## Core EVM Plugin Dependencies
The following plugins extend or use Eliza's base EVM plugin:

1. Avalanche
- Inherits EVM base functionality
- Extends with Avalanche-specific features
- Uses EVM wallet functionality

2. Cronos zkEVM
- Built on EVM base functionality
- Uses EVM hooks and wallet providers
- Customizes for zkEVM specific features

3. Story Protocol
- Utilizes EVM for wallet interactions
- Uses core EVM transaction handling
- Extends with IP/licensing features

4. zkSync Era
- Uses EVM for base transactions
- Extends with zkSync specific optimizations
- Shares EVM wallet architecture

## Plugin Categories

### 1. Basic Token Operations
Common features: transfers, balances, transactions
- Chains: Arthera, Avalanche*, Binance, Cosmos, Cronos zkEVM*, EVM (base), Flow, Fuel, Massa, Movement, MultiversX, NEAR, Quai, Starknet, Sui, TON, zkSync Era*
(*EVM-based implementations)

### 2. DeFi & Trading
#### Advanced Trading
- Binance (CEX)
- Hyperliquid (DEX)
- Rabbi-Trader (Analysis)

#### Swaps & Liquidity
- Avalanche* (YAK router)
- NEAR (Ref Finance)
- Starknet (AVNU)

### 3. NFT & IP Management
#### NFT Infrastructure
- Solana NFT Generator
- Story Protocol* (IP rights)
- Flow (NFT standards)
- MultiversX (ESDT)

#### Domain Services
- Massa (MNS)
- Starknet (Domain system)

### 4. Cross-Chain & Infrastructure
#### Cross-Chain Solutions
- EVM (LIFI bridge)
- Cosmos (IBC)
- Quai

#### Infrastructure Services
- Spheron (Compute/Deploy)
- Irys (Storage)

### 5. Protocol-Specific Features
#### Social/Content
- Lens Protocol
- Momoka

#### Oracle/Data
- Allora Network
- Hyperliquid

#### Commerce
- Coinbase Commerce

## Integration Notes
- Plugins marked with * are built on the EVM base plugin
- All EVM-based chains share common wallet and transaction handling
- Non-EVM chains implement their own transaction and wallet management
- Cross-chain features often utilize the EVM plugin for Ethereum-based operations

## Usage
Each plugin can be used independently or in combination with others. The EVM plugin provides base functionality for Ethereum-compatible chains, while other plugins extend or implement their own functionality as needed.

## Future Development
The modular architecture allows for easy addition of new chains and protocols, with the EVM plugin serving as a template for Ethereum-compatible implementations.
