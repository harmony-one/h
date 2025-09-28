2025-09-28: I verified the data tracked by the LP tracking tool. Most of the queried data is not correct. I used a script and the Binance API, Basescan, and revert finance to query the correct data for the new bot wallet (0x982116545d53f954ac348694cb1a8cf45269bbf0) to calculate fee returns, divergence loss, net PnL per position and the annualized return of the wallet since starting the farming strategy. 

So far, the strategy is not profitable (-10.24% APR) due to the high volatility of BTC, the directional volatility to be precise. The bot needs to rebalance frequently, often before enough fees in the current range are accrued to cover the divergence loss at the time of the rebalance. When BTC ranges in a small interval, the bot strategy is very profitable (70% APR based on the data of the previous wallet). The overall algorithm needs to be improved by detecting periods of directional price movements of BTC and either widen the or stop providing liquidity entirely. 

2025-09-19: Created a tool with cursor to help me checking wallet profitability a bit faster than doing it entirely in the manual way. Also researched Dune Analytics in combination with cursor to see how to utilize it for wallet analysis in the Unstaked_Owner list created by Aaron. I am still struggling to get reliable results for the task but i am optimistic to solve it. In addition, I analyzed a couple of wallets that got shared by the team to get an idea of their strategy and profitability. 

I started looking into Artems bot again, installed Docker and prepared a wallet to launch the bot myself to get better insights. recent results showed that it is more profitable than many other wallets, even such with sophisticated strategies like 0x751140b83d289353b3b6da2c7e8659b3a0642f11.

2025-09-07: Researched wallet 0x751140b83d289353b3b6da2c7e8659b3a0642f11 that deploys short-term liquidity on Aerodrome and identified its strategy, which consists of deploying liquidity and staking it during low-volume periods lasting seconds to minutes. Verified the profitability of wallet 0x751140b83d289353b3b6da2c7e8659b3a0642f11 as well. Calculated the profitability of Artem's Farming bot for the last two weeks. Compared to 0x751140b83d289353b3b6da2c7e8659b3a0642f11, Harmonies bot outperformed by 250%. 

---

2025-08-31: I started working with Dune Analytics and verified the total 90-day swap fees for the cbBTC/USDC on Aerodrome. Looked into the Bot performance and several wallets that provide liquidity to the pool to figure out their strategy. Worked with Artem and Yuri to calculate net profits of wallets and the bot. 

---

2025-08-17: I continued to support Artem and the Dev team regarding the bot functionality. Started to look into Aedrodrome liquidity position data to understand the context of the different LP strategies of user wallets. Reached out to Aaron and Yuri for extended data. Started learning Dune Analytics to visualize Data. 


---

2025-08-10: I participated in team calls to support Artem and the dev team to understand the mechanics of hedging and how the execution flow of the automated strategy should work. After hedges didn't close appropriately during last week's performance test, I had to fix the code and redeploy the strategy in a new range. Started to look into the data shared by Stephen to study the actual price impacts for rebalancing after calculating an impact based on current liquidity. 

Downloaded Docker and prepared the set-up to test the current version of Artems bot this week. 

---

2025-07-27: I wrote a document with a short thesis for each asset held by the treasury to support the decision-making regarding future asset allocations. Together with the dev team we discussed hedging alternatives and reviewed updates of the LP farming strategy. 

---

2025-07-20: I re-deployed the hedged farming strategy for BTC/USDC and started tracking its performance. Reviewed Artems and Franks LP strategy and Back-testing. Gammaswap, as well as YieldBasis introduced hedged farming strategies for concentrated liquidity pools so I started looking into them. 

I got a request from Li to provide my opinion regarding the potential performance for certain assets held by our treasury, so I started writing a paper with a short thesis for each of the named assets. 


---

2025-07-13: In collaboration with everyone involved in the definition and execution of the treasury return strategies, I provided my input and feedback on the next steps to align with the team. We had a team call to define the minimum viable product for the BTC strategy and discussed the next steps. 

I changed my test script accordingly. It works with a BTC/USDC pool now on Shadow (Sonic network). In addition, I am in the process of adding the same strategy for Aerodrome to achieve more verifiable data.  

---

2025 Q2 Review

