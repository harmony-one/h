2024-Q4:
- Hotstuff leader rotation: The Hotstuff protocol will rotate the leader with every new block. The future leader should send the new proposed block along with the commit signature, optimizing network communication by eliminating one extra step.
- 0.5 second block finality: Achieving a 0.5-second block finality, which is the theoretical minimum limit if we do not support rollback mechanics.

2025-Q1:
- Smooth integration of smart contracts into localnet development: Currently, deploying and testing smart contracts on localnet requires many manual steps. Additionally, modern frameworks for smart contract development are not supported out of the box.
- Reduce or minimize the number of required nodes for localnet development: Localnet currently starts with 22 nodes, which is excessive for development purposes. The goal is to reduce this number to 1-2 nodes or make it configurable.
- EIP-3074 sponsored transactions support: Sponsored transactions allow a third party to pay the gas fees on behalf of a user, enabling users to interact with decentralized applications (dApps) without needing to hold ETH for gas fees. This feature improves user experience and reduces barriers to entry.