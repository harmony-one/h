2024-08-08 Thu: Configured fly.io custom domain to link vertex-trade project URL with [fe.country](https://fe.country), following Aaron's DNS mapping of fe.country to the Vertex application. Conducting an ongoing review of the Vertex trading page and associated module, focusing on perpetual trades functionality. Simultaneously analyzing a perpetual contract implementation to gain deeper insights into its structure and behavior.

2024-08-08 Thu: Configured fly.io link vertex-tarde project URL with fe.country, after Aaron mapped fe.country DNS with vertex app. Worked on reviewing Vertex trading page and module to work on mock perp trades. Also, checked perpetual contracts implementations. 

2024-08-07 Wed: Updated [Dockerfile to enhance performance](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2). Modified quote token to USDT on Harmony test network. Reviewed perpetual contract logic and tokens on Harmony bridge. Talked to Aaron about updating country DNS records to link Vertex fly.io URL to fe.country.

2024-08-06 Tue: Deployed Vertex Trade App on [fly.io](https://vertex-trade.fly.dev/). Configured Dockerfile and fly.toml to work with Next.js monorepo. Fixing deploy errors related to ChainDev handling (supporting multiple chain environments such as local, testnet, harmonyMainnet, among others), package.json build scripts, and Sentry configuration.

2024-08-05 Mon: Refactoring TradingView mock interfaces/types to resolve [build script issues](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/3). Successfully running Vertex Trade App's dev and build scripts locally with Harmony Testnet chain integration. Continuing efforts to deploy Vertex App in fly.io and in Harmony mainnet.

---
2024-08-02 Fri: Working on resolving build command issues for the Vertex Trade App frontend, addressing Tailwind problems, and modifying TradingView mock hooks calls. These build-related challenges remain ongoing and require further attention. Monitored the new cluster PostgreSQL database connection with 1Bot, observing no issues and confirming successful insert statements in logs, chats, stat_bot_command, invoice, and users tables. 

2024-08-01 Thu: Migrated 1Bot database to Soph's new cluster, updating primary keys, foreign keys, Indexes, sequences, and data to match the old Database cluster. Next day's plan: monitor 1Bot/Database integration. For Vertex Defi App frontend, accessed Trade menu page locally after modifying components using TradingView mock data.

2024-07-31 Wed: Created and tested backup of 1Bot database. Soph created a cluster on fly.io from a snapshot of the primary server. This new cluster has all machines working (primary, replica, and zombie). The next step is to connect 1Bot to this new database with the update of all subsequent changes (from the snapshot date). For the Vertex Trade App, completed updating all hooks and other files that use TradingView libraries. Currently testing its functionalities with the rest of the app to ensure successful build and deployment on fly.io with no errors.

2024-07-30 Tue: Updated trading charts hooks and other files to use mock types, turning off the use of TradingView Advance libraries (85% progress). Talked to Soph regarding 1bot payments database issues throwing the Connection terminated unexpectedly error. The database zombie machine is down, and we need to back up the databases before creating a new zombie machine that will complete the architecture (primary, replica, and zombie). Tomorrow, the backup will take place.

2024-07-29 Mon: Checked issues with 1.country site and payment database connection issues on Harmony1Bot. Also worked on the Vertex Trade App mocking TradingView components.

---
2024-07-26 Fri: Finished the [withdraw mock call](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2) on the Vertex Trade Client. Also added the [VertexToken contract](https://github.com/fegloff/vertex-contracts/pull/1) to the Vertex Contracts repo and the logic to deploy it through a Proxy. Updated the deploy and initializer scripts. Finally, Kept working on using mock graphs instead of the TradingView library.

2024-07-25 Thu: Working on a mock call of the Withdraw feature due to its use of the Vertex SDK and query endpoint to handle the call. Also talked to Aaron and started to work on deploying the Vertex Token on the Harmony testnet chain. Finally, investigating a way to work with mock graphs instead of using TradingView Advance and free versions. 

2024-07-24 Wed: Talked to Aaron about the Vertex Trading App and listed the components required to have minimal functionalities. Also, worked on fixing the mock data handling on the withdraw feature, which is disabling the feature.

2024-07-23 Tue: Fixed [formatTimestamp](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2) method issues with Harmony mock data. Added spot property to harmonyClient to handle spot engine mock calls and added a method to retrieve the maximum withdrawable amount per token. Kept working on the withdrawal feature.

2024-07-22 Mon: Enabled faucet feature to mint testnet funds for Harmony Testnet on Vertex App and currently working on the withdraw feature.

---
2024-07-19 Fri: Checked TradingView data feed integration with Vertex Trade App, and transitioning to a free alternative would require a significant effort. Reviewed and created a list of missing components to port Vertex to Harmony and sent it to Li. Pushed the latest changes to Vertex Defi App [PR](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2 ) and Vertex contracts [PR](https://github.com/fegloff/vertex-contracts/pull/1).  

2024-07-18 Thu: Was able to retrieve the wallet balance using the custom multi-call hook and make a deposit. Checked TradvingView Advance integration with the Trade app, and it seems that using the free version will require significant refactoring. The TradingView library is required to access the Trade feature. Need to check how the datafeed component could affect the refactoring.

2024-07-17 Wed: Kept working on wallet connection logic and fixed an issue not allowing wallet balance to show on the Vertex Trade app. The problem was related to publicClient's multicall method of the Wagmi package. Added custom multicall hook for not supported chains.  

2024-07-16 Tue: Worked on the Vertex Trade app wallet connection (it's not showing wallet balance) and deposit methods on the Harmony Testnet chain. Had to update mock JSON files to use the mockTokens address (it's not enough to update config files). 

2024-07-15 Mon: Deployed Vertex contracts on the testnet chain for testing on the Vertex Trade app, including mock tokens. Refactored the defi app code to support the harmony testnet chain. On 1Bot disabled bard's model command due to its discontinuation to become Gemini (1bot supports Gemini 1.5, too).

---
2024-07-12 Fri: Added MockQuoteToken (for price reference, fee denomination, liquidity provision, margin, and collateral deposits, etc.) and MockUsdcToken, added localhost/hardhat chain for local testing. Added a [deposit script](https://github.com/fegloff/vertex-contracts/pull/1) to test the depositCollateral method locally on the contract level because it was not working on the Trade App site, and the local test was successful.

2024-07-11 Thu: Reviewed the deposit operation at the contract level. Refactored deploy and initialization scripts, which fixes contracts initialization, to correctly assign Spot and Perp engines to the endpoint contracts, among other improvements. 

2024-07-10 Wed: Kept working with Vertex contracts and Vertex trade app. Was able to add products to the SpotEngine contract. Also added OffchainExchange initialization. Updating the deploy/initialization script is due to contract prerequisites. 

2024-07-09 Tue: Still had issues adding products to the spot and perp engine contracts. Checked other contracts logic and created script to add spot and perp engines to clearingHouse contract, but had the same error when trying to register a product. Adding some emit events to flagging the contract method logic. On 1Bot, added [content policy violation](https://github.com/harmony-one/HarmonyOneBot/pull/362) error handling for the /dalle command (pushed live).    

2024-07-08 Mon: Working on adding products to spotEngine and perpEngine contracts. The offchainExchange address is used as the order book contract (one of the required parameters). Had gas issues, working on solving them. Expecting that after fixing the product addition, the deposit logic will be fulfilled.

---
2024-07-05 Fri: Fixed /stats and /botstats commands, which were throwing 410 errors due to [uniswap-v3-harmony](https://api.thegraph.com/subgraphs/name/nick8319/uniswap-v3-harmony) endpoint has been removed. Added error handling on the rest of API calls for stats-related commands. Looking for an alternative to bring uniswap/harmony data. Updated the new contract address after all Vertex public contracts were initialized, but still working on deposit funds logic and checking Vertex SDK.

2024-07-04 Thu: Updated Vertex's initializable contracts, adding [isInitialized method](https://github.com/fegloff/vertex-contracts/pull/1) to check if the contract was already initialized. The new method calls Openzeppelin Initializable's _getInitializedVersion() method. Also updated the initializer script and fixed ArbAirdrop (with WONE as an airdropped token) contract initialization issues. Checked the 1bot database on fly.io, and the zombie machine is down (primary and replica machines are up and running). Designed a plan to replace the zombie machine and discussed it with Artem, who will check the fly.io configuration. Also, worked on fixing 1Bot /stats and /botstats commands.

2024-07-03 Wed: Initialized perpEngine and spotEngine and had issues with contract owner initializing arbAirdrop contract (with WONE as airdropped token). Had issues initializing. Checked 1bot logs and stats and had issues with the /stats command, working on fixing database connection issues (Request failed with status code 410 error) . 

2024-07-02 Tue: Initialized [Clearinghouse contract](https://explorer.harmony.one/address/0x1dd343adb90548b7af93abb9086b26e6f9c0f280) on Harmony Mainnet. Working on perpEngine and spotEngine initialization. Reviewed TransparentUpgradeableProxy initialization, which is expecting the initial implementation contract address. According to the [bytecode](https://arbiscan.io/bytecode-decompiler?a=0x7a557dddb3f19eb9d81983b67858b6e73c140ac2) of the implementation contract, the contract includes a method of handling user positions, deposits, and withdrawals, executing trades or swaps, etc. The contract address differs from what Vertex gave on their documentation, so I wrote on Vertex Discord to seek help porting Vertex on a chain different from Aribitrum.

2024-07-01 Mon: Fixed [Verifier contract](https://github.com/fegloff/vertex-contracts/pull/1) initialize method issue. Redeployed all contracts after changes were made to the initialize method on the Verifier contract. Reinitialized the Endpoint contract but still had issues with the deposit logic on the Trade App. Kept working on this and other contract initialization methods.

---

**2024 Q2 Review (11 Hours)**

I integrated [GPT-4o to 1Bot](https://x.com/harmonyprotocol/status/1795951553024565259), implemented token-based security and refactored the codebase to facilitate adding new large language models, including Claude, Sonnet, Haiku, and subagent integration. Added model-specific conversation handling and access to Anthropic tool feature, to check stocks and Web3 tokens. I fixed simultaneous command call issues.

Porting and deploying [Vertex Trade](https://github.com/harmony-one/vertex-web-monorepo-snapshot) contracts to Harmony. To address the mono-repo's reliance on the Vertex-typescript-sdk, I implemented a harmonyClient module designed to handle mock calls while facilitating the gradual porting of all API calls to the Harmony network. Additionally, I deployed defi_greeks API which provides endpoints for calculating risk measures and greeks for various financial derivatives and improved 1.country one-and-two-letter domain handling and certificate management.

---
2024-06-30 Sun: Worked on Verifier initialize method.

2024-06-28 Fri: Medical emergency.

2024-06-27 Thu: Medical emergency.

2024-06-26 Wed: Created and deployed MockSequencer and MockSanction contracts. Created initializer script to handle contract initializations. Initialized Endpoint contract, but having issues initializing Verifier contract. Time is limited due to the medical emergency.

2024-06-25 Tue: Medical emergency, catching up on Wednesday.

2024-06-24 Mon: Worked on Portfolio's deposit logic. The deposit logic interacts with the (upgradable) Endpoint contract, calling the depositCollateral method. The Endpoint contract was deployed on Harmony Mainnet, but the initialize method has yet to be called. The method receives a sequencer contract address as a parameter, among other nonpublic contracts. The sequencer contract is linked to the order book, which is the main feature of Vertex mixed architecture. To keep working on the mock Vertex Trade app, I'm working on a mock sequencer contract (needs to create Sactions and OffchainExchange mock contracts, too). The only contract of the Vertex contract repo that uses the sequencer is the Endpoint contract. Also, added a mock method to the subaccount mock client.

---
2024-06-20 Fri: Day off

2024-06-19 Thu: Fixed [BigDecimal type issues](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2) with Arbitrum and Harmony chains, and now the Portfolio overview and deposit components are showing USDC assets for the Harmony chain. Kept working on deposit logic for the Harmony chain.

2024-06-19 Wed: Added [HarmonyContract mock](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2) for utility methods that work with contracts through Vertex SDK packages. Kept working on mock methods for Portfolio Overview and deposit components and worked on fixing issues with deposit logic that don't work with Arbitrum and Harmony chains.  

2024-06-18 Tue: Added [TransparentUpgradeableProxy contract](https://github.com/fegloff/vertex-contracts/pull/1) to the Vertex Contract repo. This contract is labeled querier contract on the Vertex monorepo. The contract was found through the Arbitrum explorer and still needs to be deployed due to the implementation contract needing to be included as part of the constructor parameters. The portfolio overview page doesn't present errors on loading thanks to the mock methods implemented, but now working on issues related to fund deposit. Still can't deploy the app due to the Trading View API key. 

2024-06-17 Mon: Talked with Theo regarding the Trading View advance charts key, which is required for the trading module. Added other market and context indexer mock calls for the Portfolio Overview and Portfolio Marging Manager components. Working on fixing the formatTimestamp error that appears when changing to the Harmony chain. 

---
2024-06-14 Fri: Added market, context indexer client, and engineClient mock calls. Fixed nextjs.config file/webpack cache issue. Need a [Traving View advanced charts](https://www.tradingview.com/charting-library-docs/) API key to solve charting_library error that is blocking the App building process.

2024-06-13 Thu: Worked on engineClient, indexerClient, and subaccount mock calls. Had issues with the Trade app's local build. The issue is related to the trading page, which is accessing a dts-bundle-generator module that can't be resolved. Working on workarounds.

2024-06-12 Wed: After trying different approaches to handle the methods specific to the Harmony chain without affecting the functionality of the existing components on Vertex's Trade app (like creating a separate HarmonyVertexClientContextProvider while keeping the existing VertexClientContextProvider), was able to find a more [straightforward approach](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2) that will help a gradual migration of each method that calls Vertex endpoints. On the data package (@vertex-protocol/web-data), created a harmonyClient module that replicates the structure of the VertexClient class but added the isHarmony attribute to check on what chain the app is working and also included the harmonyClient on VertexClientContext, making it available to the whole app. Made changes on a subaccount and quotePrice hooks to call harmonyClient methods if the isHarmony attribute is true. Still had issues deploying the app on fly.io, and testing the build script locally also didn't work (having issues with CSS directives).    

2024-06-11 Tue: Continue working on mocking [Vertex SDK methods](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/2). Had issues deploying the current Vertext version on fly.io, working on fixing the configuration issues. 

2024-06-10 Mon: Started working on Vertex Client SDK Mock for Vertex app monorepo and also working to deploy the first version of the Trade App on fe.country.  

---
2024-06-07 Fri: Progress on the Vertex porting to Harmony One has encountered a roadblock due to the Vertex mono-repo's dependency on the Vertex-typescript-sdk for querying and executing data related to spot, perp, market, and contracts. The mono-repo utilizes this package to retrieve crucial information, including portfolio chart data, bridge token balance, spot balance, staking state, account staking state, and latest perp prices, among 125 queries. Additionally, have implemented an [input validator](https://github.com/harmony-one/defi_greeks/pull/1) for all POST endpoints in the defi_greeks API to ensure data integrity.    

2024-06-06 Thu: Deployed defi_greeks API to fly.io. [Added](https://github.com/fegloff/defi_greeks/pull/1 ) fly.io configuration, environment, and logger logic, and also [API_DOC](https://github.com/harmony-one/defi_greeks/blob/main/API_DOCS.md) markdown documentation. Kept working on the Vertex Trade App, but still having issues retrieving account information.

2024-06-05 Wed: Implemented the [first version of the defi_greek API](https://github.com/fegloff/defi_greeks/pull/1) with the following endpoints: _/concentrated-liquidity_ (Calculates greeks for concentrated liquidity positions in DeFi protocols), _/squeeth_ (Calculates greeks for Ethereum power perpetual contract positions), _/calculate_greeks_ (Calculates option greeks based on input parameters) and _/health_ endpoints. 

2024-06-04 Tue: Reviewed defi_greek repo, which contains a Rust library with functions to calculate various risk measures and greeks for financial derivatives, including perpetual contracts, options, and concentrated liquidity positions. Working on enabling a webservice (although I have yet to experience with Rust) that exposes these risk calculation functionalities to other applications, contracts, or systems.

2024-06-03 Mon: Kept working on the Vertex Trade App, reviewing contract handling and external API calls using the @tanstack package. The app is not retrieving any financial information (as expected), but also neither account info (e.g. wallet balance), working on that. Also, [forked](https://github.com/fegloff/defi_greeks) the defi_greeks repo and started reviewing perpetuals/liquidity positions in Rust.

---
2024-06-02 Sun: Working on reviewing the Portfolio page on the Trade app. 

2024-06-01 Sat: Deployed Vertex contracts on Harmony's mainnet and added [multichain deployment support](https://github.com/fegloff/vertex-contracts/pull/1). Linked clearinghouse, spotEngine, perpEngine, endpoint, and arbAirdrop contracts to Trade app. Using this [contract](https://www.coingecko.com/en/coins/harmony-horizen-bridged-usdc-harmony
) for ONE_USDC token 

2024-05-31 Fri: I was sick
 
2024-05-30 Thu: Finished integrating Harmony's [Mainnet and testnet](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/1) as supported chains for the Trade app. Continued working on the Trade app integration.

2024-05-29 Wed: Deployed 1Bot latest changes, and fixed [openai issue](https://github.com/harmony-one/HarmonyOneBot/pull/362) with system message which limits completion to 100 words. Kept working on trade app porting, had progress on enabling harmonyTestnet. 

2024-05-28 Tue: Fixed simultaneous command calls on 1Bot. When commands run simultaneously, the message context could get mixed, and llms model requests get mixed as well. The solution was to create a single endpoint that handles all llms requests and redirects the request to the respective model resource (as python/flask defined namespace architecture) on harmony-llm-api. This solution requires normalizing streaming handling for Vertex/Gemini models on harmony-llm-api and 1Bot. Now, when a simultaneous command request is handled, each model will be managed by the corresponding LLMs. It will be deployed to 1Bot later today.

2024-05-27 Mon: Deployed GPT-4o model to 1Bot. The following commands and prefixes will work with gpt-4o: _/ask, /gpt, /new, and a. and dot prefixes_. The command _/gpt4_ works for gpt4 model and the command _/gpt32_ for gpt-4-32k model. Fixed an issue with edit telegram messages when processing a stream completion. Also, updated Grammy to the latest version (v1.23.1). Finally, still have issues with simultaneous command calls, and successfully tested a solution on the harmony-llm-api backend that will be implemented tomorrow.

---
2024-05-24 Fri: Fixed 1Bot multiple command handling due to context mixing on llms API calls. Also, added the [Openai GPT-4o model](https://github.com/harmony-one/HarmonyOneBot/pull/362), linked to /gpto command.

2024-05-23 Thu: Fixed chains configuration issues. Had issues linking the Harmony chain to the wallet connection on the navigation component; working on it. 

2024-05-22 Wed: Kept working on adding [Harmony chain and One token](https://github.com/fegloff/vertex-web-monorepo-snapshot/pull/1) to the Trade App and added HarmonyTestnet chain.

2024-05-21 Tue: Continued working on Vertex's trade app, adding Harmony chain and One token. After Casey's review, sent PR to the Protofire team regarding the explorer block filter and worked on finding the development server issue on the Swap Interface app.

2024-05-20 Mon: Sent [PR](https://github.com/protofire/interface/pull/5) to change tooltip text on Swap Interface (_Network Fee are paid to the ~~Ethereum~~ Harmony network to secure transactions_). This task was delayed due to local deployment issues, which were tested with different node/yarn configurations on Mac M1 and Windows OS, with no success. There is an issue when running GraphQL scripts due to two files missing. The Protofire team sent me the missing files (src/graphql/data/schema.graphql and src/graphql/thegraph/schema.graphql) and the issue was resolved. Also, worked on adding Harmony metadata/token to the Vertex common package and trade app (will send a PR on Tuesday).  

2-Week Deliverables by 2024-05-20:
Finish Claude's tool implementation to have 1Bot ready for the Defi/AI project. Support Hyperlane and Dune implementation and work on the Arbitrum wallet finder. 

---
2024-05-19 Sun: Completed the required explorer updates: _let's not show/flash empty blocks and hide "network utilization_. The changes affect mobile and desktop versions. Sent the corresponding [PR](https://github.com/fegloff/bs-frontend/pull/1) to Casey for review.

2024-05-17 Fri: Finished the required explorer updates: _autofocus on the search input field when loading, remove the red "testnet" label at the left top corner, capitalize "Harmony Testnet Explorer," spell out "txn hash" -> "transaction hash," "ETH" -> "ETH / ONE address," and remove "Dim" mode option_. Sent the corresponding [PR](https://github.com/protofire/bs-frontend/pull/13). 

2024-05-16 Thu: Despite initial challenges with the Explorer local environment, the issue was that I was working on the wrong repo. Once forked the correct one ([protofire/bs-frontend](https://github.com/protofire/bs-frontend), I was able to make progress. Had personal matters to attend to.   

2024-05-15 Wed: Continued working on Vertex's trade app porting and updating the Explorer app. However, had issues with the local environment with the corepack package and am working on fixing it.  

2024-05-14 Tue: Kept reviewing Vertex's trade app architecture/logic. 

2024-05-13 Mon: Deployed all Vertex contracts to Harmony Testnet. Currently, reviewing trade app architecture and looking at how contracts, GraphQL, and API calls are handled.

---
2024-05-10 Fri: Created the first version of the [deploy script for Vertex contracts](https://github.com/fegloff/vertex-contracts/pull/1) to the Harmony Testnet network and added comments to some contracts. Also, deployed locally mono-repo-apps and started checking out trade app architecture.

2024-05-09 Thu: Worked on porting contracts to the Harmony chain, checking all contracts, and creating a deploy script (work in progress). Also, talked with a Protofire representative regarding swap-interface local deployment issues.

2024-05-08 Wed: Started working on Vertex porting; they had a [contracts repo](https://github.com/vertex-protocol/vertex-contracts) and web apps [mono repo snapshot](https://github.com/vertex-protocol/vertex-web-monorepo-snapshot), which includes trade, dashboard, and marketing apps. 

2024-05-07 Tue: Fixed one- and two-letter domain [issues in 1.country](https://github.com/harmony-one/1-country.frontend/pull/217), skipping Web2 registrations because we already control the domains. Also, fixed certificate handling, checking if the certificate needs to be renewed before creating it. After being reviewed by Artem, changes were published. Also, kept working on the swap site update. 

2024-05-06 Mon: Checked the Hyperlance documentation; they provide the contracts on local and remote chains we want to bridge with. Talked with Yuriy about deploying Hyperlane on Harmony. Also, made some text/URL changes on the [Bridge site](https://github.com/harmony-one/layerzero-bridge.frontend/pull/26) and kept working on the requested changes on the Swap webpage.

---
2024-05-03 Sun: Reviewed 1Bot logging logic. 

2024-05-04 Sat: Started working on the tooltip text change on the swap site. 

2024-05-03 Fri: Theo updated me on the next task: I had to work on the Arbitrum network. I also kept revising the Hyperlance and worked on the requested changes on the Harmony Swap site.

2024-05-02 Thu: Tested and deployed token base security to harmony1bot and harmony-llms-api. Disabled translation prefixes on 1Bot, leaving only translation commands available. Reviewed and discussed harmony.one/defi architecture. Started reviewing [hyperlanexyz ecosystem](https://hyperlanexyz.notion.site/Hyperlane-Ecosystem-1e6d8175baf44ed88502cfba91becc45)

2024-05-01 Wed: Included [token-base security](https://github.com/harmony-one/harmony-llm-api/pull/20) for harmony-llms-api endpoint, using bearer scheme and also httpOnly for web app calls. Updated 1bot to use the new security scheme and talked to Nagesh about updating the iOS app. Fixed issues with streaming on anthropic models and the is_supported method on anthropic tools. Changes deployed on 0Bot and harmony-llm-api-dev.fly.dev. 

2024-04-30 Tue: I included the ToolBox class for related tools and added the CoinGecko toolbox with retrieving token prices and token ID tools. It is currently on 0Bot for testing.  

2024-04-29 Mon: Tested and deployed to 1Bot /ctool and /stool commands, which allow access to the Anthropic tool feature. Started working on integrating AI into harmony.one/defi project.

---
**2-Week Deliverables by 2024-04-26:**
Finish harmony1bot mayor refactoring to help integration with subagents and plugins (like voice commands) and add other subagents like PDF parsing. Also, create a demo of [anthropic tools](https://docs.anthropic.com/claude/docs/tool-use) on harmony1bot.

2024-04-26 Fri: Finished implementing the tool logic on [harmony-llm-api](https://github.com/harmony-one/harmony-llm-api/pull/19) and enabled the ticker symbol info retriever tool, which works with multiple ticker symbols. Also finished implementing the logic on [1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/362) and enabled the /ctool and /stool commands. Currently testing on 0Bot. Finally, the /new command logic was updated to refresh the conversation per active bot.

2024-04-25 Thu: Day off due to flu.  

2024-04-24 Wed: Day off due to flu.  

2024-04-23 Tue: Refactored [tools logic](https://github.com/harmony-one/harmony-llm-api/pull/18), enabling multiple tools per call. Created ToolBase, YahooFinanceTool, and AnthropicHelper classes.  

2024-04-22 Mon: Kept working on enabling tools for Anthropics models. I enabled multiple tool calls, e.g., when asking for multiple ticker symbols. Updated Anthropic packager version.  

---
2024-04-19 Fri: Added [tools logic on 1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/362) and /ct command. Created tools endpoint for Claudes models, and kept working on including a ticker symbol tool. 

2024-04-18 Thu: Finished implementing the [/pdf and /ctx commands](https://github.com/harmony-one/HarmonyOneBot/pull/362) and added logic to allow the same command to be shared between different bots. Also, started working on Claude's tool feature. 

2024-04-17 Wed: Deployed the latest changes, including Gemini 1.5 to 1Bot. Started working on adding pdf and ctx commands. I had food poisoning and took the rest of the day off. 

2024-04-16 Tue: Refactored [harmony-llms-api](https://github.com/harmony-one/harmony-llm-api/pull/17) to work with the latest Gemini packages in order to support Gemini 1.5. Also added [/g15 and /gemini15 commands](https://github.com/harmony-one/HarmonyOneBot/pull/362) to 1Bot, and refactored the session object, and deleted unused modules. 

2024-04-15 Mon: The Llama SubAgent now supports [PDF and multiple URLs](https://github.com/harmony-one/HarmonyOneBot/pull/362). It has Been tested with OpenAI and Gemini commands. Also, improved subagent performance by removing unnecessary logic. The Gemini 1.5 model has been checked and is in Preview mode.  

---
2024-04-12 Fri: Improved user prompt to include subagents output and avoid standard openai error "_I'm sorry, but as an AI language model, I don't have the ability to browse the internet or access external websites in real-time_". Also, updated the bot's context to include subagent capabilities. Here is the new context: "_You are an AI Bot powered by Harmony. Your strengths are AI API aggregation for chat, image, and voice interactions. Leveraging a suite of sophisticated subagents, you have the capability to perform tasks such as internet browsing and accessing various services. Your responses should be adaptable to the conversation while maintaining brevity, ideally not exceeding 100 words._". Finally worked on adding the PDF subagent. 

2024-04-11 Thu: Tested new subagent feature and refactored bot modules. [Fixed issues](https://github.com/harmony-one/HarmonyOneBot/pull/362) with multiple URL inquiries, running URL subagent when replying to a message with an URL.

2024-04-10 Wed: Finished refactoring the openai module into a llmsBase-derived subclass; also finished the first iteration of the [web crawler subagent](https://github.com/harmony-one/HarmonyOneBot/pull/362) and deployed it on harmony0bot for testing. Now, every model that has the subagent can include web crawling on its completion. Currently, Gemini and Openai models have it.  

2024-04-09 Tue: Continued working on AI bots refactoring and adding subagent logic.

2024-04-08 Mon: Keep working on the llamaIndex subAgents for harmony1bot.

---
2024-04-05 Fri: Finished openAI, and Dalle bots as a [derived class of llmsBase](https://github.com/harmony-one/HarmonyOneBot/pull/362), added session handling, and kept refactoring AI bots. Started working on llamaAgent (collection handling for PDF and URL) so each AI bot can use it.

2024-04-04 Thu: Added minimum balance to openAI bot for postpaid commands. Continued [code refactoring](https://github.com/harmony-one/HarmonyOneBot/pull/362) on Harmony1Bot to ease subagents integration: added llms bot base class (llmsBase) and claudeBot, vertexBot, and llmsBot derived classes. Will continue with the refactoring of openaiBot and converting PDF/URL logic to an subagent-like class. 

2024-04-03 Wed: Fixed PDF/URL parsing issues due to a vector database client/server version mismatch. On [Harmony1bot](https://github.com/harmony-one/HarmonyOneBot/pull/361), updated Grammy package to the last stable version and made code refactoring to get the latest version of the getChatAdministrators method to fix the database client isGroupWhitelisted method. Had to update the nodejs version to 20 on the Dockerfile. 

2024-04-02 Tue: Fixed the new command logic and the [minimum balance](https://github.com/harmony-one/HarmonyOneBot/pull/361) to use llmsBot models. Also, fixed the token counter for Anthropopic stream completions. Found the problem with the group whitelisting not working. Finally, fixing an issue with Chromadb that affects PDF/URL handling.  

2024-04-01 Mon: Added conversation per model discrimination on [Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/360) (deployed to harmony1bot). Now, you can have one conversation per model. Also added the /o command to work with the opus model. Finally, worked on team reviews.  

---
**2024 Q1 Review (12 hours)**

I added Harmony1Bot features: OpenAI's DALL-E 3, Vision command, and various models from Claude and Vertex. I implemented code snippets support, an Inscription lottery, voice command functionality, and fixed payment logic while upgrading the bot's performance and stream completion. Additionally, I made notable contributions to Harmony-llm-api by adding endpoints for Whisper, Anthropic, PDF inquiry, and Gemini, along with implementing streaming logic.

I contributed to the 1.country project by adding Inscription image rendering for Telegram's Image subscriptions. For the Social Map project, I implemented Whisper logic, added a markers endpoint, refactored the codebase with TypeScript, and improved the app's styling and state management. Lastly, I made enhancements to the Human Protocol project (h.country) by optimizing the Welcome and UserPage route components and improving the app's overall logic.

In optimizing harmony1bot performance, I tackled various technical challenges with targeted features. This included efficiently implementing an image generation queue to handle multiple DALL-E 3 requests and resolving prompt interpretation errors. I also enhanced stream completion for Anthropics and Vertex models, improving user experience by reducing response times. Additionally, integrating voice-command functionality streamlined user interactions, with features such as command reuse improving overall usability and user experience.

---
2024-03-29 Fri: Day off

2024-03-28 Thu: Day off

2024-03-27 Wed: Added the [CV analysis](https://github.com/harmony-one/harmony-llm-api/pull/16) endpoint to harmony-llm-api. The endpoint returns the score with the reasoning and three recommendations. Fixed word cutting in Anthropic and Gemini completion and cleaned token information on the completion response. Finally, checked the completion agents feature for Anthropic. The feature is brand new, but a [GitHub repo](https://github.com/cxbxmxcx/GPT-Nexus) just added the agent logic for [Anthropic](https://github.com/cxbxmxcx/GPT-Nexus/commit/89694a0bb978e0db1f7e00807bf1bb1d227422b6). We can check that and see how we can include it on harmony1bot. 

2024-03-26 Tue: Fixed [Anthropic namespace](https://github.com/harmony-one/harmony-llm-api/pull/15) key issue on the harmony-llm-api backend and fixed the URL params default values on the PDF inquiry endpoint. It now serves ONEResume app. Created the harmony0bot database on [elephantsql](https://api.elephantsql.com/), a free service, to deploy the Gemini command for testing. Also, the [LLM chat conversation](https://github.com/harmony-one/HarmonyOneBot/pull/359) was normalized to avoid errors when passing from/to Claude's and vertex models. Finally, prepared 1Q self-assessment

2024-03-25 Mon: Fixed the [price calculation logic](https://github.com/harmony-one/HarmonyOneBot/pull/359) of the Gemini command on Harmony1Bot (deployed to harmony0bot)  and a [PDF inquiry endpoint](https://github.com/harmony-one/harmony-llm-api/pull/15) to harmony-llm-api to use Claude's models. The endpoint accepts a URL of the PDF file and a PDF object. Anthropic doesn't support embeddings, so all inquiry requests need to include the PDF. In case multiple inquiries are required, we can use the openai embedding endpoint available on harmony-llm-api

---
2024-03-22 Fri: Continue working on generative-models.demo, keep having issues deploying locally and in Google Colab. Also fixed the Gemini command completion text on Harmony1Bot. 

2024-03-21 Thu: Added the generative-models.demo repo to Google Colab to have access to the GPU processor. Also, working on configuring the new environment and adding the a flask endpoint.

2024-03-20 Wed: Keep working on Stable video 3D integration. Have issues installing the model on my Mac M1 (Nvidia-related error). Finished the token counter [on harmony-llm-api](https://github.com/harmony-one/harmony-llm-api/pull/14) and added logic on Harmony1Bot (changes have yet to be pushed to Harmony0bot).

2024-03-19 Tue: Worked on Stable Video 3D, [forked the repo](https://github.com/fegloff/generative-models.demo), set up the dev environment, and installed the model. Also worked on adding a token counter for Gemini requests.

2024-03-18 Mon: Improved [error handling](https://github.com/harmony-one/harmony-llm-api/pull/13) on the harmony-llm-API backend; still need to make some changes on Harmony1Bot to display the proper error message (for instance, Claude's Sonnet model usually returns an overloaded_error but the bot shows "Error handling your request"). [Deployed to Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/358) Opus (/c, /claude, c.), Sonnet (/sonnet, /s) and Hariku (/hariku, /h) commands, and removed emoji on voice command error message. Added the Gemini model to [harmony-llm-api](https://github.com/harmony-one/harmony-llm-api/pull/14) and [Harmony0Bot](https://github.com/harmony-one/HarmonyOneBot/pull/359); still need to add pricing on HarmonyBot to deploy to production. Started reviewing [Stable video 3D](https://stability.ai/news/introducing-stable-video-3d).

---
2024-03-15 Fri: Fixed conversation history, added Hariku model (/haiku, /h), update Anthropic models pricing, and added [stream completion](https://github.com/harmony-one/HarmonyOneBot/pull/358) for Opus and Sonnet models. However, due to wording truncation, kept the Hariku model as rest completion.

2024-03-14 Thu: Added [stream completion](https://github.com/harmony-one/harmony-llm-api/pull/13) support for harmony-llms-api, and fixed the missing Anthropic module error after deploying. Also, updated Opus and Sonnet prices on [Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/357) and started working on stream completion logic. 

2024-03-13 Wed: Fixed Anthropic backend issue with [completion format](https://github.com/harmony-one/harmony-llm-api/pull/13) and working on deploying issues with the anthropic library. Added opus (/claude, /opus) and sonnet (/claudes, /sonnet command) to [Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/357). Fixed AI conversation error after prompt doesn't receive completion, and fixed action message infinite loop after error for LlmsBot and OpenAI bot.   

2024-03-12 Tue: Added Anthropic's Claude create message endpoint in [harmony-llms-api](https://github.com/harmony-one/harmony-llm-api/pull/13). Also, added /claude command on the Harmony1Bot local test environment.

2024-03-11 Mon: Updated the recharge message on Harmony1Bot due to some confusion regarding what token to send the funds. Also [SdImagesBot and QRCodeBot](https://github.com/harmony-one/HarmonyOneBot/pull/356) were disabled due to the shutdown of the Stable Diffusion servers. Finally, worked on enabling [live transcription](https://github.com/harmony-one/1/pull/14) on the Social Map app and configured a test account on the anthropic AI model. 

----
2024-03-08 Fri: Fixed an issue with the Social Map app that sent the [wrong file format](https://github.com/harmony-one/1/pull/13) to the harmony-llm-api for voice transcript.

2024-03-07 Thu: Keep researching Peapods Finance. Here is a good [video](https://www.youtube.com/watch?v=fW87F-l30KI) explaining how the pods work. Also, here is the last [Audit report](https://reports.yaudit.dev/reports/01-2024-Peapods/), but their repo is private. 

2024-03-06 Wed: Started researching Peapods Finance. They do not share the contracts; the only contract shown is their rewarded token, PEAS.

2024-03-05 Tue: Checked Voice AI app functionality after malfunctions reports. Tested the app live and locally, checked the Sentry log where some issues were found, and discussed them with Aaron; they seem to be isolated issues. Will keep monitoring the app in the following days. Also, I worked on a [hotfix](https://github.com/harmony-one/h.country/pull/105) on h.country where a private key import was leaked, and the filter was showing full-text tags.  

---
2024-03-01 Fri: Finished code refactoring and Typescript migration of [ONE Map app](https://github.com/harmony-one/1/pull/12): created ImageCarouselComponent and MemoCarouselComponent, also fixed recording logic.

2024-02-29 Thu: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/103): Updated the logic of the clear query param. Also worked on the following [tasks ONE Map](https://github.com/harmony-one/1/pull/11): Refactored MapViewComponent, by creating MapMarker component while migrating the code to Typescript.

2024-02-28 Wed: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/101): Updated the display of link actions because most of the time, it took two lines to show 0/B1B1 1760886692 x/17608866 (from address, username, type/username). The proposed change shows the address and the type/username info (0/B1B1 x/17608866). Also, updated the action type color, showing blue if the from address is the same as the page wallet address (key) and yellow otherwise. Also, updated the href to navigate to the payload URL; Fixed filter panel when clicking actions' from/to address. Also worked on the following [tasks ONE Map](https://github.com/harmony-one/1/pull/10): Added a UserContext to handle user wallet address, and useStorage hook to handle local storage.

2024-02-27 Tue: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/99): Updated the h.country menu option logic, setting the filter mode to 'All'; updated the selection logic of actions' from/to address, adding the updated page address to the action filter and changing the filter mode to 'address.'

2024-02-26 Mon: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/96): Updated the check-in message display logic. There is an issue with some check-in action messages (when syncUserLocation) that were unable to get the location address information, showing an empty message. For those cases, we can try to fetch the information again (calling the nomination API again), and with a second not successful operation, simply not store the check-in on Firebase. Updated the UserPage action filter look and fee. Added onClick logic to the h.country menu option; when clicked, it navigates to the UserPage with no active filters.

---
2024-02-25 Sun: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/90): Fixed [object][object] rendering on check-in action messages; fixed runtime error on intersection observer; added Firebase doc's ID to Action Type to set a unique key to every UserAction component to avoid continuing rendering. 

2024-02-24 Sat: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/89): Added user's emoji reaction to action messages; added lazy load and intersection observer to handle action list rendering. Also, I worked on [Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/353), where I fixed suffix issues and added one inquiry limitation per image on each chat.

2024-02-23 Fri: Worked on the fowolling [tasks on h.country](https://github.com/harmony-one/h.country/pull/71): Disable scroll horizontally on mobile; make text on the selection page (/hash) bigger; limit 10 chars for a tag, and locations in the hashtag section; limit 15 chars for the tag on message section; fix slash and hashtag icon; remove new user self-tagging; fixed location action message overlap; updated URL char truncation; added geolocation after the third topic selected on the welcome page; fixed menu address rendering.

2024-02-22 Thu: Worked on the fowolling [tasks on h.country](https://github.com/harmony-one/h.country/pull/71): Updated action type (self/other) color logic; updated /new route logic and fixed double wallet creation; fixed font styling (grey color and size); fixed manual topic selection tag type logic; update Grommet theme and styled component styling. Also worked on [SocialMap app](https://github.com/harmony-one/1/pull/8), finishing the following tasks: updated footer styling and marker callout styling. 

2024-02-21 Wed: Worked on the fowolling [tasks on h.country](https://github.com/harmony-one/h.country/pull/55): Updated UserPage styling; fixed tags and URL logos cut off and added isUserPage logic; updated filter panel styling and added #one and @ai filter logic; added a topic selection limit on the welcome page; added rendering logic on the welcome page when the topic query param is set.

2024-02-20 Tue: Worked on the following [tasks on h.country](https://github.com/harmony-one/h.country/pull/37): Fixed multiple wallet creation after topic selection on the hash route component, which affects actions rendering on the UserPage component. Updated the UserPage route component styling, including the messages section, texts, and styling when no address is set. Updated /hash look and feel and topic list. Updated recurrent user logic on topic selection. Fixed issues when no topic query param is on /hash route. Update redirect logic for new users to /hash route component.

2024-02-19 Mon: Worked on [h.country](https://github.com/harmony-one/h.country/pull/22). Changed the number of topics to select from 4 to 3. Added logic that creates a Tag Action for each selected topic and a Tag Action from the user to himself. Updated slash and hash colors: blue for himself and yellow for others. Pending green for verified type. Updated HeaderList component to show a 3 x 3 grid of tags in order by frequency. 

---
2024-02-16 Fri: Fixed [dark theme logos rendering](https://github.com/harmony-one/h.country/pull/12), and added meta tag logic. Added dark/light theme logic, but leave dark theme on by default. Fixed mobile full screen redering. 

2024-02-15 Thu: Keep working on the [Human Protocol](https://github.com/harmony-one/human-protocol/pull/20) user interface, updating the welcome page look and feel. Refactored Topic's logo prefetch logic. Added the Nunito font and updated the Welcome and Messages route component's styling.

2024-02-14 Wed: Worked on user interface improvements for the [Human Protocol](https://github.com/harmony-one/human-protocol/pull/18) project. Updated the Welcome route component by adding and grouping topics, changing topic container look and feel, and isSelected logic. 

2024-02-13 Tue: Worked on fixing the [Whisper demo](https://github.com/harmony-one/web-whisper.demo) to make it compatible with Chrome and Safari for mobile by updating codec handling for Safari and audio chunks logic. Here is a working [demo](https://webpage-whisper-demo.fly.dev/).  

2024-02-12 Mon: Worked on the [Whisper demo](https://github.com/harmony-one/web-whisper.demo) on React. Finished the first version of the WebApp that records voice memos and uses Openai's Whisper model to transcribe the audio. Also, added a Web Speech API transcribe option.

---
2024-02-09 Fri: [Refacored SocialMap app](https://github.com/harmony-one/1/pull/7), added the src folder modularizing components, updated the markers interface and logic, and added the Posts component.

2024-02-08 Thu: Finished the API call to the [whisper endpoint](https://github.com/harmony-one/1/pull/5). Fixed multi-voice memo recording issue and updated the code logic from expo to react-native CLI.

2024-02-07 Wed: Worked on the whisper endpoint on [harmony-llm-api](https://github.com/harmony-one/harmony-llm-api/pull/12) backend and API call on the [SocialMap app](https://github.com/harmony-one/1/pull/3). Added [markers API](https://github.com/harmony-one/1/pull/2). 

2024-02-06 Tue: Worked briefly on a Farcaster project. Reviewed the best way to implement a [Farcaster Hub](https://docs.farcaster.xyz/developers/) (like an Ethereum node), which is required to create apps on top of Farcaster and started working on a social map app on react-native.

2024-02-05 Mon: Started briefly working on v.country, a website that records and transcribes voice memos using Openai's Whisper modal. Started working on a [Farcaster](https://docs.farcaster.xyz/) implementation. 

----
2024-02-02 Fri: Added censorship check to dalle text and voice command and included content_policy_violation for [openAI](https://github.com/harmony-one/HarmonyOneBot/pull/353) errors. Also, added refund handling on openAIs and voiceCommand bots. Finally, disabled the inscription lottery.

2024-02-01 Thu: Updated Inscription payload to include user info (username, walletAddress); also added logic to delete the [share button](https://github.com/harmony-one/HarmonyOneBot/pull/353) after a successful Inscription. Updated [dot country](https://github.com/harmony-one/1-country.frontend/pull/216) to work with new inscription payload to hide Telegram's bot token. 

2024-01-31 Wed: Finished 1.country rendering of Telegram/Image subscription on [dot country](https://github.com/harmony-one/1-country.frontend/pull/216). Update [Inscription call data](https://github.com/harmony-one/HarmonyOneBot/pull/353) and fix prefix issues with Dalle and Stable Diffusion.

2024-01-30 Tue: Finished [inscription logic](https://github.com/harmony-one/HarmonyOneBot/pull/353) and progess messaging handling for image and prompt inscription on Harmony1Bot. Also, worked on 1.country with the [Telegram's inscription integration](https://github.com/harmony-one/1-country.frontend/pull/216).

2024-01-29 Mon: Worked on integrating [Inscription logic on Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/353). Created the share button and 0-cost transaction with call data and added initial logic. 

----
2024-01-26 Fri: Cleaned the [prompt-generated text](https://github.com/harmony-one/HarmonyOneBot/pull/351/commits/949701af242848e65990691eef4b73499df433c8) on voice command and updated voice command duration up to 30 seconds. Added a [share button](https://github.com/harmony-one/HarmonyOneBot/pull/353) to Dalle's generated images for inscription logic. 

2024-01-25 Thu: Added payment logic for whisper on voice-command services. [Improved user experience](https://github.com/harmony-one/HarmonyOneBot/pull/351) by adding voice command reuse to avoid the user repeating the command on each interaction. Updated the conversation queue to store the output format (voice, text) and msgId (to replace the progress message with the completion).   

2024-01-24 Wed: Added the [image (dalle) and talk command](https://github.com/harmony-one/HarmonyOneBot/pull/351) to the voice-command bot. For dalle, the user has to send a voice note starting with the command image and then the prompt. When a user sends a voice note with the command talk, the AI completion returns as a voice note.

2024-01-23 Tue: Updated the payment logic for pdf/URL web crawling services. Added [voice-command](https://github.com/harmony-one/HarmonyOneBot/pull/351) functionality for chat GPT and vision features. With voice command, the user sends a voice note starting with the command ('ask' for chat GPT, 'vision' for vision) with the prompt, and the bot generates the completion. For Vision, the voice note has to be a reply to an image. 

2024-01-22 Mon: Fixed [payment issues](https://github.com/harmony-one/HarmonyOneBot/pull/350) with dalle and Chat GPT commands. The app was storing the token and price usage for the conversation but was not using the token usage information to calculate the input token price. The new DALLE 3 implementation requires the price to be handled as cents.

----
2024-01-19 Fri: Worked on fixing whitelist issues and payment issues. Fixed [whitelist issues](https://github.com/harmony-one/HarmonyOneBot/pull/350) with private chats and the updated whitelist environment variable. Checked the implementation of whisper on Harmony1Bot. 

2024-01-18 Thu: Fixed new command prefix error when the new prompt was empty. Refactored command handling on openAi, llms, and 1Country. Added [vision completion context](https://github.com/harmony-one/HarmonyOneBot/pull/350) to provide complete responses within a 100-word limit

2024-01-17 Wed: Fixed prompts with a [code snippets](https://github.com/harmony-one/HarmonyOneBot/pull/350) that were handled as URLs and produced an error messages. Fixed an error with vision calls on group chat by requiring vision command on images reply.

2024-01-16 Tue: Added streaming completion to [vision logic](https://github.com/harmony-one/HarmonyOneBot/pull/348). Also, added /vision command that allows the user to inquire about multiple image URLs. Didn't add vision prompts/completions to the bot conversation because it uses different models, and the content key of the body parameter has a different scheme. 

2024-01-15 Mon: Worked on [deleting prefixes with familiar words](https://github.com/harmony-one/HarmonyOneBot/pull/349) to increase user experience; the removed words were 'am', 'be', 'ny', 'ha', 'no' from Translate bot.  [Deployed Vision on Harmony1Bot](https://github.com/harmony-one/HarmonyOneBot/pull/348) as a chatCompletion, not as a part of a conversation, due to a different JSON scheme for the content key. On Tuesday, will work on including in the bot conversation the vision's prompt and completion. Also, will add chunk prompting (stream) and /vision command where the user can send an image URL with a prompt.

---

2024-01-12 Fri: Started working on Vision integration. Fixed [i prefix](https://github.com/harmony-one/HarmonyOneBot/pull/347) bug. 

2024-01-11 Thu: Updated [allstats and stats reports](https://github.com/harmony-one/HarmonyOneBot/pull/346) including one-time users. Added [/i command](https://github.com/harmony-one/HarmonyOneBot/pull/345) to dalle-3.

2024-01-10 Wed: Added and updated weekly and total KPIs to the [stats report](https://github.com/harmony-one/HarmonyOneBot/pull/346), working on adding new users report. Worked on adding images command to dalle-3.

2024-01-09 Tue: Added prefixes and commands to the [dalle-3 logic](https://github.com/harmony-one/HarmonyOneBot/pull/345) and updated the SD image logic. Checked the inconsistencies reported on the bot stats report.

2024-01-08 Mon: Integrated [Dalle-3](https://github.com/harmony-one/HarmonyOneBot/pull/345) to Harmony1Bot with session image generation queue and message status.

---
2023-12-25 Mon - 2024-01-05 Fri: Paid time off.

---
2023-12-22 Fri: Added speech recognition (speech-to-text) to [voiceOn prototype](https://github.com/harmony-one/x/pull/412), and worked on [llms endpoint](https://github.com/harmony-one/harmony-llm-api/pull/11). Deployed to HarmontOneBot dev /alias /aliases command implementation.  

2023-12-21 Thu: Sergey and Yuriy help fix local deployment issues of [layer zero bridge](https://github.com/harmony-one/layerzero-bridge.frontend/pull/22). Added [add document endpoint](https://github.com/harmony-one/harmony-llm-api/pull/11) on the llms backend for the VoiceOn prototype. Found a local on-device vector database for [Swift Apps](https://github.com/Dripfarm/SVDB) to be tested for the VoiceOn prototype. Worked on [alias/aliases command](https://github.com/harmony-one/HarmonyOneBot/pull/344) for HarmonyOneBot. 

2023-12-20 Wed: Working on fixing issues with the configuration of the local development environment for layer zero bridge look and feel updates. Configured local development environment for VoiceOn prototype.

2023-12-19 Tue: Started working on [VoiceOn prototype](https://github.com/harmony-one/x/tree/main/voice/x.on), exploring Chromadb embeddings for voice transcript. Also started working on the [bridge styling](https://bridge.harmony.one/erc20) update. Supported 1.country with a domain registration issue.

2023-12-18 Mon: Worked on [AppConfig unit tests](https://github.com/harmony-one/x/pull/404), reaching 90% coverage. Had to create the RelayAuth protocol to enable RelayAuth dependency injection for unit tests.

----
2023-12-15 Fri: Worked on unit tests for [DataFeed class](https://github.com/harmony-one/x/pull/394/) after new refactoring, reaching 98,9% coverage. Also, worked on [AppConfig unit tests](https://github.com/harmony-one/x/pull/396) reaching 84.9% coverage. 

2023-12-14 Thu: Worked on [AppConfig unit tests](https://github.com/harmony-one/x/pull/388). For unit testing, refactored init and loadConfiguration functions and added an extension to help access private methods, waiting on review after AppConfig refactoring. Finally, started working on updating the DataFeed unit tests after the latest DataFeed refactoring.  

2023-12-13 Wed: Worked on unit tests for [DataFeed](https://github.com/harmony-one/x/pull/374) and reached 99% coverage. Had to redo the unit test due to Data Feed refactoring, getting back to 99% coverage. Worked on the ActivityView unit test and had issues creating a MockContext to test the makeUIViewController function. 


2023-12-12 Tue: Added unit tests for [DataFeed](https://github.com/harmony-one/x/pull/370), [TriviaManager](https://github.com/harmony-one/x/pull/355) and ActivityView. Fixed [isSharing](https://github.com/harmony-one/x/pull/361) issues on unit tests build after refactoring.  

2023-12-11 Mon: Fixed build issues on [unit tests](https://github.com/harmony-one/x/pull/344) after OpenAI refactoring. Updated TextToSpeechConverterTests and OpenAIServiceTests unit tests. Also, added trivia ActionType unit tests. Added trivia context to string Catalog. Had issues with AppleSignInManagerTests, but I am still working on it.

---
2023-12-08 Fri: Fixed AppleTests, NetworkManagerTests, and UserTest [unit tests](https://github.com/harmony-one/x/pull/335) after KeychainService class refactoring, also update CreateUser struc adding memberwise initializer initializer. Added [unit tests](https://github.com/harmony-one/x/pull/339) for the ActionsView struct and UserAPI class. 

2023-12-07 Thu: Worked on unit tests for the Voice AI project. Improved unit tests of [AppleSignInManager class](https://github.com/harmony-one/x/pull/330). 

2023-12-06 Wed: Added Custom Instructions, Shortcode Intents and speech recognition texts to [string catalogs](https://github.com/harmony-one/x/pull/318). Worked on UserAPI [unit tests](https://github.com/harmony-one/x/pull/324). Added Custom Modes [trigger logic](https://github.com/harmony-one/x/pull/325) for Voice AI Settings. Also, worked on HarmonyOneBot issues with text-to-voice and translation commands.     

2023-12-05 Tue: Researched language localization for iOS Swift. Finally, implemented a [String Catalog](https://github.com/harmony-one/x/pull/318/) to handle language localization in a single file location. Still need to figure out what to do with the texts-related function on the Texts folder. 

2023-12-04 Mon: Finished working on [Custom Instructions View](https://github.com/harmony-one/x/pull/299). Solved user experience and styling issues, updated the logic to move the user's custom instruction input to System Settings and left Default, Quick Facts, and Interactive Tutor logic on the View. Finally, reverted [Custom Instruction View Unit Test PR](https://github.com/harmony-one/x/pull/305), manually [reverted Custom Instruction View PR](https://github.com/harmony-one/x/pull/308) and updated the More Actions menu.

---
2023-12-01 Fri: Worked on fuzz test research. Also, worked on [Custom Instructions View](https://github.com/harmony-one/x/pull/299). Users can choose between Interactive Tour, Quick Facts, Default Context, or Custom on an Active Sheet look-like view. On Monday, I will work on styling issues and User Interface behavior. 

2023-11-30 Thu: Changed review [requester logic](https://github.com/harmony-one/x/commit/00c11beced436602f8d3a99b2d6c8cb1a4774b5e) for new session button action. Also, I have started to research fuzz testing for swift projects. There are not up to date tools on the market.

2023-11-29 Wed: The PR review showed issues with published attributes that handle button actions, malfunctioning the app. [Fixed](https://github.com/harmony-one/x/pull/255) property published issues, refactored ActionsViewProtocol, ActionsView struct, and MockActionsView class.  

2023-11-28 Tue: Worked on unit tests for [ActionsView struct](https://github.com/harmony-one/x/pull/255): adding reset, play, openSettings, and closures unit tests. Fixed merge issues with the main branch after ActionsView refactoring. The PR is currently in review. 

2023-11-27 Mon: Fixed unit test errors on [AppleTest](https://github.com/harmony-one/x/pull/274) and ActionsViewTests. Added lastButtonPressed, showInAppPurchase [unit tests](https://github.com/harmony-one/x/pull/270) on ActionViewTest (67%). 

---
2023-11-24 Fri: Fixed unit tests build errors on OpenAIModelsTets, AppConfigurationTests, and SettingsBundleHelper class. Added [Unit Tests](https://github.com/harmony-one/x/pull/260) for ThemeManager (100%), ActionsView (65%), UserApi (55%).

2023-11-23 Thu: Refactored Actions View to add ActionHandler [dependency injection](https://github.com/harmony-one/x/pull/255) to ease unit testing. The changes include creating ActionHandler Protocol and ActionHandlerMock class.

2023-11-22 Wed: Fixed premium expiration date format for [settings bundle](https://github.com/harmony-one/x/pull/243). Keep working on ActionsView [unit tests](https://github.com/harmony-one/x/pull/253), and updated test logic after ButtonData attributes changed. 

2023-11-21 Tue: [Joined configuration files](https://github.com/harmony-one/x/pull/241) of target x and target Sun. Now, all shared media will be handled in x\AssetsShared.xcassets file, while each discting media (like the app logo) will be governed by x\Assets.xcassets and Sun\AssetsShared.xcassets. Also, both targets will share the configuration data with x\Info_shared.plist file. Finally, removed the date's seconds value on the premium expiration date and kept working on Unit tests for ActionsView. 

2023-11-20 Mon: Added [local time](https://github.com/harmony-one/x/pull/234) for System Settings and changed custom instruction label and fixed alignment. Worked with Rikako and Nagesh on unit tests and made some updates on ActionsView unit tests (the coverage % will be updated later today). Worked on Store ObservableObject error while running Unit tests. 

---
2023-11-17 Fri: Reviewed removed [rate limit PR](https://github.com/harmony-one/x/pull/199/), Also, added logic for multiple user taps on [Surprise button](https://github.com/harmony-one/x/pull/223) (waiting on review), adding a 0.5 seconds buffer to disable double tap, and after that new request will kill the previous one. Added [Unit Tests](https://github.com/harmony-one/x/pull/199/) for ActionsView (71%), UserAPI (52%).

2023-11-16 Thu: [Optimized mic initialization](https://github.com/harmony-one/x/pull/207) (audioSession/audioEngine) reducing lagging and user words dropping (first words sometimes were missed). Updated UI for [system settings](https://github.com/harmony-one/x/pull/208) (aligning). Worked on [Unit test](https://github.com/harmony-one/x/pull/199) for Actions View.

2023-11-15 Wed: Added [user review request logic](https://github.com/harmony-one/x/pull/193) when the user presses the new session button and the following conditions occur: pressed the button for 10th times and a random function that adds 25% probability returns true. Each time the user reaches the 10th click, the counter resets. With the help of Nagesh fixed issues in my unit test environment, allowing me to work on [ActionsView unit tests](https://github.com/harmony-one/x/pull/199). Created a new OpenAI API Key for Harmony1Bot and updated and tested the new key on the Bot and on the llm-API backend.

2023-11-14 Tue: Fixed custom instructions logic that was not resetting the conversation after custom instructions changes and fixed custom instruction duplicity. Also, fixed pause/play icon responsiveness due to a 1-second delay after the user presses the pause button.

2023-11-13 Mon: Worked on [custom instructions logic](https://github.com/harmony-one/x/pull/179) enabling the user to change the conversation context. Created app settings to store conversation context and added a Reset toggle switch to reset custom instructions to the default message. One thing to consider with the app settings is that it doesn't have a button (to replace the Reset toggle switch), and the input text field is too short for the default custom instruction text. Also, update the app font to [Dotrice Bold](https://github.com/harmony-one/x/pull/184).

---
2023-11-10 Fri: Fixed _required condition is false: IsFormatSampleRateAndChannelCountValid(format)_, added Persistence and OpenAIResponse [unit tests](https://github.com/harmony-one/x/pull/160), and Speech Recognition [unit tests](https://github.com/harmony-one/x/pull/167)   

2023-11-9 Thu: Added [unit tests](https://github.com/harmony-one/x/pull/156) for ActionHandler and AppConfig classes.

2023-11-8 Wed: Added unit tests for [getTitle](https://github.com/harmony-one/x/pull/150) (surprise Action type), Message model, and added reset and surprise action handler [unit tests](https://github.com/harmony-one/x/pull/151).

2023-11-7 Tue: Added press/hold button logic and updated say more button on [blackred Theme](https://github.com/harmony-one/x/pull/128). Finished [theme logic](Tue: https://github.com/harmony-one/x/pull/124) to ease look and feel testing. The logic includes press/hold effects for buttons, icons, and labels.

2023-11-6 Mon: Worked on play/pause transition after [button pressed](https://github.com/harmony-one/x/pull/126) and also worked on the new [red/black look and feel design](https://github.com/harmony-one/x/pull/128) and pressed/unpressed logic due to button transition and adding new foreground colors.  

---
2023-11-3 Fri: Added basic [theme logic](https://github.com/harmony-one/x/pull/124/) to help look and feel color changes. This PR adds nothing to the phone's layout because it takes the theme from AppConfig.plist. The theme changes can occur by voice commands from the user.   

2023-11-2 Thu: Worked on the user interface [look and feel](https://github.com/harmony-one/x/pull/124/commits/fac6e12cfd884974c4947fd89269ce9df6805f6e), testing new Figma designs.

2023-11-1 Wed: Fixed group whitelist and image issues (the later with the help of Yuriy) on Harmony1Bot. Updated [Voice AI context](https://github.com/harmony-one/x/pull/89), including directives, also updated Wikipedia prompt.

2023-10-31 Tue: Created unit test for Context and messages for [OpeanAIStreaming service](https://github.com/harmony-one/x/pull/102). Check group admin/owner whitelist issues and /image issues on HarmonyOneBot. 

2023-10-30 Mon: Change home grid button spacing and font size to match Figma design. Added custom instructions to message context. Update context and custom instructions to streaming functionality. Started working on the unit tests for OpenAiService module
(Implement unit testing for - OpenAiService (Context) & OpenAiService (Streaming))

---
2023-10-27 Fri: Added conversation context and updated user interface on [Voice AI app](https://github.com/harmony-one/x/pull/83). Worked on fixing harmony1Bot /vkom command.

2023-10-26 Thu: Fix conversation history issues and merge to the main branch. Fixed mobile testing issues. Update Hey Frank to the latest app version. Started working on improving audio streaming on Hey Frank

2023-10-25 Wed: Implemented conversation history for [iOS app](https://github.com/harmony-one/x/pull/70/). Had issues testing it on my mobile (working on fixing it).

2023-10-24 Tue: Merged subscription logic to master branch on [stripe-payments-backend](https://github.com/harmony-one/stripe-payments-backend/pull/4). Added subscription status logic on the Discord bot. Deployed Hey Frank ios app. 

2023-10-23 Mon: Added subscription handling on [Discord bot](https://github.com/harmony-one/harmony-discord-bot/pull/1) and [stripe backend](https://github.com/harmony-one/stripe-payments-backend/pull/4). Regarding 1bot development, the top 3 tasks are as follows: 1) Finish fiat payment on Discord bot (16h), 2) Upgrade voice transcription/summary using llama-index vector database to improve summary and allow the user to inquire about the voice transcript (12h), 3) Implement Dalle 3 when available (10h), 4) (optional) Migrate ChromaDB (vector database) to the hosted solution when available (4h).

---

2023-10-20 Fri: Keep working on fiat payment for the Discord bot in a [subscription model using stripe](https://github.com/harmony-one/stripe-payments-backend/pull/4)

2023-10-19 Thu: Keep working on fiat payment for the Discord bot. Added customer creation to the user/create endpoint. Added user/guild (server) logic on discord bot.

2023-10-18 Wed: Added [group whitelist handling](https://github.com/harmony-one/HarmonyOneBot/pull/342) for HarmonyBot. When a user of the whitelist is the owner or an admin of a group, that group is whitelisted. Keep working on fiat payment for the discord bot, integrating the payment functionality to the existing stripe-payment-backend, and defining the architecture of the image subscribing model for discord users.  

2023-10-17 Tue: Added * prefix/alias for handling inquiries to the [current context (URLs/pdf)](https://github.com/harmony-one/HarmonyOneBot/pull/341). * alias works along /ctx command. Fixed /pdf issues after merging to the master branch. Made changes to the conversation array for llama-index inquiries. Worked on stripe payments backend for discord bot.  

2023-10-16 Mon: Deployed and integrated harmony-llm-api to harmony1Bot. Refactored discord bot, adding command cogs (image and payment), error handling, and basic balance logic. [harmony-discord-bot](https://github.com/harmony-one/harmony-discord-bot). 

---

2023-10-13 Fri: Deployed a hosted Chromadb server for the production environment and fixed collection storage issues for document (URL/PDF) inquiries. Keep working on the discord bot. 

2023-10-12 Thu: Fixed dependencies issues with [harmony-llm-api-dev server](https://github.com/harmony-one/harmony-llm-api/pull/10). The server has llama-index required improvements. The improvements will be tested and published in the production environment on Friday morning. Started working on the discord bot to allow fiat payments.

2023-10-11 Wed: Fixed PDF/URL automatic processing on group chats. Added URL invalid handling. Deployed dev server for llm-api backend.

2023-10-10 Tue: Added gpt-3.5-turbo to llama-index collection handling. Also, added PDF invalid handling and improved completion error handling. Fixed the flyio deployment issue that keeps restarting the server [in review](https://github.com/harmony-one/harmony-llm-api/pull/10). 

2023-10-09 Mon: Added completion message length error handling [complete](https://github.com/harmony-one/HarmonyOneBot/pull/337). Added 5 min processing time to PDF and URL collection processing to avoid unlimited requests to the backend [in review](https://github.com/harmony-one/HarmonyOneBot/pull/338).
