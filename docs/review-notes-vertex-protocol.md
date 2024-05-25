## Vertex Protocol (DEX)

Documentation: [https://docs.vertexprotocol.com](https://docs.vertexprotocol.com)

UI: [https://app.vertexprotocol.com/markets](https://app.vertexprotocol.com/markets)

Also known as: Blitz

Active on Arbitrum, Blast (Both Ethereum L2)

Built in Solidity. SDK available in Rust, Typescript, Python.

### Core principle

- maximize liquidity
- prioritize fast order fulfillment
- minimal latency
- zero to minimal fees

### Key Designs

- Perpetual DEX with built-in AMM and lending systems
- Hybrid order fulfillment
    - Primarily method: off-chain sequencer (10-30ms latency)
        - clients submits (limit and market) orders directly to sequencer (with signatures)
        - sequencer records open orders on its internal (offchain, distributed) orderbook and match if possible 
        - sequencer submits matched order to smart contract for finalization
    - Secondary method: using liquidity from built-in AMM (onchain, i.e. slow mode)
        - sequencer submits orders matched against AMM on smart contract and finalize
- Cross-margin accounts
    - all open positions (AMM LP, lending, perps...) under user account are summed up for calculating margin (a.k.a "health") requirement
        -  across all (L2) chains where Vertex is deployed
    - isolated margin (subaccounts) can be created on-demand
- Cross-L2 trading and order matching
    - can potentially be cross-chain, cross-shard, ...
    - Once orders are matched cross-chain, DEX itself can fulfill the order as a temporary "counter-party" locally, and settle later in batch 
- Hedge-aware dynamic margin calculation
    - Spreads and positions that hedge against each other are recognized, resulting higher "health" score (amount of surplus funds available for establishing newer position or maintaining existing ones)
    - Note: most parameters are pre-configured by DEX operator based on "common sense", without much tuning
- Temporary session key for one-click trading
    - Client-generated private key, with public-key recorded on-chain
    - Key can be revoked per-login-session, or until user manually disconnect
- Multiple layers of protocol protection against "bad debt"
    - Conservative oracle for liquidation-related margin and balance calculation
    - Fees accumulated towards an "insurance funds" to cover bad debt if it occurs
    - "Socialization" (need more specification) of bad debt is the last resort

### Some issues

- Sequencer code or binary is unavailable
    - Inquired on Discord in Dec 2023, and May 2024. No response received
    - Sequencer is a crucial part of the infrastructure
        - handles low-latency order matching
        - maintains the (supposedly distributed) orderbook
        - routes the orders
        - decides whether to use AMM
    - It would take some work to  re-implemente the functionalities on-chain (in Solidity) or off-chain
        - On-chain implementation would lead to slower orderbook matching (depending on block time, defeating one of the core advantage of Vertex' architecture
- Strong reliance on low-latency, accurate oracle
    - Stork is used exclusively
        - Low-latency by allowing queries to be sent and answered via websocket offchain
        - Responses are signed using pre-published, on-chain verifiable keys
        - On-chain data is only updated when absolutely required and requested (e.g. to handle a liquidation request, or "slow-mode" AMM trade)
    - May result in major security incident if oracle keys are leaked
        - significant loss would propagate across the entire DEX, since many (if not most) accounts would be engaging in higher-leverage, derivative trading

### Other notes 

Total lines of contract code is roughly ~5000, reasonable commented and organized. It would not take long to review, adjust, and redeploy the system on Harmony, assuming adequate frontend can also be prepared at the same time. The oracle issue is ideally addressed prior to launch. There is a possibility that it may be swapped out and replaced by some oracle-less design. Another key uncertainty is the amount of work in terms of re-implementing the orderbook (and sequencer) functionalities. The most time consuming part would be to debugging and testing it in production using real assets

  