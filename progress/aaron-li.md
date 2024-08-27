2024-08-26 Mon (5.6h): Discussion on SY, GX, and Vertex development. Pano: end-to-end approval and actual deposit flow. Fix issues and notification with wallet loading and unloading. Fix focus issues of textinput between main menu and submenu. Add proper error handling for sections that require wallet but none is set. Fix deposit unit error. Add token unit conversion. Fix display errors. Allow .env file or command line argument to preload a wallet. Fix stale data after transaction in deposits. Fix display defects for collateral stats. Add withdraw end-to-end. Fix withdraw confirmation bug

2024-08-25 Sun (5.8h): Pano: deposit - end to end flow except final step and balance query functions. Pano: balance queries, writable client debugging, approval and deposit transaction flow implementation, more error handling on deposit

2024-08-24 Sat (6.1h): Pano: Wallet client, context, provider implementation with decoupled setters for use in hooks. Simplify error handling in commands. Design and implement notification system for sticky, colored, stackable, and transient success and error messages. Fix bugs in notification system and use everywhere. Add menu title boxes to clarify user flow

2024-08-23 Fri (2.3h): Pano: wallet client work-in-progress. Design standalone user-input module for interactive command-input parsing and queries

2024-08-22 Thu (3.3h): Pano (Panoptic command-line-interface) - design and implement user input router, basic parsing module, error handling, basic help message. Pano  basic end-to-end flow (pool listing, stats reading, wallet selection, help message) testing and improvement. Review and research RIP7212. Review planning document and progress updates

2024-08-21 Wed (1.6h): Review 1SY updates. Review progress and discussion notes. Review devops costs and reduction opportunities

2024-08-19 Mon (5.6h): Fix duplicated client instantiation for each hook in Panoptic command-line-interface. Revised type interfaces for better error handling and prevention. Implement error handling and early-stop for invalid input or output. Implement price calculation and conversion from Uniswap internal format. Add user command prompt components and fix display output errors. Roadmap discussions. Research on smart contract vaults, oracles.

---

2024-08-18 Sun (0.5h): (Continued) and preparing roadmap topics

2024-08-16 Fri (1.5h): Find solutions and debug on type inference issues of dynamically loaded smart contract application-binary interface in Viem. Implement typechain-like generation script for application-binary interface

2024-08-14 Wed (4.2h): Debug and test newly implemented Uniswap V3 spot oracles in production. Debug on Synthetix pools. Testing statistics of collateral and pool pair verification end-to-end. 

2024-08-13 Tue (6.3h): Implement and test Synthetix V2 compatible oracle based Uniswap V3 spot prices. Research and experiment on Uniswap squared-price formats and related math precision issues. Continued on Panoptic hooks

2024-08-12 Mon (6.8h): Experiment and implement scripts to manipulate trading account balances in both tokens and native assets using swaps, minting, and impersonation. Creating scripts to replicate the process and local states for Panoptic and Uniswap pools in one execution

---

2024-08-11 Sun (4h): Panoptic command-line-interface - continued. Setting up pool and contract instances, reading basic statistics, fix type system issues

2024-08-10 Sat (1.1h): Panoptic command-line-interface - continued, fix bugs with hooks, make network selection dynamic, research on MetaMask SDK and integration methods through CLI

2024-08-09 Fri (8.1h): Panoptic command-line-interface - continued, implementing essential React hook components for trading pairs and collaterals, to make automated state update conditioned on other changing variables. Implement basic statistics reading, calculation, and parsing. Implement command line argument parsing, basic help message, and their schema configurations

2024-08-08 Thu (3.2h): Panoptic command-line-interface - Local deployment simulation by making use of existing deployed pools and production data on Uniswap and Panoptic from forked blockchain states using Ethereum mainnet, Harmony, and local Anvil. Setting up type and linting systems. Debugging spec-noncomforming RPC response issues. Configure and deploy new exchange products. dDbugging and DNS record remapping. Debug Synthetix token naming

2024-08-05 Mon (2h): Panoptic command-line-interface - scaffolding and local deployment. Domain DNS record setting feature discussion and planning. Derivative discussion and review

---

2024-08-02 Fri (1.7h): Review Panoptic simulation report

2024-07-30 Tue (1.5h): Pantopic semi-fungible position manager math and state variablesanalysis. Domain management and DNS record setting implementation planning. Uniswap v3 SDK review.

2024-07-29 Mon (3h): GX liveness and safety review. Discussion on Keeper, watcher, oracle update mechanisms, and potential monitoring dashboard. Quick evaluation on progress and code quality. Pantopic semi-fungible position manager review

---

2024-07-28 Sun (0.25h): Pantopic semi-fungible position manager review

2024-07-26 Fri (2.25h): Analysis and discussion on Synthetix token minting, staking, allocation, and deployment. Vertex protocol token and quote token usage analysis and discussion

2024-07-25 Thu (4.4h): Security audit on GX deployments, modifications, relevant server components, and contract snippets. Discussion on liquidity provider risk and incentives for GMX, Synthetix, Opyn, Panoptic. Vertex modification code and mock review

2024-07-24 Wed (2.1h): Security audit on GX. Review comments on lending market. Revisit notes on Euler v2 and Ethena. Discussion on Vertex missing components. Revisit GMX, Synthetix, Opyn, Panoptic liquidity provision mechanisms and prepare notes

2024-07-23 Tue (7.5h): Debugging Synthetix ProxyERC20 and SNX token source. Debugging SNX oracle. Security audit on GX. Fix sites failed to auto-renew SSL. Fix URL redirect configuration endpoint bug which left residual CNAME record and prevents redirections taking effect. Fix domain manager API path which prevents CNAME and redirect configuration from functioning. Fix notion page URL configuration and parsing bug in page manager. Migrate new special domain. Write lending market operation and security guide

2024-07-22 Mon (0.9h): Band oracle reader production debugging

---

2024-07-21 Sun (1.4h): (Continued) and review lending market security incidents

2024-07-20 Sat (2.1h): (Continued) and liquidation and forced exercise internal implementations, correctness and potential corner cases handled by type casting and bit operations.

2024-07-19 Fri (7.9h): Analyze and debug Panoptic collateral tracker, all internal functions, and math implementation details

2024-07-18 Thu (3.3h): Notes for Panoptic test failure and fix. Analyze Panoptic pool code. Plan on command-line based account health monitoring, auto liquidation, and exercise tools

2024-07-17 Wed (2.6h): Lending market security issue review. Analyze Panoptic implementation for liquidation and forced exercise tool development. Notes for Panoptic test failure and fix.

2024-07-16 Tue (4.6h): Implementation of band oracle contract with Chainlink and Pyth interfaces. Evaluate code contributions and commits. Band oracle reader deployment and usage notes

2024-07-15 Mon (5.9h): Deep dive on Panoptic and Synthetix code and their use of Cannon and Foundry. Debug Cannon, Foundry, review their implementations and practicality for use in developing in CLI and frontend tools. 

---

2024-07-14 Sun (0.3h): (Continued)

2024-07-13 Sat (1.7h): Experiment with Cannon build and configuration for Synthetix. Review Cannon tools, upgradeable proxy storage collision avoidance, and related hardhat plugin

2024-07-12 Fri (4.1h): Fix Panoptic test failures. Review Panoptic test code. Prepare developing liquidity provider command line tool. 

2024-07-11 Thu (4.6h): Review Panoptic test code, test failures, and deployment parameters. Key domain renewal and certificate management. Synthetix oracle integration with Band. Review Foundry/Cannon configuration files for Panoptic and Synthetix, deployment scripts, and efficient ways for customization. Certificate renewal automation issues

2024-07-10 Wed (1.7h): Analyze, discuss, debug Synthetix v2 oracle code (Chainlink data feed, Pyth). Review points system, Synthetix v2 oracles 

