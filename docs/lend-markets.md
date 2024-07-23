## Securing lending markets on lend.country

Tens of millions of dollars were lost in 2023-2024 due to a known security issue in Compound v2. Specifically, when an operator (i.e. admin) adds a new market (i.e. a "share" token representing shares of the pool) to the lending-borrowing system, but fails to simutaneously mint initial share tokens or to add sufficient liquidity to that market, a hacker could manipulate the price of the share token, then borrow and redeem other fairly-valued assets (BTC, ETH, ...) from the system using the share token as collateral while its perceived-value is very high. Because of a rounding calculation error, the number of required share token is less than what it should be - in extreme cases, rounding down from 1.999999... to 1, resulting a near 50% mismatch in monetary calculation. Then, the borrowed assets can be transferred to a wallet the hacker's control, and the hacker may use the excess assets to reset the pool (via liquidation feature) and repeat the attack indefinitely.

Because all these operations could be packed and completed in a single transaction with funds ending in the hacker's wallet, it is nearly impossible to recover the funds after the hack is completed. 

Example hack transactions:

- https://etherscan.io/tx/0xf7c21600452939a81b599017ee24ee0dfd92aaaccd0a55d02819a7658a6ef635
- https://etherscan.io/tx/0x27a3788d504af542681436bfdecf1823f7a8a691d04309ad33e6d3825e899746

To learn more, read a detailed step-by-step with debugging traces (as screenshots) in this articles

https://blocksec.com/blog/6-hundred-finance-incident-catalyzing-the-wave-of-precision-related-exploits-in-vulnerable-forked-protocols

Relevant discussions:

- https://www.comp.xyz/t/hundred-finance-exploit-and-compound-v2/4266
- https://rekt.news/onyx-protocol-rekt/
- https://medium.com/@SonneFinance/post-mortem-sonne-finance-exploit-12f3daa82b06
- https://blog.verichains.io/p/compound-v2-forked-vulnerability

### Mitigation

#### Initializing new markets 

As suggested in the artcles, preventing price manipulation is sufficient to tharwt the hack and make other steps ineffective. This can be done by simply ensuring the number of share-tokens in the new market is large enough, such that even the hacker follow through other steps, the mismatch in monetary calculation due to rounding down becomes negligible. For example, in the step-by-step analysis above (published in blocksec.com), the hacker succeeded only because the hacker controls the entire supply (for share tokens) and managed to leave only 2 wei share-tokens in circulation.

In simpler terms, when a new market is deployed, use a multisig wallet to deposit a nominal amount of tokens (e.g. worth $100) then use the `mint` function (a permissionless external function) with a reasonable token-amount as the parameter (e.g. whatever amount is worth $100, and covert to wei - for USDC [6 decimals] this is 1e+6 * 100 = 1e+8 weis) to initialize the market.

Do not announce the new market in any way, until the multisig wallet is secured and the initialization is completed.

#### Find hidden markets and setting alerts

Some markets may be deployed during initial development and debugging period. A lot of times, they become overlooked and forgotten, with near zero liquidity and share tokens in them. But ackers could find these markets by following the transaction history in deployer accounts and querying lending contract states.

To prevent that, we should have a dashboard enumerating all existing markets, their current supply, exchange rate (and pricing), and last activities. Alert should be set if at any time there is any market that has close to zero supply or liquidity 

#### Monitoring existing market and analytics

For existing markets, we should closely monitor supply and recent transactions, and add the information to the existing analytics. We should be alerted if any market has a gradually declining supply or unusual change in exchange rate.