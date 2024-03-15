**2-week Deliverables**

Implement on-chain royalties to harmony's shard 1 using Story protocol. Create a demo to show how AI model training (specifically for maps or voice data) can be done using these on-chain royalties.

---
2024-03-14 Thu: Followed through this [tutorial](https://docs.storyprotocol.xyz/docs/get-started-with-the-smart-contracts) on setting up smart contracts with Story protocol. With the massive help of Julia, learned how to deploy smart contracts on Harmony's blockchain, and test deployed contracts.

2024-03-13 Wed: Researched and found deployed smart contract address for [Royalty Policies](https://docs.storyprotocol.xyz/docs/deployed-smart-contracts-1). Looked into how to put this on shard 1.

2024-03-12 Tue: Looked into the solidity contract for Story protocol, started researching how we can implement this on shard 1.

2024-03-11 Mon: Watched and read documentation on Story protocol, tested their existing products (Hey, Magma, artcast, etc) and researched how we can implement this for /data.

2024-03-10 Sun: Further continued, looked into on-chai royalty policy and did some research on different AI models and their specs (MMLU, etc).

2024-03-09 Sat: Further continued market research (eg. modulus, eternis) lisetd on the edgeai notion site and looked around Twitter.

2024-03-08 Fri: Continued market research on crypto companies doing data collection (gensyn.ai, semiotic labs, etc).

ETH Denver summary and future goals:

At ETH Denver, my engagement with companies at the forefront of integrating cryptocurrency with physical devices illuminated the vast potential and innovation within the blockchain domain, particularly in blending digital and tangible technologies. The event served as a platform to explore the extensive applicability of blockchain beyond digital realms, notably through my interaction with Lendr's CEO, Nathaji, and their unique business model. Lendr exemplifies the innovative use of crypto rewards by lending devices for public Wi-Fi hotspots and compensating hosting venues, showcasing the diverse ways cryptocurrency can add value across various sectors.

The focus on Ethereum storage solutions was prominent, with companies like EthStorage showcasing their efforts in leveraging decentralized smart contracts for Web3 resource management, indicating the potential of decentralized technologies to revolutionize data storage and access. This, coupled with insights gained from Uniswap's mobile app launch and Protofire's collaboration on the Gnosis Safe, highlighted the blockchain ecosystem's dynamic evolution and the ongoing innovations addressing core challenges such as storage efficiency and transaction cost optimization.

Reflecting on the range of projects and ideas presented, including the creative Aavegotchi game, the experience at ETH Denver was profoundly inspiring, particularly in contemplating future work at Harmony. It underscored the richness of innovation within the Web3 space, especially in enhancing Ethereum network storage and transaction efficiency. This exposure has equipped me with valuable perspectives and motivation to leverage innovative ideas and the unique advantages of our chain to contribute meaningfully to the blockchain domain's evolution, focusing on reducing transaction fees and increasing transaction speeds.

My focus on enhancing One Social Map involves substantial improvements in both the user interface and backend functionalities. I aim to refine the UI, particularly the carousel that displays user notes and photos, making it more intuitive and user-friendly. On the backend, efforts will be directed towards optimization to enhance performance and scalability. Additionally, I plan to implement more complex functionalities to enhance app reliability, such as preventing users from checking into the same location multiple times when the app is restarted. These enhancements are geared towards providing a seamless and bug-free user experience.

For h.country, my objective is to advance the platform's integration and usability features. This includes improving the oAuth login mechanism and linking usernames directly to user accounts, thereby streamlining the authentication process. I intend to expand the range of oAuth providers available, broadening the accessibility for users across different platforms. Furthermore, the integration of the check-in function with the One Social Map app will be prioritized, aiming to create a cohesive and interconnected user experience between the two applications. This effort is directed towards facilitating a smoother and more efficient interaction for users navigating between h.country and One Social Map.

In my pursuit of market research, I am dedicated to uncovering and exploring new crypto products, aiming to stay at the forefront of blockchain innovation. This exploration is not limited to theoretical research; I plan to actively participate in more events, engaging with the blockchain community to gather insights and trends firsthand. A particular focus will be on keeping abreast of emerging trends such as farcaster (and AGI), which represents the cutting edge of blockchain and crypto developments. By doing so, I aim to attract more users to our ecosystem, leveraging these insights to inform strategic decisions and enhance our offerings. This commitment to market research and community engagement is pivotal to our strategy of continuous innovation and growth.

2024-02-29 Thu ~ 2024-03-03 Sun: ETH Denver

2024-02-25 Sun:
Worked on setting up Telegram oAuth (father bot) and integrating to Auth0.

2024-02-24 Sat:
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

2024-02-18 Sun: Looked into the updated firestore logic with the payload replaced instead of the hashtag action and worked on merging over my previous implementation for showing links.

2024-02-17 Sat: Finished implementing "links" feature to display as mentions (currently we only have "tagged" for hashtags), see more details here in comments: [https://github.com/harmony-one/h.country/pull/16]. Will work later tonight to resolve merge conflicts.

2024-02-16 Fri (Half PTO): [Merged](https://github.com/harmony-one/h.country/pull/8) conflicts for the window.popup() screen in /auth (added component, configured routing, disabled oAuth for now until we figure out how to fecth usernames). Debugged deploy to cloudflare (CI is trigerred anytime there is ESLint issues or too many unused React imports/components.) Started work on configuring links feed for userPage (looked into existing firebase codebase, investigated structure for adding social media links, added some UI components) on seperate branch [here](https://github.com/harmony-one/h.country/tree/addlinks).

2024-02-15 Thu: Implemented new UI for user authentication page (instead of just having social media site names as buttons, they are now social media names if the user has not added their username. If they have added their username, their username shows up next to a shorthand name of each social media site (eg. "x/rika"). Updated the user flow of oAuth - if the user has not added their username, clicking on the social media site name will popup a window.popup() modal asking to add their username. If the user enters text, it is saved to localStorage and the social media name is now replaced with the names. If they cancel or do not type anything, they are taken to the oAuth page (see here: [https://github.com/harmony-one/human-protocol/pull/21].) Debugged and worked on configuring CloudFlare to my forked repo. It is now deployed to rh.country (server-side must be still ran locally for oAuth to work.) Worked on migrating server-side code from local to Heroku.

2024-02-14 Wed: 
Human Protocol: Added manual implementation of LinkedIn oAuth without using Auth0 (third party service) by developing a server and handling callback URIs. After researching Auth0 and finding out that custom actions and rules are allowed, I implemented a custom login system using Auth0 for 5 different social media websites by creating another custom server and a callback URI handling system. This now enables users to login to 5 different social sites because the server and callback files I coded can handle all OpenID Connect supported oAuth APIs just by passing the provider id. Read more about it in my comments here:  [https://github.com/harmony-one/human-protocol/pull/17]. TO-DO: Configure API keys for more social media oAuths. Create a login system for handling oAuth APIs that don't support OpenID Connect. 


2024-02-13 Tue: Human Protocol: Added an account verification system by implementing oAuth with Auth0. Implemeneted log-in via 7 social media websites by setting up each of their developer accounts and configuring their connections [https://github.com/harmony-one/human-protocol/pull/13]. Also worked on just adding oAuth manually for every single website by creating a server with Node.js + Express, and sending GET requests with Axios. Currently debugging with Postman to configure endpoints and redirect URIs.

2024-02-12 Mon: ONE Map: [Implemented](https://github.com/harmony-one/1/commit/7acbbb7ac9b3e03f35256d288647bb029bae24d2) Firebase to app through react-native-firebase package, debugged errors caused due Flipper and AppDelegate settings. Created a collection and structured documents in Firestore to store check-in counts. [Implemented](https://github.com/harmony-one/1/commit/cdf54474d7375815713e06186e9beaafe4899fd4) React components to read/write check-in counts at each location to and fro Firestore, updated check-in button UI. Created build, and deployed to testflight.

Human Protocol: Went over with Sun on the details/next steps, looked into implementing MetaMask OAuth log-in.

---

2024-02-11 Sun: Worked on further debugging settings bundle (for system settings) to react native bridge. 

2024-02-10 Sat: ONE Map: [Worked](https://github.com/harmony-one/1/commits/systemSettings) on debugging the system settings map selection. NSUserDefaults is not correctly being fetched, bug probably caused from the bridging between iOS and React Native.

2024-02-09 Fri: ONE Map: [Worked](https://github.com/harmony-one/1/commits/rika/) on implementing Firebase. Investigated how to access single Firehost database with multiple Firebase API keys to enable tracking. Added UI updates (microphone icon, app logo) and modified app store submission info. Implemented in-app browser (when location name is clicked, will open a browser linking to Julia's hashtag url). Uploaded deliverables to Testflight and tested app. [Worked](https://github.com/harmony-one/1/commits/systemSettings) on configuring system settings to enable map selection through iOS settings app (created custom settings preferences and modules to bridge NSUserDefaults to React Native).

2024-02-08 Thu: Worked on updating configurations and resolving iOS build run issue - had problems with installing cocoapods due to update in project from Expo workframe to native CLI, was able to solve it with Nagesh's help. Looked into how Julia's firestore is set-up in order to configure the check-in counts on our app. Looked into more frames and casts on Warpcast. 

2024-02-07 Wed: Added vinyl record shops around Denver as sample locations to [map.json](https://github.com/harmony-one/1/blob/main/rh/map.json). Worked on [ONE Map](https://github.com/harmony-one/1/tree/main/map): updated app version to be compatible with latest iOS, merged with Nagesh's branch, stripped down unneccessary UI, configured to pull marker data from maps.json, added Marker labels and buttons ("check-in", "Voice Memo") to each of the pinned lcoations, produced builds and deployed to testflight through EAS (Expo Application Services) and Expo.dev. TO-DO: Connect to Julia's backend and implement POST + GET requests for check-in data, resolve testflight build issues.

2024-02-06 Tue: Researched trending casts on Warpcast and tested out frames. Looked into Neynar (Node.js framework for implementing Farcaster), created a back-end and implemented REST APIs to gain user information such as get user profile from user id ([here](https://github.com/rika97/neynar)).
Created Harmony ONE Map app using React Native ([here](https://github.com/harmony-one/1/tree/main/map)). Created UI framework with react navigation and tabs, created assets (splashscreen logos, etc), and implemented Apple Maps.
\
![image](https://github.com/harmony-one/s/assets/27670355/4d298a2b-d84f-4ea0-a7da-1f8583101057)


2024-02-05 Mon: Tested Warpcast, investigated casts, and documented interesting frames on [Notion](https://harmonyone.notion.site/Frames-on-Warpcast-746d04f697884e3c95ba76ff95436af8) with Theo.F and Alaina. Followed tutorial on how to create frames in Farcaster and looked into documentation of relevant libraries (eg. Frames.js). Created static site and deployed on Cloudflare Workers + created KV namespace. 

---

2024-02-04 Sun: Further work on social media oauth: Initially started work on implementing Firebase but only supports limited number of social log-ins. Looked into creating back-end for SSO-login with [OneAll](https://docs.oneall.com/services/implementation-guide/social-login/) instead, which supports 40 social media websites: investigating workflow and implementing REST API.

2024-02-03 Sat: Worked on implementing social media oauth for s.country. Created landing page and added React components to display social media icons ([here](https://github.com/harmony-one/s/blob/main/s-game/client/src/Screens/Auth.jsx)).

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

2024-01-28 Sun: Yesterday's continued.

2024-01-27 Sat: Tested apps adopting Harmony such as Knights and Peasants , DEUS App, Curve.fi, Crypto Royale, and FishFight, and others. Drafted summaries for the tested products in preparation for announcement to x.country telegram.

2024-01-26 Fri: Researched and tested Harmony related apps, (eg. CougarSwap, XP.NETWORK, DefiKingdoms, AnotherWorld, ) and researched about various concepts on yielding (farms, pools, uniswap, pancakeswap, sushiswap, WONE, Jewel LP - especially the tokens for providing liquidity pools).

2024-01-25 Thu: Researched 90+ Harmony community projects in depth, noting down their github activity, cheking their Twitter feeds, open source status, and researching other relevant projects developed by the organization. Updated to the [same notion page](https://www.notion.so/harmonyone/Master-Sheet-88c9a7016be04cb4a711cd97a53ec703) as yesterday.

2024-01-24 Wed: Researched approximately 100+ projects/apps integrating Harmony network. Looked at their app, open source status, EVM compatibility, and researched relevant (forked projects). Updated [here](https://www.notion.so/harmonyone/Master-Sheet-88c9a7016be04cb4a711cd97a53ec703)

2024-01-23 Tue: Assisted Julia with the Telegram embedded wallet (searched relevant chain names on CoinGecko and added them as transaction options). Looked into/worked on debugging the setup for our forked iOS Telegram. Reverse searched for "1666600000" on GitHub and researched ecosystem projects using our mainnet (added to [Notion](https://www.notion.so/harmonyone/Master-Sheet-88c9a7016be04cb4a711cd97a53ec703).)

2024-01-22 Mon: Researched Unisat, Argent and Thor chain. Tested telegram embedded wallets/chat bots such as Unibot, Boxbet and Banabot. Researched on flips (Harmony's Q1 goal) for cross-chain.

---

2024-01-21 Sun: Researched, forked and tested open source iOS Apps (telegram, metamask). 

2024-01-20 Sat: Investigated multisig safe wallets for TIA, RUNE, etc (eg. THORsafe, keplr wallet). 

2024-01-19 Fri: Continued research on PRC-20 inscription tokens (top minted eg. POLS, Sponge V2), Polkadot and Onescription.

2024-01-18 Thu: Updated UI for multisig iOS - edited UI view controllers and added Harmony logo to onboarding/privacy protection screens, removed unwanted sections in settings screen, removed chainprefix settings and set their defaults to false, updated theme color. Created demo video for multisig iOS.

2024-01-17 Wed: Updated UI for multisig iOS - updated chain logo, removed help center section and replaced it with various social media/privacy policy links and icons, updated app name to Harmony Multisig Wallet, updated configurations on info.plist, removed dApps tab and modified navigation router, removed collectibles and forum section. Tested minting inscriptions on various PRC-20 tokens.

2024-01-16 Tue: Researched different inscription tokens/XRC-20s (eg. AVAX, AVAV, ASC-20, PRC-20, SPL-20, NRC-20, ...,) their marketplace, and its relevant concepts (UTF to HEX, etc).

2024-01-15 Mon: (Holiday) Researched about sending inscriptions transactions.

---

2024-01-14 Sun: Further investigation on how to fix the wallet connection issue on Gnosis. (TheoF was able to fix it.)

2024-01-13 Sat: Investigated further on how to fix the wallet connection issue on Gnosis.

2024-01-12 Fri: Investigated how to setup harmony testnet on Gnosis multisig ios app. Reached out to protofire team regarding an issue I raised [here](https://github.com/safe-global/safe-singleton-factory/issues/337). Added backend connection to harmony testnet and other configuration setup such as connecting API and adding assets. Tested Sun's USDC flip.

2024-01-11 Thu: Resolved environment config issues for Gnosis safe fork, got forked app to work with Goerli testnet, investigated how to adopt harmony ONE as custom network for safe-ios. TO-DO: Will look into PRs made by protofire team for existing safe contract/safe singleton factory. (Relevant PRs: [https://github.com/safe-global/safe-singleton-factory/pull/15], [https://github.com/safe-global/safe-deployments/pull/62])

2024-01-10 Wed: Researched into Multisig wallets, and Gnosis Safe. Set-up API keys, debugged, and resolved  configurations for Harmony safe-ios fork to get it to build.

2021-01-09 Tue: Researched into Thor swap, more campaigns into airdrops, minting soulbound ERC721, Unistat, and relevant topics such as layer2 and minimla on-chain.

2021-01-08 Mon: Created [repo](https://github.com/rika97/s/tree/main/s-nft) for minting soulbound nft tokens by using ERC721 contract with Openzeppelin. Investigating changes due to openzeppelin updates to make tokens burnable and making them soulbound. 

---

2021-01-07 Sun: Researched about different existing marketing campaigns using soulbound and neighboring concept (rewards for token holders).

2024-01-06 Sat: Researched more about chainflip, and how to implement soulbound tokens.

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