2024-07-09 Tue (4.8h): Synthetix custom deploy and oracle review, and dependency security review. Evalaute Synthetix oracle integration with Band Protocol.

2024-07-08 Mon (2.4h): Review "Panoptic Guide" and associated trading scripts. Panoptic experimentation. Panoptic contract deep dive and debugging. Research and evalaute perps^2 and options

---

2024-07-07 Sun (1h): Experiment with modified Panoptic. Debugging remapping, foundry

2024-07-05 Fri (1.1h): (Continued) and review derivative articles

2024-07-04 Thu (1.3h): Revisit Panoptic contracts and derivative variables. Review change of meaning in implied volatility, vega, volatility skew. Experiment with local deployments

2024-07-03 Wed (0.5h): Domain Debugging. Security issue review and confirmation. Review derivative development status and plans

---

2024-06-30 Sun (1.1h): Debug and discussion regarding issues with addresses from deploying contracts using pre-determined signatures due to RLP encoding differences. Possible solutions on tooling and Synthetix.

2024-06-29 Sat (2.6h): Debug RLP encoding and v-signature recovery issues, and deploy fixed-address create2 factory. node operations and infrastructure update

2024-06-28 Fri (3.2h): Review Orderly. Analysis, discussions, articles related to Opyn, Squeeth, and other derivatives (Panoptics, Smilee, GoodEntry)

2024-06-27 Thu (2.2h): Debug Safe address issues for LayerZero claim. Debug arachnid Create2 contract issues. Review Contango analysis and documentations

2024-06-26 Wed (0.6h): Review Contango analysis and documentations 

2024-06-25 Tue (4.7h): Review SynFutures analysis, docs, analytics. Review Uniswap greeks, Pyth analysis. Quick review on Contango  

2024-06-24 Mon (3.7h): Debug LayerZero claim issue. Examine Squeeth analytics. Review Drift protocol and analytics, oracle risks for bridge and staked assets. Review SynFutures analysis, docs, analytics.

---

2024-06-23 Sun (0.8h): Review Drift, product, and presentation

2024-06-21 Fri (6.2h): Analysis and discussion on landscape and priority, oracles. Examine, compare, review Band and Pyth oracles. Detailed review of Band oracle innerworkings, code, library, contracts, compatibility issues. Review third-party research, comparisons and analysis. Review Pyth documentation, usage, community notes. Review Pods Yield, Olive Network, Hegic. Quick review on KeeperDAO / Rook, Vega, tranched yield products, early versions of Ribbon and Theta vaults, and various projects from 2022.

2024-06-20 Thu (8.3h): Security incident script review, impact re-evaluation, protocol code review. Review analysis on Opyn, Squeeth, Lyra, related option protocols, vaults, related tools (such as Pyth), and historical product evolutions. Review option trading interfaces

2024-06-19 Wed (3.3h): Finalize domain management utility (renew, cert generation, cert renewal, metadata fix, and metadata sync). Opyn code and history review. Substack preview issue in notion.

2024-06-18 Tue (3.8h):  Security issue script minor fix and manual address and transaction inspections. Domain management utility. Opyn code and history review. Substack preview issue in notion

2024-06-17 Mon (4.6h): Follow up on security incident and impact. Review Perpetual Protocol v2 details. Examine premium domain renewal failures. Review Opyn strategies and recent security issue. Fix DNS record issues, batch renew domains, add options to handle domains in the grace period. Review security incidents that may have impacted ETH^2.

---

2024-06-16 Sun (1.9h): Review ApeX, Gearbox, Nekodex, Perpetual Protocol, vAMM. Analyze lending, option, perpetual markets.

2024-06-15 Sat (1.8h): Review Gamma Protocol and Convexity Protocol.

2024-06-14 Fri (4.1h): Security issue impact re-evaluation. Research on option trading user interfaces and experience. Review Perennial.

2024-06-13 Thu (2.8h): Panoptic code, onboarding flow, beta UI/UX, long presentations.

2024-06-12 Wed (2.0h): Review external security incident report. Debug deployment error for deterministic deployment proxy. Resolve issues with chain signature in Synthetix deployment. Debug deployment error for deterministic deployment proxy. Research on Deribit, Opyn, diffusion model. Research on Panoptic code, license. possible frontend. Examining dydx licenses and code structure.

2024-06-11 Tue (3.3h): Setup gx.country, fe.country. GCP access control for Vertex deployment. Synthetix deployer contract and deployment debugging and discussions. Review Foundry, Forge script, Anvil. Review Panoptic presentation and development progress. Research and review user experience issues on perp DEX, deposit and withdraw, and problematic scenarios.

---

2024-06-08 Sat (2.1h): Experiments and discussion on security issue and possible exploits. Review DeFi derivative analysis

2024-06-06 Thu (5.4h): Review virtual automated market maker mechanisms and landscape. Quick review of Hubble, Ribbon Finance, Thetanuts, Rollbit, Floor (NFT) perpetual instrument design. Review and verify staking and security issue impact and resolution. Domain managements for gx.country, gpt.country, and similar ones. Escalate and follow up domain dispute. Review and examine audit and development work of prospective collaborator (SwiftGate, Teller Finance, Titles, Exactly Protocol, veRWA). Review Everything Perpetual and verify mathematical derivations and possible extensions. Quick review of GMX technical analysis, DeFi derivative analysis. Evaluate and verify security issue impact.

2024-06-05 Wed (7.3h): Investigate urgent staking and security issue. Research on time-weighted automated market maker and possible uses in derivatives. Research on liquidity mining, math for ever lasting option, power perpetual. Resolve domain trademark and logo misuse issues. Research and discuss licensing issues. 

2024-06-04 Tue (5.7h): Review updates, on-chain options development plans. Review Panoptic analysis on LP tokens, delta neutral synthetics and parity analysis. Review onchain option plans, related presentations, EIP 4626 vaults. Reivew dydx evolution and UX review. Revisit perp historical evolutions and theories, price impact and calculations in old and new AMM. Discussion on expertise and familiarity of Panoptic UI and smart contract tasks planning with Alex. Discussion and resolving Chainlink oracle and CCIP deployment issues with Artem for use in Synthetix. 

2024-06-03 Mon (2.8h): Review expirationless option analysis and comparison against native perpetual. DNS management for gm.country. Review analysis and products referenced in Three Sigma research on perpetual landscape. Review high frequency trading systems.

---

2024-06-02 Sun (2.5h): Panoptics liquidation, forced exercise, risks. Panoptic security, pool and collateral tracking contract functions, put-call parity analogies, data structures

2024-06-01 Sat (2.5h): (Continued) and Panoptic presentations, Streamia (option premium) details, commission and fee calculations, adversarial scenarios analysis

2024-05-31 Fri (6h): Panoptic fee model and protocol specs. Review Panoptic tech specs, presentation, code. dydx security incident review and comparison to Panoptic mechanism. Risk analysis for bad debt on Panoptics and potential attacks

2024-05-30 Thu (1h): Deep dive on Panoptic product, code and documentation

2024-05-29 Wed (3h): (Continued) and review modified Synthetix configuration scripts for Harmony deployment and packaging. Review Cannon source code and documentation, debug deployment issues and workflow

2024-05-28 Tue (1h): (Continued)

2024-05-27 Mon (3h): Review Panoptic code and deep dive on documentation and mathematics

---

2024-05-26 Sun (5h): Research and review on Surf exchange and protocol. Revisit Uniswap v3 technical details and analyze relation to options based on Panoptic analogy. Revisit Uniswap v3 paper, mathematics, and implementation. 

2024-05-25 Sat (6.5h): Deep dive into Infinity Pool protocol and its mathematics, liquidity reserve mechanisms, option analogy, fixed term and revolving loans. Review Hubble exchange history and design. Quick review on Infinity Pool community discussions and developer topics. Reviewing dydx history and version changes. 