Q2 was entirely driven by identifying the problems of liquidity pools and the lack of profitability of liquidity providers, especially when it comes to concentrated liquidity pools. Benchmarks and test scenarios revealed that most losses are attributed to suboptimal rebalancing during high-volatility periods. The findings helped to look into potential solutions. The measurement of volatility-to-price correlation only delivered weak results. Still, it was clear that a phase of strong price moves needs to be avoided when farming concentrated pools or even having automated rebalancing in place. 

My current solution is an automated hedged farming strategy with manual range selection. The script tracks Token balances in the LP and opens equivalent hedges once the position moves out of range. This way, strong price movements are caught while avoiding a potentially malicious rebalancing.   After the deposit, the entire process is automated and integrates with Sadow Exchange as well as Sonic and using price data from Coingecko. I coded the Python script with Cursor after learning the foundations of LLM-based development (vibe coding). The script has been tested successfully and currently runs on a virtual machine for performance testing.

---

2025-06-22: The S/BTC strategy script has been completed and tested successfully after several tweaks to the calculation logic. I sought opportunities to run the script on a server to minimize network interruptions for extended performance testing. The script tracks the LP deposit on Shadow exchange, identifies range breaks and triggers equivalent market orders to hedge the asset exposure and catch deviation of both (Pair trade). 

---

2025-06-15: Continued building the strategy deployment so S/BTC with significant progress. A script is pulling prices every 5 seconds for selected pair trades. The connected test wallet can successfully execute Trades on Hyperliquid based on price triggers, which are in rough limit pair trade orders. Limit pair trade orders do not exist on any protocol yet (For example Pear Protocol) so the execution marks a milestone in the development of the strategy. The script can also query LP positions held by the wallet on Shadow exchange but is not able to see the exact amount of Tokens held in the position due to the missing ABI. Once, that is solved, the strategy can be executed entirely. 

---

2025-06-08: I backtested my LP strategy for BTC/S in combination with Cursor and manual testing. The results are promising, outperforming holding BTC by 150% despite S losing value compared to BTC. The next step is to implement the strategy with real money, tracking actual returns on an ongoing basis. Despite being simple and performant, the approach requires manual decision-making in terms of rebalancing. That needs to be automated, too. 

---

2025-06-01: I assessed and gave feedback to LP strategies developed by Li (via LLM) and Aaron. Researched backtesting tools to verify the perp-hedged LP strategy for the BTC/S LP on Shadow Exchange (Sonic). Theo provided a subgraph that I can use as a foundation to backtest the specific pool. 

HyperEVM is a promising ecosystem for yield opportunities, with several protocols set to launch their tokens soon. The sentiment towards the chain is more positive compared to Monad (upcoming) or Berachain. 

---

2025-05-25: I researched yield opportunities for BTC and S on the Sonic network. The results show a low available yield for BTC except when paired with S. Currently working on a strategy on how to provide liquidity with minimal loss risk while capturing the upside by combining the LP position with a pair trade. I started researching the Hype EVM ecosystem to assess its potential.

---

2025-05-18: I continued learning "vibe coding" to build tools. Due to my research about funding rates, I came across an opportunity to build a yield-accruing product based on the arbitrage of on-chain funding rates and started adding a section to the yield-bearing asset vault product. After the discussion with Aaron I received more funding rate data for Hyperliquid to analyze it. 

---

2025-05-11: I started learning to build Apps with the help of LLMs. My goal is to build useful tools that can test a given thesis faster. After an initial success with a basic pendle-related app I began to build an app that tracks funding rates of Tokens and will connect it to a liquidity manager or trading bot. 

---

2025-05-05: I got data on S funding rates and am currently analyzing it to see if changes in funding rates are a good indicator of upcoming price moves. 

I also did a status check-up on the Berachain ecosystem since it is a potential ecosystem to look into after Sonic. My conclusion is that in the current market environment, the chain economics are not sustainable, especially with the characteristics of participants in their chain ecosystem. 

Besides that, I continued to help the team understand Pendle strategies and assess risks involved. 

---

2025-04-27: I looked deeper into options and the Box Spread strategy Aaron proposed. First results did not look very promising in terms of potential profitability, yield distribution and its effects on a tokenization, and how safe the yields are. 

