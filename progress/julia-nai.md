2 week: Minimal application agent. Apply for a specific job using an LLM and autofill to intelligently respond to all application questions based on resume and any user input.

---

2024-04-18 Thu: Packed boxes at the office. Packed swag and cleaned closet. Moved desk and some chairs out.

2024-04-17 Wed: Synced on expectations for extension form filling. Set 2 week deliverables. 

2024-04-16 Tue: Drafted system engineer requirements that are not listed in job description. Tested different input methods for ChatGPT to get best resume matches. 

2024-04-15 Mon: Tested form filling with chrome extensions. Reviewed more system engineer applicants.

---

2024-04-14 Sun: [1 hour] Moved some boxes out of the office.

2024-04-13 Sat: [1 hour] Reviewed progress and code for performance reviews. 

2024-04-12 Fri: Frameworked a extension system for automatic job application.

2024-04-11 Thu: Tested using selenium for automatic job application. Ran into recaptcha issues.

2024-04-10 Wed: Wrote basic form filling with selenium.

2024-04-09 Tue: Sync on automatic job application matching (applicant side rather than employer side).

2024-04-08 Mon: Revised and finalized performance reviews. 

---

2023-04-07 Sun: [4 hours] Moved some big items out of the office.

2023-04-06 Sat: [1 hour] Reviewed more system engineer resumes.

2023-04-05 Fri: Wrote and revised employee reviews.

2023-04-04 Thu: Manually reviewed applicants for system engineer.

2023-04-03 Wed: Reviewed applicant resumes and noted good and bad aspects for training. 

2023-04-02 Tue: Continued Lever API resume pulling.

2024-04-01 Mon: Started using Lever API to pull applicant resumes. Ran into issue with API and contacted support. 

---

**2024 Q1 Review (92 hours)**

I prototyped a social media platform called Remote Emitter using Firestore for message storage, adding features like username-based posting, timestamping, location stamping, user-specific pages, and hashtag support. I optimized storage and indexing for sub-100ms updates, integrated with Cloudflare for automated deployment, and utilized Neo4j to calculate nth-degree user connections with sub-400ms latency up to 6 degrees. For the h.country project, I migrated relevant Remote Emitter features, implemented link handling, defined action specifications, and created a prod deployment process, while also researching AI models trained on unlabeled voice data.

I worked on the Onescriptions ONES launch, gathering statistics, testing inscriptions on Avalanche, and developing minimal on-chain security proof-of-concepts and a BTC-ONE flip prototype. I focused on data analysis, model training, and resume collection for the PmF project, implementing wallet lookup features using 4 digit codes, emojis, and error codes. I automated parsing of comments from "Who wants to be hired?" posts on Hacker News, manually collected 500 resumes for GPT analysis, and researched additional resume sources to expand the dataset.

I researched voice AI models particularly focusing on those capable of processing unlabeled data such as vave2vec and looking into papers experimenting with the impact of more unlabeled data on model quality. I concluded that the largest novel application that we could pursue would be a LLM analogue operating purely on unlabeled voice data (a voice to voice model rather than a voice to transcription to text to synthesis flow). The feasibility of this project was determined to be outside of our 3 month scope as existing implimentations were not compelling enough, especially on our available dataset. 

---

2024-03-31 Sun: [3 hours] Compared first 100 Lever resumes for System Engineer with hard requirements. 

2024-03-30 Sat: [2 hours] Gathered Lever resumes for searching against applicants. 

2024-03-29 Fri: Attempted to improve prompt for resume comparison. Brought Li up to speed with project. 

2024-03-28 Thu: Compared first 100 resumes with more specific hard requirements for System Engineering. 

2024-03-27 Wed: Attempted ordered ranking rather than best fit of set to order all resumes in a set. 

2024-03-26 Tue: Ran comparisons on first 100 resumes for best fit for System Engineering position. Compared 10 at a time in rounds. 

2024-03-25 Mon: Compared multiple resume ranking methods against my own choice top candidate of a set of resumes. 

---

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

2024-03-03 Sun: [16 hours] ETHDenver

2024-03-02 Sat: [19 hours] ETHDenver

2024-03-01 Fri: ETHDenver

2024-02-29 Thu: Flew to Denver. Visited main expo and 4 side events. 