2024-05-24 Fri (5.5h): Review Vertex SDK code. Detailed review on Vertex on-chain code. Revisiting Vertex code and designs. Writing Vertex protocol notes. 

2024-05-23 Thu (4h): Quick review on recent regulatory compliance updates, content and impact of pending congressional bills, and updates for impactful cases on appeal.

2024-05-22 Wed (4.5h): Research and review on Vertex Edge and general system design, cross-margin design, health subaccounts, insurance, liquidation, PnL calculation.

2024-05-21 Tue (4h): (Continued) and review on option vault providers, Ribbon Finance, streaming premium analysis. Detailed review on Vertex design, Solidity implementations.

2024-05-20 Mon (5h): Quick review on GMX code. Review on Phoenix technical designs, implementation, SDK, and settlement mechanism. Quick review on Defi derivative resources. Quick review on Vertex APIs. Detailed review and discussion on Vertex offchain order matching, sequencer, and hybrid automated market maker. Detailed research and review on Panoptic, streaming premium design, option vaults, and options activities in practice.

---

2024-05-19 Sun (3.5h): Review Perp Defi resource list and references. Quick review on Jupiter audits, security, stack, code, portability, and technical specification. Quick review on Birdeye trader data, TradingView integrations, calendar, and unique data sources. Review Jupiter API, research proposals, algorithmic trading discussions. Create notes on Jupiter.

2024-05-18 Sat (2h): Detailed review on design and history of Squeeth and related derivatives, and Jupiter pool design, dollar cost average design and mechanisms. Quick review on Phoenix exchange, orderbook contracts.

2024-05-17 Fri (3.5h): Detailed review and analysis of Jupiter design, mechanism, pools, and some code.

2024-05-13 Mon (1.5h): Review Jupiter documentation and quick research on mechanisms and code. Analysis on key uncertainties for copy-trading, complete analysis on RPC, and polishing prior sections.

---

2024-05-12 Sun (4h): Discussion and analysis on copy-trade data acquisition methods. Research on The Graph, Nansen, Arbitrum RPC, Dune queries in practice.

2024-05-10 Fri (5.5h): In-depth review of perpetual DEX analysis, collateral and fee distribution mechanisms, volumes, growth and adoptions. Review on dydx, GMX, Synthetix data. Quick additional review on Vertex and Jupiter. Quick review and discussion on depegged asset orderbook, recovery proposals, historical conclusions. Review Harmony Portfolio code development on bridging and token management. Review and discuss CSS systems and client framework options. Review, discuss, and close copy-trade tasks. Quick review on perpetual DEX fork options.

2024-05-09 Thu (1.5h): Review on perpetual DEX valuations, evolutions, design.

2024-05-08 Wed (4.5h): Review on Harmony portofolio implementation, security, architecture. Quick review on Blockscout staking implementation in Elixir language. Research and review on perpetual DEX token design, mechanisms, usage and distribution.

2024-05-07 Tue (1.5h): Review and discuss Q2 Defi plans, compliant issues on token launch and decentralization, geofencing and potential legal issues, layer 2 usage and analytics. Discuss registration and renewal procedure for reserved domains.

2024-05-06 Mon (1h): Review and discuss data API access and latency between Dune, Nansen, dAppRadar, and alternatives. Debug and fix certificate issues for reewnable domains. 

---

2024-05-04 Sat (3.0h): Research and review Einstein Labs and similar platforms. Research, review, and discuss Dune analytics data freshness, curation, delay, and queries. Review uniswap v4 dollar cost average documentation. 

2024-05-03 Fri (3.0h): Discussion on copy-trade tasks, arbitrage and price difference issues, data acquisition from Dune and Graph. Review and discuss Dune, The Graph, and RPC methods for implementation options. Experiment and testing Dune analytics queries and delays.

2024-05-02 Thu (1.0h): Analyze and resolve DDOS attacks on SMS / Telegram Wallet. Add rate limiting on signup. Review, analyze, discuss list of notable Q2 2024 defi projects. 

2024-05-01 Wed (1.0h): (Continued) and discuss practical limitations, implementation steps, tasks.

2024-04-30 Tue (2.0h): Review Another World rune mechanisms and project proposal. Review Telegram Bot analysis. Write specs and implementation plans for copy-trade features of SMS-Telegram Bot.

---

2024-04-25 Thu (1.0h): Discuss and review DeFi plans and Telegram bot products.

2024-04-23 Tue (1.0h): Resolve final issues with nginx SSL + gunicorn deployment. Automate certificate renewal and redeployment. Discussions on defi and infrastructure.

2024-04-22 Mon (3.5h): Evaluate nginx production deployment with gunicorn. Deploy and test end-to-end using nginx with SSL + gunicorn worker production. Discussions on frontend, integration, next stage, and future tasks related to job recommendation. Production server access token credential management with replication commands and examples.

---

2024-04-21 Sun (7.0h): Research on using ElasticSearch for word-vector indexing and retrieval-augmented-generation, and related production-ready plugins (LangChain, LlamaIndex). Candidate recommendation system production server deployment, SSL setup, and debuggin issues with static files and separation of Python gunicorn worker and front-facing services (nginx). Research on Django database setup, credentials, synchronization. Constructing and deploying databases; Dependency simplification, ensuring server can replicate virtual environment, and bug-free execution under Python 3.11. Production service deployment. Debugging issues with SSL server in production. Research alternatives to gunicorn and performance. Evaluate, configure, deploy gunicorn for SSL in production. Make dependencies consistent.

2024-04-20 Sat (0.5h): Candidate recommendation system frontend barebone construction.

2024-04-19 Fri (2.0h): Review and document areas of improvements. Python and Django production environment setup at Debian server

2024-04-16 Tue (5.5h): Burner statistics cross-contract aggregation, automatic inference of block range, chart update. Bug fixes and statistics, end-to-end verification of data integrity, deploy new statistics, charts, and data. Implement built-in semi-automatic oracle for market price update, and corresponding client-side live statistics calculation. Further discussions and planning on Shard1 retrieval-augmented generation architecture, candidate recommendation frontend and follow-up implementations, recovery devops

2024-04-15 Mon (0.5h): Evaluation and feedback on comparisons of progress in specific aspects. Discussion on next.js and related framework. Review and experiment Gemini 1.5 API in context of job and candidate recommendation. Review, code evaluation, and feedback on progress of second group

---

2024-04-14 Sun (0.5h): Renew key domains and setup automations. Quick documentation on steps to fix in case of incidents

2024-04-12 Fri (4.5h): (Continued) and basic discussion on retrieval-augmented generation. Recovery discussions on sustainability and proposed solutions. Feedback and detailed evaluation of code and progress of first group

2024-04-10 Wed (1.5h): Review and feedback on progress of first group. Recovery progress and statistics review. Discussion on plans, rate, sustainability, solutions

2024-04-08 Mon (1.5h): Experiments and end-to-end testing of REST API on candidate recommendation server. Bug fixes. Remove Django sensitive information from repo

---

2024-04-07 Sun (0.5h): (Continued)

2024-04-06 Sat (1.0h): Candidate recommendation: bug fixes on server configuration, environment variable setting, and package and dependency management for deployment and remote development

2024-04-04 Thu (0.5h): Review and discussion on Foundry fixed CREATE2 deployer address issue encountered during Optimism rollup deployment 

2024-04-03 Wed (0.5h): (Continued) and deploying REST server for job recommendation

2024-04-02 Tue (3.0h): Refactoring candidate matching implementation for more flexible model and data selection. Research on GPU VM instance pricing and options to run self-hosted large models. REST API for job candidate matching with flexible candidate number, model, and data source

2024-04-01 Mon (2.0h): Backend and module implementation for candidate matching system based on job description

---

2024-03-30 Sat (4.0h): Prompt design for job matching from a pool of candidates. Review Claude SDK, documentations, unique designs. Claude and Gemini implementation and initial experiments for response performance. Cost analysis

