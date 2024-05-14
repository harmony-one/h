# AnotherWorld / Runes Project Overview

[Repository](https://github.com/rika97/scaffold-eth-2)

## Summary

This project was devised to seamlessly transition BTC Rune into ERC20 tokens on platforms like Harmony. The process unfolds as follows:
1. Users deposit BTC Rune.
2. We employ an API to meticulously verify their transactions, ensuring accuracy in amount and address.
3. ERC20 tokens are minted and delivered to the user's address post-transaction confirmation.

### Technology

- Scaffold-ETH
- Next.js
- HardHat
- OpenZeppelin

![Project Image](https://github.com/harmony-one/h/assets/27670355/dd3e644a-8bad-4ac9-87e4-556b756e8ebe)

## Token Minting

A smart contract dubbed "WrappedRune" was crafted and deployed onto Harmony Mainnet (shard1) to initiate the minting process of ERC20 tokens (_ticker: "wRUNE"). Minting privileges are exclusively bestowed upon the smart contract deployer through the meticulous use of the `_mint` function, which comes pre-configured with specifications such as total supply.

![Token Minting Image](https://github.com/harmony-one/h/assets/27670355/74de2ec4-5b95-4c39-80d0-7d827fdc65c8)

## Token Factory

Another smart contract, "WrappedRuneFactory," serves as the custodian of all wRUNE tokens and facilitates their deployment. When users initiate transactions to convert Rune into wRUNE, our system meticulously verifies the transaction before seamlessly transferring the tokens to the user.

![Token Factory Image](https://github.com/harmony-one/h/assets/27670355/7f0e5b95-d2d9-43d9-874c-5ef89ecd539e)

## Challenges and Future Goals

The endeavor encountered its most formidable challenges during the configuration of scaffold-eth settings for deployment on shard1 and the intricate debugging of smart contracts. Looking ahead, our vision involves integrating an API capable of extracting user transaction details seamlessly and constructing an automated system to validate transactions and facilitate the transfer of wRUNE tokens.