2024-02-28 Wed: Continued researching offices. Planned ETHDenver first day with Sun and Alaina. 

2024-02-27 Tue: Gathered feedback on h.country from Theo P and Theo F. 

2024-02-26 Mon: Added test data to h.country. Looked into offices. 

---

2024-02-25 Sun: [1 hour] Coordinated with Theo P on changes from his ETHDenver feedback. 

2024-02-24 Sat: [1 hour] Cleaned up backend deploy process to mantain live version for Theo P. 

2024-02-23 Fri: Toured offices. Coordinated final changes before ETHDenver. 

2024-02-22 Thu: Changes:
- [Changed](https://github.com/harmony-one/h.country/commit/995b4cde33ebfd8c8e9b31ea8b1524cb25eeaee8) window prompt text
- Review and [merged](https://github.com/harmony-one/h.country/commit/8136bca4a2f0a816ffdbee79458cd4289cacb7ac) PR #72
- Updated some frontend displays
- Made white versions of the number and slash svgs to fix color issues
- Defined URL handling

2024-02-21 Wed: Coordinated UI changes for prompt texts. 

2024-02-19 Mon: Updated package lock to fix deploy. 

---
2024-02-18 Sun: [1 hours] Updated the actions specification rules. 

2024-02-17 Sat: [2 hours] Created hprod repo to deploy to h.country (prod). h.country repo deploys to g.country (dev). 

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

2024-02-10 Sat: [6 hours] \
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

2024-01-28 Sun: [1 hour] Tested Phantom mobile.

2024-01-27 Sat: [1 hour] Continued using Diamond on Deso and testing various social finance products. 

2024-01-26 Fri: Interview candidated. "share" button on 1Bot image generation to inscribe prompt and put on last 2 letters of txn .county. Tested DeSo Diamond. 

2024-01-25 Thu: Planned new lottery system for social referrals

2024-01-24 Wed: Footprint SQL queries to gather lottery stats. 8 hours in, approximately 512 total inscriptions and 22 unique addresses.

2024-01-23 Tue: [Pushed](https://github.com/harmony-one/s/commit/34cc3c3e6d80cf63071a23a134012b0b301e8d0e) minimal multi-owner contract, and [pushed](https://github.com/harmony-one/s/commit/db2a42f1478528752efcb5b9bb010a61c8f3a5a3) minimal single-owner contract. [Wrote](https://github.com/harmony-one/s/blob/main/s-msw/README.md) README.md.
 
2024-01-22 Mon: [Created](https://github.com/Aishlia/PaperTradesBot/commit/f2c6b20d58c70c0fe387ffa752a82088277a743c) telegram paper trades bot. [Fixed](https://github.com/Aishlia/PaperTradesBot/commit/9b839cada02f2e7153648aeeb9216113f2693aeb) logic of bot. [Added](https://github.com/Aishlia/PaperTradesBot/commit/cce2fd7ba8d93178c9a03b7cdd33e722789b2873) live price fetch. 

---

2024-01-21 Sun: [2 hours] Inlined variables and simplified Minimal Social Wallet. 

2024-01-20 Sat: [1 hour] Researched Polymarket and searched for similar projects. 

2024-01-19 Fri: Monitored Onescriptions ONES launch and gathered basic launch stats.

2024-01-18 Thu: Found new lead for senior eng position. Prototyped new pool based flip with Theo. Setup and tested podcast. 

2024-01-17 Wed: Pulled protocol stats for Harmony, Polygon, Avalanche, and Near from footprint and API calls. Created spreadsheet comparing gas fees, utilization, and other stats for Harmony, Polygon, and Avalanche (could not find reliable easily accessible sources for Near). 

2024-01-16 Tue: Tested interacting with inscriptions on Avalanche (AVAV on Avascriptions). Minted inscription tokens and listed new tokens. Generated graphic for Harmony x Onescription announcement. 

2024-01-15 Mon: Fed Holiday

---

2024-01-14 Sun: [4 hours] Wrote speaker bios and other response questions for team members for ETHDenver applications. 

2024-01-13 Sat: [2 hours] Tested minimal secure wallet. 

2024-01-12 Fri: Created POC for a contract that holds ONE tokens for you. This limits your hot wallet's exposure. When you need more tokens, you can send a transaction work 0 ONE to the contract and the contract will automatically send you 100 ONE tokens back. This way, you still have access to all of your funds, but in the event you sign something you shouldn't, your exposure is limited to however much you want to refill your account with. [Contract](https://explorer.harmony.one/address/0x80a7f21728d263a64a4acac56e9c43dea997ee30) and [code](https://github.com/harmony-one/s/commit/fc63f102bf473ce615f94cbcaab11e558f141f35).

2024-01-11 Thu: [Added](https://github.com/harmony-one/s/commit/ce97d2b7aeadfbe18735a43abea1d5df8f8e59a9) fee counter for bridge stats to find gas charged across bridge transactions from fly.io. Generated and designed graphic for Harmony 2024: ONE Finality substack post. 

2024-01-10 Wed: [Found](https://github.com/harmony-one/s/commit/dfa3fdeea1b30d5c14946936b9a0375063c7ade1) top 3 pairs from Harmony to other chains and top 3 pairs from other chains to Harmony on the bridge. Created manual prototype for BTC - ONE flip using call data and OP_RETURN. Created front end with hex converter. 

2024-01-09 Tue: Planned btc.country setup and researched methods for deriving receipt address from send address on Bitcoin. [Created](https://github.com/harmony-one/s/commit/91071fd9cfaf9389c984b5d10b9009e3cbe23610) quick bridge stats scraper. Currently gets transaction value and number of transactions in various statuses (waiting, in progress, error, success etc.) for the last week. [Added](https://github.com/harmony-one/s/commit/95c3d3bf40930020af74089668029a21f7da16bf) list of networks by number of transactions. Reviewed pricing model for moc.

2024-01-08 Mon: [Reviewed](https://lucid.app/lucidchart/e2275294-1899-4f72-a1e8-d934146d2942/edit?invitationId=inv_49cc2640-ae23-4c26-aed0-d95e788e3ca6) moc setup and btc.country.

2024-01-07 Sun: [1 hour] Reviewed Q1 roadmap.

2024-01-06 Sat: [2 hours] Tested custom ownable function added in PR#8.

2024-01-05 Fri: Reviewed [steemit.com](https://steemit.com/) reward structure implimentation with Casey— created first draft reward tiers for A tokens. [Added](https://github.com/harmony-one/s/pull/9) custom burn function to remove ERC20Burnable.sol dependency from OpenZeppelin and removed ERC20FlashMint.sol dependency.

2024-01-04 Thu: [Added](https://github.com/harmony-one/s/pull/8) custom ownable functions to enable removal of Ownable.sol dependency from OpenZeppelin (more notes in PR#8). [Created](https://lucid.app/lucidchart/e2275294-1899-4f72-a1e8-d934146d2942/edit?invitationId=inv_49cc2640-ae23-4c26-aed0-d95e788e3ca6) basic framework for user interaction with .country and reward structure with A tokens. 

2024-01-03 Wed: Researched other decentralized management application, and wrote some [notes](https://github.com/harmony-one/s/commit/427ece5f557f53b637d884389ba207ad4ba10acf) on how .country single letter sites could be governed. 

2024-01-02 Tue: [Created](https://github.com/harmony-one/s/pull/5) contract for tokens. Researched best methods for token allocation and tokenomics for governance letter tokens.

2024-01-01 Mon: New Years OOO

---

2023-12-31 Sun: [3 hours] Continues debugging sendToken.

2023-12-30 Sat: [3 hours] [Added](https://github.com/harmony-one/s/pull/4/files) implementation started on Friday for interaction with safe ABI. sendToken uses execTransaction from safe. Currently using a placeholder ERC20 ABI in getERC20ABI().

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

---

2023-12-15 Fri: Continued to heavily test text-based RPG with app. Tested Talk to ME! [Adjusted](https://github.com/harmony-one/x/pull/398) output for log parser. 

2023-12-14 Thu: [Created](https://github.com/harmony-one/x/pull/387) parsing script for VoiceAI transcripts to generate a text file with user readable conversation transcript and some session analytics. Continuously tested playing text-based RPG with app. 

2023-12-13 Wed: Opened PR to [whitelist](https://github.com/harmony-one/swap-token-list/pull/2) lUSDC and [for](https://github.com/harmony-one/swap-token-list/pull/3) lUSDT. Tested opening a ONE/lUSDC pool on swap. Waiting for Ethereum to Linea bridge to open larger pool on swap. [Created](https://github.com/harmony-one/x/issues/382)/[investigated](https://github.com/harmony-one/x/commit/51436e3107e0b7faafe1c814965968c0bedf40e3) issue #382 on pausePlayBug branch.

2023-12-12 Tue: [Optimized](https://github.com/harmony-one/x/pull/363) microphone latency by removing debouncer on press & hold button. Pushed [fix](https://github.com/harmony-one/x/issues/364) for issue #364 to synchronously handle Press & Hold interrupting playback. Added haptics logging to transcript to attempt to diagnose issue #345.

2023-12-11 Mon: [Added](https://github.com/harmony-one/x/commit/104db3f7f393ef50970fd96d5362095c40f145e2) haptics and increased button timeout of trivia gesture. [Hotfixed](https://github.com/harmony-one/x/commit/614ebbcfdea3f8380b37804fc5b012d089e952cd) surprise me button long press disabling other buttons. [Fine-tuned](https://github.com/harmony-one/x/commit/bb3578fd57c198b60519bb910767ca9f57099372) response. [Adjusted](https://github.com/harmony-one/x/commit/27b2849ab6d38f33569ee7cfa345c856b815d08c) queries to directly use preferredLocal; evaluating the need to keep Languages.swift. Validated dialect support\* with Cantonese. [Fixed](https://github.com/harmony-one/x/commit/296fde859f85e3b4fe13ad5f4b911edd73cca311) and added more [fixes](https://github.com/harmony-one/x/commit/8a62bfb74d11781319cd3663e802a4d43305eca9) for \<private\> transcript issue (waiting to see if fix works for testflight/appstore). 

\* Because of Apple's language code handling, system language set to `Cantonese, Traditional 繁體廣東話` does not work with the app— transcription fails. However, system language set to `Chinese, Traditional (Hong Kong) 繁體中文（香港)` does work with the app.

---

2023-12-10 Sun: [Created](https://github.com/harmony-one/x/commit/6941361763852c94919c1f3e3517b8140b69fd49) framework for analytics docs. [Added](https://github.com/harmony-one/x/commit/355f7e742277ecc748774113274bde54afa92518) trivia as long press on Surprise Me button.

2023-12-09 Sat: Time moved to Sunday.

2023-12-08 Fri: Pulled Voice 2 metrics for usage and total sessions. Researched Google Gemini API, confirmed API availability on Dec 13. Filmed text based RPG demo video (need to edit over the weekend). Demoed Whisper trivia to Theo F.

2023-12-07 Thu: Debugging tests suite not running. [Created](https://github.com/harmony-one/x/commit/eb6758a48f1f8047e3bb4b5a420419ba78207949) collection script for data from Elasticsearch and Sentry. [Fixed](https://github.com/harmony-one/x/commit/475032959171946201ae9abf3e7d69f6914a292d) the error counter and verified against Sentry dashboard. Assisted Alaina in setting up and running collection scripts. [Created](https://github.com/harmony-one/x/commit/cdeeb88b8863b31018b0a8189f4e5db02f51e689) basic beginner guide readme for collection scripts. 

2023-12-06 Wed: [Created](https://github.com/harmony-one/x/commit/17e6e0f27a5b13cbd31d6311f312cde7484e551d) openAI API stat scraper. [Added](https://github.com/harmony-one/x/commit/d6be2635c595dc09e19fe1662682b565d93b1395) average first and total response times. Helped debug the tests not working. 

2023-12-05 Tue: [Created](https://github.com/harmony-one/x/commit/fe6f76f2e3365e77d210f9265bc40b632544ff8c) and [updated](https://github.com/harmony-one/x/commit/17396077f1c767298d73017e858eff7b4b3ebaa6) test for CreateUser.swift. [Expanded](https://github.com/harmony-one/x/commit/da8686567602b4aebc7b80b68e3e2d5da56e96fe) testing for buttons in ActionViewTests. [Resolved](https://github.com/harmony-one/x/commit/e8f32dd2170059616a65923fbd5911173f7f9b25) some lint issues. 

2023-12-04 Mon: [Add](https://github.com/harmony-one/x/commit/2302110822a940c743f358961eb474deaf8c6595) guard against empty return in RandomFact.swift. [Updated](https://github.com/harmony-one/x/commit/51f16b7eca0e38576fc01b6b8a4d714c01f2a8b0) testGetTitle. [Added](https://github.com/harmony-one/x/commit/970dc6f69b994e043cc6d6828125544c275ddce6) tagging to differentiate Sentry alerts from internal testings vs. live app. Fixed incomplete ArticleManager test and removed test for removed function. 

---

2023-12-03 Sun: Tested and merged [PR#250](https://github.com/harmony-one/x/pull/250) first pass removal of custom instructions from saved transcripts. Finally got API key working on local build. Worked with Rikako to plan getting test coverage to 99%. 

2023-12-02 Sat: There are multiple instances of the custom mode text in the app, so I am working on identifying which are still needed and which are extraneous. Worked on getting local build working again with new API key.

2023-12-01 Fri: Tested the app and identified some issues with custom mode selector. The original implementation of custom instructions through the system seems does not seem to be connected entirely so overriding that with custom modes does not produce the intended results. 

2023-11-30 Thu: [Changed](https://github.com/harmony-one/x/commit/685e963c17facf4cec04549d8bde487e58c97c37) wording and capitalization of action sheet options in line with specifications. Moved account related options to a sub-page of "Purchase premium" option in action sheet. 

2023-11-29 Wed: [Implemented](https://github.com/harmony-one/x/commit/74f2753e7d696440765db255341103a3e7aebbe3) selection of custom modes detailed by Theo P [here](https://harmonyone.notion.site/3-Predefined-Custom-Instructions-b36546c4ee544aea8168c7f046c476c5?pvs=4) as a drop down in the [system settings page](https://github.com/harmony-one/x/commit/0a75eca8eea805767139e8784f45dcaa77aec2c3). The example interactions are added as user/agent. Needs to be tested. 

2023-11-28 Tue: [Wrote](https://github.com/harmony-one/x/commit/c4055e2625f2f0e89f0d2084fb807bfb9509d0a2) a function to test how liveliness check may work. [Created](https://github.com/harmony-one/x/commit/58208f43f42f0e9558a48fb92e25a8e44e903911) framework for custom instructions test. This test will make sure that custom instructions are working by expecting certain outputs given fixed inputs (ex. name is Sam, no "Sorry" etc.). 

2023-11-27 Mon: Researched how to impliment component testing for liveliness check for GPT through app. Began implimenting testing in app.

---

2023-11-26 Sun: Tested app build to see if build issues from Friday were resolved. Ran a small feasability test through ChatGPT whisper. While the responses for debate partner could be good, the lack of recent information does limit the topic. Something like a more esoteric moral debate seems to work. Hallucinations make a fact based debate rather difficult. (In debate terms, a LD or old PF would work best). 

2023-11-25 Sat: Migrated relevant private notes off of Notion pending my removal from Notion editing.

2023-11-24 Fri: [Reviewed](https://github.com/harmony-one/x/pull/250) removal of ChatGPT custom instruction from Nagesh and Aaron. Worked on resolving issues with building. When attempting to run latest build, encountered build failiures as a result of recent changes. 

2023-11-23 Thu: Thanksgiving

2023-11-22 Wed: [Removed](https://github.com/harmony-one/x/commit/bcafb1b131f8c82d066931c0dd486c3d5b2ac6df) the custom instructions from saved transcripts ([#250](https://github.com/harmony-one/x/pull/250)). Began working on liveliness check for GPT component (automated testing of hard coded intput and response). 

2023-11-21 Tue: Worked on removing the white background from action sheet. Worked on saving the conversation transcript from Voice AI to notes.

2023-11-20 Mon: [Updated](https://github.com/harmony-one/x/commit/7efbe822df80d1100b10cbc6218d58b43fb00855) topArticles list to remove some footballers, content with adult themes, and potentially repetitive titles. Total topics reduced from 1182 to 1158. 
[Added](https://github.com/harmony-one/x/commit/bf345dc969fc34fbdc2e43f35e3d2e5ecd50e146) action sheet for long press on Pause/Play button. TODO: remove white background and replace with darkened app screen. [Updated](https://github.com/harmony-one/x/commit/b0c79a60bf77a7bdbe846c8a22c72afe46a700a2) object name. 

---

2023-11-12 Sat - 2023-11-19 Sun: Paid time off.

---

2023-11-10 Fri: Engaged in product testing, investigating the handling of overlap with the tap/hold buttons. When both are activated, the other occasionally does not turn off. This seems to be related to the way stop transcribing is handled. [Assisted](https://github.com/harmony-one/x/commit/73204359eae8079c968d531fd0333591db373642) in reverting code that was causing some compile issues. Triaging issues related to .gitignore. [Merged](https://github.com/harmony-one/x/pull/163) and reviewed #163 Add updates to unit tests.

2023-11-09 Thu: [Created](https://docs.google.com/spreadsheets/d/1IlE0EpLUsmmDPwdx2b6adzw1UGeY3f-o-dO6qbWN0b8/edit?usp=sharing) dynamic pricing calculator spreadsheet for GPT 4 with adjustable assumptions. 
[Reverted](https://github.com/harmony-one/x/commit/0659298ca8caca81ec4c34f26ce3e2fd05a4c897) custom instructions.
Worked on investigating the tap to speak button slowness. I have a local build which dumps extra debugging information in an overly verbose way, but I have not been able to identify the source of the issue yet. 

2023-11-08 Wed:
[Created](https://github.com/harmony-one/x/commit/9f894a4c88da0b87dd56cef53bebd61ebdf91a1b) app to test for optimal synthesis chunking strategies and replicate odd synthesis behavior.
[Implemented](https://github.com/harmony-one/x/commit/d6ec4b9b140decad26b39d5b234a8b6a827e8c30) Theo P’s custom instruction set as default. Now, the user can ask questions about the app and receive guidance on how to use the app. The app says it is created by x.country team and gives some input on what can be done with the app.
[Reviewed](https://github.com/harmony-one/x/pull/143) Rikako’s language implementation. Tested Mandarin, English, Korean, and Spanish with great success.The user can speak in the language that their iPhone is set to and the app will respond in that language. For reasons seemingly related to the way dialects are handled by Apple, Cantonese does not seem to work. The random fact button will still read out in English. 

2023-11-07 Tue: I [started](https://github.com/harmony-one/x/tree/tap-to-send) work on the framework for the Tap to Speak/Tap to Send button. I reviewed Sun's [PR](https://github.com/harmony-one/x/pull/137) and began researching how to implement the missing component "Make the button interruptible." \
Right now, there seems to be some unintended behavior with interruptions. I am reviewing how the stopRecording() function is implemented. To have proper interpretability, I believe I will have to change the way stopRecording is implemented to avoid sending an incomplete query to GPT. 

2023-11-06 Mon: \
[Updated](https://github.com/harmony-one/x/commit/9fc0405b8d205f26b635035b95cb6d8762a78445) Skip button to use LongPressGesture and removed timer. Changed the long press times to default. \
[Hard coded](https://github.com/harmony-one/x/commit/a24e51d763529d81bba6a627931e3394f3efdf6c) 600ish wiki titles and changed the random fact query to summarize a random topic from the array of titles. \
[Increased](https://github.com/harmony-one/x/commit/ad46b0dbe9b0640690d5045c19d9938dc71dabf1) the number of hard coded titles to 1182 from a combination of most views Wiki articles of all time and top 400 wiki articles from 2021 to avoid ChatGPT’s knowledge cutoff. \
[Added](https://github.com/harmony-one/x/commit/2760b2bef0f64552e1e7a91a35c9d5a404037b08) Say More feature: a new button to expand on last topic. This button replaces the Skip button. \
[Began](https://github.com/harmony-one/x/tree/surprise-me) changes to make Random Fact button into Surprise Me button. Currently functional with wikipedia summary, riddles, trivia questions, jokes, inspirational quotes, and fun facts, but there is higher than acceptable repetition in riddles, trivia question, jokes, and inspirational quotes. 

---

2023-11-05 Sun: [Changed](https://github.com/harmony-one/x/commit/bfc50ee2c6c8b9d18c6b23f39debeb20b79a6bfd) the random fact button to summarize a random wikipedia topic from the top wikipedia topics in 2 sentences or less. 

[Added](https://github.com/harmony-one/x/commit/3709ad808179f494cb3bab3d2b380725e5c5bb07) long press on Repeat Last button to open settings and [resolved](https://github.com/harmony-one/x/commit/5f0cf52887a863c8f5967840497c5c80f96e7559) an issue with longer-than-default long presses being inconsistent. When the minimum long press time is changed from default, the long press seems to only work 80% of the time. I believe this is because sometimes, since 3 seconds is very long, the finger moves more than the allowed distance; therefore, it is not registered as a long press. I added a geometry reader to match the maximum distance that your finger can move during the long press to the size of the button.

2023-11-03 Fri: [Implemented](https://github.com/harmony-one/x/commit/67c11ec307580d8b79525326c05a44586408a281) randomness for the random fact button. [Added](https://github.com/harmony-one/x/blob/main/voice/voice-ai/x/SpeechRecognition/SpeechRecognition.swift) a cap to the synthesis buffer. If the response doesn't have punctuation, the buffer would wait for the entire response to be streamed before synthesizing. Now, the buffer has a cap of 5 words. 
Extensively tested the random fact button. ChatGPT seems to be deterministic with random facts. From the ChatGPT website, I tried starting new multiple new conversations with the same prompt asking for a random fun fact and I got the same fun fact every time. Sun and I tested various ChatGPT parameters, but we could not stop the same fact from showing up repeatedly.  

Sun, Aaron, and I discussed the following action items for potentially reducing latency. 1 word chunking for synthesis sounds bad as tested today. Consider “dynamic” or “exponential” chunking for synthesis. The first word will be synthesized as a single word, then the next two words will be synthesized together, and so on. Some fine tuning will likely be required. At a certain point, synthesis will transition to chunking by punctuations. If 3.5 is drastically faster than 4, we can send the user query to 3.5 and 4, use the faster response from 3.5 to give the initial sentence or phrase, and then complete the response with 4. This introduces concerns regarding response flow. To resolve this, an alternate implementation of this idea is to get the response from 3.5. As the the first sentence of the 3.5 response is speaking, send the first sentence response from 3.5 with the user input to 4 and start synthesizing the rest of the response. We would essentially have the whole time it takes for the first sentence from 3.5 to finish speaking, to get the response and synthesize the first phrase of 4. Aaron also suggested the possibility of loading llama 2 on device to accomplish something similar. Rather than using 3.5 to generate the initial response, we could use an on device llama 2. However, there are size concerns as llama 2 is 1-2 GB. 

2023-11-02 Thu: [Fixed](https://github.com/harmony-one/x/commit/9161edd65b7714d9af34e3350dba1a109ac304f3) MockSpeechRecognition to match changed base class. Prepared for 3:30 pm onward event by testing product and loading demo. 

2023-11-01 Wed: Added tests for [AppConfig.swift](https://github.com/harmony-one/x/commit/f9fe3fb4f963e5589c18abf748eb635027e50dec), [Usage.swift](https://github.com/harmony-one/x/commit/ef92b990f2ed76f4579cf0a9ee5f1c2628ad45a8), [AudioPlayer.swift](https://github.com/harmony-one/x/commit/eb0d4e9163a2c0676324515ca083c3803358a874), [VibrationManager.swift, DashboardView.swift, and String.swift](https://github.com/harmony-one/x/commit/2b9946097c63c0c5a1aaa41064f2391b0c7bf225). Raised total test coverage by 10%. Fixed MockSpeechRecognition after SpeechRecognitionProtocol class was changed. 

2023-10-31 Tue: [Modified](https://github.com/harmony-one/x/commit/ec269538f031671e2e845d34281c738f58e0d94d) ActionHandlerTests.swift (a complete tearDownWithError(), added assert messages, and removed file header). Added tests for [Permission.swift](https://github.com/harmony-one/x/commit/f1e15f9d9a114c7185ee5e2cb4c9e6fadcb109c4) and [SpeechRecognition.swift](https://github.com/harmony-one/x/commit/5eb27dc0ea82e53446f4d07655d9c47609c3a186).

2023-10-30 Mon: [Removed animations](https://github.com/harmony-one/x/commit/fb2ac5bbf6c4b41970e9773345a99867019f526b). Started researching [live test attestation](https://developer.apple.com/documentation/devicecheck/establishing_your_app_s_integrity) data. 

---

2023-10-27 Fri: Added in [visual feedback](https://github.com/harmony-one/x/commit/db24712085daae84c8f9bee4e60a3996ff72ec61) for when the app is synthesizing. In progress: Ending the synthesizing indicator when the app starts speaking and starting the speaking indicator. 

2023-10-26 Thu: Worked on the [selection of voices](https://github.com/harmony-one/x/commit/b754c92eabc5942f74763e95416c4f1206a75900) (added Evan for the male voice per Theo P's request). Continued work on iOS 16 compatability changes. 

2023-10-25 Wed: Worked on duplicating code base and working on making a new version that is compatable with iOS 16 (Nagesh taking over). Worked with Sun to [implement](https://github.com/harmony-one/x/commit/2d881a3635251c8cade4778f9321046bef6daa92) a more pleasing voice (Ava enhanced) to his demo. 

2023-10-24 Tue: Created [settings page](https://github.com/harmony-one/x/commit/b93a5b0bbe4a02452fa0b17ec4a0e6ee20a7b285) per /app. Ran through change iterations Theo P to add support for more custom instructions and improve user clarity. There will be a selection for which profile to use and then a child menu to create a new custom instruction (Name & Custom Instruction fields). There will also be a user profile selection to add a name and description. 

2023-10-23 Mon: Pushed [PR build](https://github.com/harmony-one/x/commit/fbbe80dbe41c1d378dac74dfcb2d39ed2bff24dd) under Julia (bundle id: com.country.x.julie). Wrote up [deployment steps](https://www.notion.so/harmonyone/Deploying-Eve-to-Testflight-f77e9d2b6e864813ab6242d173ba48f5?pvs=4) to build and deploy apps to TestFlight for Sun and Yuriy. Working on resolving build issues (app builds directly from Xcode to iPad, but the installation from TestFlight is hung). 

---

2023-10-20 Fri: I built the edge build locally by resolving the missing AppConfig with the help of Aaron. Aaron also walked me through verifying and deploying the app to testflight (which I am now able to do with my credentials -- the most recent version of Ask Eve was deployed by me). I have started remaking Yuriy’s emotion build demo in swift. 

2023-10-19 Thu: Focused on collaborating with Yuriy to integrate the emotion build into the project. Yuriy is currently developing the application using React and hosting it as a web app on yuriy.x.country, and I am working on the cross platform react + expo stack to easily bring the app to iOS. 

2023-10-18 Wed: [Updated iOS app](https://github.com/harmony-one/x/commit/6c05a2aa64eb1b86b608124839631eba11026bd2) to display all available voices on device that the user can pick from (ie. native and user-downloaded) and added an icon. Assisted Theo F in loading app; he was able to confirm that downloaded premium and enhanced voices are accessible to apps. I will be investigating the best workflow to have the user download recommended voices. 

2023-10-17 Tue: Built a quick app that loads on [iPadOS 17.0.3](https://github.com/harmony-one/x/tree/main/mobile/samantha) that test the build in TTS synthesizer in iOS. While the speed is very very fast, the quality is very middling. Theo P has tested the various always available voices and selected 3 that are particularly good, and Theo F will test tomorrow. I will be looking into any potential methods for obtaining the [higher quality voices](https://developer.apple.com/documentation/avfaudio/avspeechsynthesisvoicequality/enhanced) that Apple has. However, these voices have to be downloaded on device before they can be used. 

2023-10-16 Mon: Downloaded the necessary simulators and application to build the iOS template. Beginning to study Swift/Obj-C (specifically focusing on audio classes that will be utilized). Through discussions with Frank, code refactoring for Discord bot will be done by tomorrow. 

---

2023-10-13 Fri: [Audio input testing](https://github.com/harmony-one/x/tree/main/audio_input_testing/end_to_end_test). Did some audio input testing in python. Synced with Stephen, will be shifting focus to transcription streaming APIs. Working with Theo P to determine metrics for user acceptance. 

2023-10-12 Thu: Set up Jupyter notebook to compare runtimes between PlayHT, Murf, Suno's Bark, and Vocode. Synced with Frank on the code structure of Discord Harmony bot and billing expectations.