2024-03-29 Fri (4.5h): Explore workarounds to access Gemini 1.5 via API. Gemini API experimentation with different model versions and test prompts for recommendation. Review Gemini documnetation and SDK. Huggingface data processing and sampling for resume and hiring data. Basic scaffolding for backend 

2024-03-28 Thu (3.5h): Python server scaffolding and debugging on SSL settings. Setup data analysis environment. Review OpenAI fine-tuning documentations and practical options. Review Huggingface dataset SDK and designs. In-depth review of hackernews resume and job post dataset, and alternatives. Review Gemini models, environment settings, API usage and API key scopes.. 

2024-03-27 Wed (4.5h): Review models and existing work using hackernews job data. Detailed examination of hackernews data and its patterns. Review existing implementation of GLRec and latest language models that support Chinese. Review feasibility of building AI systems in Rust. Review options for Python production server, type safety, performance, and API framework. Python data-analysis server security settings, production settings, debugging, and testing

2024-03-26 Tue (9.5h): Systematic review of existing language-model based recommendation systems using survey paper. In-depth review of GLRect paper, methods, data, and cited work. Review and analysis of JobRecoGPT and compare against GLRec. Review and analysis of JobRecoGPT and compare against GLRec

2024-03-25 Mon (6.0h): Review development trends of language-model based recommendation systems, classification, methods that stand test-of-time, and study effectiveness of methods under the context of long context-window. Briefly review cited work and related papers

---

2024-03-24 Sun (4.0h): Review survey on integration of language models in existing recommendation systems, and roles that language models played when different techniques are employed

2024-03-20 Wed (0.5h): Debugging and resolving domain registration and certificate issue

2024-03-18 Mon (1.0h): Review, comment, and discuss Bitcoin Swap Farcaster frame implementation. Review Celestia data availability modules

---

2024-03-17 Sun (4.0h): In-depth review on models and state-of-the-art research most relevant to conversation AI focusing on voice with limited, unlabelled new training data. Review on V-JEPA, quick review on self-supervised learning with contextual target representation, VATT, PromptTTS 2, NaturalSpeech 2, T5. Discussion and analysis on NaturalSpeech3, Mega-TTS 2, voice conversion models such as SEF-VC, and others. Discuss, review, and experiment with VALL-E-X for cross-language audio generation. Experiment with Grok-1

2024-03-16 Sat (7.5h): Detailed review of analysis of data collection apps and platforms. Review Claude Opus and exceptional results on low resource language. Review data iimpact research, job and dating matching system outlines. Review speech models (Deep Speech, Google USM, Chirp, and others). Review analysis and unsolved problems on recruiting, job searching, job matching. Review relevant products, platforms, new language models for jobs and matching, adoption of AI in existing products. Review wallet infrastructure analysis, existing solutions. Review hackernews dataset and LinkedIn skill recognition model

2024-03-15 Fri (5.0h): Review techniques and results of training and fine-tuning Whisper. Review zkBridge, product details, integration requirements. Review Inference Labs litepaper and documentation. Review Zero1 Labs and Axiom. Review local inference tools and machines. Detailed review of mytiki datasets, integrations, team, documentation, architecutre, SDK, and mechanisms. Review Caden datasets, background, B2B products and solutions

2024-03-14 Thu (1.5h): Discussion on AI data intelligence demo proposals, and specific possibilities and plans. Review speech and lanauge model benchmarks, and adversarial approaches (SuperGLUE, HellaSwag, TruthfulQA)

2024-03-13 Wed (2.0h): Review phishing email and potential malicious domain traces. Review Story Protocol and IP discussions. Review and discuss BTC swap Farcaster frame demo and its implementation.

2024-03-11 Mon (0.5h): Batch legacy domain renewal and checkup operations. Certificate maintenance and automation

---

2024-03-10 Sun (2.5h): Discuss and help debug BTC swap Farcaster frame implementation and use of ngrok tunnel, debugging and validation methods. Configure development website (hiddenstate-0306). In-depth review and discuss B-squared protocol. Burner rate issue investigation. Research on voice models and benchmark. Quick review of VideoPoet

2024-03-09 Sat (7.0h): Research on BitTensor incentive mechanisms and technical components. Research and discussion on BitTensor data universe code and data sources. Conceptualizing voice and map data products. In-depth review of BitTensor consensus protocol, staking, delegation, mining, validation, CLI and SDKs. (Continued) in-depth review of BitTensor subnets, design details, and OCR subnet example. Discussion on flaws, feasibility, and common issues of existing AI / data blockchain projects

2024-03-08 Fri (3.0h): Review on car voice data collection and related technical work on language models. Research on BitTensor initial whitepaper, data gathering mechanisms, and underlying protocol, and relation to Polkadot parachain . Research on voice data gathering sources, analogue-VoIP devices, potential hardware on the market and plugins

2024-03-07 Thu (3.5h): Discussion and analysis on data categories, gathering methods, use cases and future potential

2024-03-06 Wed (6.0h): Research and overview on 0G protocol design, use cases, code, contributors. Review Grass, its Chrome extension, and its growth metrics. Review 0G architecture, documentation, incentive and transaction mechanisms, API design, data aggregation, security models, and proof techniques. Review Farcaster account sharing methods and potential security issues. Review Farcaster account and security models. Setup and management of sharable Farcaster accounts (hiddenstate-0306)

2024-03-05 Tue (1.5h): Review Sentry reported errors for Voice AI app, help debug and discuss solutions (local attestion timeout / rate limited, missing HTTP error message, fallbacks, persistency of error)

2024-03-04 Mon (3.5h): (Continued) In-depth review on Lorenzo, Babylon, BOB, Celestia components 

---

2024-03-03 Sun (4.5h): Review and research on AI Data tokens, Bitcoin interoperability SDK, Bitcoin Layer 2 systems, and Bitcoin inscription frameworks and projects

2024-03-02 Sat (1.0h): Add option to render SVG to PNG for iOS Warpcast compatibility. Debug sharp compatibility issues with cloud Debian and arm64 architecture. Deploy and test in production. Burner rate update

2024-03-01 Fri (10.0h): Implement new map based frames with review and check-in. Implement counters for mint and 24-hour mint. Add mock-mint mode. Deploy and demo in production. Implement styled dynamic text at line-level for SVG. Improve location parsing and display. Allow optional location suffix, and natural syntax for users to override on location suffix. Debug and submit single-letter domain issues on Warpcast. Test redirect, proxy, CNAME, URL transform and various ways to circumvent the single-letter naked domain bug. Improve text and button display for map extension. Separate basic-map and map extensions. Implement permanent key-value storage for review and check-in. Deploy, configure and test redis for embedded web service. Implement safe mint, count, and balance query, and dynamic image for with cache control. Implement static statistical image API. Inscribe review and check-in location on-chain during mint. Deploy to production and test end-to-end

2024-02-29 Thu (8.0h): (Continued) Breakdown and refactor Farcast implementations by extensions. Fix multiple implementations bugs and structural issues. Discussions, technical Q&A, and task planning on Farcaster frame implementations. Research on WARP tokens. Cloud configuration and deployment. Implement Redis client. Research on Redis data structures to use for temporal count and aggregation. Deploy, configure and test redis for embedded web service.  Debug dot-country purchase issues. Reconfiguration of lend.country documentation sites and discussion on SSL wildcard certificate renewal and auto-deployment issues

2024-02-28 Wed (3.5h): Review and test fixes for Substack error message. Burner rate and mechanisms update, redeployment. Review and comment on DCReward on-chain minting implementation. Research on Promise pool, implement queued asynchronous minting with fast frame resposne. Review and finalize fixes for Substack error message issues. Review and revise on-chain minting code, metadata, and configurations based on DCReward.

