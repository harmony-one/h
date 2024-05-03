**2024 Q1 Review (97 hours)**

In Q1, I researched over 100 Harmony network community projects, focusing on soulbound/inscription tokens and swapping mechanisms. I developed the OTP connection page for our social geo game website and created a Telegram bot for processing Harmony network transactions. Additionally, I led the development of Harmony's mobile applications using Gnosis Safe through forking and configuration.

Later in Q1, I analyzed AGI market trends, tested frames on Farcaster, and examined projects from 43 companies in the AGI Edge hackathon. Using the Story Protocol framework, I created robust royalty policies and deployed a smart contract for them on Harmony's shard 1. I also initiated the ONE Map project with React Native, implementing location check-in buttons with Firebase, refining the UI for /links, and facilitating OAuth authentication for Human Protocol across 7 platforms.

Deploying the Story Protocol on Harmony presented a formidable task, particularly in ensuring the seamless deployment of all 29 contracts upon which this singular contract depended. This endeavor also involved intricate configuration adjustments, transitioning the original contract deployed on Polygon to align with the parameters of Shard 1. Notably, amidst these complexities, the implementation of the royalty policy contract emerged as a pivotal feature, empowering users to specify dividend allocations for a designated IPID, thereby enhancing the platform's functionality and versatility.

---

2024-05-02 Thu: [Created](https://github.com/rika97/scaffold-eth-2/commit/94935a6fb664615ba08c567eac34054c5baa681b) and deployed factory contract for ERC20. [Added](https://github.com/rika97/scaffold-eth-2/commit/a13fda98989d72e7bd61ce07ed9f2aa1822ad843) some front-end for Rune deposit page. Looked into our ["hardhat-starter-pack"](https://github.com/harmony-one/hardhat-starter-pack) to make updates to our repo with Adam.

2024-05-01 Wed: Made changes to configuration and fixed bugs so that contract now also works on Harmony, not just localnet ([commit](https://github.com/rika97/scaffold-eth-2/commit/aed2a4f71308ea99709fabe61780611d2bea03bb)). 

2024-04-30 Tue: Deployed smart contract using Hardhat and Scaffold-eth, and setup network configurations. [[Repo](https://github.com/rika97/scaffold-eth-2)]

2024-04-29 Mon: Created a minimal prototype for Rune -> ERC20 wrap ([deployed](https://explorer.harmony.one/address/0x8b981a0afae43cdb85cb89fbac1d75a4021e6269?activeTab=0
) smart contract onto Harmony using OpenZeppelin and Remix).

---
2024-04-28 Sun (1.5 hrs): Looked into how to wrap tokens to ERC20 on Harmony blockchain using OpenZeppelin and Hardhat.

2024-04-27 Sat (1.5 hrs): Ramping up to understand BTC Rune: their functionalities and overview.

2024-04-26 Fri: Had a meeting with Jackie and discussed the AnotherWorld project. We went over Rune coins on MagicEden, viewing transactions on brc20 API (eventually automate the process), opened my bitcoin wallet, overview of the end-to-end prototype, and how we can create a platform to wrap BTC Rune to ERC20 on shard 1.

2024-04-25 Thu: Conducted more research on token economics and Rollkit. Reviewed Jackie's document on AnotherWorld-Rune project and conducted some research regarding it. Refined my Q2 deliverables.

2024-04-24 Wed: Conducted market research for A(G)I data (specifically $EAT and $3D), existing validation with model training, data performance, labeling, and respective economic values. Worked on Q2 deliverables.

2024-04-23 Tue: Researched for Social A(G)I: ranking, farcaster frames (Farcaster.country) for "Human Protocol for love" (Hot or Not emoji reactions), $MAP (like Aaron's frames, token minting for location check-ins.)

2024-04-22 Mon: Aided with configuration debugging for Privy fork (Auth0 API key setup in swift project.) Looked into RUNE, zkproofs (AiMM: salary matching for candidates and recruiters, purchase data for e-commerce), and further work on Polygon CDK reading and following documentation.

---

2024-04-21 Sun: (1.5 hrs): Looked into/play tested AnotherWorld in preparation for campaigns.

2024-04-20 Sat (2.5 hrs): Working on the 3 goals for Q2 by conducting market research, mainly on cross-chain projects.

2024-04-19 Fri: Further work on Polygon CDK by folling through Roll-up tutorial, setting up Docker, building and testing Docker image, workaround for MacOS, configuring node deployment. Cleared office.

2024-04-18 Thu: Research on Hummingbot through checking out their Discord channel, watching their YouTube videos, and looking through their github documentation. Cleared office.

2024-04-17 Wed: Investigated Polygon CDK, following through their CDK rollup tutorial.

2024-04-10~16 : More candidate search, revision on 2 week deliverables and thought through/drafted Q2 achievement goals.

2024-04-09 Tue: Mon continued + also spent personal time at a software engineer meetup to build connections.

2024-04-08 Mon: More candidate search on lists on Layoff.fyi, LinkedIn, and Twitter. Also revised summary of story protocol deploy and looked into further integrations useful for our community.

---

2024-04-07 Sun: Looked for more resumes and linkedin profiles on the layoffs list on layoff.fyi.

2024-04-06 Sat: Fri continued, also looked for candidates on slack channels for tech groups.

2024-04-05 Fri: Looked for more resumes and profiles on LinkedIn search

2024-04-04 Thu: Looked into AI model datasets for our deployed story protocol contract + continued resume search.

2024-04-03 Wed: Continued resume search by testing existing database and testing job aggregator sites such as ZipRecruiter, PostJobFree, Monster, Indeed, Dice, Discord channels, etc. 

2024-04-02 Tue: Tested various ATS resume checkers + LinkedIn profile scoreres (Enhancv, ResumeWorded, Jobalytics, etc.)

2024-04-01 Mon: More resume search on LinkedIn. Got in touch with Jackie to later set DNS for 9.country.

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

