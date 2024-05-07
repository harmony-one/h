# 1 second finality

Empty blocks, Uncle rewards, Parallel signatures

- Resource profiling on mainnet nodes for optimizing BLS signature aggregation (determining if CPU bound on 1 thread, or parallelizable to 4 cores)
- Change block finalization during consensus from 99% signature collection to 80% (using uncle blocks for validator rewards)
- Reuse components from HotStuff (semi-synchronous consensus and aggressive pipelining like RapidChain), already implemented in Aptos and Sui; as well as larger deploys in Binance Smart Chain (100 nodes) and Cosmos chains (300 nodes)