2024-02-26 Mon (0.5h): Analysis and debug of AWS to embedded web service redirect issues and unicode / ASCII encoding issues. Review embedded web service preview generation and special routes 

---

2024-02-24 Sat (2.5h): Farcaster integration debugging and discussions. Warpcast client - frame server interaction flow analysis. Access-controlled dot-country reward minting contract with metadata URI management. Dependencies and compiler upgrades. Bug fixes of Farcaster frame preview

2024-02-23 Thu (11.5h): Implementation and testing of dynamic rendered text in SVG with styling options. Alternative Farcaster frame use case exploration. Research on Google mapping embedding and SVG-based solutions. Research, experiment, and integration of static Google map image and styling, and interactions with Farcaster frame and its requirement. Bug fixes and Farcaster POST message validation analysis. Dynamic static, styled map image for Farcaster frame, callback route and error handling, end-to-end debugging, testing, deployment, demo, and production trial. Dynamic-image generation for Farcaster text frame, Farcaster text inscription initial frame, POST callback route and error handling, with debugging, and testing. End-to-end deploy, debugging, demo, and production trial for text-inscription Farcaster frames. Discussion of TODO on token minting in production.

2024-02-22 Thu (10.5h): Evaluate Substack page DOM structures, various DOM parsers, and experiment on adding Farcaster frame data through DOM manipulation. Finalizing Notion embedded page and Farcaster frame integration. Add customizable token name, initial Substack support, and fix issues in configuration. Farcaster frame and Substack integration. Resolve compatibility issues, add configuration syntax . Test through management UI. Initial implementation of Farcaster callback route. Add and implement unified parse settings for Substack and Notion, add Farcaster flags and extension syntax. Resolve Farcaster certificate validation issues for tunneled development host. Add HTTP support, configurable protocol, host extraction, default image in absense of OpenGraph image from Substack or Notion page. Fix missing frame properties, bugs, add redirect routes. Fix Farcaster frame-mint failure cases, redirect handling. Fix Farcaster message validation, add id extraction, lookup and owner address mapping. Fix hub client integration. End-to-end deploy, debugging, demo, and production trial of Notion and Substack default Farcaster integration. Demo and experiments on error handling and text-input submission and validation. End-to-end deploy, debugging, demo, and production trial of Notion and Substack default Farcaster integration. Demo and experiments on error handling and text-input submission and validation

2024-02-21 Wed (5.5h): Farcaster specification review, API and hub experimentation. Review and evaluate sample frame implementations and production apps. Initial implementations in dot-country embedder for integration. Design and implement Farcaster partial template and configurations. Integrate with existing opengraph renderer server implementation, and settings from embedded-web-services contracts

2024-02-20 Tue (4.0h): Review Farcaster FIPs, documentation for client development, core concepts, account, messages, and names. Evaluate Farcaster developer toolkit, community-developed packages, and simple demo frames related to mint and polling. Evaluate compatibility issues of server-side rendering and use of next.js. Evaluate Farcaster APIs, frame specifications, data schemes

2024-02-19 Mon (3.5h): Review Human Protocol new developments, plans, and issues. Review Farcaster design, architecture, developer documentations, APIs, and frame integrations. 

---

2024-02-12 Mon (0.5h): Evaluate and discuss Human Protocol demo apps, suggest features and engineering improvements

---

2024-02-11 Sun (0.5h): Compute, review, and discuss recovery analytics and implications of increased market rate for depegged assets. Update and aggregate results from multiple contracts belonging to a large round.

2024-02-09 Fri (4.5h): Configure, deploy and end-to-end testing for VPN with network congestion simulation. Create one-click VPN installation profiles for macOS and iOS. Manual Cisco VPN setup instructions. Fix DNS, certificate, and subdomain embedding issues with lend.country and docs.lend.country (reassigning nameserver, re-generate certificates, fix infinite redirect loop by Cloudflare, fix missing ownership on blockchain by manual registrations, manual configuration of DNS and notion embeddings, bifurcate subdomains and reassign nameserver to Cloudflare). h.country DNS and nameserver migration. Documentation for VPN server with traffic control. 

2024-02-08 Thu (6.0h): Review progress and discussion on Lottery and Human Protocol implementation. Research on Telegram group-wallet design based on Human Protocol / Minimal Social Wallet. Debugging and fixing L2TP IPSec VPN server and ppp issues caused by non-standard GCP cloud linux kernels. Research and experiment on options and tools for network emulation in GCP (Cloud Armor), docker (pumba), and vanilla Linux tools (netem).

2024-02-07 Wed (5.0h): Resaerch and discuss Godaddy and ENS integration and examples. Review ENS DNSSEC implementation and OffchainDNSResolver. Discuss general ways to support new preview crawler. Review Cloudflare Page hosting and discussions on DNS requirement and nameserver migration and limitation. Initial review of Cloudflare API. Review Cloudflare worker and KV store documentations. Discuss choice of key-value database for fastest response. Review Cloudflare API documentation on batch domain activation. Review Cloudflare token architecture and access control, and configure limited scope tokens accordingly. Review OffchainDNSResolver contract and ENS-GoDaddy gasless domain registration architecture. Discuss downsides anad flaws. Migration of special 2-letter domains to Cloudflare. Fix social preview issues of embedded web services for farcaster, analyzed and expanded user agent matching list. Initial IPSec / IKEv2 VPN deployment, Debian isntance setup, Docker configuration. Initial testing of VPN server via Debian host machine instead of container CoreOS.

---

2024-02-02 Fri (1.0h): Research on plans and features in human protocol

2024-02-01 Thu (2.0h): Domain renewal documentation and script usage. Refine domain renewal document. Review discussions and progress on new projects on lottery, Telegram bot, inscription, and dot-country changes

2024-01-31 Wed (1.0h): Review inscription backend services and change requested for embedded web services in catering 2-letter domains. Discuss minimal implementation and fork. Quick review and discussion on client side changes of dot-country

2024-01-29 Mon (5.0h): Domain web2 renewal API, registrar domain info and expiring domain list API integration. Script for batch domain renewal, review existing user and test domains, end-to-end debugging and testing. Discuss erroneous Namecheap renewal API response and incorrect account and pricing setup with registry. Implement lookup-only mode for renewal script. Manual domain renewals and management. Discussion on enable-subdomain errors and ens-registrar-relay routes, and existing main implementations (Notion, Substack) for embeeded web service.

---

2024-01-28 Sun (4.0h): Docs for batch certificate renewal, management, access control, and modification guide. Refactor scripts for multi-purpose. Setup certificate management instances and access. Docs for manual certificate renewal for external domain. Renew certificates for key domains

2024-01-25 Thu (0.5h): Discussion and documentation on certificate generation, renewal, management, and processes

2024-01-23 Tue (2.0h): Review minimal social wallet POC and history. Review paper trading bot. Review partial evaluation implementations in blockchain and smart contracts, and analyze options.

2024-01-22 Mon (2.0h): Legal research and analysis on Clark v. CFTC appellate opinion, injunction, history and applicability of CFTC no-action letters and enforcement practice. Legal analysis on prediction market risks and issues on developing, deploying, operating a platform, and importance of decentralization. 

---

2024-01-21 Sun (8.0h): Implement and deploy system services for email alias services. Auto renew certificate on regular schedule. End-to-end testing printer use cases, with SMTP and email alias forwarding. Research on prediction markets. Research on the history and various legal opinions regarding Polymarket and its terms of service. In-depth analysis of CFTC v. Polymarket. Research and analysis on Thales prediction market design, contracts, AMM, UMA oracle, and demo prediction market contract. Evaluate alternatives.

2024-01-20 Sat (6.5h): Refine and finalize batch multi-certificate renewal scripts. Verify reserved and blocked domains. Quick review of ICANN rule. Debug and test premium domains. Sync all domain-related repositories. Review prediction market products, legal research on applicable laws and enforcement actions. Experiment with SMTP services for email alias services. Upgrade email alias services to latest common stack (ether v6, node 20). Debug various type and compile issues arising from hardhat, typechain, and typescript. Debug and implement workaround for missing Harmony protocol RPC implementation on eth_gasEstimate

