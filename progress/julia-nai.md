2-Week Deliverables:
Decide on dataset and product plan for AI data gathering. 

2024-03-24 Sun: [4 hours] Looked for more sources of resumes. Pulled 350.

2024-03-23 Sat: [2 hours] Researched sources of resumes and manually pulled 100.

2024-03-22 Fri: Worked on automatically pulling pdfs from comments. Reddit resumes are highly annonymized (lots of blackout). Focused on drive and dropbox posts on hackernews (though this only comprised around 16-20 resumes per monthly post). 

2024-03-21 Thu: Attended GTC. Manually pulled 50 resumes to test GPT analysis of resumes.

2024-03-20 Wed: Attended GTC. Spoke with Sapia team on their mass hiring product. 

2024-03-19 Tue: Automated parsing of comments from Who wants to be hired? posts to pull general stats. Attempted to automate pdf resume pulling from comments.

2023-03-18 Mon: Created [aimm](https://github.com/harmony-one/aimm) repo to scrap "Who wants to be hired?" posts on Hacker News.

---

2024-03-17 Sun: [2 hours] Finalized thoughts on voice to voice path for next 3 months as well as feasibility. 

2024-03-16 Sat: [3 hours] Looked into Linkedin popularity amongst younger generations as social media. Continued research on audio tokenization models. 

2024-03-15 Fri: Worked through contract deploy methods and solidity overviews with Rikako. Researched potential voice to voice implementations that completely skip text translation. Looked into potential voice tokenization methods. 

2024-03-14 Thu: Discussed platform to intelligently collect product information and present information/reviews that are up-to-date. Explored rewarding users for leaving reviews with low barrier (through voice). 

2024-03-13 Wed: Looked into feasibility of training LLM on purely voice input avoiding the text translation layer. Compared training hours and token quantities of existing models. 

2024-03-12 Tue: Researching more into data types that can be used for unlabeled data sets. Looking into ways that users can be incentivized to provide data that reasonably improves models more than free data. 

2024-03-11 Mon: Reading wav2vec experiments with extra unlabeled training data and the impact on model performance. Looking into Whisper training set and finding correlation between data in and data out. 

---

Summary progress: 2/6 Tue - 2/28 Wed and 3/4 Mon - 3/10 Sun \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;I prototyped a social media with Firestore as the NoSQL key-value storage of messages. I titled this project Remote Emitter and added relevant features as they were brought up. First, I started by adding barebones messages sent under a user changeable username. I developed a home page where users could enter whatever username they wanted to post under and make a post. I added a timestamp and location stamp to each post. Then I added user specific pages routed under /<username>. Clicking on a username would take you to a page with all posts done from that username. I added location-specific pages as well. I worked on optimizing the storage and index methods so that updates were under 100 ms across all devices. Remote Emitter was setup to automatically deploy on-push from Cloudflare to jn.country through CNAME routing. I changed usernames to be non-user-changable, and added hashtag support (clicking on a hashtag would take you to /<hashtag> were you could see all posts that use that hashtag). Utilizing Neo4j, I was able to calculate directional nth degree connections between users. A user clicking on another user’s profile could see if there was a chain of people, that they have mutually tagged, connecting them. I tested up to a 6th degree connection with sub 400ms latency and added in the framework for a strength ranking. Later, I added mutual user of the same hashtag as a potential connection method between two nodes. I added posts and mentions tabs to profile pages and global and home feeds to the home page. I added image support and top 3 hashtags counter to the home page and user pages.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;After transitioning development to h.country, I migrated a lot of the features of Remote Emitter that were relevant to the new design and direction. I started by adding in action support initially only handling tags. Messages were changes to actions in an actions Firestore collection with predefined specifications detailing how each action should be displayed and what data should go with each one. I added in timestamps and location data to the tag action and displayed it globally on home page (later removed) and on user pages. I added initial methods for link support and the first pass automatic handling of certain specific links. I started with in-line link adding but transitioned to clicking on the slash to enter any link. By specifying how certain links should be handled, I was able to match the mock’s intention of using abbreviations for certain commonly used sites. h.country was also setup to auto-deploy on-commit from Cloudflare.\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;I was sick quite a lot of this week, but following recovery, I have been looking into models that were originally trained on unlabeled voice recording data. I have been reading about experiments that teams have done measuring model improvement given more unlabeled voice data and looking into businesses that utilize these models for profit.

---

2024-02-23 Fri: 

2024-02-22 Thu: Changes:
- [Changed](https://github.com/harmony-one/h.country/commit/995b4cde33ebfd8c8e9b31ea8b1524cb25eeaee8) window prompt text
- Review and [merged](https://github.com/harmony-one/h.country/commit/8136bca4a2f0a816ffdbee79458cd4289cacb7ac) PR #72
- Updated some frontend displays
- Made white versions of the number and slash svgs to fix color issues
- Defined URL handling

2024-02-21 Wed:

2024-02-19 Mon: Updated package lock to fix deploy. 

---
2024-02-18 Sun: Updated the actions specification rules. 

2024-02-17 Sat: Created hprod repo to deploy to h.country (prod). h.country repo deploys to g.country (dev). 

2024-02-16 Fri: Changes:
- [Added](https://github.com/harmony-one/h.country/commit/74d6878a8abd53f6a7e782739af68521b6ef437c) handling for Instagram links. Automatically converts link from https://instagram.com/username/ to ig/username linked to profile
- [Added](https://github.com/harmony-one/h.country/commit/593476255f122301375a1269bca3a3fbb09c06dd) new spec for actions firestore collection. All actions are now stored in the same firestore collection with a different specification.
- [Moved](https://github.com/harmony-one/h.country/commit/a7e6a6aa536e09eaeb87f4e2c52cc498d612a339) hashtag fetch and feed to actions collection
- [Added](https://github.com/harmony-one/h.country/commit/ea79a08cdbe7077c3374652a46862e6481773cc5) lat long to actions address
- [Created](https://github.com/harmony-one/h.country/commit/cb4cce3c527663024eb46ad2d72dbfd15bf65865) DEVELOPER.md to define action specs

2024-02-15 Thu: Migrated to new [h.country](https://github.com/harmony-one/h.country) repo with new frontend design. Changes:
- [Added](https://github.com/harmony-one/h.country/commit/6771b92eaaabd830197f2d804419dde929e56617) query for top 3 hashtags and counts.
- [Added](https://github.com/harmony-one/h.country/commit/43ff99e94c9f03b6db31db76cfc518907b796970) text box to add hashtags from you to user's profile
- [Added](https://github.com/harmony-one/h.country/commit/e280901a2a139857e9e4be30b003e0e24b534f8c) show global and user actions
- [Added](https://github.com/harmony-one/h.country/commit/6ccf68d3cdfb226409f4c19572b581d05520f040) duplicate message checker
- [Added](https://github.com/harmony-one/h.country/commit/95e1244aa0de24f26b733f6c755242ba94a48b49) timestamps
- [Added](https://github.com/harmony-one/h.country/commit/13b9ebf98c051033a60018cf991336c74419a0d3) homepage
- [Added](https://github.com/harmony-one/h.country/commit/06ac8d7cb9720de77f45ea0bdbd7cf0c44a1f6b5) links for profiles on profile page
- [Added](https://github.com/harmony-one/h.country/commit/f450ac6f353da8718de8c6a16983a46754d1b237) popup for url submission

2024-02-14 Wed: Planned h.country changes.

2024-02-13 Tue: Remote Emitter - [Added](https://github.com/Aishlia/remote-emitter/commit/07645d60e7951c8333c82530c06ba465a8e06c6b) top 3 hashtags on homepage in.

2024-02-12 Mon:\
Change log for Remote Emitter

**Major Changes**
- [Added](https://github.com/Aishlia/remote-emitter/commit/e076cbbef889f74a4c0d6ed278b870888e7f3bd2) support for posting images.
- [Added](https://github.com/Aishlia/remote-emitter/commit/6503e1fee7b4fb9439c4c539e92b90d48817f703) connections between users that use the same hashtag. (ie. @BeautifulJewel82 ↔ @DeterminedXenops71 -#cats- @EnergeticHunter60 → @UniquePiano39 ← @AncientCat37)
    - In this instance, DeterminedXenops and EnergeticHunter both used #cats in a post completing the chain between BeautifulJewel and AncientCat.
    - Mentions are considered a better connection than using hashtags so are ranked higher
    - Hashtags are treated as Hashtag nodes in graph so a path involving the same users and only mentions will be shorter.

---

2024-02-11 Sun: [7 hours] \
Change log for Remote Emitter

**Major Changes**
- [Rewrote](https://github.com/Aishlia/remote-emitter/commit/2a42c762dd741290e4ed2d0b16048bbf891b7f84) connections logic to utilize Neo4j graph db. Users are now stored as nodes and their connects are vertices. 6th degree connection displays faster than Firestore implimentation's calculation of 3rd degree. 
- Removed directionality of connections (temp removal). For now, all mentions are treated as bi-directional.
- [Redesigned](https://github.com/Aishlia/remote-emitter/commit/ee36638d4b313aa92e526b7f33094c8e7b295ff0) graph data structure. Re-added connection directionality. Connection type is now stored in vertices. (@UniqueRobot65 ↔ @VibrantBee22 ← @ZealousWanderer97 → @QuirkyXenops7)


**Minor Changes**
- Updated frontend to properly display new information. When a user clicks on another user's profile, they see the chain of users that connects them (ie. @me - @friend - @friend2 - @friend3 - @target_user)
- [Removed](https://github.com/Aishlia/remote-emitter/commit/63dd92734a7cc982451d402745b926e3be372b7d) formatPath function
- [Readded](https://github.com/Aishlia/remote-emitter/commit/b516fa6906c7752721294ad6fc303fa6651d19b5) location data. Not sure when I accidentally removed it
- [Adjusted](https://github.com/Aishlia/remote-emitter/commit/9fe92e3dedb9a412b8234eb9e8999b39f87c228f) graph query to remove extra names. Connection chains start with the viewing user and end with the profile being viewed.
- [Add](https://github.com/Aishlia/remote-emitter/commit/b13361084841e0c67c163bfbfa2c473c9e3eb8a8) prevention of double submitting with submit state. New submitions not allowed when submit state is on. 

2024-02-10 Sat: [4 hours] \
🧧🧨🔴 Happy New Year 🐲🐉🏮 \
Change log for Remote Emitter

**Major Changes**
- Changed chain logic. Added semi-functioning directionality. @a mentioning @b should be counted as @a → @b. @b then mentioning @a back should be counted as @a ↔ @b

**Minor Changes**
- Minor CSS changes for mobile view

2024-02-09 Fri: \
Change log for Remote Emitter

**Major Changes**
- [Added](https://github.com/Aishlia/remote-emitter/commit/5da19d881c538c33c33701f6aa5fa6c36331d902) new Firestore interests collection to store followed hashtags. Users who use a hastag are now following that hastag.
- [Added](https://github.com/Aishlia/remote-emitter/commit/1d9ac584f575e5f3a8937916d127c6c26ca437eb) global view and home view to HomePage. Global view shows all posts, home view shows only posts tagged with a hastag that the user is following.

**Minor Changes**
- Finally [ran](https://github.com/Aishlia/remote-emitter/commit/99dfbd879bea76cd0c9278337357030c0445579c) prettier
- [Wrote](https://github.com/Aishlia/remote-emitter/commit/c4c2d18d887dd8f58def86df1d9ac03a4b8370c4) README overview of how Firestore collections are used

2024-02-08 Thu: \
Change log for Remote Emitter

**Major Changes**
- [Added](https://github.com/Aishlia/remote-emitter/commit/04caf6a9ab13729a50e52a5919c68ab31c9dfa1a) Heatmap POC
- [Created](https://github.com/Aishlia/remote-emitter/commit/be61e64c70d7642454c359ef70e05b7fb00ae4a6) POC for connection chain calculation using new Firestore collection "connections"

**Minor Changes**
- [Added](https://github.com/Aishlia/remote-emitter/commit/810d17d8227eca7c7a301a2f9aaa18a9eb672acb) links to global heatmap to HomePage
- [Removed](https://github.com/Aishlia/remote-emitter/commit/a52fbd1b3bbcc14ef09e9047d6080e598276b828) unused const assignment

2024-02-07 Wed: \
Change log for Remote Emitter
- Introduced session-based unique names
- Linked @mentions to user pages.
- **Added # tagging functionality with /tag/\<tag\>**
- Updated homepage logo for return navigation
- Shortened datetime and address displays\
/\ v0.0.0
- Made usernames non-editable; set Cloudflare environment variables
- Removed submit button from UserPage; removed send button from HomePage
- **Added mention array and hashtag array columns to database**
- Added posts and mentions buttons to profile
- **Introduced top 3 hashtags feature**
- Linked main username on HomePage to /\<username\>

2024-01-06 Tue: Planned high level objective for webapp (Remote Emitter). Added spam filter to prevent repeat messages. 

2024-02-05 Mon: Created test webapp with nosql client-side db. User can post a message and set some username. The message is posted with the current location and timestamp. Clicking on a username loads a /<username> page with all posts from that username. 

---

2024-02-4 Sun: [2 hours] Began creation of testing webapp that compares various location service APIs to see which is most accurate under a variety of conditions. 

2024-02-3 Sat: [5 hours] [Created](https://github.com/harmony-one/s/commit/7b770fcee25c79ff4ed6868fb86fa71e6cf64ab0) webpage to display location data from OpenStreetMap Nominatim API. [Created](https://github.com/harmony-one/s/commit/0c9ad101603b14b927f19a63fcf7c114b1a9495e) iOS app to display location data via Apple NSLocation data. Working on allowing specific location and coordinate dump. [Reviewed](https://aws.amazon.com/blogs/mobile/add-a-map-to-your-webpage-with-amazon-location-service/) archetecture for amazon location services mapping. Began setup of demo with service.

2024-02-2 Fri: Researched potential location tracking methods and the limitations of airdrop and NFC on iPhone.

2024-02-01 Thu: Created a test of in-mem data. No issues with querying from 100k rows of wallets stored in mem (no internet connection needed). Massive slow downs by 200k rows. 

2024-01-31 Wed: [Created](https://github.com/harmony-one/s/commit/fc87750c2e77a58921d7306ff30390da12373b03) base of PmF. [Implemented](https://github.com/harmony-one/s/commit/91264c4bb5cf5053decc122172189068795a1aa7) wallet lookup based on last 4 digits and emoji encoding and 2 error codes. 

*2024-01-30 Tue: Review code changes to 1Bot for image inscription. Review method for image storage (either store images or use Telegram API to fetch images on page load). If open-source social collection project is found, see if feasible to implement prior to ETHDenver. Work on the framework for the chained lottery.

*2024-01-29 Mon: Trying Phantom quests. Look for open source projects that use a social collection aspect that doesn't require NFC. Review code changes to 1Bot that remove all but 1 ONE from user wallet to cover gas fees for inscription of images.

---

2024-01-28 Sun: Tested Phantom mobile.

2024-01-27 Sat: Continued using Diamond on Deso and testing various social finance products. 

2024-01-26 Fri: Interview candidated. "share" button on 1Bot image generation to inscribe prompt and put on last 2 letters of txn .county. Tested DeSo Diamond. 

2024-01-25 Thu: Planned new lottery system for social referrals

2024-01-24 Wed: Footprint SQL queries to gather lottery stats. 8 hours in, approximately 512 total inscriptions and 22 unique addresses.

2024-01-23 Tue: [Pushed](https://github.com/harmony-one/s/commit/34cc3c3e6d80cf63071a23a134012b0b301e8d0e) minimal multi-owner contract, and [pushed](https://github.com/harmony-one/s/commit/db2a42f1478528752efcb5b9bb010a61c8f3a5a3) minimal single-owner contract. [Wrote](https://github.com/harmony-one/s/blob/main/s-msw/README.md) README.md.
 
2024-01-22 Mon: [Created](https://github.com/Aishlia/PaperTradesBot/commit/f2c6b20d58c70c0fe387ffa752a82088277a743c) telegram paper trades bot. [Fixed](https://github.com/Aishlia/PaperTradesBot/commit/9b839cada02f2e7153648aeeb9216113f2693aeb) logic of bot. [Added](https://github.com/Aishlia/PaperTradesBot/commit/cce2fd7ba8d93178c9a03b7cdd33e722789b2873) live price fetch. 

---

2024-01-21 Sun: Inlined variables and simplified Minimal Social Wallet. 

2024-01-20 Sat: Researched Polymarket and searched for similar projects. 

2024-01-19 Fri: Monitored Onescriptions ONES launch and gathered basic launch stats.

2024-01-18 Thu: Found new lead for senior eng position. Prototyped new pool based flip with Theo. Setup and tested podcast. 

2024-01-17 Wed: Pulled protocol stats for Harmony, Polygon, Avalanche, and Near from footprint and API calls. Created spreadsheet comparing gas fees, utilization, and other stats for Harmony, Polygon, and Avalanche (could not find reliable easily accessible sources for Near). 

2024-01-16 Tue: Tested interacting with inscriptions on Avalanche (AVAV on Avascriptions). Minted inscription tokens and listed new tokens. Generated graphic for Harmony x Onescription announcement. 

2024-01-15 Mon: Fed Holiday

---

2024-01-14 Sun: Wrote speaker bios and other response questions for team members for ETHDenver applications. 

2024-01-13 Sat: Tested minimal secure wallet. 

2024-01-12 Fri: Created POC for a contract that holds ONE tokens for you. This limits your hot wallet's exposure. When you need more tokens, you can send a transaction work 0 ONE to the contract and the contract will automatically send you 100 ONE tokens back. This way, you still have access to all of your funds, but in the event you sign something you shouldn't, your exposure is limited to however much you want to refill your account with. [Contract](https://explorer.harmony.one/address/0x80a7f21728d263a64a4acac56e9c43dea997ee30) and [code](https://github.com/harmony-one/s/commit/fc63f102bf473ce615f94cbcaab11e558f141f35).

2024-01-11 Thu:[Added](https://github.com/harmony-one/s/commit/ce97d2b7aeadfbe18735a43abea1d5df8f8e59a9) fee counter for bridge stats to find gas charged across bridge transactions from fly.io. Generated and designed graphic for Harmony 2024: ONE Finality substack post. 

2024-01-10 Wed:[Found](https://github.com/harmony-one/s/commit/dfa3fdeea1b30d5c14946936b9a0375063c7ade1) top 3 pairs from Harmony to other chains and top 3 pairs from other chains to Harmony on the bridge. Created manual prototype for BTC - ONE flip using call data and OP_RETURN. Created front end with hex converter. 

2024-01-09 Tue: Planned btc.country setup and researched methods for deriving receipt address from send address on Bitcoin. [Created](https://github.com/harmony-one/s/commit/91071fd9cfaf9389c984b5d10b9009e3cbe23610) quick bridge stats scraper. Currently gets transaction value and number of transactions in various statuses (waiting, in progress, error, success etc.) for the last week. [Added](https://github.com/harmony-one/s/commit/95c3d3bf40930020af74089668029a21f7da16bf) list of networks by number of transactions. Reviewed pricing model for moc.

2024-01-08 Mon: [Reviewed](https://lucid.app/lucidchart/e2275294-1899-4f72-a1e8-d934146d2942/edit?invitationId=inv_49cc2640-ae23-4c26-aed0-d95e788e3ca6) moc setup and btc.country.

2024-01-07 Sun: Reviewed Q1 roadmap.

2024-01-06 Sat: Tested custom ownable function added in PR#8.

2024-01-05 Fri: Reviewed [steemit.com](https://steemit.com/) reward structure implimentation with Casey— created first draft reward tiers for A tokens. [Added](https://github.com/harmony-one/s/pull/9) custom burn function to remove ERC20Burnable.sol dependency from OpenZeppelin and removed ERC20FlashMint.sol dependency.

2024-01-04 Thu: [Added](https://github.com/harmony-one/s/pull/8) custom ownable functions to enable removal of Ownable.sol dependency from OpenZeppelin (more notes in PR#8). [Created](https://lucid.app/lucidchart/e2275294-1899-4f72-a1e8-d934146d2942/edit?invitationId=inv_49cc2640-ae23-4c26-aed0-d95e788e3ca6) basic framework for user interaction with .country and reward structure with A tokens. 

2024-01-03 Wed: Researched other decentralized management application, and wrote some [notes](https://github.com/harmony-one/s/commit/427ece5f557f53b637d884389ba207ad4ba10acf) on how .country single letter sites could be governed. 

2024-01-02 Tue: [Created](https://github.com/harmony-one/s/pull/5) contract for tokens. Researched best methods for token allocation and tokenomics for governance letter tokens.

2024-01-01 Mon: New Years OOO

---

2023-12-31 Sun: Continues debugging sendToken.

2023-12-30 Sat: [Added](https://github.com/harmony-one/s/pull/4/files) implementation started on Friday for interaction with safe ABI. sendToken uses execTransaction from safe. Currently using a placeholder ERC20 ABI in getERC20ABI().

2023-12-29 Fri: Read through Gnosis safe [source code](https://github.com/safe-global/safe-contracts/blob/main/contracts/Safe.sol) and Protofire gnosis python CLI [source code](https://github.com/harmony-one/safe-cli) to find relevant contract. Worked on generating ABI from contract that matches expected ABI of our safe implimentation.

2023-12-28 Thu: Worked on the Gnosis interaction. [Refactored](https://github.com/harmony-one/s/pull/2) gnosis function logic. 

2023-12-27 Wed: Researched various implementations of interactions with Gnosis Safe. Reviewed safe contracts to get a better understanding of what needs to be implemented.

2023-12-26 Tue: [Added](https://github.com/harmony-one/s/commit/e2cb652e89681a48dc7f412962e3064a9a94d9b6) test for create wallet function and testing TODO. [Created](https://github.com/harmony-one/s/commit/1e69377af23a9e5feef4addb87e5926bd6d3c09c) Gnosis send framework and reorganized files. [Added](https://github.com/harmony-one/s/commit/78c0424688880f6449ca6b207d9b419eccc845ff) check balance for gnosis safe. Validated metric collection for VoiceAI.

2023-12-25: Christmas OOO

---

2023-12-24 Sun: Assisted in comparing alternate bridge effectiveness and fees.

2023-12-23 Sat: Began writing testing for wallet.

2023-12-22 Fri: Reviewed [dependency source code](https://github.com/ethereum/go-ethereum) to see how much needs to be re-written. Wallet currently utilizes 5 go-ethereum imports and approximatly 20 external functions.

2023-12-21 Thu: [Added](https://github.com/harmony-one/s/commit/4a40d98bb398f25ecd9c7b9a2e63baa640aaa2ad) framework for Gnosis safe interactions focusing on approving pending transactions. [Reworked](https://github.com/harmony-one/s/commit/d1b31b16d20a6423852f69af25796c5c883bb87e) parsing logic to improve consistency and clarity.

2023-12-20 Wed: [Created](https://github.com/harmony-one/s/commit/5fa578235ebf035b1f78b8564a1401697f55cded) go implementation of wallet with ability to create new wallets, receive tokens, check balance, and import wallet. [Added](https://github.com/harmony-one/s/commit/54b5c65708ea4bfeb8a9e5e3bccc37305f940260) send token functionality.

2023-12-19 Tue: [Created](https://github.com/harmony-one/s/commit/8b1a61d65068d27dcb035ec0a3636d3e38fb7505) c test function for pulling balance data. 
