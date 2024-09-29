**Q3 Review Draft:**

In Q3, my primary focus was on replicating our GMX fork, testing various Telegram Mini Apps and prediction markets, and most notably, developing the Hod1 Telegram Bot. The initial phase of Hod1 involved building a Telegram bot for lottery trains by implementing smart contracts and designing the user interface on Telegram. Over time, I transitioned the Hod1 app from a chat-based interface to a full-fledged Telegram Mini App, replacing the lottery trains with an incentivized reward-based system.

I developed the front-end UI using React and JavaScript components tailored specifically for the Telegram Mini App environment, deploying it to Netlify. Key features I implemented include a leaderboard page, a social login system (YouTube subscription verification using OAuth), a reward system for watching videos from our YouTube playlist, and a referral system that incentivizes user growth by awarding points for referring new users. On the backend, I created and deployed a REST API and server on Heroku to manage user data, such as points, watched videos, and task completion, as well as retrieving user rankings. Additionally, I explored and tested various prediction market platforms, including Polymarket, Gnosis, and TON, for potential integration with the Harmony blockchain.

---

2024-09-28 Sat: Further testing pump, and looked jnto links on solana token launch. Worked on adding links to Q3 summary and further refinery.

2024-09-27 Fri: Further looked into client-side for 1market-demo and tried redeploying contract on local. Also continued looking through the links on the memecoin notion page, and pump.

2024-09-26 Thu: Looked into client components and configuration for 1market-demo. Started working on memecoin prediction by researching through the links on Solana token launch.

2024-09-25 Wed: Team sync with Li, Frank, and Theo, and refined Q3 review as well as started working on Q4 goals. Further looked into 1market repo to understand architecture for bot integration.