2024-01-19 Fri (6.0h): Review and analysis on inscription contract code: mint, buy, sell, withdraw, supply and balance control, and other internal logic. Review new Telegram embedded wallet proposal, analyze prior art, evaluate options to extend SMS Wallet and other design options. Debug and fix issues related to unable to manage domains using dot-country domain manager. Premium and reserved domain management. Implement batch multi-certificate renewal script

2024-01-18 Thu (5.5h): Deploy certificate auto-renew automations on key dot-country and ai-bot services. Debug dot-country Substack embedder URL link hostname issues, analyze new scripts and page load mechanism from Substack. Experiment with a variety of DOM and Javascript listeners. Deploy temporary fix. Quick review of inscription contract code on security, integrity, and deployment issues. Review latest Multisig configuration and code change log. Discussion on technical and legal issues pertaining to raffle / lottery, prediction market, and similar mechanisms through NFT airdrops

2024-01-17 Wed (4.0h): Analysis and in-depth review on amicus brief by DeFi Education Fund in SEC v. Coinbase, review hearing transcript and updates of the case, discuss legal authority on asset ownership in custodial service, distinguishing factors of ministerial v. managerial service providers, and how they apply to bridge and swap services

2024-01-16 Tue (5.5h): Debug and discuss Multisig iOS RPC call issues. Review code and UI update progress. In-depth legal research and analysis on Underwood v. Coinbase, effect and importance of user agreement, asset title transfer, asset custody, control, transaction and order fulfilment mechanism, fees, and choice of assets on the platform. Review related cases such as Anderson v. Binance.

2024-01-15 Mon (4.5h): Legal research on Uniswap terms of service, legal structures, and litigations. In-depth legal research and analysis on federal district court opinion and case files on Risley et al. v. Uniswap, cited case laws, statutes, alleged facts, and applicaibility to bridge / swap products

---

2024-01-14 Sun (5.5h): Analyze reusable components in SMS Wallet mini-wallet for minimal social wallet and modifications required for inscription use cases. Research and analysis on lottery, contest, sweepstake statute and case laws, and applications in on-chain transactions and inscriptions. Research on calldata limitations and block size historical changes. Quick review and discussions on Safe iOS code and configurations.

2024-01-13 Sat (2.0h): Research on inscription technical development history, use cases, adoption, and minimal social wallet integration and design. Research and discussion on recovery supply issues and bugs in explorer backend for computing supplies

2024-01-12 Fri (2.0h): Implementing CNAME record setup for root subdomain in dot-country domains, testing and deployment end-to-end. Domain renewal and management. Review and research on inscription data carrying and retrieval capacity.

2024-01-11 Thu (2.5h): Review #393 (comment over defining test behavior using class variable instead), #394, #395, #396, #397, #398, #399 (concern over access control), #400, #401, #402, #403, #404, #405, #406 (comment on sampling rate), #407, #410, #411, #412, #414, #415 (note on TTS response streaming, and model name confusions), #392 (draft). Burner launch and resolving cache issues.

2024-01-10 Wed (4.5h): Review #318, #319 (concern on confusion over exporting transcript / log), #320, #321 (concern over dropping support for other languages), #322, #323, #324, #325, #327, #328, #330, #331, #332 (comment on private key could derive address), #333, #334, #335, #336, #337, #338, #339, #340, #341, #343, #344, #348, #353, #354, #355, #361, #363, #368, #369, #370 (comment on JSON parsing complexity), #371 (comment on function signature modification solely for testing), #372, #373, #379, #381, #383, #385, #386, #380 (concern on conflicts and PR being left open), #387, #388, #389, #390, #391

2024-01-09 Tue (2.0h): Recovery live stats, analytics and charts with WONE support. v7 client portal. New contract and revised parameters for large rounds. Technical Q&A. Domain management and renewal reversal

---

2023-12-11 Mon (5.0h): Draft and publish design and architecture document for personalized response and Twitter integration 

---

2023-12-10 Sun (4.0h): Research on Twitter API access, authentication, OAuth flow, pricing, rate limit, usage caps, restrictions, and differentiation on app and user access. Experiment on Lists and search, and related APIs

2023-12-09 Sat (4.5h): Refactoring Benchmarking code logic and variables to be consistent with documentation. Add total text-to-speech time, Fix text-to-speech time related comments. Update ElasticSearch mapping definition and Relay request processing, and env examples. Increase relay setting retrieval timeout. Fix missing send log triggers. Add speech-to-text preparation time. Measure app recording time and speech-to-text recording time to TimeLogger. Add model fields to records. Add new Relayer for production server. Check backward compatibility. Update ElasticSearch mapping. Debug and test end-to-end

2023-12-08 Fri (2.5h): Discussion and research on personalized context based on Twitter and other data sources. Review #329 (comment on text-to-speech measuring issues, branches with zero speech-to-text, and future TimeLogger structure). Fix benchmarking guideline typos. Further review #329 (comment on branches of execution where logs are not sent, premature termination of benchmarking, incorrect measurement of speech-to-text text result and benchmarking termination). Research and test built-in SpeechRecognition non-blocking calls, callback checkpoints and finalization flags. Test end-to-end and evaluate correctness

2023-12-07 Thu (4.5h): Benchmarking guideline: measurement timelines, key metrics, metadata, client implementation notes. Investigate wallet theft and unusual fund flows

2023-12-06 Wed (5.5h): Discussion and feedback on benchmarking and measurement. Research on locale and language settings for tests, and issues related to optional chaining and branch conditions in test coverage. Drafting benchmarking guideline: infrastructure details, and measurements

2023-12-05 Tue (3.0h): Debug MetaMask mobile signing issues on Gnosis and Multisig, replicate signature issues in version 7.12.0. Inspect Gnosis backend service code for potential workarounds, and review MetaMask code changes and version history. Discussion on ways of audio capturing improvements. Review MetaMask mobile reported issues, debug underlying cause, create a workaround and demo. Research on edge models and Apple Silicon ML frameworks. Review #298, #299, #300, #301 (comment on API key's access and safety, and sentry capturing tags), #302, #303, #304, #305, #306, #307, #308, #309, #310, #311 (request for version alert extra content), #313, #314 (comment on silent failure), #315, #316, #317, #312 (open, question on integration with Siri, watch, and apps)

2023-12-04 Mon (1.0h): Debug and fix tweet embedding issues. Further analysis on pull requests and commits

---

2023-12-03 Sun (1.0h): Demonstration and discussions on Kibana client metrics and raw log. Analysis on pull requests and commits.

2023-12-02 Sat (0.5h): Research and discussions on sheet popup sizing and layout control options, limitations prior to iOS 16, alternative libraries and potential impact to build. Review logs and events captured during end-to-end testing of apps

2023-12-01 Fri (3.5h): Review #273, #274, #275, #277, #278, #279 (comment on sign-in test coverage), #280, #282, #285 (comment on nil-able variables), #286, #287, #288, #289 (comment on configurable variable), #283 (draft), #284 (draft, comment on mock benchmark purposes), #290, #291 (comment on language code as setting). Review iPad actionsheet issue. Discuss ElasticSearch charting issues and tasks. Discuss NLP pipeline and processing of other languages. Review #296 (concern on redundant ElasticSearch implementation at client), #292, #294, #293, #295. Research options for multi-action popups for iPad actions and compatibility, experiment, debug, and fix issues 

2023-11-30 Thu (1.5h): Review and debug multisig 422 error and signing issues from some devices. Review #266, #267, #268, #269, #270 (questions on deterministic test issue), #271, #272 (questions on audio tap removal, comment on whether actual functionalities are tested and need for more advanced action simulation).