I decided to use tracking of funding rates to optimize liquidity provision in volatile pools and looked for backtesting tools. A data set with historical funding rates in short intervals will bring more clarity if the combination of funding rates and liquidity strategy increases profitability for LP management. 

---

2025-04-20 I helped finalize the farming strategies that will be deployed on Sonic and discussed automated liquidity management strategies further to find a solution for identifying upcoming volatility for certain coins.

Taking the basis trade yield product idea, Aaron suggested an option-based yield product. I started studying the basic mechanics of options and how they work. In addition, I looked into MegaETH to identify its potential compared to Berachain from a yield farming perspective. 

---

2025-04-13 I started collecting volatility data of coins such as BTC or S to develop a first draft of a portfolio-balancing strategy. The strategy leverages a top-down approach to identify the optimal range in concentrated liquidity pools and measure weather to adjust the range during increased levels of volatility. The strategy needs to get tested and verified once we have price data on the minute level. 

I connected with Artem to help him navigate the Sonic ecosystem during his tests and explain how protocols work or where to find certain functions.

---

2025-04-06 I helped finalizing treasury farming strategies across Sonic and discussed the next steps with Theo after the treasury funds were deployed. The focus will be on products and measurements that have the most positive impact.

I started researching the Berachain ecosystem and its mechanisms to find potential opportunities that we can leverage for ourselves. Berachain offers the best yields across most chains and has an interesting flywheel effect going on.

---

2025 Q1 Review

The vision for Harmony to be the Home of Simple DeFi became more structured and detailed, with most of my work contributing to that vision. Q1 was driven by extensive product research focussing on laying the knowledge foundation to develop cross-chain products on Harmony. Users should be able to access yield opportunities across several ecosystems in a simple click and leverage custom strategies on Harmony. 

The Yield Enhancer is ready to be launched, and the treasury is accruing yield for it. To enable a better user experience, the bridge infrastructure of Harmony needs to be improved. I built a partnership with Socket protocol to make any asset quickly available via the issuance of wrapped tokens and ensure fast deposits and withdrawals for users. Additional product ideas are evolving around stablecoins, yield product leveraging, and portfolio management.

---

2025-03-23 Sun: This week, I mostly researched the most profitable farming opportunities for treasury farming and to help the team understand certain protocol mechanics, risk factors, strategy execution steps, etc. Apart from that, I continued writing the product description for a basis trade stablecoin protocol earning fees from funding rates. 

---

2025-03-17 Sun: I discussed a more detailed relationship model with Socket Protocol and joined a call with them and Aaron to discuss the technicals. We are waiting for more detailed technical descriptions. 

To get a deeper understanding of ALM strategies, I researched LVR and impermanent loss. In discussion with Theo, we synthesized the most valuable next step towards an actual better product compared to existing managers: Track the real-time volatility of certain assets. 

I researched more potential strategies to deploy stablecoins from the treasury to generate returns. We are still in the progress of identifying optimal allocations and protocols. 

---

2025-03-09 Sun: I researched automated liquidity management and related data to support the product development of the cross-chain portfolio manager. The synthesis for a successful product may be related to depend the ALM on asset volatility changes. 

After additional conversations with Socket Protocol, a partnership will be very interesting to enable cross-chain deposits to Harmony. In the long run, the partnership will work towards an app-based, user-centric product approach, abstracting chains completely to lift user experience to the next level.

---

2025-03-01 Sat: I updated with Li and Theo regarding product development, Consensus recap, and next steps in the beginning of the week. The outcome of the task to unify the bridge assets into a single USDC.e differed significantly from the expectation. It is a learning for improving communication in product development. It is a dependency to assure a smooth launch of the Yield enhancer. I also connected with Socket protocol as well as debridge to explore alternative bridge solutions and a better user experience when interacting with Harmony. 

I started researching the Sonic ecosystem to gather potential options for the Harmony AI portfolio manager. However, my focus is to understand why Sonic is popular now and how the products interact with each other. 


2025-02-24 Mon: I participated in Consensus Hong Kong events last week to gather feedback from communities and projects. Besides that, my focus is to integrate with fast bridge infrastructure to enable cross-chain deposits and strategies leveraging Harmony-foreign products. Here is a summary of my visit at consensus: 