2024-09-24 Tue: Started looking into [HarmonyOneBot repo](https://github.com/harmony-one/HarmonyOneBot) and further looked into [1market repo](https://github.com/harmony-one/1market-demo/tree/1market_demo) in preparation for integration. Further refined Q3 review, and researched prediction markets on Messari.

2024-09-23 Mon: Continued cleaning/reorganizing react components for Hod1. Looked into Kings and Quests, further looked into Gnosis contracts, refined Q3 review.

---

2024-09-22 Sun (2.0h): Worked on writing draft for Q3 review. Further tested Polymarket.

2024-09-21 Sat (1.5h): Looked into code for 1market demo repo. Also fixed a couple bugs related to netlify build folder/router for Hod1.

2024-09-20 Fri: Continued working on updating UI for Hod1 and redability of code. Further tested Polymarket, and continued testing similar Telegram Mini Apps for Hod1.

2024-09-19 Thu: Continued working on implementing logic for adding points when subscription verified - altering the code for point and user system as it currently is only adapted to videos, working on making it more general/cleaner code. Further look into Gnosis repo for 1market.

2024-09-18 Wed: Debugged Google oAuth token error by fixing GoogleApi endpoint - now Youtube subscriber verification correctly works. Working on modifying it to update the user points when subscription verified, and adding pop-up modal UI so that the SocialTasks page UI is cleaner.

2024-09-17 Tue: Looked more into Gnosis conditional tokens repo for 1market. Continued working on social media oAuth and memory for Hod1, started working on UI improvement (perhaps, similar to Tapswap's).

2024-09-16 Mon: Further worked on Hod1 by working on how to verify user retweets. Also looked into moving memory from local in server to database. 

---

2024-09-15 Sun (1.0h): Worked on organizing code for hod1, dividing parts into separate react components. Looked into how to verify users retweeted our tweets.

2024-09-14 Sat (9.0h): Completed YouTube implementation (just waiting for app approval from Google Cloud to use YouTube Data API scope) - debugged Cloud console API configs, created google login page with oAuth, created auth redirect handler page, added API to verify subscriber in subscriber list, submitted a app verification request form to Google. Youtube verification now works by making user open login page in system browser and login to YouTube via oAuth (not allowed to directly open within Telegram Mini App), then checking their subscription and redirecting them back to Telegram.

2024-09-13 Fri: Worked on Youtube integration and moving user data to a database instead of memory to avoid data reset. Also looked into Gnosis conditional tokens.

2024-09-12 Thu: Implemented referral code system that works through a link to open app with referral code parameters and implemented logic to correctly award new users + their referrers with points. Implemented leaderboard system to show ranking of users with top scores, modified app navigation to have bottom navigation tool bar, changed organization of "Tasks" page to a tab-based system to sort different tasks depending on category (videos, social media, etc), and updated ReadMe (repo [here](https://github.com/harmony-one/Hod1)).

2024-09-11 Wed: Further looked into alternative options for Polymarket with better open source. Created youtube subscriber oAuth integratation for Hod1, working on merging to main repo.

2024-09-10 Tue: Tested and minted NFTs on Sepolia with [Skateboard workshop](https://park.skatechain.org/) on SkateChain and Galxe, tested Hamster Kombat. Discussed about 1market in team sync, further tested polymarket (seems a little buggy resolving deposits from Coinbase), and looked into repos for alternatives as well (sx-bet, Kalshi, Hedgehog Markets).

2024-09-09 Mon: Further tested with Polymarket. Continued working through referral links and youtube subscription for Hod1.

---

2024-09-08 Sun (1.5h): Looked into Polymarket for our 1market. Further looked into Skate + continued working on referral links for Hod1.

2024-09-07 Sat (1.0h): Tested $DOGS mini app, and worked on connecting binance account. Further look into Skate (Zealy and Galxe campaigns).

2024-09-06 Fri: Worked on youtube user verification integration: oAuth to ask for username and using webhook to verify subscribers list. Also looked into dogs miniap, and currently researching ways to generate referral links + verify them.

2024-09-05 Thu: Re-configured configurations (Botfather, API keys, t.me miniapp url) for Hod1 bot, renamed to @HarmonySocialBot. Worked on re-structuring organization of tasks/quest data, and also working on implementing verification for YouTube subscription (seems straightforward to do it with oAuth /manually asking their username, but ideally we'd do it with just redirect like Tapswap and not ask for username authentication so looking into DeepLinking.)

2024-09-04 Wed: Read through and researched the links on [1Market](https://stse.substack.com/p/1market-as-binary-options-for-explosive). Looked into Skate chain docs, started working on react-navigation for Hod1, and tested Blum.

2024-09-03 Tue: Looked into Skate, Polymarket, wagerbot, and Hamster Kombat. Discussed insights/clarified some issues for Hod1 through team sync, and worked on smaller tasks (troubleshooting Telegram account, Fragment auction, reviewed current Hod1 code and forked to harmony repo.)

2024-09-02 Mon (Labor Day, 1.5h): Continued looking into gas update issue in our developer documentation. Also looked into vidiq and other scraping services collecting Youtube data.

---

2024-09-01 Sun (2.0h): Looked into our [developer documentation](https://docs.harmony.one/home/developers/getting-started) and see if up-to-date. Specifically, looked into commands regarding estimateGas issue.

2024-08-31 Sat (3.0h): Further continued working on restructuring code + database. Also looked into how to connect wallet + referrals on Tapswap.

2024-08-30 Fri: Cotinued working on improving UI, Telegram Mini App navigation, and user database for storing user data. Further continued with Tapswap testing and restructuring Hod1 repo files for cleaner code.

2024-08-29 Thu: Continued with Hod1: implemented logic to block skipping/fastforwarding video, fixed react effect hook issue, updated UI [[PR here](https://github.com/rika97/Hod1/pull/5)]. Further worked on updating UI (tested Tapswap for implementing navigation buttons) and working on user database to move from current heroku server.

2024-08-28 Wed: Added video player for [Hod1 (miniApp branch)](https://github.com/rika97/Hod1/commits/miniApp/) using 'react-player', and implemented a tracker to keep track of user's viewing status for the video every fraction of a second to verify that they have indeed watched the video until the end. Production deploy that was earlier working stopped working correctly, reverted production commit to last working one and currently debugging issues (perhaps related to cache problems and Material-UI rendering.)

2024-08-27 Tue: Created YouTube stats REST API, added inline keyboard menu button to Hod1, updated readme doc [[PR Here](https://github.com/rika97/Hod1/pull/3)], and started working on embedded video player. Gained insights on Telegram Mini App game apps (tested Hamster Kombat) by our team sync, conducted market research on tap-to-earn games.

2024-08-26 Mon: Big progress🥳, transformed [Hod1](https://github.com/rika97/Hod1) from chat-base interaction to Telegram Mini App, correctly updates user NIL balance, and stores/hides watched videos. Created front-end for web-app with React and deployed to Netlify, created backend for bot interaction, created REST API for user interactions and fetching/pushing stored user data (both deployed to Heroku), integrated web frontend to Telegram bot, and wrote production notes [here](https://github.com/rika97/Hod1/blob/main/README.md).

---

2024-08-25 Sun (1.5h): Further testing with Tapswap and Ton ecosystem community projects. Continue upgrading chat bot to mini app.

2024-08-24 Sat (2.0h): Fixed heroku server deploy error, hod1 bot now works (@HarmonyLotteryBot). Now further testing Tapswap and looking into upgrade UI from text chat to miniapp.

2024-08-23 Fri: Tested Tapswap, [created a MVP](https://github.com/rika97/Hod1/commit/886abc720b19c8b11c6b5c301e607d71bce53933) for a new version of our Hod1 bot. It can now store and retrieve each user's NIL balance, show list of videos to watch for rewards, and allow users to type '/watch' along with video id to gain reward (you can test @HarmonyLotteryBot, but Heroku server may be buggy. In that case, you can clone [this repo](https://github.com/rika97/Hod1) and run on local, I will give you API key.)

2024-08-22 Thu: Set-up off-chain user database with MongoDB since storing data (friends, etc) at a large-scale on a smart contract can be challenging and started investigating how to implement the backend to handle interactions between contract and database. Continued market research with TON ecosystem by testing apps/reading through telegram community account messages, started writing summary notes [here](https://www.notion.so/harmonyone/3ed75673844e4cefa233a2a1617c540c?v=79ee561107094a94b4b297b4ab54d14a&pvs=4), and re-read through finalized 2025 roadmap document.

2024-08-21 Wed: Working on debugging smart contract startTrain() function, issues regarding data type when storing participant info for each train. Further tested TON space (also update: yesterday's bid for fragment was overriden as someone else put a higher bid, will keep bidding for cheaper numbers.)

2024-08-20 Tue: Looked into the general overview of Harmony's current progress by adding some notes to the 2025 roadmap and syncing with Li. Conducted some research on Telegram social games, further testing with TON space, monitored and placed bid on Fragment for telegram number.

2024-08-19 Mon: Worked on updating [smart contract](https://github.com/rika97/Hold1-contracts/commit/cd1ab6570fec1ab081efa1d37663db488bd5f481) for Hold1 train, created a [testing space](https://github.com/rika97/hold1-test) with scaffold-eth to test run the contract on Harmony testnet, currently still figuring out about storing user/friends list in database. Looked through Harmony 2025 roadmap, writing down notes to be discussed in tomorrow's sync.

---

2024-08-18 Sun (1.5h): Started working on the [smart contract](https://github.com/rika97/Hold1-contracts/blob/main/contract.sol) for lottery train: outlined some of the functions needed and implemented some logic. Working on figuring out how to setup user database system and connect it to this contract (to fetch data such as friends, new user, etc.)

2024-08-17 Sat (2.0h): Brainstormed and came up with an overview on how to integrate the Hold1 lottery train with telegram bot and the list of commands/app structure required (outlined some tasks [here](https://github.com/rika97/HarmonyLottery/blob/main/README.md).) [Updated](https://github.com/rika97/HarmonyLottery/commit/58d5b7fc8fbb36e05e72a37a496945fa5e59c0f0) bot commands from those listed on /Lottery to commands required for implementing Hold1.

2024-08-16 Fri: Continued working on Hold1: looked into + outlined process for smart contract logic to implement "Hold1 train" (step 4). Also worked on implementing user regsitration and management on telegram bot (step 5).

2024-08-15 Thu: Created [Harmony Lottery website](https://rika97.github.io/HarmonyLotteryWebsite/) using [Github Pages](https://github.com/rika97/HarmonyLotteryWebsite/tree/master), created [Telegram bot](https://github.com/rika97/HarmonyLottery) (@HarmonyLotteryBot) which now has 4 interactive commands (/register, /buyticket, /draw, /winners), and deployed bot server on Heroku. Now working on step 5 of [Lottery](https://github.com/carokiainfox/Lottery), by creating user database for implementing lottery logic with mongoose.

2024-08-14 Wed: Tested Telegram wallet P2P market by creating new overseas account. Started working on recreating [lottery](https://github.com/carokiainfox/Lottery) on Telegram app by creating a new bot, currently working on implementing bot commands and integrating TON.

2024-08-13 Tue: Read/watched and researched through the links on [/yen](https://xn--qv9h.s.country/p/black-forex-yen-carry-trade-yield) (dollarendgame, delphi digital). Resolving telegram wallet region issues (requested verification but their automated process is faulty, cannot does not detect residency document in foreign languages. Changing number to JP number did not work. Currently working on making new account with JP number.)

2024-08-12 Mon: Tested telegram apps such as staking (Tonstakers, TonPad), wallets such as Telenova and Pixel Wallet, and looked into NotCoin. Also looked into more apps listed on Tonkeeper.

---

2024-08-11 Sun (1.5h): Tested for non-US username on telegram. Looking into ways to override territorial issues.

2024-08-10 Sat (2.0h): Tested with TON Space on Telegram wallet, found main that the main feature was that minted NFTs for Telegram Usernames ([contract here](https://tonviewer.com/EQCA14o1-VWhS2efqoh_9M1b_A9DtKTuoqfmkn83AbJzwnPi)) shows as "Collectibles" within the app (still in beta mode but users can also see transactions, stake, and swap within the app.) Tested more NFT and Utilities apps on Tonkeeper, found interesting apps such as TON Domains, TON Midjourney, and TON VPN (can be used with OpenVPN).

2024-08-09 Fri: Viewed Harmony X Space recording, further looked into CLI scripts for squeeth (MintAndShort, MintAndLP, OpenLong). Started working on perp trading with telegram wallet (created wallet+bought tokens on Tonkeeper, purchased telegram account on Fragment), tested with Storm Trade Bot by opening a position (TON-USDCM).

2024-08-08 Thu: Facing some issues with hardhat when deploying some of the contracts in squeeth, working on debugging. Also looked into the new swap router updates (DeploySwapRouter.sol, GetCode.sol).

2024-08-07 Wed: Looked into squeeth-monorepo, compiled some trade executions for test, looked into ISwapRouter.sol and Test.sol for exactInputSingle issue as well as understanding overall code + reviewing recent commits. Continued looking into signer data for earn page on gmx.

2024-08-06 Tue: Continued debugging signer in StakeV1 (for GMX Earn page). Signer bug comes from delay due to improper React useEffect hook when fecthed from useWallet.ts, was able to fix useWallet.ts to return signer after data loaded from wagmi's useWalletClient but still trying to fix rerendering issues in StakeV1.js.

2024-08-05 Mon: Continued working on testing squeeth monorepo. Worked through understanding CLI scripts (MintAndDeposit, BurnAmount, DepositCollateral.) 

---

2024-08-04 Sun (1.5h): Started replicating Opyn squeeth trading (setting up configurations.) Working on testing to suggest improvements.

2024-08-03 Sat (2.0h): Continued debugging the ethers signer problem in stake. Read through Simaro's Opyn Squeeth documentation/monorepo.

2024-08-02 Fri: Updated some constants for token/chain configs. Continued looking into React hook/ethers bug raised from signer in the Stake Modal in StakeV1.

2024-08-01 Thu: Working on adapting "Earn" page for GMX Harmony fork. Debugging some configuration issues raised in StakeV1 and tokens.ts.

2024-07-31 Wed: Started looking into Synthetix: tested stake & borrow (SNX tokens) on sy.country. Worked on replicating Harmony's synthetix: cloned [synthetix Harmony fork](https://github.com/ArtemKolodko/synthetix/tree/harmony_new_deployment) and [synthetix-js-monorepo](https://github.com/ArtemKolodko/synthetix-js-monorepo), worked on deploying contracts and BandOracleReader (reading through [Aaron's notes](https://github.com/polymorpher/synthetix-v2/blob/band-oracle/oracle-notes.md) on oracles.)

2024-07-30 Tue: Conducted research on Mode Network (livespace, ModeMax, posts on blog: mode.mirror.xyz, X, discord). Looked into Harmony GMX Security audit and Yuriy's priceFeed update using band oracle integration.

2024-07-29 Mon: Continued looking through the links on finance for dependent type security, languages & formalism. Further continued testing gmx-interface and looking into gmx-synthetics.

---

2024-07-28 Sun (1.5h): Looked into [b.country](https://stse.substack.com/p/bitcoin-futures-and-options-on-harmony) and [Chaos Summer](https://stse.substack.com/p/invincible-summer-fight-to-recovery). Also looked into [strong proofs for secure finance](https://stse.substack.com/p/dependent-types-as-strong-proofs), reading into links on formal security, dependent-type security and OTPs.

2024-07-27 Sat (1.5h): Continued looking through gmx contracts for rewards and leaderboard. Continued testing ux and seeing features for improvement.

2024-07-26 Fri: Reading through [GMX v1 docs](https://docs.gmx.io/docs/trading/v1) to get insight on topics/organization of documentation, brainstorming ideas on how to write on our version. Further looking into the rest of the features not yet replicated in our fork: understanding how rewards/incentives work by reading through contracts, looking through community projects on ecosystem (Copin, Blueberry, etc.)

2024-07-25 Thu: Kept further working on GMX: Tried interface with new price keeper/contracts update, tested current UX of gx.country to observe notable bugs/modifications. Created a [Gitbook](https://harmony-5.gitbook.io/harmony-gmx-docs) to start writing Harmony's version of GMX docs.

2024-07-24 Wed: [Updated](https://github.com/harmony-one/gmx-interface/pull/7) UI (fixed links, modified navigation header, modified GLP to GXP) for gmx-interface. Deployed new contracts with [h-gmx-contracts](https://github.com/harmony-one/h-gmx-contracts), updated [interface](https://github.com/rika97/gmx-interface-replica/pull/1) and [price-keepers](https://github.com/rika97/gmx-price-keeper/pull/1) with new addresses.

2024-07-23 Tue: Working on replicating new updated deploy script for gmx-contracts and keepers. Also working on updating UI/UX for price-updates/graphs, and fixing some links on interface.

2024-07-22 Mon: Looked into how code for "leaderboard" stats work with subsquid+GraphQL client, and features on "earn" page (vesting, staking, esGMX/rewards, incentive program, voting). Further investigating how [V1 contracts](https://github.com/gmx-io/gmx-interface/blob/master/src/config/contracts.ts) for [staking](https://docs.gmx.io/docs/api/contracts-v1#staking) works, and updated some notes [here](https://github.com/harmony-one/h/blob/main/docs/gmx-features.md).

---

2024-07-21 Sun (2.0h): Investigated GMX app (dashboard and leaderboard) and looked into their code (gmx-stats, gmx-subgraph, gmx-interface). Looked into how they were querying subgraph data and [updated](https://github.com/harmony-one/h/blob/main/docs/gmx-features.md) notes on how they are deployed.

2024-07-20 Sat (3.5h): Investigated code for GMX referrals and how they work (distribution, tiers, referral codes), wrote a summary [here](https://github.com/harmony-one/h/blob/main/docs/gmx-features.md). Doing the same for Dashboard, and looking into how they interact with gmx-stats.

2024-07-19 Fri: Updated gmx-interface with all GLP (for UI text) to GXP ([PR here](https://github.com/harmony-one/gmx-interface/pull/6)). Moved my gmx-interface replica from fork to a new repo [here](https://github.com/rika97/gmx-interface-replica) and redeployed to rh.country (created a new clean slate fork so I can PR to harmony-one/gmx-interface without including my version of config addresses). 

2024-07-18 Thu: 
[Modified and redeployed](https://github.com/rika97/gmx-contracts/commit/660e8aefb5c0762c82bbfa0ef5b0761de0dee987) "set-tokens" + "deployPriceFeed", and updated [price-keeper](https://github.com/rika97/gmx-price-keeper/commit/0723cfcc79d27fb9273d993c515171e116b8fc75) + ["gmx-interface"](https://github.com/rika97/gmx-interface/pull/6) with new addresses. rh.country is now up-to-date with gx.country and contract addresses are stored at [deployAll](https://github.com/rika97/gmx-contracts/commit/ff5ae0ce780230c0ba79396f5f6a270e32cd76a2#commitcomment-144359366) and [fastPriceFeed + Vault](https://github.com/rika97/gmx-contracts/pull/7).

2024-07-17 Wed: Redeployed all contracts [https://github.com/rika97/gmx-contracts/pull/5], priceFeedTimeLock (addresses [here](https://github.com/rika97/gmx-contracts/commit/ff5ae0ce780230c0ba79396f5f6a270e32cd76a2#comments)), deployPriceFeed [https://github.com/rika97/gmx-contracts/pull/6] (addresses [here](https://github.com/rika97/gmx-contracts/pull/6)). Updated gmx-interface with some of the new addresses [https://github.com/rika97/gmx-interface/pull/3].

2024-07-16 Tue: Monday continued. Still having troubles with redeploying some of the contracts, looking into scripts to figure out the issue of when adding address to interface (seems to be mistmatch when using address from deployAll). Also working on syncing interface with new addresses from contracts, and looking into hardhat.config and helpers.js to debug deployPriceFeedTimelock with framesigner issue.

2024-07-15 Mon: Working on updating all contracts to display liquidity and price correctly. Also working on token configuration for GMX (deploying set-tokens script).

---

2024-07-14 Sun (1.5h): Bugs in current deploy on rh.country for gmx-interface found: prices for opening positions (long, short, swap) are not corrrectly rendering, looking into this issue. Also looked into [liquidity (rewardRouter) fix](https://github.com/potvik/gmx-contracts/commit/44106a0add88d14a33577ffb7d0cbdc707c3c096) and bug for adding positionRouter contract to interface.

2024-07-13 Sat (2.0h): Further look into gmx-subgraph pricing issue (how to configure for Harmony.) Also looked into 
some recordings from EthCC 2024.

2024-07-12 Fri: Deployed keepers script locally (planning to also replicate deploying on host service). Debugging issues related to adding fastpricefeed to reflect on keepers. Looking into gmx-subgraph pricing issue.

2024-07-11 Thu: Read through Theo's Harmony perpetual launch plan gmx. Worked on debugging scripts for deploying pricefeedtimelock,  vaultpricefeed and checked for missing contracts from deloyAll script.

2024-07-10 Wed: Re-deployed contracts for [deployPriceFeedTimeLock](https://github.com/rika97/gmx-contracts/pull/1) in gmx-contracts and updated contracts from deployAll script into [gmx-interface](https://github.com/rika97/gmx-interface/pull/1). Deploy script was not working as expected due to signer problem, updated script for deploy PriceFeedTimelock.js. Working on debugging contract address error regarding PositionRouter and also investigating missing components in deployAll script such as tokenManager.

2024-07-09 Tue: Meeting with Li, and looked into more about Balaji and Dalio. Deleted previous and created a new fork for [gmx-contracts](https://github.com/rika97/gmx-contracts), worked on deploying gmx contracts for fastPriceFeed, trying to replicate [Yuriy's price feed contracts deployment script](https://github.com/potvik/gmx-contracts/commit/80f1caf25eaffc6d9f31f88c778c9e519df33e8e#diff-f3bb021897a1d6b42fe3c000dfea4a38bc19f77f4cb989aa8b62640c7bb4a677) to run keepers script on local and display correct price on interface.

2024-07-08 Mon: Connected with Yuriy on GMX, still working on implementing keeper API, and looking through the workarounds for subgraph issue. Will update in a few hours again (still working tonight). Updated my /progress with summary of project links for each quarter (listed under each review section.)

---

2024-07-07 Sun (1.5h): Continued further reading and watching youtube videos on S*.

2024-07-06 Sat (1.5h): Tested gx.country. Read through S*: Social Finance, Superchain, Synthetic Futures on Substack and looked through some of their links.

2024-07-05 Fri: Work on replicating refactored keeper service code and further continued work on integrating the apis to reflect on interface.

2024-07-04 Thu (1.0h): Holiday: Fourth of July. Further continued looking into integrating gmx repos (keeper, gmx-stats) to reflect on interface.

2024-07-03 Wed: Looking into how to integrate price keeper to contracts and price feed configuration. Also working on deploying gmx-stats.

2024-07-02 Tue: Deployed production build of gmx-interface (first to cloudflare but isn't compatible with 1.country so moved to netlify.) Worked on updating the interface to integrate keepers API for price feed.

2024-07-01 Mon: Debugging issues regarding to setting DNS and CNAME configurations for rh.country (will come back to this later since I need account access to cloudflare). Further looking through the keeper service API to update GMX interface replica.

---

**2024 Q2 Review (36.5 Hours)**

For [Another World](https://x.com/harmonyprotocol/status/1775979150630596911), I implemented smart contracts on Harmony's shard 1 to [transition Bitcoin Runes into ERC20 tokens](https://github.com/harmony-one/h/blob/main/docs/anotherworld-runes.md). This project involved a two-step process: first, creating a smart contract to mint tokens (wrapped Rune), and second, developing another smart contract (token factory) to serve as a custodian for the wrapped Runes.

Additionally, I conducted [research](https://github.com/harmony-one/h/blob/main/docs/leveraged-perp-trades.md) on perpetual trading platforms such as Jupiter and Vertex, with a particular focus on their leverage features. Using Dune analytics, I analyzed the [most profitable trades on GMX](https://github.com/harmony-one/h/blob/main/docs/top-gmx-traders.md), focusing on the profit-and-loss of top traders and their trading pairs. I also worked on replicating GMX and adapting its configurations to function on Harmony's shard 1. This involved the complex analysis and deployment of repositories such as GMX-contracts, GMX-stats, and GMX-synthetics. The interface will soon be deployed to the front-end.


**2024 Q2 Relevant Deliverables Links Summary**
 - AnotherWorld Rune to ERC20 wrapper
   - [Code Repo](https://github.com/rika97/scaffold-eth-2)
   - [Documentation](https://github.com/harmony-one/h/blob/main/docs/anotherworld-runes.md)
   - [WrappedRune Factory contract](https://explorer.harmony.one/address/0x97E633cC18473799cED685f6E90A01f302788B17?shard=0)
   - [WrappedRune contract](https://explorer.harmony.one/token/0xB485E2367b18077fE6126DdE60Ba01Ee33800d4c?shard=0)
 - Perps
   - [GMX Top Traders Dune Analysis Documentation](https://github.com/harmony-one/h/blob/main/docs/top-gmx-traders.md)
   - [GMX Top Traders Dune Analysis Dashboard](https://dune.com/rikaharmony/gmx-dydx-stats)
   - [Leveraged Perpetual Trading Platforms](https://github.com/harmony-one/h/blob/main/docs/leveraged-perp-trades.md)
   - [GMX on Harmony (Yuriy's work, not mine)](https://gx.country/)
   - [GMX on Harmony replicated on rh.country](https://rh.country/#/v1)
   - [/chart (perps market research)](https://docs.google.com/spreadsheets/d/1u8dfUT5hRPi-9F80NWSIvoS9hG5yHc1lKwqLgej62Kg/edit?gid=0#gid=0)

---

2024-06-30 Sun (1.5h): Worked on configuring rh.country to deploy my gmx-interface. Read through S*: Social Finance, Superchain, Synthetic Futures on substack.

2024-06-29 Sat (1.5h): Worked through understanding Yuriy's keepers scripts. Specifically, replicating [position keeper for GMX](https://github.com/harmony-one/gmx-price-keeper/commit/a5817f73dc3d1eb349d4c4d1d792f9af2a290f0f) and [Service API](https://gmx-keeper.fly.dev/api).

2024-06-28 Fri: Looked into [Balaji & Dalio substack](https://stse.substack.com/p/balaji-and-dalio-dollar-crisis-vs), "changing world order" and "how the economic machine works" video, Balajis substack posts (fiat crisis, bond villain, etc). Looked into Squeeth portal, [variance perpetuals](https://research.opyn.co/variance-perpetuals), continued further looking into Squeeth monorepo.

2024-06-27 Thu: Continued further work on Squeeth monorepo by looking into their code for subgraphs and interface. Tuned into TGI-S*. Read through more links posted on /ETH^2 (OPYN AMA, etc).

2024-06-26 Wed: Continuation on power perpetuals: cloned Squeeth monorepo, read through gitbook documentation (crab and zenbull strategies, payoff diagrams, auction, oSQTH.) Worked on setting up environment + dependencies for packages/frontend, also looked through core contracts and deploy script for hardhat local deployment.

2024-06-25 Tue: Looked into Yuriy's GMX v1 updates and worked on replicating them (keepers scripts integration, deploy scripts.) Investigated S3 buckets for deploy. Continued with research on Opyn ETH (incentives for LPs, Bull Strategy, Liquidity, etc.)

2024-06-24 Mon: Read into Uniswap math insights series on [Medium](https://medium.com/@med456789d), looking into LP hedging and Bachelier model. Cloned Uniswap's [v3-core](https://github.com/Uniswap/v3-core) and looked into their smart contracts (Factory, Pool, PoolDeployer, interface.)

---
2024-06-23 Sun (1.5h): Saturday continued. Looked into Topaze Blue, partially collateralized options with Opyn (tutorial video), AD Derivs, Defi options and derivatives.

2024-06-22 Sat (1.0h): Looked into further documentation and links on /eth-power: Pods Yield, Olive Network, and Power Perpetuals.

2024-06-21 Fri: Continued reading through links on "on-chain & open source perpetual". Also read through on opyn protocols (crab strategy, ribbon, impermanent loss, pods finance, olive network). Started looking into replicating [Ribbon Finance v2 theta vault](https://github.com/ribbon-finance/ribbon-v2). 

2024-06-20 Thu: Read through substack docs on Timeless Story + ETH^2 (Power Perpetuals, Jumbo Crab) and their links. Joined Launchpad live. Went over some document work with Amanda. Attended Kush's TGI-AI event.

2024-06-19 Wed (1.0h): Holiday. Reworked theough /progress and some AWS for gmx fork deployment.

2024-06-18 Tue: Continued with rewriting my past progress (will upload them once finished). Checked out Yuriy's updates on the positions feature of GMX-subgraph Harmony fork (storeVolumeBySource), and worked on deploying some of the missing contracts in deployAll script for GMX-contracts.

2024-6-17 Mon: Worked through my Q2 deliverables with Li, got AWS debugged with Soph, reworking through my previous /progress adding links/metrics to make my deliverables so far more clear. Currently working on GMX (will update this page again later tonight.)

---

2024-06-16 Sun (2.0h): Continued work with GMX synthetics scripts, specifically working on config, and further looking into more contracts (oracle system, pricing, fees, and market). Further worked on refining my Q2 goals.

2024-06-15 Sat (1.0h): Refined Q2 goals by incorporating specific links and metrics to ensure clarity and measurable outcomes. Additionally, rewrote progress updates to provide a clear and comprehensive overview of achievements and areas needing attention.

2024-06-14 Fri: Continued the refinement of Thursday's work and initiated an in-depth analysis of the GMX synthetics by cloning repo, reading through the contracts and the deployment scripts to see how each of the functions work and if this can be deployed to shard 1.

2024-06-13 Thu: Further continued work on liquidity function, positions, stats modules on GMX-subgraph. Listened to twitter space. Initiated an in-depth analysis of the GMX synthetics contracts by reading through the ReadMe on General & Technical Overview, understanding the swaps, position orders, order pricing, oracle prices, funding fees, etc.

2024-06-12 Wed: Investigated the processes for opening positions and the swap function within the GMX fork to enhance liquidity management. Additionally, focused on resolving display issues for charts to ensure accurate and user-friendly visual data representation.

2024-06-11 Tue: Currently working with Soph to get AWS setup. Further examined the prices and stats code from the GMX-subgraph repository and reviewed Yuriy's progress to streamline the deployment of statistical data.

2024-06-10 Mon: Redeployed several GMX contracts with Yuriy's assistance and updated the GMX interface to reflect these changes. Explored methods to display chart positions on the front end by leveraging mapping and helper functions from the GMX subgraph repo, ensuring accurate real-time data visualization.

---

2024-06-09 Sun (3.5h): Updated GMX-interface with my deployed contracts and commited to a [forked repo](https://github.com/rika97/gmx-interface/tree/harmony). Working on debugging some contract deploys and updating user interface with charts, looking into ["gmx-subgraph"](https://github.com/harmony-one/gmx-subgraph) (network chart does not seem to be displaying correctly, also trying to figure out the contract address configuration for "Synthetcis" by looking into the deploy script.

2024-06-08 Sat (2.5h): looked into how to deploy onto my domain with AWS S3 bucket. Looking into deployment configurations with gmx-interface.

2024-06-07 Fri: Continued research and looking into links + relevant content on the protocols mentioned on /perps (Gauntlet, Gearbox, Vega, Voltz, etc).

2024-06-06 Thu: Synced with Li. Continued watching through remaining options trading videos, more reserach into dydx, started reading /perps.

2024-06-05 Wed: Continued watching through the links on options trading/Panoptic ("LPs are selling free options", "AD Derivs", "Introducing Panotpic", "KB7 Defi Guild", "Defi Toronto").

2024-06-04 Tue: Watched through panoptic oracle-free options trading talk, looked for slides, took screenshots. Watched other talks by Guillaume Lambert ("Your Protocol's Token Will Go to Zero", "Quantum Trades", "Taking DeFi Options To The Next Level").

2024-06-03 Mon: Continued working on deploying GMX clone to testnet (status by 6PM, will update this later as I continue work).

---

2024-06-02 Sun (1.0h): Continued working on deploying GMX clone to testnet.

2024-06-01 Sat (1.0h): Started to work on deploying clone of Yuriy's GMX replica to testnet.

2024-05-31 Fri: Returned to previous tasks that were still pending: looked through GMX clone code, played around with https://gmx-harmony.web.app/, looked through "hardhat-starter-pack" for issues.

2024-05-30 Thu: Office move out, watched dydx's Panoptic Eth-Denver talk and took screenshots of the slides, continued watching options trading essentials playlist.

2024-05-29 Wed: Looked into options trading, specifically by watching the options trading essentials [playlist](https://www.youtube.com/playlist?list=PLg1ZigTkffEYONORRq7FLA4XecwQ4OVuv).

2024-05-28 Tue: Continue studying finance course on Khan academy, market research on Panoptic.

2024-05-27 Mon (Memorial Day, 2.0h): Watched [Synthetix V3 video](https://www.youtube.com/watch?v=66m9BKiQSDs), researched on Panoptic (read blog, twitter) and read a couple of blog posts by Guillaume Lambert on Medium.

---

2024-05-26 Sun (1.5h): Looked into Gammaswap Docs for Trade Perpetual options (PnL, Risk, etc). Also looked into "Black-scholes formula" on Khan academy and watched other parts of the "finance and capital markets" course.

2024-05-25 Sat (1.5h): Read through [Panoptic Options Trading Strategies](https://panoptic.xyz/research/panoption-trading-strategies-the-basics), looked into Lemma Labs and InfinityPools.

2024-05-24 Fri: Continued market research by reading through the links as posted on "invincible summer". Looked up more into details of GMX technical overview (vault, routers, price feeds.)

2024-05-23 Thu: Continued replicating GMX v1 code, read through contracts/docs. Read many articles and researched on trading: strategies, options trading, Messari & Delphi digital reports, perp comparisons.

2024-05-22 Wed: Forked Yuriy's GMX v1 deploy code, looked into docs, and worked on replication + understanding code.

2024-05-21 Tue: Read ["Invincible Summer" post](https://stse.substack.com/p/perps-invincible-summer-of-1000x) and their links, researched into topics such as "order books", "history", "product roadmap", "synthetic margin trading", "crypto-native insurance", etc.
Looked through "dydx v4", "GMX v2", "0x defi derivatives" contracts repo and docs. Looked into Solcasino and [top web3 gambling dApps](https://dappradar.com/rankings/category/gambling).

2024-05-20 Mon: Completed 'mainnet launch date'. Added some parts to 'forked from', 'block finality', 'roadmap', 'whitepaper', 'audit', 'BTC bridge'. Added 'twitter', 'blog', 'github', 'userguide' for newly added projects. TO-DO: complete 'forked from', 'block finality', 'transaction finality', 'match finality'.

---

2024-05-19 Sun (1.0h): Revised for some missing cells on /chart. A lot of projects seemed to be missing whitepaper.

2024-05-18 Sat (2.0h): Finished filling in the remainder cells for /chart ("whitepaper", "BTC bridge", and some of "ETH bridge"). 

2024-05-17 Fri: Filled in "user guide", "whitepaper", "audit", "token symbol", "top contributor", "hacks/incidents" on /chart. Need to still complete "BTC bridge" and some of the "whitepapers" that I couldn't find.

2024-05-16 Thu: Researched and added links for "Github", "docs", and "website" for /chart. Looked through existing charts and tables for dydx perpetual data on Dune to find the right asset for analyzing top traders and most profitable trades.

2024-05-15 Wed: Worked on /chart with Alaina, added all the data for 14 rows (from "0x" to "Perp v2".) Looked through 10+ datasets on GMX perpetual, found the most relevant one and analyzed the most profitable trades for all users + top 1000 users with the most PnL on Dune ([documentation](https://github.com/harmony-one/h/blob/main/docs/top-gmx-traders.md), [dashboard](https://dune.com/rikaharmony/gmx-dydx-stats)). Searched for datasets for dydx perpetual.

2024-05-14 Tue: Summarized work for [AnotherWorld/Runes project](https://github.com/harmony-one/h/blob/main/docs/anotherworld-runes.md) and [perpetual trading](https://github.com/harmony-one/h/blob/main/docs/perpetual-trading.md). Tested out more features on Vertex.

2024-05-13 Mon: Look into Dune analytics for daily users and profitable trades.

---

2024-05-12 Sun (1.0h): Saturday continued, further progress on Q2 milestones☀.

2024-05-11 Sat (1.0h): Looking further into GMX.

2024-05-10 Fri: Debugging some configuration and look into for Harmony hardhat starterpack repo. Playing around with perpetual exchange and reading docs on Jupiter (JLP Pool, trading), GMX (look into trading and couple of ecosystem projects). Vertex is restricted in the U.S., looked into similar trading platforms.

2024-05-09 Thu: Reviewed Q2 tasks for deliverables. Looked into LP-trader perpetual exchange on Jupiter, and Perps on Vertex.

2024-05-08 Wed: Further work on 20 things to do list. Looked into Ambient Finance for LP, Phaver app (farcaster) and some quests, etc.

2024-05-07 Tue: Look into Hyperlane/Nexus Bridge TIA, Arbitrum DeFi and Arcade, and some projects from Taiko ecosystem.

2024-05-06 Mon: Explored with NFTs on MagicEden.

---
2024-05-05 Sun (1.0h): Saturday continued.

2024-05-04 Sat (1.0h): Further look into debugging the configuration setup for hardhat starter pack.

2024-05-03 Fri: Looked into APIs for scraping and processing BTC Rune transaction data for our wrapping prototype. Looked into some of the projects mentioned in the "20 things to do" list tweet.

2024-05-02 Thu: [Created](https://github.com/rika97/scaffold-eth-2/commit/94935a6fb664615ba08c567eac34054c5baa681b) and deployed factory contract for ERC20. [Added](https://github.com/rika97/scaffold-eth-2/commit/a13fda98989d72e7bd61ce07ed9f2aa1822ad843) some front-end for Rune deposit page. Looked into our ["hardhat-starter-pack"](https://github.com/harmony-one/hardhat-starter-pack) to make updates to our repo with Adam.

2024-05-01 Wed: Made changes to configuration and fixed bugs so that contract now also works on Harmony, not just localnet ([commit](https://github.com/rika97/scaffold-eth-2/commit/aed2a4f71308ea99709fabe61780611d2bea03bb)). 

2024-04-30 Tue: Deployed smart contract using Hardhat and Scaffold-eth, and setup network configurations. [[Repo](https://github.com/rika97/scaffold-eth-2)]

2024-04-29 Mon: Created a minimal prototype for Rune -> ERC20 wrap ([deployed](https://explorer.harmony.one/address/0x8b981a0afae43cdb85cb89fbac1d75a4021e6269?activeTab=0
) smart contract onto Harmony using OpenZeppelin and Remix).

---
2024-04-28 Sun (1.5h): Looked into how to wrap tokens to ERC20 on Harmony blockchain using OpenZeppelin and Hardhat.

2024-04-27 Sat (1.5h): Ramping up to understand BTC Rune: their functionalities and overview.

2024-04-26 Fri: Had a meeting with Jackie and discussed the AnotherWorld project. We went over Rune coins on MagicEden, viewing transactions on brc20 API (eventually automate the process), opened my bitcoin wallet, overview of the end-to-end prototype, and how we can create a platform to wrap BTC Rune to ERC20 on shard 1.

2024-04-25 Thu: Conducted more research on token economics and Rollkit. Reviewed Jackie's document on AnotherWorld-Rune project and conducted some research regarding it. Refined my Q2 deliverables.

2024-04-24 Wed: Conducted market research for A(G)I data (specifically $EAT and $3D), existing validation with model training, data performance, labeling, and respective economic values. Worked on Q2 deliverables.

2024-04-23 Tue: Researched for Social A(G)I: ranking, farcaster frames (Farcaster.country) for "Human Protocol for love" (Hot or Not emoji reactions), $MAP (like Aaron's frames, token minting for location check-ins.)

2024-04-22 Mon: Aided with configuration debugging for Privy fork (Auth0 API key setup in swift project.) Looked into RUNE, zkproofs (AiMM: salary matching for candidates and recruiters, purchase data for e-commerce), and further work on Polygon CDK reading and following documentation.

---

2024-04-21 Sun: (1.5h): Looked into/play tested AnotherWorld in preparation for campaigns.

2024-04-20 Sat (2.5h): Working on the 3 goals for Q2 by conducting market research, mainly on cross-chain projects.

2024-04-19 Fri: Further work on Polygon CDK by folling through Roll-up tutorial, setting up Docker, building and testing Docker image, workaround for MacOS, configuring node deployment. Cleared office.

2024-04-18 Thu: Research on Hummingbot through checking out their Discord channel, watching their YouTube videos, and looking through their github documentation. Cleared office.

2024-04-17 Wed: Investigated Polygon CDK, following through their CDK rollup tutorial.

2024-04-10~16 : More candidate search, revision on 2 week deliverables and thought through/drafted Q2 achievement goals.

2024-04-09 Tue: Mon continued + also spent personal time at a software engineer meetup to build connections.

2024-04-08 Mon: More candidate search on lists on Layoff.fyi, LinkedIn, and Twitter. Also revised summary of story protocol deploy and looked into further integrations useful for our community.

---

2024-04-07 Sun (1.0h): Looked for more resumes and linkedin profiles on the layoffs list on layoff.fyi.

2024-04-06 Sat (1.0h): Fri continued, also looked for candidates on slack channels for tech groups.

2024-04-05 Fri: Looked for more resumes and profiles on LinkedIn search

2024-04-04 Thu: Looked into AI model datasets for our deployed story protocol contract + continued resume search.

2024-04-03 Wed: Continued resume search by testing existing database and testing job aggregator sites such as ZipRecruiter, PostJobFree, Monster, Indeed, Dice, Discord channels, etc. 

2024-04-02 Tue: Tested various ATS resume checkers + LinkedIn profile scoreres (Enhancv, ResumeWorded, Jobalytics, etc.)

2024-04-01 Mon: More resume search on LinkedIn. Got in touch with Jackie to later set DNS for 9.country.

---

**2024 Q1 Review (97 hours)**

In Q1, I researched over 100 Harmony network community projects, focusing on soulbound/inscription tokens and swapping mechanisms. I developed the OTP connection page for our social geo game website and created a Telegram bot for processing Harmony network transactions. Additionally, I led the development of Harmony's mobile applications using Gnosis Safe through forking and configuration.

Later in Q1, I analyzed AGI market trends, tested frames on Farcaster, and examined projects from 43 companies in the AGI Edge hackathon. Using the Story Protocol framework, I created robust royalty policies and deployed a smart contract for them on Harmony's shard 1. I also initiated the ONE Map project with React Native, implementing location check-in buttons with Firebase, refining the UI for /links, and facilitating OAuth authentication for Human Protocol across 7 platforms.

Deploying the Story Protocol on Harmony presented a formidable task, particularly in ensuring the seamless deployment of all 29 contracts upon which this singular contract depended. This endeavor also involved intricate configuration adjustments, transitioning the original contract deployed on Polygon to align with the parameters of Shard 1. Notably, amidst these complexities, the implementation of the royalty policy contract emerged as a pivotal feature, empowering users to specify dividend allocations for a designated IPID, thereby enhancing the platform's functionality and versatility.

**2024 Q1 Relevant Deliverables Links Summary**

 - Story Protocol
   - [Royalty Policy IAP contract on Harmony](https://explorer.harmony.one/address/0x54ef56ee76d696d33b9ba469a3bb5235aff46370?activeTab=6)
 - Human Protocol
   - [Human Protocol Github Repo (deprecated, moved to h.country)](https://github.com/harmony-one/human-protocol)
   - [h.country Github Repo](https://github.com/harmony-one/h.country)
   - [h.country Website](https://h.country/)
 - ONE Map
   - [ONE Map Github Repo (deprecated)](https://github.com/harmony-one/1/tree/main/map)
   - [ONE Map Github Repo (new version)](https://github.com/harmony-one/1/tree/main/socialMap/SocialMap)
   - [ONE Map on App Store](https://apps.apple.com/jp/app/one-voice-map/id6477570243?l=en-US)
 - Farcaster (Warpcast frames)
   - [Neynar API (back-end for fetching farcaster info)](https://github.com/rika97/neynar)
 - s.country
   - [Website for Handling Social Media oAuth login: Github Repo](https://github.com/harmony-one/s/tree/main/s-game)
   - [OTP Connection Handling Website](https://65bbe0909d7fba10443b4511--sgame-test.netlify.app/)
   - [Harmony Transaction Handler on Telegram (Bot)](https://t.me/harmony_telegram_bot)
   - [Harmony Transaction Handler on Telegram (Bot): Github Repo](https://github.com/Aishlia/PaperTradesBot)
 - Multisig Wallet
   - [Gnosis Safe Harmony Fork](https://github.com/harmony-one/safe)
   - [Harmony Safe (Gnosis Safe Harmony Fork on App Store testflight)](https://appstoreconnect.apple.com/apps/6476511661/distribution/ios/version/inflight)
 - Market Research
   - [ETH Denver talks/projects (Notion)](https://harmonyone.notion.site/Projects-98f4c496c68f444ab1f1b3b885abfdeb)
   - [Harmony Community Projects Master Sheet (Notion)](https://www.notion.so/harmonyone/Master-Sheet-88c9a7016be04cb4a711cd97a53ec703)
 - Others
   - [Soulbound Tokens Inscription](https://github.com/rika97/s/tree/main/s-nft)
   - [Uniswap Single Swap Protocol](https://github.com/rika97/s/tree/main/s_swap) 
---

2024-03-31 Sun (2.5 hours): Same as Sat. Looked into more resumes for my tasked keywords ("data engineer", "5 YOE", "modeling, security, indexing").

2024-03-30 Sat (2 hours): Continued work on finding resumes for our next candidate pool.

2024-03-29 Fri: Worked on collecting resumes through LinkedIn, Discord chats, and learnt how to use Lever. 

2024-03-28 Thu: Researched more job matching platforms (Handshake, Indeed, ZipRecruiter, Ripplematch), W-2 hiring platforms (Adecco, Robert Half, Pasona, UpWork), ATS parsing platforms (Greenhouse), start-up based platforms (YCombinator, wellfound, Plug and Play). Looked into papers for LLM ("Learning to Retrieve for Job Matching", "Generative Job Reccomendations with LLM", etc).

2024-03-27 Wed: Researched into various job matching platforms for our /AIMM such as Simplify, and Layoffs.fyi. Tested resume feedback with Claude Opus. Looked into salary data marketplace such as Blind, and Levels.fyi. 

2024-03-26 Tue: Did some research on tokenized resumes as per /aimm. Working on testing the previously deployed smart contract (fork of RoyaltyPolicyLAP.sol) by looking into implementing IP assets also with Story Protocol to enable test transactions with ipid.

2024-03-25 Mon: Toured 2 new office locations. Resolved RoyaltyPolicy deploy bug by manually uploading all files. Deployed smart contract to [shard 1](https://explorer.harmony.one/address/0x54ef56ee76d696d33b9ba469a3bb5235aff46370?activeTab=6
).

**2-week Deliverables**

Implement on-chain royalties to harmony's shard 1 using Story protocol. Create a demo to show how AI model training (specifically for maps or voice data) can be done using these on-chain royalties.

---

2024-03-24 Sun (1 hour): Debugging further continued, reflected upon my goals and milestones for Q1.

2024-03-23 Sat (2 hours): Followed through a tutorial on hardhat to debug/resolve flattening issues.

2024-03-18 Mon ~ 2024-03-22 Fri: PTO (Always available on Telegram)

---

2024-03-17 Sun (1 hour): Continue debugging and adapting contracts to shard 1.

2024-03-16 Sat (1.5 hours): Debugging issues regarding concatenation with Hardhat.

2024-03-15 Fri: Worked on concatenating 29 smart contract files into one solidity contract to deploy on Remix. 

2024-03-14 Thu: Followed through this [tutorial](https://docs.storyprotocol.xyz/docs/get-started-with-the-smart-contracts) on setting up smart contracts with Story protocol. With the massive help of Julia, learned how to deploy smart contracts on Harmony's blockchain, and test deployed contracts.

2024-03-13 Wed: Researched and found deployed smart contract address for [Royalty Policies](https://docs.storyprotocol.xyz/docs/deployed-smart-contracts-1). Looked into how to put this on shard 1.

2024-03-12 Tue: Looked into the solidity contract for Story protocol, started researching how we can implement this on shard 1.

2024-03-11 Mon: Watched and read documentation on Story protocol, tested their existing products (Hey, Magma, artcast, etc) and researched how we can implement this for /data.

---

2024-03-10 Sun (1 hour): Further continued, looked into on-chain royalty policy and did some research on different AI models and their specs (MMLU, etc).

2024-03-09 Sat (1.5 hours): Further continued market research (eg. modulus, eternis) lisetd on the edgeai notion site and looked around Twitter.

2024-03-08 Fri: Continued market research on crypto companies doing data collection (gensyn.ai, semiotic labs, etc).

---

**ETH Denver summary and future goals:**

At ETH Denver, my engagement with companies at the forefront of integrating cryptocurrency with physical devices illuminated the vast potential and innovation within the blockchain domain, particularly in blending digital and tangible technologies. The event served as a platform to explore the extensive applicability of blockchain beyond digital realms, notably through my interaction with Lendr's CEO, Nathaji, and their unique business model. Lendr exemplifies the innovative use of crypto rewards by lending devices for public Wi-Fi hotspots and compensating hosting venues, showcasing the diverse ways cryptocurrency can add value across various sectors.

The focus on Ethereum storage solutions was prominent, with companies like EthStorage showcasing their efforts in leveraging decentralized smart contracts for Web3 resource management, indicating the potential of decentralized technologies to revolutionize data storage and access. This, coupled with insights gained from Uniswap's mobile app launch and Protofire's collaboration on the Gnosis Safe, highlighted the blockchain ecosystem's dynamic evolution and the ongoing innovations addressing core challenges such as storage efficiency and transaction cost optimization.

Reflecting on the range of projects and ideas presented, including the creative Aavegotchi game, the experience at ETH Denver was profoundly inspiring, particularly in contemplating future work at Harmony. It underscored the richness of innovation within the Web3 space, especially in enhancing Ethereum network storage and transaction efficiency. This exposure has equipped me with valuable perspectives and motivation to leverage innovative ideas and the unique advantages of our chain to contribute meaningfully to the blockchain domain's evolution, focusing on reducing transaction fees and increasing transaction speeds.

My focus on enhancing One Social Map involves substantial improvements in both the user interface and backend functionalities. I aim to refine the UI, particularly the carousel that displays user notes and photos, making it more intuitive and user-friendly. On the backend, efforts will be directed towards optimization to enhance performance and scalability. Additionally, I plan to implement more complex functionalities to enhance app reliability, such as preventing users from checking into the same location multiple times when the app is restarted. These enhancements are geared towards providing a seamless and bug-free user experience.

For h.country, my objective is to advance the platform's integration and usability features. This includes improving the oAuth login mechanism and linking usernames directly to user accounts, thereby streamlining the authentication process. I intend to expand the range of oAuth providers available, broadening the accessibility for users across different platforms. Furthermore, the integration of the check-in function with the One Social Map app will be prioritized, aiming to create a cohesive and interconnected user experience between the two applications. This effort is directed towards facilitating a smoother and more efficient interaction for users navigating between h.country and One Social Map.

In my pursuit of market research, I am dedicated to uncovering and exploring new crypto products, aiming to stay at the forefront of blockchain innovation. This exploration is not limited to theoretical research; I plan to actively participate in more events, engaging with the blockchain community to gather insights and trends firsthand. A particular focus will be on keeping abreast of emerging trends such as farcaster (and AGI), which represents the cutting edge of blockchain and crypto developments. By doing so, I aim to attract more users to our ecosystem, leveraging these insights to inform strategic decisions and enhance our offerings. This commitment to market research and community engagement is pivotal to our strategy of continuous innovation and growth.

2024-03-03 Sun (14 hours): ETH Denver
2024-03-02 Sat (19 hours): ETH Denver
2024-03-01 Fri: ETH Denver
2024-02-29 Thu: ETH Denver

---

2024-02-25 Sun (3.5 hours):
Worked on setting up Telegram oAuth (father bot) and integrating to Auth0.

2024-02-24 Sat (3 hours):
Looked into oAuth for social media websites and their process (setting up developer accounts)

2024-02-23 Fri: 

h.country: 

Resolved bugs pertaining to connecting backend oAuth server with frontend:
- Fixed CORS access issues [[#82](https://github.com/harmony-one/h.country/pull/82)] [[#81](https://github.com/harmony-one/h.country/pull/81)]
- Fixed redirect uri mismatch issues (for exchanging authorization tokens) 
- Fixed Heroku configurations for running node.js

Now, oAuth is fully integrated and can be used on g.country

2024-02-22 Thu: h.country: 
- Fixed the following bugs when clicking on big '/' [[#66](https://github.com/harmony-one/h.country/pull/66)]:
  - If the domain already matched predefined domains, it would sometimes not correctly replace those predefined texts but instead create new text links due to regex issues
  - When "www." was not entered in URLs, it would sometime not be recognized properly due to regex issues
  - If domain was correctly matched with one of the predefined domains, it would show the domain name as well (eg. "twitter.com/stse" -> "twitter/stse") due to using same single function "extractUsernameFromURL()" which was originally created for undefined custom links. Implemented separate function "extractUsernameForProvider()" to account for this case.
- Fixed substack domain bug [[#67](https://github.com/harmony-one/h.country/pull/67)]
- Enabled twitter to also be added with "x.com" input [[#68](https://github.com/harmony-one/h.country/pull/68)]
- Looked into disabling duplicated URLs to be added
- Merged oAuth frontend work: set up configurations, modify deploy domain name, integrate existing code [[#70](https://github.com/harmony-one/h.country/pull/70)]
- Set up oAuth server [[#73](https://github.com/harmony-one/h.country/pull/73)], deploy to heroku and configured server settings[[#74](https://github.com/harmony-one/h.country/pull/74)]

**2024-02-21 Wed:**

ONE Map: Made minor change to UI, created and deployed build to testflight.

h.country: 
- Cleaned up and organized code, moving all constants to "components/links/index.ts"
- Made minor changes to prepare code for merging with oAuth components (providerName, displayName) [[#46](https://github.com/harmony-one/h.country/pull/46)]
- Made major changes to our parser for adding links to userpage [[#54](https://github.com/harmony-one/h.country/pull/54)]
  - Added special case handling for substack link: while other urls were in the format (twitter.com/username), substack was in the format (username.substack.com)
  - Implemented logic for handling when the big '/' is clicked on the userpage
    - User can now add links without worrying about semantics (whether they type 'www.', 'http://', 'https://' or even nothing and it wouldn't matter.)
    - If the user enters a link to social media already available for oAuth (eg. Twitter, Substack), it will display as "t/stse" automatically
    - If the user enters a particular page of a website say "wiki.com/cats" it will show as "wiki/cats"
    - If the user enters just the homepage of a website say "www.stse.com" it will show as "stse.com"
    - If the user enters just a word it will link to a google search of that word
    - Implemented random string generator so that these custom links will be saved into Firebase data collection without overlapping field names

**2024-02-20 Tue:**
- Fixed bug to show new user joined message [[#29](https://github.com/harmony-one/h.country/pull/29)].
- **Previously window.popup() only showed when clicking on big hashtag/slash logo and unadded social media names were not shown. Changed to display unadded social media names and make them each clickable with a window.prompt().**
Looked into the current structure of the window.popup() screen - the userpage was currently split into two components (UserPage and headerList). While UserPage was mostly the logic and headerList was mostly the UI components, the two were both mixed. Userpage covered hashtag sorting while the headerList contained popup logic + wallet rendering. Looked into ways to make these files clean to resolve confusion from functions and props being called in these two separate files. Previously where JSX elements were each mapped from UserPage and being passed onto headerList to show each hashtags and links, I changed the structure to pass on item props from UserPage to headerList so that UI is now mostly handled in headerList. Implemented a dictionary of predefined social media websites. Implemented the logic to show the link if the user has a registered username (g/rika97) or a clickable text of the social media name to display window.prompt() [[#30](https://github.com/harmony-one/h.country/pull/30), [#36](https://github.com/harmony-one/h.country/pull/36), [#38](https://github.com/harmony-one/h.country/pull/38)].
- **Added oAuth components**
Calling oAuth requires 5 steps -
  1. Setting up environment variables (in local and cloudflare)
  2.  Creating a REST API for POST function to grab authorization token from oAuth, GET function to fetch data using the grabbed token. Depoying this on a server.
  3.  Creating a component to send the user to oAuth screen and grabbing an authorization token from POST function in API
  4.  Creating a file to handle callback/redirect after the auth token is grabbed and call the GET function from API
  5.  Handling routes for the callback method (adding redirect URLs and implementing correct routing for the callback component

  Edited and merged these components from the work I did in previous repo (human-protocol). [oAuth](https://github.com/harmony-one/h.country/tree/oAuth) now works if the REST API server is run on localhost.
 
2024-02-19 Mon: Further looked into merge conflict and also showing new user creation message in the user profile page.

---

2024-02-18 Sun (2 hours): Looked into the updated firestore logic with the payload replaced instead of the hashtag action and worked on merging over my previous implementation for showing links.

2024-02-17 Sat (1.5 hours): Finished implementing "links" feature to display as mentions (currently we only have "tagged" for hashtags), see more details here in comments: [https://github.com/harmony-one/h.country/pull/16]. Will work later tonight to resolve merge conflicts.

2024-02-16 Fri (Half PTO): [Merged](https://github.com/harmony-one/h.country/pull/8) conflicts for the window.popup() screen in /auth (added component, configured routing, disabled oAuth for now until we figure out how to fecth usernames). Debugged deploy to cloudflare (CI is trigerred anytime there is ESLint issues or too many unused React imports/components.) Started work on configuring links feed for userPage (looked into existing firebase codebase, investigated structure for adding social media links, added some UI components) on seperate branch [here](https://github.com/harmony-one/h.country/tree/addlinks).

2024-02-15 Thu: Implemented new UI for user authentication page (instead of just having social media site names as buttons, they are now social media names if the user has not added their username. If they have added their username, their username shows up next to a shorthand name of each social media site (eg. "x/rika"). Updated the user flow of oAuth - if the user has not added their username, clicking on the social media site name will popup a window.popup() modal asking to add their username. If the user enters text, it is saved to localStorage and the social media name is now replaced with the names. If they cancel or do not type anything, they are taken to the oAuth page (see here: [https://github.com/harmony-one/human-protocol/pull/21].) Debugged and worked on configuring CloudFlare to my forked repo. It is now deployed to rh.country (server-side must be still ran locally for oAuth to work.) Worked on migrating server-side code from local to Heroku.

2024-02-14 Wed: 
Human Protocol: Added manual implementation of LinkedIn oAuth without using Auth0 (third party service) by developing a server and handling callback URIs. After researching Auth0 and finding out that custom actions and rules are allowed, I implemented a custom login system using Auth0 for 5 different social media websites by creating another custom server and a callback URI handling system. This now enables users to login to 5 different social sites because the server and callback files I coded can handle all OpenID Connect supported oAuth APIs just by passing the provider id. Read more about it in my comments here:  [https://github.com/harmony-one/human-protocol/pull/17]. TO-DO: Configure API keys for more social media oAuths. Create a login system for handling oAuth APIs that don't support OpenID Connect. 


2024-02-13 Tue: Human Protocol: Added an account verification system by implementing oAuth with Auth0. Implemeneted log-in via 7 social media websites by setting up each of their developer accounts and configuring their connections [https://github.com/harmony-one/human-protocol/pull/13]. Also worked on just adding oAuth manually for every single website by creating a server with Node.js + Express, and sending GET requests with Axios. Currently debugging with Postman to configure endpoints and redirect URIs.

2024-02-12 Mon: ONE Map: [Implemented](https://github.com/harmony-one/1/commit/7acbbb7ac9b3e03f35256d288647bb029bae24d2) Firebase to app through react-native-firebase package, debugged errors caused due Flipper and AppDelegate settings. Created a collection and structured documents in Firestore to store check-in counts. [Implemented](https://github.com/harmony-one/1/commit/cdf54474d7375815713e06186e9beaafe4899fd4) React components to read/write check-in counts at each location to and fro Firestore, updated check-in button UI. Created build, and deployed to testflight.

Human Protocol: Went over with Sun on the details/next steps, looked into implementing MetaMask OAuth log-in.

---

2024-02-11 Sun (4 hours): Worked on further debugging settings bundle (for system settings) to react native bridge. 

2024-02-10 Sat (3 hours): ONE Map: [Worked](https://github.com/harmony-one/1/commits/systemSettings) on debugging the system settings map selection. NSUserDefaults is not correctly being fetched, bug probably caused from the bridging between iOS and React Native.

2024-02-09 Fri: ONE Map: [Worked](https://github.com/harmony-one/1/commits/rika/) on implementing Firebase. Investigated how to access single Firehost database with multiple Firebase API keys to enable tracking. Added UI updates (microphone icon, app logo) and modified app store submission info. Implemented in-app browser (when location name is clicked, will open a browser linking to Julia's hashtag url). Uploaded deliverables to Testflight and tested app. [Worked](https://github.com/harmony-one/1/commits/systemSettings) on configuring system settings to enable map selection through iOS settings app (created custom settings preferences and modules to bridge NSUserDefaults to React Native).

2024-02-08 Thu: Worked on updating configurations and resolving iOS build run issue - had problems with installing cocoapods due to update in project from Expo workframe to native CLI, was able to solve it with Nagesh's help. Looked into how Julia's firestore is set-up in order to configure the check-in counts on our app. Looked into more frames and casts on Warpcast. 

2024-02-07 Wed: Added vinyl record shops around Denver as sample locations to [map.json](https://github.com/harmony-one/1/blob/main/rh/map.json). Worked on [ONE Map](https://github.com/harmony-one/1/tree/main/map): updated app version to be compatible with latest iOS, merged with Nagesh's branch, stripped down unneccessary UI, configured to pull marker data from maps.json, added Marker labels and buttons ("check-in", "Voice Memo") to each of the pinned lcoations, produced builds and deployed to testflight through EAS (Expo Application Services) and Expo.dev. TO-DO: Connect to Julia's backend and implement POST + GET requests for check-in data, resolve testflight build issues.

2024-02-06 Tue: Researched trending casts on Warpcast and tested out frames. Looked into Neynar (Node.js framework for implementing Farcaster), created a back-end and implemented REST APIs to gain user information such as get user profile from user id ([here](https://github.com/rika97/neynar)).
Created Harmony ONE Map app using React Native ([here](https://github.com/harmony-one/1/tree/main/map)). Created UI framework with react navigation and tabs, created assets (splashscreen logos, etc), and implemented Apple Maps.
\
![image](https://github.com/harmony-one/s/assets/27670355/4d298a2b-d84f-4ea0-a7da-1f8583101057)


2024-02-05 Mon: Tested Warpcast, investigated casts, and documented interesting frames on [Notion](https://harmonyone.notion.site/Frames-on-Warpcast-746d04f697884e3c95ba76ff95436af8) with Theo.F and Alaina. Followed tutorial on how to create frames in Farcaster and looked into documentation of relevant libraries (eg. Frames.js). Created static site and deployed on Cloudflare Workers + created KV namespace. 

---

2024-02-04 Sun (3 hours): Further work on social media oauth: Initially started work on implementing Firebase but only supports limited number of social log-ins. Looked into creating back-end for SSO-login with [OneAll](https://docs.oneall.com/services/implementation-guide/social-login/) instead, which supports 40 social media websites: investigating workflow and implementing REST API.

2024-02-03 Sat (1 hour): Worked on implementing social media oauth for s.country. Created landing page and added React components to display social media icons ([here](https://github.com/harmony-one/s/blob/main/s-game/client/src/Screens/Auth.jsx)).

2024-02-02 Fri: Further work on 1wallet, burner wallets, candidate interview.

2024-02-01 Thu: Further work on social geo game app: added scripts to create a database in local storage, send transactions to Harmony network, and sync transactions whenever device is online [repo](https://github.com/harmony-one/s/tree/main/s-game). Attended SUI event.

2024-01-31 Wed: Worked on the social geo game app. Created OTP connection page that fetches wallet address from Metamask and displays last 4 digits, connections, social bond (groups), and ENS registration page. Live working demo: [here](https://65bbe0909d7fba10443b4511--sgame-test.netlify.app/) (must be opened with desktop or any ethereum compatible wallet browser eg. Metamask mobile browser).

*Planned: Further work on Telegram bot with Julia. Research more about community projects, etc to prepare for promotion at Eth-Denver.

\
2024-01-30 Tue: Added and tested more projects (20~) to notion master list. Went over with Julia on how to build the OTP architecture for the QR code/game.

*Planned: Check-in with Julia, add further features to Telegram bot (we have basic features but I believe we still need to work on implementing wallet and setting connections for transactions, have to check with her.)

\
2024-01-29 Mon: Tested and documented ecosystem projects found through dApp radars and twitter (EzCasino, Chibi Cats Cafe, Speed Star, Crypto Royale, DappRadar, Synapse, Aragon, Coherence ONE, Defi Tower, Defira, Defimons, Galaxii, QiDao, ACryptoS, Elk Finance, Coin98, Beefy Finance, and Harmony Punks.) Sent top 3 projects summary to x.country telegram.

*Planned: Finish testing the remaining projects noted in Notion. Choose top 3 projects and announce to x.country. If finished, continue more product testing (only 150 projects were listed since Github limits search results to 5 pages. Will look for ways to display other search results, eg. check Twitter)

---

2024-01-28 Sun (1.5 hours): Yesterday's continued.

2024-01-27 Sat (6 hours): Tested apps adopting Harmony such as Knights and Peasants , DEUS App, Curve.fi, Crypto Royale, and FishFight, and others. Drafted summaries for the tested products in preparation for announcement to x.country telegram.

2024-01-26 Fri: Researched and tested Harmony related apps, (eg. CougarSwap, XP.NETWORK, DefiKingdoms, AnotherWorld, ) and researched about various concepts on yielding (farms, pools, uniswap, pancakeswap, sushiswap, WONE, Jewel LP - especially the tokens for providing liquidity pools).

2024-01-25 Thu: Researched 90+ Harmony community projects in depth, noting down their github activity, cheking their Twitter feeds, open source status, and researching other relevant projects developed by the organization. Updated to the [same notion page](https://www.notion.so/harmonyone/Master-Sheet-88c9a7016be04cb4a711cd97a53ec703) as yesterday.

2024-01-24 Wed: Researched approximately 100+ projects/apps integrating Harmony network. Looked at their app, open source status, EVM compatibility, and researched relevant (forked projects). Updated [here](https://www.notion.so/harmonyone/Master-Sheet-88c9a7016be04cb4a711cd97a53ec703)

2024-01-23 Tue: Assisted Julia with the Telegram embedded wallet (searched relevant chain names on CoinGecko and added them as transaction options). Looked into/worked on debugging the setup for our forked iOS Telegram. Reverse searched for "1666600000" on GitHub and researched ecosystem projects using our mainnet (added to [Notion](https://www.notion.so/harmonyone/Master-Sheet-88c9a7016be04cb4a711cd97a53ec703).)

2024-01-22 Mon: Researched Unisat, Argent and Thor chain. Tested telegram embedded wallets/chat bots such as Unibot, Boxbet and Banabot. Researched on flips (Harmony's Q1 goal) for cross-chain.

---

2024-01-21 Sun (2.5 hours): Researched, forked and tested open source iOS Apps (telegram, metamask). 

2024-01-20 Sat (4 hours): Investigated multisig safe wallets for TIA, RUNE, etc (eg. THORsafe, keplr wallet). 

2024-01-19 Fri: Continued research on PRC-20 inscription tokens (top minted eg. POLS, Sponge V2), Polkadot and Onescription.

2024-01-18 Thu: Updated UI for multisig iOS - edited UI view controllers and added Harmony logo to onboarding/privacy protection screens, removed unwanted sections in settings screen, removed chainprefix settings and set their defaults to false, updated theme color. Created demo video for multisig iOS.

2024-01-17 Wed: Updated UI for multisig iOS - updated chain logo, removed help center section and replaced it with various social media/privacy policy links and icons, updated app name to Harmony Multisig Wallet, updated configurations on info.plist, removed dApps tab and modified navigation router, removed collectibles and forum section. Tested minting inscriptions on various PRC-20 tokens.

2024-01-16 Tue: Researched different inscription tokens/XRC-20s (eg. AVAX, AVAV, ASC-20, PRC-20, SPL-20, NRC-20, ...,) their marketplace, and its relevant concepts (UTF to HEX, etc).

2024-01-15 Mon: (Holiday) Researched about sending inscriptions transactions.

---

2024-01-14 Sun (5 hours): Further investigation on how to fix the wallet connection issue on Gnosis. (TheoF was able to fix it.)

2024-01-13 Sat (3.5 hours): Investigated further on how to fix the wallet connection issue on Gnosis.

2024-01-12 Fri: Investigated how to setup harmony testnet on Gnosis multisig ios app. Reached out to protofire team regarding an issue I raised [here](https://github.com/safe-global/safe-singleton-factory/issues/337). Added backend connection to harmony testnet and other configuration setup such as connecting API and adding assets. Tested Sun's USDC flip.

2024-01-11 Thu: Resolved environment config issues for Gnosis safe fork, got forked app to work with Goerli testnet, investigated how to adopt harmony ONE as custom network for safe-ios. TO-DO: Will look into PRs made by protofire team for existing safe contract/safe singleton factory. (Relevant PRs: [https://github.com/safe-global/safe-singleton-factory/pull/15], [https://github.com/safe-global/safe-deployments/pull/62])

2024-01-10 Wed: Researched into Multisig wallets, and Gnosis Safe. Set-up API keys, debugged, and resolved  configurations for Harmony safe-ios fork to get it to build.

2021-01-09 Tue: Researched into Thor swap, more campaigns into airdrops, minting soulbound ERC721, Unistat, and relevant topics such as layer2 and minimla on-chain.

2021-01-08 Mon: Created [repo](https://github.com/rika97/s/tree/main/s-nft) for minting soulbound nft tokens by using ERC721 contract with Openzeppelin. Investigating changes due to openzeppelin updates to make tokens burnable and making them soulbound. 

---

2021-01-07 Sun (4 hours): Researched about different existing marketing campaigns using soulbound and neighboring concept (rewards for token holders).

2024-01-06 Sat (4 hours): Researched more about chainflip, and how to implement soulbound tokens.

2024-01-05 Fri: PTO

2024-01-04 Thu: Researched into soulbound tokens, ERC (ethereum guidelines), deploying smart contracts and different "accomplishments" such as airdrop, and researched more into deploying swaps on chainflip.

2024-01-03 Wed: Implemented and updated [single swap protocol](https://github.com/rika97/s/blob/main/s_swap/contracts/SingleSwap.sol) using Uniswap V3. In order to swap ERC20 to native token like $ONE, need to implement an intermediary. Researched UniswapX and bridging for cross-chain swap.

2024-01-02 Tue: Started investigation into how to mint Soulbound NFT, looked into defi recap reading, and researched minimal-on-chain for intent-based applications (Uniswap, Anoma, Chainflip). Currently minimal uniswap prototype still in progress - will push progress so far after cleaning code.

2024-01-01 Mon: Sunday continued, further investigation on how to create a test environment to execute tests.

---

2023-12-31 Sun: Continued following along solidity tutorial, scrapped previous demo code and started work on implementing uniswap prototype - figuring how to write a smart contract to execute swap on V3.

2023-12-30 Sat: Recapped fundamental understanding of blockchain and started following along this (solidity tutorial series)[https://www.youtube.com/watch?v=umepbfKp5rI]. Also studied Harmony ONE tokens (sharding to achieve 100x lower transaction fee, ~2s transaction time).

2023-12-29 Fri: Continued research now focused on uniswap, (UNI tokens, ERC20 token swap, Uniswap liquidity pools). (Followed along this uniswap tutorial)[https://www.youtube.com/watch?v=GwMyv7CmoRs]

2023-12-28 Thu: Continued research (smart contract, liquidity pool, transaction fees (gas), bridging vs. swapping)

2023-12-27 Wed: Continued research (dApps, defi, dex, token vs coin, proof of stake vs proof of work, validator vs staking).

2023-12-26 Tue: Investigated how to implement harmony tokens to uniswap and how to integrate with other components of our app. Got very confused and was completely lost during uniswap tutorial: figured I take a step back and started learning crypto fundamentals (blockchain, nonce, hashing, ethereum and eth based tokens).

2023-12-25 Mon: Forked and implemented minimal uniswap code. In need of access to harmony testnet in order to test out contract. Currently still working on swap code.

---

2023-12-24 Sun: Further research into the frameworks needed for writing basic swap contracts, looked more into Solidity and Uniswap.

2023-12-23 Sat: Researched more into different frameworks required for conducting swaps such as dApp, Alchemy, and investigated more about Mainnet Fork.

2023-12-22 Fri: Forked "s" repo and researched into how to implement minimal uniswap using solidity and hardhat testing framework.

2023-12-21 Thu: Researched into and implemented time-based OPT (TOTP) verification by creating a counter based on epoch, implementing a secret key generator in base32, function to generate hash from base32 key, and a function to generate OTP from secret key and counter.

2023-12-20 Wed: Initialized simple file for OPT verification, read assigned papers on COQ & keyless crypto wallets, and investigated how to implement OTP.

2023-12-18 Mon: Increased unit test coverages for LogStore (100%) [https://github.com/harmony-one/x/pull/401], TextToSpeechConverter (98%) [https://github.com/harmony-one/x/pull/402], and SettingsBundleHelper (100%) [https://github.com/harmony-one/x/pull/403].

---

2023-12-17 Sun: Further readings on COQ.

2023-12-16 Sat: Readings on COQ proofs.

2023-12-15 Fri: Increased unit test coverages for TimeLogger (99%) [https://github.com/harmony-one/x/pull/393], and TextToSpeechConverter (79%). Updated MockActionHandler & MockSpeechRecognition protocols.

2023-12-14 Thu: Created tests and refactored original code for [RandomTrivia](https://github.com/harmony-one/x/commit/66de2e031e78c9d7c80b4accd6768ba9ccc7e03d) (100%) TimeLogger (0->52%) and Store (52->69%) [https://github.com/harmony-one/x/pull/385]. Writing tests for store was also complex, will look into ways to how to refactor these codes.

2023-12-13 Wed: Further worked on RelayAuth tests (76.3%) [https://github.com/harmony-one/x/pull/371]. Was pretty complex to add additional tests for error handling. So far depending on dependency injection but will have to look into better ways as the refactored code may look a little awkward.

2023-12-12 Tue: Added RelayAuth tests [https://github.com/harmony-one/x/pull/371] (30% increase). Did a lot of refactoring for the original code, isolated some complex parts into simpler functions since some functions threw NSerrors without returning anything and it would be difficult for replicating this error durign testing.

2023-12-11 Mon: Added tests for RelayAuth [https://github.com/harmony-one/x/pull/348] (40% -> 67%). These tests are complex to write since the original code includes a lot of logError throws, timer functions, and case handling using AppConfig values. Will further work on refactoring the original code to isolate them. Assisted Julia in resolving .trivia bugs.

---

2023-12-10 Sun: Continued investigating the ActionsView issues, and some of the bugs that may be side affects of dispatch queue, clogging the main thread.

2023-12-09 Sat: Continued investigating how to conduct unit tests regarding OSLog.

2023-12-08 Fri: Added tests for KeychainService (100%) [https://github.com/harmony-one/x/pull/340], Persistence (100%) [https://github.com/harmony-one/x/pull/341], and AppSettings (93%) [https://github.com/harmony-one/x/pull/337]. [Resolved threading issues](https://github.com/harmony-one/x/commit/8b81c998e7f21cd18e304f49ed78732e867f689f) again which kept blocking the entire test from running (it was due to calling main thread on dispatch queue numerous times).

2023-12-07 Thu: Added tests and refactored code for LogStore (94%) and AppSettings (92%). Cleaned code for ConverterTests. Investigating how to provide coverage for code that dispatches notification (OSLog, warnings, NSNotification) - they seem better if covered in integration testing but finding a work around to bring their unit test coverage to 100%.

2023-12-06 Wed: Solved threading error from SpeechRecognition.swift which was causing entire tests to fail. Cleaned code that wasn't being used. Updated tests for SettingsView, and all the Intents tests to 100% (SurpriseIntent, AppSettingsIntent, NewSessionIntent, PlayPauseIntent, IntentManager, VoiceAIShortcuts). Helping fix the unit tests for ActionsView, which require UI testing (still investigating issue).

2023-12-05 Tue: Raised tests for SettingsBundleHelper to 100% [https://github.com/harmony-one/x/pull/315], APIEnvironment to 100% [https://github.com/harmony-one/x/pull/316], MixpanelManager Tests to 90% [https://github.com/harmony-one/x/pull/314], and cleaned/refactored AppConfig tests + original file [https://github.com/harmony-one/x/pull/317] (currently still updating).

2023-12-04 Mon: Resolved conflicts and merged language updates [https://github.com/harmony-one/x/pull/306] [https://github.com/harmony-one/x/pull/291], wrote some tests for CustomInstructionsConfig [https://github.com/harmony-one/x/pull/302] and language [https://github.com/harmony-one/x/pull/307].

---

2023-12-03 Sun: Investigated Speech Recognition tests and some of the test code issues regarding dispatch queues.

2023-12-02 Sat: Added haptics to "press and hold" button. Currently working on speech recognition test coverage.

2023-12-01 Fri: Tested and investigated issues for the flush rate + speech text delimiter for different languages (may rely on built-in libraries for NLP methods as given advice by Aaron, though still figuring out what's the best way for translations if we intend on adding more text). Investigated making speech recognition tests more comprehensive.

2023-11-30 Thu: Updated language support for button label text, added translations settings menu, answer limit warning text and delimiting punctuations for all languages. Replaced all warning messages given to the user through convertTextToSpeech()from just Strings to Strings returned from getFunctions() created in Language translation files [https://github.com/harmony-one/x/pull/291]. TO-DO: 1. test delimiting punctuations + flushing speed, translations of messages for different languages. 2. Investigate if manual translations is the best approach compared to API.

2023-11-29 Wed: Updated [AppConfig tests](https://github.com/harmony-one/x/commit/f6be1d1f759ebd4f764fa70d9e9f6552f6f6880b) to match new API key requirements. 
Made voice overs available in all iOS supported languages by creating dictionaries of translations. Fixed unavailable voice folder issue for some of the language-region codes passed to AVSpeechSynthesizer. Created a function to verify if language was supported otherwise default to English. Modified app to only take in language instead of language and region to ensure language support in textToSpeechConverter. Progress made in [branch](https://github.com/harmony-one/x/commits/rika-languages).
TO-DOs - 1. Buffer capacity needs to be modified for each language, since some languages such as Japanese have characters with longer pronounication and it takes time to flush the OpenAI response. 2. Currently, translations for basic messages are stored in a dictionary in order to reduce latency of requesting translation to OpenAI. However the main latency issue might just be due to buffer+flush rate. Investigate this so that if any other messages are added, we don't have to manually translate each message for each language.

2023-11-28 Tue: Worked on Timer Manager tests (90%) [https://github.com/harmony-one/x/pull/280] and RelayAuth tests. Investigated how to make some functions (surprise, etc) available in other languages.

2023-11-27 Mon: Raised the overall app test coverage from 61% to 74%. Worked on SpeechRecognition Tests [https://github.com/harmony-one/x/pull/272], raised its coverage from 40% to 90%. Investigating bugs for the SurpriseMe function when using the app in another language and updating Network Manager tests.

---

2023-11-26 Sun: Added some unit tests to speech recognition [https://github.com/harmony-one/x/pull/267]. Will need to implement mock text to speech converter and figure out how to oragnize the structure.

2023-11-25 Sat: Revised the code coverage to see tests that need more coverage. Observed that SpeechRecognitionTests was barely doing anything - saw that mocks had been implemented so far but they're not testing any of the actual functions. Started work on writing tests for this file, implemented tests for testGetCurrentTimestamp() and testRegisterTTS(), created MockTextToSpeechConverter [https://github.com/harmony-one/x/pull/262]. This file really needs refactoring for better organization as it is confusing to be using SpeechRecognition.swift for some test cases and others using MockSpeechRecognition.swift - will be working on this the next few days as solving the previous mentioned "View" SwiftUI issue seems a bit more complex.

2023-11-24 Fri: Continued investigating issues for creating unit tests for SwiftUI Views.

2023-11-23 Thu: Cleaned up test files for better structure and added all the missing test classes. Still investigating ActionsView unit test issues.

2023-11-22 Wed: Continued investigating resolutions for inability to access environment objects from a view during unit testing (issues pertaining to AppSettings and Store). Will look into frameworks for workarounds - StoreKit Testing and ViewInspector seems to be suggested.

2023-11-21 Tue: Worked on resolving ActionsView tests that were failing due to the setups of environment objects and views. [https://github.com/harmony-one/x/pull/240] Implemented theme manager and vibration unit tests, still investigating how to create unit tests for other functions since the original code needs refactoring to be testable.

2023-11-20 Mon: Created tests for [App Settings](https://github.com/harmony-one/x/pull/233) (90%), [Review Requester](https://github.com/harmony-one/x/pull/232) (81%), [Create User](https://github.com/harmony-one/x/pull/230) (100%), and [Timer Manager](https://github.com/harmony-one/x/commit/dcd7bae73e4ea719d0e7d1e1f33e33f92fc09714) (71%).

---

2023-11-19 Sun: Still working on debugging previous tests, been working on partitioning functions into smaller functions to make easier for testing.

2023-11-18 Sat: Worked on debugging to raise test coverage of Store.swift.

2023-11-17 Fri: Created tests for SettingsBundleHelper [https://github.com/harmony-one/x/pull/217] (coverage: 100%) and Store [https://github.com/harmony-one/x/pull/212]. Updated the tests for API Environment & Keychain Service [https://github.com/harmony-one/x/pull/213], and Persistence [https://github.com/harmony-one/x/pull/214], raising their coverage to 100%.

2023-11-16 Thu: Updated PermissionTests [https://github.com/harmony-one/x/pull/202]. Created unit tests for KeychainService [https://github.com/harmony-one/x/pull/204], APIEnvironment [https://github.com/harmony-one/x/pull/205], Persistence [https://github.com/harmony-one/x/pull/206] and raised all of their test coverage to 100%. Surveyed friends for feedback on app and generated quiz questions on Harmony. Fixed issue of some test files being ignored when opening project.

2023-11-15 Wed: Updated and merged haptics [https://github.com/harmony-one/x/pull/194]. Restructured Permissions.swift to better suit for unit test purpose, and added unit tests to [PermissionTests](https://github.com/harmony-one/x/commits/rika-permissiontests) for different cases of Microphone access and speech recognition authorization, raising its coverage to 81% in.

2023-11-14 Tue: Worked on increasing coverage for AudioPlayerTests (debugging [this](https://github.com/harmony-one/x/commits/rika-tests)). Worked on appconfig tests [https://github.com/harmony-one/x/pull/186] and [https://github.com/harmony-one/x/pull/187] (currently investigating unit tests to cover methods for decrypting API keys as they require a special workaround since they are private functions.)

2023-11-13 Mon: Added unit test for convertTextToSpeech.swift when language is supported by adding speak() in MockAVSpeechSynthesizer [https://github.com/harmony-one/x/pull/164]. Changed alert sounds ("beep") to only occur when there is recognition or OpenAI error in SpeechRecognition.swift [https://github.com/harmony-one/x/pull/175]. Removed the "share app" dialogue. Worked on unit tests for Audio Player (added test cases in AudioPlayerTests.swift, added mocks for AVAudioPlayer and AVAudioSession). Fixed errors regarding to merge conflicts.

---

2023-11-12 Sun: Worked on debugging unit test case for no language support in TextToSpeechConverterTests.

2023-11-11 Sat: Further implemented a unit test for TextToSpeechConverterTests to handle convertTextToSpeech() when provided device language is not available in the AVSpeechSynthesisVoice framework. Submitted PR: [https://github.com/harmony-one/x/pull/164]. Worked on unit test when voice is available for the language.

2023-11-10 Fri: Investigated debugging "IsFormatSampleRateAndChannelCountValid(format)". Implemented unit tests for TextToSpeechConverter, made a mock class for AVSpeechSynthesizer, updated TextToSpeechConverter by adding a protocol, and added code to make test debugging easier at breakpoints. Raised the overall test coverage for textToSpeech to a 93%, submitted PR: [https://github.com/harmony-one/x/pull/163].

2023-11-09 Thu: Debugging for bugs caused by unit tests requesting microphone permission (issue due to "IsFormatSampleRateAndChannelCountValid(format)" causes entire test to fail due to thread kill). Currently still working on it but so far: 1. Improved error handling for audioSession.recordPermission(). 2. Added NS microphone permissions requestg in Info.plist 3. Set up AVAudioSession properly by setting setCategory() and setActive() for AVAudioSession() 

2023-11-08 Wed: Resolved haptics issue which was earlier colliding with recording functions (PR: [https://github.com/harmony-one/x/pull/141]). Implemented language support so that app defaults to device's preferred first language instead of English (PR: [https://github.com/harmony-one/x/pull/143]). Debugging on compiling issues for running unit tests.

2023-11-07 Tue: Investigated a method to mitigate the haptics issue using UIImpactFeedbackGenerator and modifying SpeechRecognition.swift (Haptics feedback using AudioServicesPlayAlertSound() had bug: conflict with AVAudio when functions .playAndRecord() or .record() are in action). Investigated unit test failures due to new functions being implemented, which were leading to threading errors. Assisted Theo with preparation for the TGI event.

2023-11-06 Mon: Added context message rule to OpenAI service, added and debugged haptic feedback (vibration) when buttons are pressed, updated unit tests in ActionHandlerTests and MockSpeechRecognition to match new function sayMore(). 

---

2023-11-05 Sun: Changed "press to speak" to "press & hold". Added unit test coverage for play() function in ActionHandler.handle. Created MockGenerator for UIImpactFeedbackGenerator, implemented unit tests for stopVibration() and vibrate() in VibrationManagerTests, increasing its total coverage to 100%.

2023-11-04 Sat: Implemented unit tests for ActionHandler, increasing coverage from 55% to 96%.

2023-11-03 Fri: Learnt about testing (unit, integration, UI) in XCode, and how to do mock testing. Looked into missing parts of current test coverage within SpeechRecognition.swift and investigated how to incorporate their unit tests.

2023-11-02 Thu: Further investigated protocols inside MockSpeechRecognition.swift and various functions imported from AVFoundation used for SpeechRecognition.swift. Aided Theo with generating test codes for product demo.

2023-11-01 Wed: Understood concepts unique to Swift: protocol oriented programming (inheritance, extensions), classes vs. structs, enums for switch statements. Grasped the structure of XCode files (workspace, projects, targets, schemes).

2023-10-31 Tue: Synced with Sun on unit tests. Understood each function of SpeechRecognitionProtocols (reset, randomFacts, isPaused, capturing, cleanup). Debugged my build.

2023-10-30 Mon: Got onboarding documents done (signed up for Gusto and Google Workspace). Tested Whisper and Voice AI with Theo.

---
In 3 weeks (2023-11-20):
100% coverage of automated tests (units, components, submit, and release).

In 3 months (2024-01-30):
Make Voice AI compatible with 10 regions and dialects. 

In 3 seasons(2024-06-30):
Create a developer ecosystem. Curate a HuggingFace community. Build custom models of speech synthesis. Implement emotions by customizing annotation, pacing, excalamation and tones.

In 3 years (2026-10-30):
Understand ML architectures and LLMs. Build custom models, make project open source, build a developer community.

---
1. Native App / Open Source
Full-stack engineering is my strongest suit, as I work on building mobile apps using React Native through my current job. We are building a contact sharing app and have implemented features such as user dashboard and background location tracking to detect and display where contacts were added. I have also worked solo on a months-long personal project where I built an open source event sharing social media app using Google Cloud Platform and released it publicly on Expo.

2. Applied Mathematics / Optimization
During my graduate studies, I took courses on large scale data mining/complex networks, reinforcement learning, and optimization through linear programming. I utilized this knowledge while working on multiple Kaggle competition projects, as well as my research in Human Computer Interaction (HCI). Here I focused on transfer learning, applying clustering methods, and generating synthetic data to improve the quality of classification. I was also part of a mathematics olympiad team during undergrad, where I achieved a high score at the Putnam Mathematical Competition.

3. Parallelism
During my research internship at Caltech, I was part of a group called the LIGO collaboration where I developed our open-source Python library to classify different types of astronomical signals collected by the LIGO gravitational wave detectors. Our signals had strain dimensions of 10^-18, making it very difficult to detect our signals underlying in variant noise sources. To do this, we built a Python library and used ML to predict the types of signals. My task was to improve the classification accuracy of this library. I built a Python program to simulate variants of different astronomical signals, and then built a parallel program to simulate these signals at a large-scale in a significantly reduced amount of time. Each simulation cost approximately 1 minute and nearly 10,000 signals were simulated in an hour, reducing the time complexity by more than 99%.

https://rikah.netlify.app<br>https://github.com/rika97<br>https://www.linkedin.com/in/rikako-hatoya/<br>https://www.ted.com/profiles/7659431/translator