2023-11-28 Tue (1.0h): Research and discuss benchmarking options and metrics. Research scalable benchmarking and user testing tools (Mechanical Turk, Sofy, Usertesting, and others).

---

2023-11-25 Sat (6.5h): Review #260, #262. Devops role and user setup for Kibana and ElasticSearch. End-to-end testing and cluster management for voice app client performance and metric analysis. Perform Apple device check on relay using client submitted device token. Retrieve relay mode and OpenAI base URL from server. Fix attestation caching, key regeneration mechanisms and triggers. Add ways on server to expire an attested key. Allow multiple package ids for hard attestation verification. Bug fixes and end-to-end testing, deployment.

2023-11-24 Fri (7.5h): Review #235, #236, #237, #238, #239, #240, #241, #242, #243, #244 (commented on concern over use of trademark terms and proposed alternative), #245 (press and hold delayed processing - commented on concern over missing input word), #246, #247, #248 (tests on OpenAI streaming - commented on possible improvements on using mock server instead of states that are only useful for tests), #249 (multi-button tap - commented on complexity concern), #251, #252 (performance metric measurements - commented with TODO), #253 (UI action tests - requested additional tests with more depth), #254, #256, #257, #258, #250 (open, transcript export - commented on concern over ineffective filtering), #255 (open). Relay API for performance times and metrics. Refactoring relay APIs and utilities. Client side implementation for TimeLogger. Refactoring device token generation. Creating generic time and performance metric logging and measurement utility.

2023-11-20 Mon (2.0h): Analysis of first response time. Kibana quick setup for Voice AI app. Research on latency improvement plans and alternatives to OpenAI. Review #221, #222, #223, #224, #227, #229, #230, #232, #233, #234.

---

2023-11-19 Sun (1.5h): Research on Azure compute, AI support, and Anthropic. Wallet theft analysis. New Burner mechanisms through WONE, end-to-end testing, production deployment.

2023-11-18 Sat (N/A): Technical research on state-of-the-art and recovery community service.

2023-11-17 Fri (8.5h): Debug issues that prevent some clients from obtaining relay tokens. Add structed errors and codes for relay client. Capture errors. Auto-retry at client side. Do not override token if failed to get one. Allow new session button to get a new relay token. Cache attestation and challenge at client side. Deterministic generation of relay token. Implemented banned list for relay token. Added ElasticSearchintegration and basic request and response measurement. Store attestationHash and ban user based on that, instead of auth token. Make auth token change every 30 minutes. Review #210, #181 conflicts, #217, #214, #213, #212, #211, #209, #208, #207, #206, #205, #204, #203, #202, #198, #197, #194, #193, #192, #190, #189, #187, #185.