It was the first event week where I emphasized building DeFi on Harmony. The main purpose was to gather feedback from projects and people in the industry. There are surprisingly many people still holding some $ONE. Most remember the days of DeFi Kingdoms as good times so Harmony as a chain triggers rather a positive feeling in them. All of those that used Harmony before are excited that we are trying to revive the chain, some asked me when they can use the first products like the yield enhancer.

There were a couple of questions and recommendations: 

- A rebrand could be useful to get rid of the past fully
- We should try to launch a unique retail-friendly product, abstracted from the chain. One example was an on-chain Mahjong Game. 
- We need to figure out an incentive programs for teams to onboard
- Build/attract a cross-industry product to onboard more retail users such as a health device (such as https://x.com/Moonringai) or fitness-to-earn. 

Besides, I talked with projects for potential partnerships whereas I mainly focused on infrastructure projects such as socket protocol for bridging or Spark Fi for Lending. Since we want to leverage profitable, yield-distributing products on harmony, cross-chain integrations are an integral part of enabling unique strategies on top of them. GameFi projects were also interesting since Harmony is performant and has the DeFi Kingdom's History.

Follow-ups are due this week. 

---

2025-02-09 Sun: My week was driven by research about trends and new developments in 2025. Specifically, DeFAI in its early stages and its potential to see how we can apply it to Harmony. The whole approach needs to be revisited. Apart from that, general trends for this year need to be identified to see how we can improve Harmony as an ecosystem. I see the vision of Harmony becoming the "Savings Chain" leveraging products from other chains and presenting them in a consumer-friendly, simple way. 

---

2025-02-01 Sat: The Yield Enhancer is ready to be launched. Only bridge assets need to be unified to prepare for better liquidity. I finalized the DeFi roadmap for Harmony, which will be published within the next few days before the Yield Enhancer launch alongside additional content. In addition, I am researching current solutions and trends to identify how a potential interaction with DeFi apps could look in the near future utilizing new technologies such as the use of LLMs, Agents, Wallet abstractions, gamification, and more. The goal is to onboard new user groups that are not familiar with DeFi to the Harmony ecosystem. 

---

2025-01-25 Sat: Given the start of the new year, I prepared an article outlining the DeFi roadmap for Harmony in 2025 and gathered material for a general DeFi-related outlook. The Outlook is going to be published in a video format and will cover new trends, the general environment, and previously emerging innovations across the DeFi landscape. 

In addition, to anticipate the launch of the Harmony Yield Enhancer I prepared additional content that can be used for marketing purposes such as an article and raw Twitter content. 

---

2025-01-18 Sat: The last two weeks were occupied by testing the Harmony Yield Enhancer, planning the next steps for the product, and preparing a marketing strategy for its launch. I curated a list of KOLs focussing on yield farming and DeFi that I can contact at launch. I prepared content to promote boostDAI strategies on the Harmony Twitter account.

After launch, cross-chain deposits and 1-click deposits with any asset from any chain should be possible. I am currently talking with Across as a partner to enable those features. 

In general, a broader audience outside of the current Harmony community needs to be reached. I had a discussion with Zi about potential cross-community marketing, especially non-crypto natives.

---

Q4 Review

My first 2.5 months at Harmony were all about assessing the status Quo, analyzing the ecosystem for its strengths and weaknesses, and identifying a potential direction where to go from here. In terms of Defi, I developed the strategy to funnel returns offered outside of Harmony into our ecosystem. In addition, there are two user groups that we can target: 

- New/non-native users who dont know about farming
- Power users able to deploy advanced strategies

All product developments will evolve around those two user groups. 

Achieved so far: 

- The treasury farms yield to distribute it to our products after potential strategies have been elaborated and assessed
- 1sDAI (11.5% APY) is deployed on Harmony
- The yield Enhancer product conception is ready and to be deployed (target is within December)
- Several product descriptions targeting more advanced strategies are ready (Lending Market, 1Swap Gauge)

---

2025 Goals:

My mission for 2025 is to **make Harmony the home of simple DeFi.**

100 Million $ TVL:
Liquidity is crucial for attracting users, teams, and projects, while also providing a seamless experience that drives adoption. Deep liquidity will be achieved by offering competitive returns through a variety of yield strategies within the ecosystem.

10,000 Wallets with a Balance of $200+:
The balance of wallets is a key metric in determining whether users view Harmony as a place to store their funds. To reach this goal, we will target non-native retail investors by offering simple and accessible savings strategies.

10,000 Daily Active Wallets:
Daily active wallets reflect user retention and the success of attracting "Power Users" who naturally influence others. To achieve this goal, we will focus on creating engaging, gamified experiences, advanced high-yield farming strategies, and utility-driven products that keep users returning daily.

---

2024-11-27 Wed: This week is about to get the Yield enhancer ready. I went through the final concept with Theo and wrote an additional detailed description of the vault mechanics. Besides that, I am ideating how to market the upcoming pump fun launch and started updating the Harmony documentation. Apart from that, I started engaging a little bit with the community and plan to get more feedback from them to see what they want to use or look for. 

---

2024-11-20 Wed: Last week was mostly occupied by DevCon SEA. I connected with many builders and particularly attended events of Base chain to talk with builders there and what they perceive as valuable in the ecosystem. Product-wise, Theo and I decided to launch the Harmony yield enhancer as soon as possible, optimally before the Christmas holidays. I prepared a wireframe + the final product description to be handed to the developers. On Tuesday, I met with Li to discuss the first treasury farming strategy (Buying JLP) and we discussed each step in detail. I also finished the first draft of the 1Swap Gauge product description. 

---

2024-11-10 Sun: The rest of the week I continued to design the tokenomics of the Gauge system for 1Swap. It will be a novel model that is reflexive to 1swaps earnings and therefore aligned to the state of the Harmony ecosystem. Emissions are distributed according to a certain formula incentivizing projects to participate in bribing and to lock up Token supply without worrying too much about its price performance. Since Saturday, DevCon week started in Bangkok and I visited some side events. Besides meeting the Stephens contacts, my goal is to connect with as many builders as possible. 

2024-11-06 Wed: This week, I started writing the product description of a Gauge system for 1Swap. The critical point here is the tokenomics. Although veDEXes have proven their PMF, the failure rate of new veDEXes is high due to their tokenomics. My focus is to develop a sustainable token system that dynamically grows with Harmony. For that, I researched innovative tokenomics and recent standards at other protocols such as IntentX, Liquid Driver, Ramses, Camelot, and others. 

---

2024-10-31 Thu: DeFi Research on synthetic credit lines, Product launches

2024-10-30 Wed: Finalization of the Harmony Yield Enhancer Product Description

2024-10-29 Tue: DWF Labs Call, Further Research on MakerDAO, Governance Contract Tokenomics Ideation for 1Swap

2024-10-28 Mon: Harmony Yield Enhancer Product Description, Lednign Market Finalization

---

2024-10-25 Fri: AI Agent Research, Ideation of Ecosystem products

2024-10-24 Thu: Lending market finalization, DeFi Research

2024-10-23 Wed: AI Agent coin research

2024-10-22 Tue: Lending market user stories, start of writing the Harmony yield enhancer product description

2024-10-21 Mon: Researching Pump.Fun iterations, AI Agent Tokens. Continued the product conception of the AAVE V2-based lending market

---
2024-10-18 Fri: DeFi Research, Ideation

2024-10-17 Thu: Low-risk farming research, Lending market product conception

2024-10-16 Wed: Lending market tokenomics conception in detail,

2024-10-15 Tue: Treasury farming feedback and discussion, more stablecoin research, especially yield-bearing products, contacted all potential partners

2024-10-14 Mon: Research of yield-bearing products, reached out to a couple more stablecoin issuers

---
2024-10-11 Fri: Detailing selected yield strategies and their execution

2024-10-10 Thu: Prioritizing, further due diligence on selected yield opportunities

2024-10-09 Wed: Identification of Yield opportunities for treasury income

2024-10-08 Tue: Lending market tokenomics design, farming DD, research

2024-10-07 Mon: Lending market research, Outline tokenomics, Outline product description




Welcome Philipp!

https://medium.com/@philipp.petzka
https://www.linkedin.com/in/philipppetzka

You will initially manage product development, curate trader community, and run monthly campaigns. Later, you may as well engage business development, build partnership integrations, and grow marketing reach.

You are expected for startup-like long hours and relentless dedication. You should synchronize daily with the global team, in particular some overlapping hours during 9am to 7pm California hours. We work during weekends but not necessarily with scheduled meetings.