2023-11-16 Thu (2.5h): End-to-end debugging and testing for app attestation and relay-based OpenAI queries. Debug and fix issues related to verifying develop-environment attestation. Fix issues related to non-functioning app caused by multiple initialization of relayer authentication module. Review devops TODO list proposal. Review and discuss in-app purchase flows (#196) and integrations with server.

2023-11-15 Wed (6.0h): Review in-app-purchase issues and existing implementations. Discuss key leakage issues and review logs. Implement RelayAuth client module for app attestation and relay token management. Debug and fix issues with relay app attestation verification and logging. Discussion on key protection. 

2023-11-14 Tue (3.5h): Fixing SSL issues and domain registration issues. Review and implement EWS Substack anchor link sharing. Review implementation plan and issues for account signup, login, in-app purchase restoration. Review #179, #181, #183, #182, #184. GCP IAM setup for devops personnel, and ElasticSearch operation instructions. Debug MetaMask mobile issues on multisig. Recovery security discussions. Research on and discuss OpenAI Assistant and threading APIs.

2023-11-13 Mon (3.0h): Technical interview and post-interview analysis. Implementing and testing in-app purchase for GPT-4 booster. Review #167, #168, #169, 170, #171, #173, #174, #175.

---

2023-11-12 Sun (0.5h): Review app payment server and API design and discussions.

2023-11-11 Sat (6.0h): Implement basic key protection in relay with AES encryption, multi-key rotation, device id and ip tracking, ban list, and key retrieval API with rate limit. Implement client side decryption and initialization. Client side bug fixes, end-to-end testing. Deployment on GCP and systemd service with instance metadata as parameter. Setup and build guide. Allow local key override.

2023-11-10 Fri (1.5h): Review #141, #157, #159, #160. Research on GPT chat session, context compression and effects. Interview preparation and discussion on technical problems.

2023-11-09 Thu (5.0h): Review #144, #145, #146, #148, #149, #150, #151, #152. Implement QPM limit on streaming services, and rate-limit error handling. Test end-to-end. Research and analysis on iOS market shares by versions, and minimally required versions for key features. Code refactor and applying universal formatting. Implement GPT model switch based on GPT usage time. Implement random alert to share and review based on app usage time. Test end-to-end and fix bugs.

2023-11-08 Wed (4.0h): Review #138, #139. Testing for bugs in complex audio conditions. Update production checklist. Review language requirement, support channel integration, built-in analytics. Review and discussion on checklist suggestions. Technical interview preparation. Extend production checklist with audio bugs, UI bugs, and customer support features. Cleanup and backup Notion data. Fix issues on mail aliases services, implemented pagination. Update checklist on version control issues. Review deep links into settings.

2023-11-07 Tue (2.5h): Make initial production checklist. Research on app analytic systems and integration complexity. End-to-end testing of the app. Fix SSL issue and document steps for future incident resolution. Fix Tweet embedding issues, CSS issues for notion embedding, and research on tweet libraries.

2023-11-06 Mon (2.0h): Review #114, #115, #117 update, #118, #119, #120, #121, #123, #125. Review OpenAI new offerings and ways of integrations.

---

2023-11-03 Fri (0.5h): Review #117. New domain and DNS configuration. Review Linux ML development portability to iOS.

2023-11-02 Thu (1.0h): DNS configurations for lend and Cloudflare issue diagnosis. Lend legal term review. Discussions with security vendors on manual review of swap. Review on-device models and compatibility with iOS devices.

2023-11-01 Wed (4.5h): Fix "Repeat" button's queueing issue. Fix "New Session". Fix speak button press and release logics. Experiment with shorter word utterance. Fix EAS rate limiting and maintainer issues on x.country and implement caching. Review recent updates (#108, #105, #104, #101, #99) and resolve merge conflicts. Fix "Pause / Play" button bug where the button is sometimes ineffective.

2023-10-31 Tue (2.5h): Reimplement for press-to-talk mode, end-to-end debugging and testing. Further research and actions on phishing warning resolutions. Review #93, #95, #97. Fix bugs and crashes related interrupting OpenAI queries. Discussions on present user experience issues and bugs. (Continued) and discussions on on-device work TODOs.

2023-10-30 Mon (5.5h): Review code updates and errors related to OpenAI streaming (#82, #83, #88, #87, #86, #84, 81). Fix OpenAI streaming implementation and integrations, graceful error handling, crash issues in classic Speech Recognition crash issues, various button failures and unexpected responses. End-to-end debugging and testing, and publishing new deployment in Hey Sam. Discuss findings and tasks related to key protection and attestation. Live discussions related to OpenAI streaming issues.

---

2023-10-29 Sun (1.0h): Code review and discussions on alternative OpenAI and Deepgram streaming implementations, recent pull requests and versions, product updates.

2023-10-27 Fri (4.5h): Deploy and setup relay server instance with domain and certificates. Implement certificate chain verification and binary to PEM conversion. Revise and fix bugs on attestation verification. Implement client side examples for using Relay with TODOs.

2023-10-26 Thu (6.5h): Documenting, testing implementation and TODOs. Implementation of Relay and integration with attestation verification. Code review on recent PRs #70, #73. Review attestation formats, WebAuthn libraries, research on DER encoding, Octet string, ASN.1 sequence, and the maximal use of jsrsasign library. Revise attestation verification implementaiton on missing steps (nonce verification, certificate chain). Research on X.509 custom extension field retrieval, jsrsasign library inner working and utility functions, and past issues and solutions

2023-10-25 Wed (5.5h): Research on OpenAI key generation process, security recommendations. Research on Apple app attestation and integrity services, verification algorithm and reference implementations. Research on CBOR and WebAuthn standards and related libraries, and app attestation design and format. Step by step implementation of attestation verification. Verify reference implementation on public key construction.

2023-10-24 Tue (9.0h): Fix issues with streaming ASR error handling, payload parsing, keep-alive, auto-resuming, and closing. Implementing OpenAI streaming response handling, piping ASR to OpenAI, streamed toke nresponse processing. Piping to Speech synthesizer for end-to-end demo. UI Button integration and implementation based on streamed components. Debugging, end-to-end testing of streaming ASR (Deepgram) + LM (OpenAI). Debugging capturing activation for AVCaptureSession and implementing workarounds. Implement basic measures to counter self-interference (pause listening while speaking), fine-tune parameters and sentence delimiting to compare model performance, deploy to TestFlight. Review PlayHT streaming implementation, documentations, models and styles. Resolve merge conflicts. Implement TTS streaming skeleton. Review latest code commits, package dependency sizes. PlayHT basic partial integration, with TODO instructions. Evalaute and experiment with PlayHT models and parameters.

2023-10-23 Mon (6.0h): Complete Deepgram integraiton. Research on audio buffer splitting and joining. Implement and debug stream ASR end-to-end. Research, debug, and fix issues related to native websocket continuous receiving errors, reconnects, and sending errors for various payloads (keepalive, data). Simplify JSON payload parsing and encoding. Research and implementations on audio buffer merging, splitting, metadata retrieval and computation, and raw buffer parsing and manipulation. Debug x.country preview issues, app store app internal user access issues. Discussion on development process, concurrent implementation structure, forks, and merges.

2023-10-22 Sun (5.0h): Deepdive on Deepgram API option and experiemtnation. OpenAI streaming API research and issue review. Building websocket messaging around Deepgram streaming integration and error handling. Research on low level header files for settings related to audio encoding, sample rate, and others for configuring output buffer. Research on audio buffer manipulation and experimentation. Implementation of audio buffer data conversion. Review simjilar issues reported online related to merging and splitting audio buffer. debugging and testing.

---

2023-10-21 Sat (2.5h): Implementing ASR websocket integration, functions for basic commands and controls. Revisiting documentation on Core Audio streaming methods and determine the best implementation approach. Review AudioToolBox and related alternatives and evaluate. Reviewing and implementing AVCaptureSession and AVCaptureAudioDataOutput

2023-10-20 Fri (3.0h): Review Hey Julia code. Fix configuration issues, build, deploy on TestFlight and discuss minimal steps for continued development. Forking iOS development versions, reconfigure projects in each folder, and deploy Hey Eve

2023-10-19 Thu (0.5h): Manage new app bundle ids, Test Flight configurations, corresponding provisioning profiles, and internal tester groups.

2023-10-18 Wed (4.5h): Research on iOS audio, speech, networking (native websocket v. third-party libraries such as Starscream) capabilities across recent versions, market share, and optimal cutoff version. Experiment on native websocket and assess deficiencies. Research on Swift Package Manager v. Cocoapods for managing external dependencies. Review, build, and test new iOS code (#35). Manage and debug on iOS provisioning profiles, signing certificate requests, and distribution certificate. Debug and fix issues related to x.country redirects and email alias contract management.

2023-10-17 Tue (2.5h): Testflight fine-grained access, profile, certificate setup. Build and publish new versions. Test latest demos and debug. Voice provider API testing and debug.

2023-10-16 Mon (3.5h): Review code update (#25, #28), all progress updates and results. Debugging Swift dashboard UI mockup bugs, Swift extensions.
Review and test Swift UI mockup fixes. Review code updates (#26 willow e2e, #28 Safari support, #10 error handling, deployment fixes), recent demos
Review, test, and compare Swift websocket libraries and code. Code review #4 (audio player base, elevenlabs), #25 (gpt4 context and deepgram), #26 (voice detection), #27 (willow e2e) and related components. Test commercial TTS provider APIs.

---

2023-10-14 Sat: (2.0h) TestFlight build, launch, bug fixes, and configurations. Review Deepgram benchmark and documentations.

2023-10-13 Fri: (7.0h) Research and analysis on audio libraries and frameworks under react native and iOS native system (CoreAudio, AVFoundation), [write ups](https://github.com/harmony-one/x/blob/main/doc/audio.md), [boilerplate app setup](https://github.com/harmony-one/x/pull/21), and code review. Progress review. X app configuration, framework imports, permission updates. Manual x.country domain management, maintainer updates. Long-term renewal, and bug fixes.

2023-10-12 Thu: (1.5h) Research on AVFoundation, Apple audio session programming, web audio controls, react-native sound and expo AV.

2023-10-11 Wed: (5.5h) Code review and discussion of contributor all historical commits. Manual subdomain record management. Discussions on findings of Twilio voice, voice models, performance, technical limitations, and streaming techniques and capabilities. Analyze use cases, engineering requirements, product prioities, development plans. Research on Apple GPU and Metal inference capbility, on-device APIs, and performance.

2023-10-10 Tue: (1.5h) Deepgram review. Twilio voice review and research.

2023-10-09 Mon: (0.5h) General code review. Research note and documentation reivew. React native app setup and Test Flight configuration.

---

2023-10-08 Sun: (2.0h) Research, analysis and discussion on model size, distribution mode, hybrid deployment, performance trade off, edge device benchmark, and real-time factors. Research on Whisper streaming workaround. Analysis of performance and practicality of wav2vec2.

2023-10-06 Fri: (1.0h) Voice cloning and synthesis experimentation, note review. Revisiting Huggingface experiments.

2023-10-05 Thu: (3.5h) Research on Whisper, paper and notes, performance data in practice, and related speech recognition development. Research on vector database. Kibana reconfiguration on payment analytics. x.country expiration issue, manual, renewal and general .country maintainer permission update.

2023-10-04 Wed: (2.5h) Discussion and analysis on voice product, tech stacks, and use cases. Task planning and work allocation. Speech model performance review. Research on Twilio voice streaming.

2023-10-03 Tue: (5.0h) Personalized task planning. Huggingface models and spaces experimentation (tortoise, coqui, others) . Ad-hoc performance and latency measurements. Domain renewal and functionality technical discussions. ElasticSearch payment statistics code review and discussions. Discussions on voice related hugginface AI models, benchmark, and possible tasks. GCP Vertex AI permission settings and service account. Experiment with commercial XTTS and TTS models.

2023-10-02 Mon (1.0h): Bot analytics reporting permission setup. Data export. Discussion and bot code review on payment amount capturing

---

2023-09-29 Fri: (6.0h) Bug fixes on trasient bot state for analytics. End-to-end testing. Research and experiments on state of the art speech related models, performance metrics, pratical experience, and use cases. Analysis and discussion on Whatsapp business platform and bot feasibility.

2023-09-28 Thu: (4.0h) Fix time measurement issues, type issues, and compile issues with the bot. Kibana dashboard update, raw log view setup, and version rolling. Testing end-to-end and data analytics. Review analytics data. Review context and session constructions in grammY. Move request-based transient data to appropriate places Fix issues with negative time measurement for good.

2023-09-27 Wed: (4.0h) Discussions on bot, voice AI products, technical limitations, and use cases.

2023-09-26 Tue: (1.0h) Research on voice AI state of the art demos and improvements (tortoise, coqui, bark, fastspeech, naturalspeech, promptts, and others).
