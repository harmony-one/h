2025-09-21 Sun: (2.0h) Continued timeline script review. Insight: found possible sign change issue, currently counting positive vs negative rather than detecting sign change.

2025-09-20 Sat: (2.0h) Continued going through Aaron’s timeline script. Insight: made slight change for yearly calculations, assuming strategy will be multi-year, IRR, internal rate of return, we can use 365.25, reduces error from ~0.27% in leap years to ~0.07% maximum error.

2025-09-19 Fri: Access by Aaron for backtest and timeline script. Insight: issues with IRR (internal rate of return) calculations, could be due to high defi yields being out of IRR range.

2025-09-18 Thu: Sync with Amanda and sourcing 2024 research and development per team member, accomplishments and difficulties, for Amanda.

2025-09-17 Wed: Team sync, narrowing focus on specific wallets to simplify finding IRR (internal rate of return) for leading wallets, supplied non-gauge wallets and higher earning wallets based on research and shared 6 target wallets with team. 

2025-09-16 Tue: Recalculation of Accelerated Recovery Proposal. Insight: removal of short term bonus leads to lower complexity and higher understanding.

2025-09-15 Mon: Governance Beta released to various community member, sourcing feedback. Insight: majority asking for custom governance space options for community DAOs, adds complexity that may be added post-launch.

---

2025-09-14 Sun: (2.0h) Iteration on scripts for wallet tracking, going back to Aaron’s original lp-data. Insight: Grid strategy covering multiple 100-tick LPs showing most consistent profitability.

2025-09-13 Sat: (2.0h) Continued tracking wallets. Insight: strategy is known, trading capital is known, missing information remains profitability, focus should be on simplifying wallets to track, not most profitable may be easier.

2025-09-12 Fri: Started base network script to track target wallet behavior. Operations for Lend contracts, and reviewed Infrastrucrure DAO. Made changes to upcoming governance release, correcting 50%+1 and 66.67% to be quorum and approval rate, respectively, matching most recent documentation.

2025-09-11 Thu: Sharing insights with team in detail, sync with Li, Artem, Frank, Rika. Added target wallet contracts found on [Nansen](https://www.nansen.ai/) for increasing and removing liquidity to track behavior.

2025-09-10 Wed: Added details to master product requirement document, answering clarifying questions from Artem. Continued dive into [Nansen AI](https://www.nansen.ai/). Insight: trace shows "multicall" and "increaseLiquidity" are only actions target wallet takes, proving positions are already open, and only liquidity is flowing, multi-position strategy of 100-tick positions. Distribution is not shown, the missing piece is seeing how the 99.9% liquidity of the wallet is being used every few minutes.

2025-09-09 Tue: Sync with Rika on tasks and guidance for defi concepts, covered AMMs (automated money markets) and basics to understand strategies for maximizing gains. [Nansen AI research](https://www.nansen.ai/) into target wallets. Insight: live actions show target wallet removes and increases 99.9% of their liquidty every few minutes. 

2025-09-08 Mon: Deep research into defi [LP strategy resources](https://medium.com/@rilwanwild/dlmms-pioneering-the-future-of-decentralized-finance-abc4970d199a). Insights: found DLMM (Dynamic liquidity market makers) as strategy that models our target wallet behavior.

---

2025-09-07 Sun: (1.0h) Continued community recovery vault calculations, initial governance should also show as beta, until all features are implemented.

2025-09-06 Sat: (2.0h) Reviewed snapshotX and initial spaces for governance. Insight: two default spaces available from beginning, Harmony Improvement Proposals, and Harmony General. (HIP space will include quorum)

2025-09-05 Fri: Continued verification for reward distribution from [Slipstream]((https://github.com/aerodrome-finance/slipstream)) source code. Insight: 100-tick range earns 9.5x more AERO rewards than 10% width liquidity while in range. Final feedback for initial governance product, initial release will not have opt in/out functionality, but off-chain solutions can be applied, two spaces by default will be Harmony Improvement Proposals, for protocol HIPs, and Harmony General, for non-protocol voting that does not require network stake quorum.

2025-09-04 Thu: Sync with Artem, Frank, Rika, and Li. Shared insights for internal wallet tracking and external wallet data found in Dune queries, focusing on grid strategy for AERO extraction. Shared initial findings and wallets that use the 100-tick grid strategy with team.

2025-09-03 Wed: Iterations for [Aerodrome queries](https://dune.com/queries/5725937), showing events and detailed rewards. Inisght: paired with other Dune queries, this shows the wallets profit within their 31 position grid strategy.

2025-09-02 Tue: Continued Aeordome search and created queries to test target wallet performance.. Insights: for Dune, found CLgauge2 is the target source for tracking wallet performance, [initial wallet overview query](https://dune.com/queries/5721307?category=decoded_project&namespace=aerodrome&contract=CLGauge2&blockchains=base) will continue with in depth review, following source isolation.  

2025-09-01 Mon: Labor Day

---

2025-08-31 Sun: (2.0h) Weekend deep dive into Aerodrome v3 concentrated liquidity mechanics. 

2025-08-30 Sat: (2.0h) Review of governance voting mechanisms and cli integration.

2025-08-29 Fri: Dune query analysis comparison between "DEX trade" and "Aerodrome trade" volumes. Sharing inconsistencies requiring further investigation.

2025-08-28 Thu: Review and edit of Alaina's Harmony Marketing 1-pager. Sync with Alaina and Amanda on current deliverables and project milestones.

2025-08-27 Wed: Total network stake calculations for opt-in style voting. Insight: minimum threshold of 33% total network stake (opt-out + opt-in) would need to be in place ot ensure robust protocol governance.

2025-08-26 Tue: Sync with Amanda for current work priorities. Governance system architecture planning and review of voting power.

2025-08-25 Mon: Review and sync with Alaina on daily and weekly deliverables.

---

2025-08-24 Sun: (2.0h) Community space with Crypto Land DAO, and Tenacious, going over governance, recovery, and development updates.

2025-08-23 Sat: (2.0h) Focused on new target wallet analysis using Aaron's data with Claude Code. Insight: identified potential Just-in-Time (JIT) liquidity providing strategy with 60% of positions closed within 10 blocks, 100% swaps hiting LP range (liquidity maximizing reward capture), 478 same-block operations. New fee reward information not matching directly with lp-data, needs further verification.

2025-08-22 Fri: Sync with Li and Artem on portfolio manager progress, shared new discoveries from Aaron's data analysis that need verification. Coordination on integrating verified strategies into portfolio management framework.

2025-08-21 Thu: Cloned Aerodrome's [Slipstream repository](https://github.com/aerodrome-finance/slipstream) locally to verify strategies against Aaron's dataset. Documentation gaps in Aerodrome requiring source code paired with Aaron's data as source of truth for accurate strategy modeling.

2025-08-20 Wed: Downloaded Aaron's complete lp-data and discussions with Stephen regarding immidiate initial discoveries.

2025-08-19 Tue: Initial review of Dune Analytics for Aerodrome pool. Finalized Aaron's strategy analysis.

2025-08-18 Mon: Review of team progress and q3 coordination. Cloned Aaron's repo to answer specific strategy questions and analysis with Stephen.

---

2025-08-17 Sun: (2.0h) Weekend review of community discussions.

2025-08-11 Mon - 2025-08-15 Fri: Out of Office

2025-08-10 Sun: (1.5h) Sync with RMC for potential Twitter space for next week.

2025-08-09 Sat: (1.0h) Pushed community feedback on initial governance structure moving forward with SnapshotX implementation finalization.

2025-08-08 Fri: Sync with Alaina on Q3 expectations and discussed potential coordination with Amanda.

2025-08-07 Thu: Troubleshooting wrapped ONE logging issues and lend utilization ratio discrepancies with protofire team.

2025-08-06 Wed: Recovery solution iterations and continued coordination on governance system first release requirements with Yuriy. Addressed ongoing integration challenges.

2025-08-05 Tue: Continued governance solution development with Yuriy, clarified requirements for first release of governance system. Insight: governance system requirements more complex than initially scoped, not all features possible onchain via snapshotX.

2025-08-04 Mon: Attended Stanford Blockchain Week event and discussions. Insights: no DeFi specific projects and protocols, discussed security with Aleo team and treasury management with CommonPrefix, collaborating on BTC strategies, most common, even from crypto insiders, is simply using Lombard and Babylon abstract platfroms with lower yields, no direct advanced BTC strategy for higher yields.

---

2025-08-03 Sun: (2.0h) Troubleshooting wrapped ONE logging issues, and reviewing % yield from funding rate arbitrage vs current perfect LP hedging strategy. Insight: funding rate arbitrage yield is higher (10%+ compared to consistent LP strategy), but higher risk of lower liquidity, higher slippage, and liquidation risks.  

2025-08-02 Sat: (1.0h) Follow up with protofire for rate limiting issues.

2025-08-01 Fri: Sharing sync recap with team and specific focus for continuation of Q3. Updating governance needs with Yuriy.

2025-07-31 Thu: In-person sync with Stephen and Li. Breakdown from community, governance, internal team, yield strategy progress, and deep dive into profitable LP strategies.

2025-07-30 Wed: Completed first month of Q3 review for tomorrow’s in person meeting. Released initial draft for recovery 1-year solution, community more active recently and more momentum to push accelerated recovery proposals.

2025-07-29 Tue: Iterations on 1-year recovery solution with chefsoysauce, RMC, and validators. 

2025-07-28 Mon: Reviewed current [portfolio-manger](https://github.com/harmony-one/portfolio-manager) progress and team commits.

2025-07-27 Sun: (1.0h) Completed Hummingbot review. Insight: LP strategies are very basic, only support downside protection for LP, no dynamic hedge, no upside capture.

2025-07-26 Sat: (1.0h) Review of Hummingbot LP strategies and funding rate arbitrage.

---

Completed team reviews and continued AI roll out across engineering team, establishing AI-native workflows that improved engineering efficiency. Personally led onboarding and tool standardization, unlocking over $1,000/month in API access per engineer via the Claude Max Plan (prior to [Aug 28](https://techcrunch.com/2025/07/28/anthropic-unveils-new-rate-limits-to-curb-claude-code-power-users/).

Authored and posted bridge [recovery alignment](https://talk.harmony.one/t/horizon-bridge-recovery/24675/31?u=theo1), aligning with RMC and partners as a temporary non-voting solution. Designed a phased approach using unused validator funds with a set claim period to end recovery within 1 year.

Led governance production from research to implementation with Yuriy, now in final testing. [Current solution](https://sx-harmony.web.app/#/explore) offers hybrid on and off chain voting similar to previous Snapshot system. Small interations for funding rate arbitrage following Vertex sunset, replaced with GMX, DEX-only strategies still delivering 50%+ APR.

---

For in-person Q3 sync.

2025-07-25 Fri: Shared governance details with Yuriy for sx-cli. Insights: sx-cli has broken functionality and not as robust as need for our governance system, discussed potential to implement SnapshotX via our own cli tool instead. 

2025-07-24 Thu: [Posted](https://talk.harmony.one/t/horizon-bridge-recovery/24675/31?u=theo1) finalized temporary recovery burn solution to talk forum, verified with partners and RMC. Note: this is not the finalized recovery completion proposal, this non-voting proposal adds clear guidelines on current processes.

2025-07-23 Wed: Team sync, contributions and suggestions for Artem’s multi-tool call addition and Rika to look through OHLCV data for more accurate Hyperliquid backtesting for funding rates, current implementation was based on estimates and averages. 

2025-07-22 Tue: Continued recovery negotiations and collaborations, sync with Matt, Quoc, and RMC, updated recovery solution with updated funds from previous validator initiative. Insight: un-used funds an be used to bring an immediate end to recovery, with a 1-year expiration for users to claim funds, must pass governance first.

2025-07-21 Mon: Review of Recovery1 updates, Quoc [retrospective](https://recoveryonefoundation.medium.com/recovery-the-story-of-harmony-resilience-55197aa19d42), and drafted temporary recovery solution that is non-voting and abides by HIP-30v, currently in review. Sync with Yuriy for sx-cli (SnapshotX) progress.

---

2025-07-20 Sun: (2.0h) Reviewing community discussions regarding recovery. 

2025-07-19 Sat: (2.0h) Dive into additional assets for strategies. (shared final results with Li, 07-21 Mon) 

2025-07-18 Fri: Out of Office

2025-07-17 Thu: Completed extensive recovery calculations, drafted initial proposal that completes recovery in a capped 1 year, shared proposal with Recovery Multisig Custodians to review. Coordination to renew [swap.country](https://swap.country/) and subgraph migration with protofire , renewal complete, still waiting on subgraph, recent contact confirms migration will be complete before July 31st deadline. 

2025-07-16 Wed: Team sync. Helping Philipp with GitHub files. Continued comparison between Hummingbot LP strategy support and our internal portfolio-manager and lp-hedger repos.

2025-07-15 Tue: 8h Hackathon in SF, meeting AI engineers. Meetup with Li, Rika, and Alaina. Insights: claude code clear winner for developers, majority using Max plan for more than $1k monthly free usage.

2025-07-14 Mon: Prep for hackathon, sync with Alaina for event and travel coordination. Reviewed Franks’s aerodrome rewards.

---

2025-07-13 Sun: (1.0h) Initial look into hummingbot btc strategies. More depth code review needed to compare functionality with our internal tooling.

2025-07-12 Sat: (3.0h) Testing new Kimi open source model, claude sonnet comparison at minimal costs, high quality tool following but API based pricing cannot compete with Claude Code monthly Max plan. Every engineer should be on the $200/m Claude plan while they still offer it, thousands in free API usage will not last forever.

2025-07-11 Fri: Sync with Yuriy for SnapshotX. CLI secure validator voting and Harmony unique validator stake weight integrations remain, awaiting prioritization, currently balancing BTC strategies with snapshotX development. 

2025-07-10 Thu: Reviewing July recovery burn delays, continued working on updated recovery plan that would be best for ecosystem, solution is non-trivial, but there may be an optimal solution. Community sentiment is more in favor of burning instead of recovery.  Shared updates with Li.

---

2025 Q2 Review (40h)

[Aerodrome LP functionality](https://github.com/harmony-one/portfolio-manager/pull/16)

Created 5 custom yield strategy repositories (initial [btc-hyperliquid-aerodrome](https://github.com/ONETheo/btc-hyperliquid-aerodrome) script, [pendle](https://github.com/ONETheo/pendle) PT yield monitoring, [shadow-lp-analyzer](https://github.com/ONETheo/shadow-lp-analyzer) for profitability analysis, [stablecoin-lp-optimizer](https://github.com/ONETheo/stablecoin-lp-optimizer) for vfat.io parameter optimizations, and [lp-optimizer-v2](https://github.com/ONETheo/lp-optimizer-v2) for liquidity backtesting). Conducted extensive aerodrome tracking with Yuriy, turning 1000+ positions into human-readable, actionable insights. Achieved consistent 50% returns across initial funding rate arbitrage. Optimal 10%+ stablecoin yields achieved through testing and on-chain verifications.

Added [Aerodrome LP functionality](https://github.com/harmony-one/portfolio-manager/pull/16) to portfolio-manager, which supports Uniswap, Hyperliquid, and Aerodrome. Coordination with recovery multisig custodian (RMC) operations and resolved June burn delay, leading to RMC pushing recovery past 32%, 2 additional recovery partner proposals ([CryptoLandDAO](https://talk.harmony.one/t/crypto-land-dao-as-additional-recovery-partner-for-the-harmony-horizon-bridge-hack/26462) & [UtilityDAO](https://talk.harmony.one/t/proposal-utilitydao-recovery-partner-for-harmony-protocol/26467)), and initialized SnapshotX development for Harmony.

Led AI-native development workflow sessions, targeting 10x efficiency gains internally with Li for Yuriy, Artem, Frank, Sun and Rika on model usage and MCP best practices. In Q3, we will extend these improvements to the protocol team. 

---

2025-07-09 Wed: Completed emergency parameter initial list, extensive and production coverage, but will cut some away for minimal build, shared with Artem for initial review. Reviewing recovery updates and team project updates, looking into ETH positions based on meeting notes. Uniform tracking also necessary. 

2025-07-08 Tue: Coordination with validators, updates on [SnapshotX integration](https://sx-harmony.web.app/#/explore). Started testing phase. Sync with Yuriy.

2025-07-07 Mon: Adding to team Q3 doc. Clarifying each team member to test individually leveraging current working implementations, but applying their own strategies to compare later on.

---

2025-07-06 Sun: (1.0h) Continued strategy review, sourcing on o4-mini-high and perplexity, pull from Harmony publications for aerodrome strategies. 

2025-07-05 Sat: (2.0h) Reviewed [lp-delta-hedge](https://github.com/adamkhakhar/lp-delta-hedge?tab=readme-ov-file) and [lp-option-hedging](https://github.com/Aureliano90/LP-Option-Hedging). Insights minimal implementations, more complex math implementations we can leverage, but no modern connections to higher volume platforms.

2025-07-04 Fri: July 4th.

2025-07-03 Thu: Adding points to q3 planning, more details on specific strategies, and answering team questions.

2025-07-02 Wed: Full team sync. Providing initial questions, parameter optimizations, and product direction for BTC strategy. 

2025-07-01 Tue: Continued review of lp-hedger, went back to Yuriy’s aerodrome [position data collection](https://github.com/harmony-one/shadow-pool-analytics/blob/main/aerodrome/export_USDC_cbBTC/positions_stats_USDC_cbBTC_all.tsv). Insights: wider range 25%+ performed best over 90 days, no rebalance, for backtesting, will be best to implement minimal rebalance aimed at weekly max.

2025-06-30 Mon: Editing Q2 video to remove default captions for Alaina, reviewed Q2 report.

---

2025-06-29 Sun: (1.0h) Filming Q2 video.

2025-06-28 Sat: (2.0h) Reviewing Aaron and Artem codebases for goal of merging work, transitioning from our previously siloed experimentation and development. Insight: missing websocket, and game theory protections implemented within Aaron’s repo can be brought on into Artem’s overall portfolio manager.

2025-06-27 Fri: Team calls and Q2 reviews. 

2025-06-26 Thu: Reviewing Stephen’s Q2 review. Coordination and breakdown sent to Artem and team.

2025-06-25 Wed: Completed [PR #16](https://github.com/harmony-one/portfolio-manager/pull/16) for portfolio manager, merged into main by Artem. Insight: adds Aerodrome support, adding to current Uniswap only, also adds flexibility of dual LP system and options.

2025-06-24 Tue: Progress on repo merge between Aaron’s production-ready code, the team’s portfolio manager, and Philipp’s strategy. Completed quarterly review and started reviewing team progress.

2025-06-23 Mon: Research into graph sunset, coordination with Protofire to migrate Lend and other necessary tooling. Sync with Alaina for progress and marketing.

---

2025-06-22 Sun: (2.0h) Initial attempt to merge Aerodrome and Hyperliquid implementations from lp-hedger, and automation from portfolio-manager, as well as implement Philipp’s strategies. 

2025-06-21 Sat: (3.0h) Reviewing Aaron’s lp-hedger, and Artem, Frank, Rika’s portfolio-manager. 

2025-06-20 Fri: Change in priorities for Yuriy with community proposal’s needing governance. SnapshotX implementation underway.

2025-06-19 Thu: Coordination with Ulad for validators operating under efficiency threshold. Additional reminder for team quarterly reviews. 

2025-06-18 Wed: Sync with Yuriy and Li for the next few days. Expectations, complete deep dive into Artem and Aaron's code and putting the Hyperliquid and Aerodrome implementations together. Completed product requirement document for our DeltaHedge minimal product, with CLI interface.

2025-06-17 Tue: Recovery multisig custodian coordination, June burn finalized. Snapshot, or open source version of snapshotX needed to proceed with proposal.

2025-06-16 Mon: Sync with Frank about claude code. Coordination with team for quarterly updates and with Gheis for further protocol onboarding as we push towards AI-native internally. Continued communications with recovery multisig custodians following [new proposal](https://talk.harmony.one/t/crypto-land-dao-as-additional-recovery-partner-for-the-harmony-horizon-bridge-hack/26462), still missing 2 signatures for June burn.

---

2025-06-15 Sun: (2.0h) Continued research, claude code is currently the clear winner, custom commands also allow for better automation and efficiency for development environment. Insight: Max plan is where the significant value add is made, claude code must be running in terminal, moving from search to coding environment remains inefficient, and custom claude code commands do not work for web based usage.

2025-06-14 Sat: (2.0h) Research into agentic coding tooling, claude code turning into clear winner with value proposition of $100-200/month Max plan allowing users to pull thousands in value, rather than paying per use for API credits. 

2025-06-13 Fri: Completed wallet sign in functionality and API updates on DeltaHedge, sync and updates with Yuriy for next week meeting. RMC (recovery multisig custodian) June burn transaction created, awaiting signatures.

2025-06-12 Thu: Continued recovery breakdown and potential ways forward. Sync with recovery multisig custodians, and Yuriy for aerodrome pools. 

2025-06-11 Wed: Sync with Alaina for Colossus announcements and marketing videos. Outreach for resolving June recovery burn.

2025-06-10 Tue: Cursor onboarding for Sun with Li tailored for eventual protocol onboarding. Insight: engineering trends follow heavy “tab” usage, most optimal for critical changes, but slowest implementation method, definitely room to 10x. Additional trend of note, external knowledge search in separate Claude or ChatGPT webpage, can all be optimized within MCP search within cursor. 

2025-06-09 Mon: Troubleshooting with Yuri for complex aerodrome rewards. Pooled data isn't clear where vAERO tokens are being distributed for accurate APR recordings. Previous top 50 positions all show initial placement of one sided pools below LP range, clarification that goal is continuous LP rather than short term discount BTC.

---

2025-06-08 Sun: (1.0h) Prep for next cursor tooling session. Context7 MCP addition (allows for continuous update context into codebase).

2025-06-07 Sat: (2.0h) Reviewed and adding pool risk management for aerodrome LP.

2025-06-06 Fri: Continued review of Yuriy’s [aerodrome position data](https://github.com/harmony-one/shadow-pool-analytics/blob/main/aerodrome/export_USDC_cbBTC/positions_stats_USDC_cbBTC_all.tsv) for USDC/cbBTC. Insight: top 50 positions show 90-115% APR, all 50 show 0 impermanent loss, meaning positions were opened below current BTC pricing, captured fees, then are now out of range.

2025-06-05 Thu: Troubleshooting [connecting wallet issues](https://github.com/ONETheo/btc-hyperliquid-aerodrome) with LP + Short/Long platform that brings both aspects of strategy in one place.

2025-06-04 Wed: Cusor deep dive and demo with Li, Frank, and Rika. Going in depth covering cursor best practices and 10x MCP (model context protocol) plugins for cursor.

2025-06-03 Tue: Reviewed Yuriy’s Aerodrome sourcing. Insights: 5% for max returns on pools that are showing 100%+ APR is too large a discrepancy, will need to unpack with Yuriy further to find the optimal width for the initial BTC LP position.

2025-06-02 Mon: Sync with Philipp. Continued with [BTC yield product](https://github.com/ONETheo/btc-hyperliquid-aerodrome), adding frontend for easy interactions for testing, allowing for opening and closing aerodrome LP and hyperliquid perpetuals.

---

2025-06-01 Sun: (2.0h) Continued testing cursor, trying claude-4 max mode. Insights: excellent for large code changes, will try to add unwanted code unless repeatedly guided, pricing unoptimal for changes made, gemini 2.5 max may be best value, but currently claude-4 base and gemini 2.5 base are more than capable for most tasks.

2025-05-31 Sat: (1.0h) Debugging [BTC strategy issues](https://github.com/ONETheo/btc-hyperliquid-aerodrome) from [Aaron’s BTC-LP](https://hackmd.io/@polymorpher/btc-lp) strategy. Insight: options funding cut too much into fees earned in pool, better to initialize with hyperliquid only positions.

2025-05-30 Fri: Finalized cursor optimization guide for engineers. Review and [initial testing](https://github.com/ONETheo/btc-hyperliquid-aerodrome) from [Aaron’s BTC-LP](https://hackmd.io/@polymorpher/btc-lp) strategy. Insight: robust strategy, but currently relies on options with expirations and sharp increase in holding costs, possibly a way to run a similar strategy with only short/long from hyper liquid.

2025-05-29 Thu: Reviewed Aerodrome, SwapX, and Shadow pools for BTC strategy. Adding best opportunities to [pre-Hummingbot parameter](https://github.com/hamood1337/CryptoFundingArb) fill. Insight: websockets are necessary for reliable pricing, current arbitrage analysis is too slow from provided repo.
 
2025-05-28 Wed: Led initial cursor onboarding and tooling sync with Li, Artem, and Yuriy. Continued iterations on Aerodrome and Hyperliquid strategies.  
2025-05-27 Tue: Sync with Li for cursor team planning and BTC yield strategy next steps. Coordination with Artem and Yuriy for cursor best practices.

2025-05-26 Mon: Federal Holiday

---

2025-05-25 Sun: (1.0h) Adding DEX only sourcing for Hummingbot. Insight: largest opportunities are coming from CEX-DEX funding rates, but sticking to DEX-only may be optimal for later productization.

2025-05-24 Sat: (2.0h) Reviewing [Hummingbot docs](https://hummingbot.org/docs/) for v1 vs v2 strategies for market making and funding rates.

2025-05-23 Fri: Sync with Yuriy to break down BTC strategy into tasks, optimizing for aerodrome liquidity providing, and hyper liquid for perpetual hedging and upside protection.

2025-05-22 Thu: Completed initial 1-pager detailing steps for complete BTC strategy, initial strategy includes [cbBTC from aerodrome](https://aerodrome.finance/deposit?token0=0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913&token1=0xcbB7C0000aB88B473b1f5aFd9ef808440eed33Bf&type=2000&chain0=8453&chain1=8453&factory=0x5e7BB104d84c7CB9B682AaC2F3d509f5F406809A), which may add additional provider risk, but highest returns for yields. 

2025-05-21 Wed: Sync with Li, going over Li and Aaron discussions on BTC strategies, suggesting combination of funding rates and hedging to produce highest possible returns against holding BTC. Sync with Rika to teach her best cursor usage, efficiency gained from cursor is a must for engineers, but some learning pains to get through.

2025-05-20 Tue: Review and aggregation of Yuriy’s platform data. Split [Ichi](https://github.com/harmony-one/shadow-pool-analytics/tree/main/export_swapx_ichi) and [shadow](https://github.com/harmony-one/shadow-pool-analytics/tree/main/vfat_shadow_stats)

2025-05-19 Mon: Successful run of hummingbot v2 funding rate arbitrage strategy. Insight: basic strategies only go so far, our edge will need to come from opportunity gathering, currently hummingbot only supports manual asset and exchange inputs, this needs to be automated for our implementation.

---

2025-05-18 Sun: (1.0h) Using o3 from openAI to find optimal strategy with risk tolerance, with every out of the box strategy Hummingbot offers. Insight: XEMM (cross-exchange market making) and funding rate arbitrage are the winners for consistent returns that are not dependent on market swings.

2025-05-17 Sat: (2.0h) Deep dive on [Hummingbot documentation](https://hummingbot.org/docs/).

2025-05-16 Fri: Added missing initial arbitrage opportunity search for tokens before the start of the funding rate arbitration rather than default hummingbot with manual token inputs. Issues with sqlite initialization.

2025-05-15 Thu: Switched to Hummingbot for direct application of funding rate strategies. Insight: connectors to new protocols like [lighter.xyz](https://lighter.xyz/) may need manual placement, first is profitability with established perpetual exchanges. Sync with Amanda for finalizing usd* testing, resolved issues with [Equilibria](https://equilibria.fi/stake) and [SwapX](https://swapx.fi/swap?tokenIn=0x0000000000000000000000000000000000000000&tokenOut=0xA04BC7140c26fc9BB1F36B1A604C7A5a88fb0E70). 

2025-05-14 Wed: Initial look into funding rate arbitrage. Coinalyze offers most API results, but no direct connectors, will need to switch to Hummingbot, websockets more optimal.

2025-05-13 Tue: Sync with Philipp. Decided on market subset for [lighter.xyz](https://lighter.xyz/), [hyper liquid](https://app.hyperliquid.xyz/trade), and [vertex](https://vertexprotocol.com/) as initial funding rate arbitrage spread. Insight: Lighter API blocked, Philipp will apply for it, strategy for funding rate arbitrage determined to be higher reward potential and less risk than Pendle inefficient bond market capitalization.

2025-05-12 Mon: Shift from Pendle. Reviewed funding rates. Sync with Alaina for best practices on cursor usage, to get more out of it than with base ChatGPT. 

---

2025-05-11 Sun: (3.0h) Continued look into yields, checked Idle, Babylon, Beefy, Aerodrome, Aave. Insight: current best strategy with long term bullish on BTC - [cbBTC<>wETH aerodrome](https://aerodrome.finance/deposit?token0=0x4200000000000000000000000000000000000006&token1=0xcbb7c0000ab88b473b1f5afd9ef808440eed33bf&type=100&chain0=8453&chain1=8453&factory=0x5e7BB104d84c7CB9B682AaC2F3d509f5F406809A) pool (fees and Aero rewards automatically harvested to cbBTC via vfat), observed apy 40%. 

2025-05-10 Sat: (1.0h) Look into Badger DAO, and Yearn for BTC yields.

2025-05-09 Fri: Troubleshooting reward spreadsheet for usd* strategies, fixing misunderstandings and calculations based on compounding protocols vs. non-compounding protocols. 

2025-05-08 Thu: Sync with Philipp for Pendle strategy and implementation. Insight: cursor is a tool for everyone, even non-coders, but mindset for using the IDE and prompting are main limitations and areas of inefficiency. Will test another approach with Alaina. 

2025-05-07 Wed: Sync with Yuriy for shift to bitcoin yields. Insight: looking into two main strategies, one that aims to be market neutral, yielding rewards and protection against price volatility, and the other is maximizing return in BTC amounts, more aggressive, will suffer more downturns, but long term potential for yield higher returns.

2025-05-06 Tue: Corrections on funding rate sourcing, fixed “e” formatting issues. Syncs with Li, Amanda, Alaina, and Phillip for alignment on current yield strategies and areas of production. Initialized strategy spreadsheet for Amanda. Iterated on allocation %. Insight: with recent price increase of PT aUSDC and PT USDC (Silo-20) we could have locked in a 12% APY instantly if we had a PT USDC (Silo-20) fixed rate open. Adjusted allocations in spreadsheet based on current market rates.

2025-05-05 Mon: Completed iteration on Li’s pendle for [PT-USDC (Silo-20)](https://github.com/ONETheo/pendle). Insight: product that sources all PT variations and gives highest divergence can be useful and profitable if we want to push in that direction. 

---

2025-05-04 Sun: (1.0h) Contuniued look into Pendle yields. Insights: even though PT yield may drop from a PT asset, the underlying PT appreciates in value, allowing the holder to capitalize on difference immediately rather than wait for expiration.

2025-05-03 Sat: (2.0h) Looking further into Pendle yields.

2025-05-02 Fri: Testing funding rates from Artem’s message, shared relevant data with Phillip for Sonic funding rates since Jan 30 2025. Made copy edits and completed a read through for the April newsletter with Alaina.

2025-05-01 Thu: Changed allocation % for usd* strategy. Insights: Pendle ausdc and silo-20 usdc offer similar risk profiles, but 3%+ apr is too much of a difference to spend allocation adversely.

2025-04-30 Wed: Iterations on [notebook for Shadow pools](https://github.com/ONETheo/shadow-lp-analyzer), pulling APR usd* specific information., Completed initial allocation % for usd* strategy, optimizing for highest return with lowest smart contract and rebalancing losses.

2025-04-29 Tue: Working on funding rates for Sonic. Most funding rate api’s are restricted. Will try [coinalyze](https://coinalyze.net/).

2025-04-28 Mon: Completed initial [Jupyter-like notebook for Shadow pools](https://github.com/ONETheo/shadow-lp-analyzer) based on Yuriy’s data collection.

---

2025-04-27 Sun: (2.0h) Reviewed marketing copy for Colossus, made corrections and sent edits to Alaina and Colossus team. 

2025-04-26 Sat: (1.0h) Collected April team updates to iterate on monthly newsletter title. Sync with Alaina for newsletter.

2025-04-25 Fri: Continued sourcing aggregated stable coin bond markets. Answered [Euler](https://app.euler.finance/strategies?network=sonic) and Pendle due diligence questions. Insight: usdc.e supply on Euler without liquidation risks pairs well with Pendle expiring bonds. Necessary step is finding vePENDLE value to obtain maximum boosted directly on Pendle to see if locking is worth it. Strategy without locking, which allows for much more favorable liquid assets, is Equilibria. 

2025-04-24 Thu: Sourcing Penpie and Equilibria fee distributions to compare with native [Pendle](https://app.pendle.finance/trade/pools?chains=sonic). Insights: [Equilibria](https://equilibria.fi/stake) offers highest returns without locking vePENDLE for the end user. (12.67% for Equilibria vs 13.69%) values updated every 7 days.

2025-04-23 Wed: For Sonic [Pendle pools](https://equilibria.fi/stake), 9.3% Sonic rewards are the main driver for aUSDC liquidity providing yields. Insight: important for us to keep in mind how Sonic will be released (June 2025: 25% immediately claimable, 75% vested over 270 days via NFT positions.)

2025-04-22 Tue: Completed custom Dune analytics queries to verify [Penpie metrics](https://www.pendle.magpiexyz.io/stake/0x88C4F34B86907b7221c0061f7a0bBeC9391Ea727). TVL metrics and time to achieve current TVL. Found [anomalies for two markets](https://dune.com/queries/5022329/8302746) which increased TVL by more than 100,000% and 7000% in August of 2024 and 2025. Update: these came from PT-sfPEPE-26SEP2024 and PT-ctsUSDe-10APR2025 respectively.

2025-04-21 Mon: Sync with Yuriy covering additional usd* tracking pairs and [SnapshotX](https://github.com/snapshot-labs?q=sx&type=all&language=&sort=) as primary open source governance tooling. 

---

2025-04-20 Sun: (2.0h) Continued looking into tracking market states. Putting together volatility correlation mapped against key events.

2025-04-19 Sat: (1.0h) Finalizing usd* best options for highest returns paired with lowest risks, Pendle fixed rates provides high returns with balance between risks, Euler multiplying offers higher returns, but risk of liquidation of entire position is too high for our liquidity amounts. Looking into market trends, with more movements into crypto, stable coin approach should be tied to current market state.

2025-04-18 Fri: Continued search into open source governance, [SnapshotX](https://github.com/snapshot-labs?q=sx&type=all&language=&sort=) provides best option that follows our previous governance tooling. Sync with Yuriy to expand data collection to all usd* pools to find the most profitable usd* pool from the last 90 days. Insight: only 3 usd* pools on Shadow have TVL higher than $1m, needs to be kept in mind for allocation dilution. 

2025-04-17 Thu: Completed Vfat [usd* liquidity refactor](https://github.com/ONETheo/stablecoin-lp-optimizer) complete to prioritize stable pairs, with pair volatility tracked over 90 days for tick placement. Insight: largest observed base rate was only 1.89% APR, significantly lower than yield shown on shadow. Shadow allocates xshadow earned through fees from other pools to funnel back into stable pairs. For yields on pairs, weekly tracking of rewards is needed. For strategy, this ties stable yield to volatile governance, leading to uncertainties. [Euler](https://app.euler.finance/positions/0xF6E2ddf7a149C171E591C8d58449e371E6dc7570/0x196F3C7443E940911EE2Bb88e019Fd71400349D9?network=sonic) markets and [Pendle](https://app.pendle.finance/trade/markets?chains=sonic) fixed rates offer higher and more consistent yields.

2025-04-16 Wed: Bridge issues resolved, looking into open source governance alternatives. Reviewed [Aragon OSx](https://www.aragon.org/osx), [OpenZeppelin](https://docs.openzeppelin.com/contracts/4.x/governance) and [SnapshotX](https://github.com/snapshot-labs?q=sx&type=all&language=&sort=) as open source alternatives.

2025-04-15 Tue: Coordination for resolving bridge and ledger issues. Refactoring liquidity optimizations for strictly usd*.

2025-04-14 Mon: Sync with Yuriy. Reviewed Aaron’s four step options play on panoptic against traditional options market. Insight: Panoptic’s streamia (streaming premium rather than fixed) and volatility are keys to the success of this strategy, which may show more stable and guaranteed gains than our original usd* plan.

---

2025-04-13 Sun: (1.0h) Further testing. Base data for volatility and pairs are there, but a path of improvement is in the ability to add any pair and find the best path of rewards throughout the 90 day backtest.

2025-04-12 Sat: (2.0h) Testing [vfat optimization tool](https://github.com/ONETheo/lp-optimizer-v2). Insight: pairing backtesting with real time volatility indexing may prove more profitable, resulting in rebalance spending, but prior to position being out of range. Note: would need a different tool, as vfat does not support this type of rebalancing.

2025-04-11 Fri: Completed [liquidity optimization tool](https://github.com/ONETheo/lp-optimizer-v2) for Aerodrome and Shadow Pools. Insight: allows for quick backtesting and pool performance calculations via subgraphs. Sync with Yuriy for data priority and collecting wallet data.

2025-04-10 Thu: Troubleshooting updates to LP optimizer to include subgraph and volatile pool pairings, tracking best performing [vfat.io](https://vfat.io) parameters over past 90 days.

2025-04-09 Wed: Sync with Yuriy for merging usd* historical data with vfat optimizer to calculate best performing strategies. Insight: risk from new sonic usd pegged assets remains too high, earning stable yields from holding longer term proven usd assets while shorting newer usd assets may be the best strategy, Aaron looking into this currently.

2025-04-08 Tue: Completed optimization backtesting framework for USD* pool parameters. The [repo](https://github.com/ONETheo/liquidity-pool-optimizer) now provides comprehensive simulation capabilities for liquidity provisioning strategies, including width, buffer, and cutoff parameter optimization.

2025-04-07 Mon: Alignment for Q2 moving forward and Q1 review. Main push for yield earnings, prioritizing tooling for optimized liquidity provisions. Using coingecko api to track 100 daily, 100 hourly prices for historical volatility necessary for realtime volatility estimations.

---

2025-04-06 Sun: (2.0h) Further research on [vfat.io](https://vfat.io). Insight: fees, slippage, and out of bounds rebalancing make larger pool width more profitable. 

2025-04-05 Sat: (1.0h) Planning for real-time volatility script.
 2025-04-04 Fri: Starting deeper focus on [vfat.io](https://vfat.io) for rebalancing. Specifically looking into parameters for USD pools ([USDC/scUSDC](https://vfat.io/farm?chainId=146&farmAddress=0xf8440c989c72751c3a36419e61b6f62dfeb7630e&poolId=0) and [USDC/USDT](https://vfat.io/farm?chainId=146&farmAddress=0xf3ac5aef4116abfd322fdc683420a4fc4b7f2d73&poolId=0) for optimal returns. 

2025-04-03 Thu: Review of correlated and non-correlated assets for yield earning. Insight: correlated pairs offer a safe alternative for higher yields compared to USD pairs. Looking into DeBank and Sushi sunsetting Harmony. Finalized [mock for a potential 1earn product](https://1earn.vercel.app/) bringing simple strategies to Harmony.

2025-04-02 Wed: Sync with Li covering BTC yields and breakdown of leverage looping within Euler. Troubleshooting Claude API for Harmony1Bot.

2025-04-01 Tue: Sync with Philipp for portfolio manager and DeFi products. Troubleshooting Q1 review copy with Alaina. Answered community questions regarding Soph’s farewell.

---

2025 Q1 Review (51h)

I enhanced core DeFi infrastructure by implementing [Lend](https://lend.harmony.one/) contract updates (closefactormantissa, liquidationincentivemantissa) enabling liquidations and improving stability againts bad debt. I developed the Yield Boost frontend and [added details](https://github.com/harmony-one/yield-enhancer/compare/main...ONETheo:yield-enhancer-1:patch-2) (targeting 15%+ stablecoin APY), [contributed code](https://github.com/harmony-one/pump.fun.client/pull/17) and user-driven strategy to Pump.ONE's dual-launch system, and designed the initial [universal bridge UI](https://github.com/harmony-one/usdc-converter/pull/1) to eliminate USDC fragmentation into unified USDC.e.

I led the strategic 0x prioritization initiative to resolve our top user onboarding friction point via seamless address compatibility. I researched Loss-Versus-Rebalancing (LVR) for optimized liquidity strategies and built custom SQL queries for accurate on-chain TVL and fee tracking. I resolved CoinMarketCap supply data issues bringing our untracked reporting from 2.65B to 0. Sonic ecosystem analysis led to critical feature potential comparing industry leading rebalancing tools like [vfat.io](https://vfat.io), tracking revealed 50%+ of APY values for various pools come from artificial incentivized yields, confirming a market opportunity for simplified DeFi.

Efforts also boosted Harmony's market presence. Securing the ['Made in USA'](https://www.coingecko.com/en/categories/made-in-usa) category listing on CoinGecko and [perpetual futures for ONE](https://pro.kraken.com/app/trade/futures-one-usd-perp) on Kraken, further increasing market access.

---

2025-03-31 Mon: Iterating on simple DeFi product offering. Insight: [defi.app](https://defi.app) includes all DeFi aspects people want, most still coming soon and unreleased, but this direct offering of all features scares users away. Goal should be to abstract difficulties from users, only showing yields based on their risk tolerance and optimizing their positions accordingly, no manual selection unless configured in settings.

---

2025-03-30 Sun: (2.0h) Finalizing Q1 review, and main Q1 draft. Added [potential intro](https://www.notion.so/harmonyone/Q1-DeFi-Intro-1c6a38fc048780639bf2f0c22f15fda1) following original deeper DeFi focus.

2025-03-29 Sat: (1.0h) Further testing of [vfat.io](https://vfat.io). Insight: ignoring fees and slippage lost during rebalancing, auto rebalance only happening outside of bounds is a critical issue that we can improve upon allowing users to rebalance before their position leaves their desired range.

2025-03-28 Fri: Draft for Q1 review and deep dive into Euler Finance contracts. Insights: main concern stems from 2023 exploit, however new modular contract approach with proxy logic allows for smoother crisis aversion.

2025-03-27 Thu: Followed up with 0x prioritizations. Update: potential continuation following necessary due diligence. Reviewed usd* pools and strategies to optimize for high yields while reducing platform risk due to new products or higher leverage. Iterated panoptic options UI for usability. Insight: up/down with user testing is much easier, could combine with call to action button showing long or short but main interaction remains up/down.

2025-03-26 Wed: Sync with Li and Rika. Continued Sonic testing moving liquidity positions, tested Magpie additional Pendle pool deposits and vicuna finance lending. Insights: an automated looping aggregator would be a helpful product when lending and borrowing rates are optimal.

2025-03-25 Tue: Changed Q1 video to unscripted version, slightly longer, but includes more context into overall Q1 updates. Set up closefactormantissa transaction for Lend. 

2025-03-24 Mon: Shared simple product ideas with team for DeFi use case and security. Recorded Q1 update.

---

2025-03-23 Sun: (2.0h) Looking into Lend contracts following liquidityincentivemantissa update, research into closefactormantissa.

2025-03-22 Sat: (4.0h) Continued testing [vfat.io](https://vfat.io). Insight: vfat product offering is missing a key feature that would allow auto rebalance prior to price moving outside of liquidity bounds. Adding this feature on a larger liquidity spread would lead to more “time in the money” for liquidity providers, earning more consistent yield.

2025-03-21 Fri: Extensive review and estimates for portfolio strategy. Insights: clear distinction between aggressive strategies in terms of % allocations, decision needs to be made for consistent rewards vs higher risk potential rewards.

2025-03-20 Thu: Troubleshooting with Frank. Sync with Alaina for Colossus co-marketing for ONE integrations on Firebrick, and Amanda.

2025-03-19 Wed: Meeting with Soph for Lend contract changes. Further testing of Euler and Shadow pools. Insights: fixed yields work best for medium to long term, but with active management pools acquire the highest APY with limited risk (for certain pools). Completed clarification on CoinMarketCap discrepancies, continued push for 0x prioritization.

2025-03-18 Tue: Group call with Frank and Rika to prioritize focus on stable pools and shadow specific information not available on DefiLlama. Submitted ticket for Paladin rewards issue.

2025-03-17 Mon: Set up meeting times for Frank and Rika sync tomorrow. Reviewed AthleteFi marketing post. Deep dive into USD pairings for lending, pools, and vaults to earn stable yields as a base strategy. Insights: Pendle fixed rates offers lower guaranteed yields, with x33 pools tied to USD with added incentives looks a strong yielding strategy in order to take advantage of Shadow platform. 

---

2025-03-16 Sun: (2.0h) Looking into [Silo sonic markets](https://v2.silo.finance/). Insights: Lending on yields remains beneficial for hedging on more aggressive strategies, or as a short for underlying assets, otherwise best to stay with pools and emissions.

2025-03-15 Sat: (1.0h) Reviewed Yuriy’s [Q1 update](https://github.com/harmony-one/h/blob/main/progress/yuriy-menkov.md).

2025-03-13 Thu: Direct coordination for 0x support and extensive troubleshooting unlocked values for [CoinMarketCap](https://coinmarketcap.com/currencies/harmony/). Sync with Philipp for sourcing Shadow emissions outside of Shadow platform, and general vault and rebalancing findings.

2025-03-12 Wed: Coordination with team for Q1 Reviews. Continued Shadow verifications, currently trying to add emissions to Dune dashboard. Insights: need to sync with philipp on how to best source this information, as xShadow is emitted but not available for extraction, unless 50% penalty. Total supply and vesting information is available, but precise pair emissions are needed to verify values.

2025-03-11 Tue: Panoptic testing, narrowing down strategies, Reviewed a16z [Arbitrage Extractable Value](https://a16zcrypto.com/posts/videos/arbitrage-extractable-value/). Insight: this combines the notions from Loss-Versus-Rebalancing (LVR) from [a16z](https://a16zcrypto.com/posts/article/lvr-quantifying-the-cost-of-providing-liquidity-to-automated-market-makers/), providing liquidity in a way that optimizes for limiting loss-versus-rebalancing gives the arbitrage extractable value to the original liquidity provider rather than the arbitrage user.

2025-03-10 Mon: Attended [Base Roll-Up](https://lu.ma/37ykg387) & AI Summit in San Francisco with team. Insights: lots of the same conversations regarding privacy, AI, and DeFi, as well as Layer 2 conversations. Non-crypto native conversations gave insights into narrowing down user personas for upcoming products.

---

2025-03-09 Sun: (2.0h) Discussions on bridging the gap between DeFi power users and non-native. Platforms like Panoptic offer ideal strategies for markets, but offer too much customization options for greater adoption.

2025-03-08 Sat: (3.0h) Continuing search for the optimal automated LP platform or product.

2025-03-07 Fri: Review and deep dive on Loss-Versus-Rebalancing (LVR) from [a16z](https://a16zcrypto.com/posts/article/lvr-quantifying-the-cost-of-providing-liquidity-to-automated-market-makers/), accompanying [arxiv paper](https://arxiv.org/abs/2208.06046). Insights: calculations and optimizations are straightforward, benefit of a standard similar to Black-Scholes for traditional options, next steps can be building custom tracking and implementation for optimized liquidity providing. Found an [LVR minimization repo](https://github.com/aloantony/LVR-Minimization-Tool-for-Uniswap-v4), but limited, building our own and having the right differentiators looks to be the best path.

2025-03-06 Thu: Auto-rebalancing strategy set up on [vfat.io](https://vfat.io), testing x33/shadow, deep dive on ideal strategies for liquidity providers. Community Tx DAO signers able to queue transaction for AthleteFi. 

2025-03-05 Wed: Fixed USD value issues, added accurate onchain fees, volume, TVL, and APR to [Dune queries](https://dune.com/theo1/shadow-swapx). Insight: separated raw logic with USD values for calculations, with TVL and APR for 24hr and 7d, we can identify pools with consistent performance vs. recent activity spikes.

2025-03-04 Tue: Testing [vfat.io](https://vfat.io) and [writing queries](https://dune.com/theo1/shadow-swapx) for Dune analytics. Insights: current dashboards are pulling from DefiLlama API, created custom sql to verify onchain data. Found for pairs with “shadow” data is calculated only on one side, reducing accuracy. Currently able to pull legacy and concentrated liquidity positions, troubleshooting getting human readable dollar amounts for fees and rewards.

2025-03-03 Mon: Sync with Li and Rika, established prioritizations on [Dune analytics](https://dune.com/theo1/shadow-swapx) and upcoming Bridge updates. Insights: Yield Enhancer contracts are complete, universal bridge and UX changes pending for launch. Dune issue to work around: SwapX volumes from 0xkhmerlab unavailable.

---

2025-03-02 Sun: (2.0h) Product strategy based on using Aerodrome (established) and Shadow (new and improved). Insights: Base going for both average user and DeFi power users (50/50), Shadow 100% on DeFi power users, this leaves a gap for 100% on average user, while giving strong yields.

2025-03-01 Sat: (2.0h) Using Shadow and navigation with x33. Insights: abstraction for yield automation makes minting x33 win-win for holders and platform.

2025-02-28 Fri: Continued deep dive into Aerodrome vs. Shadow. Insights: current market dominance favors Aero, but 100% DeFi focus will help in the long run. Submitted and sync with Soph for Lend contract updates.

2025-02-27 Thu: Launch of [Pump.one](https://pump.one). Sync with community on current bridge issues. Continued metrics collecting and testing for Shadow.

2025-02-26 Wed: Completed and submitted [pull request](https://github.com/harmony-one/pump.fun.client/pull/17) for [Pump.one](https://pump.one) rules page. Continued Sonic ecosystem testing. Inisghts: beyond complexity of accessing yields, what works well is everything is connected, each action on Sonic leads to points, Veda vaults compound into Rings, Rings assets compound into more points on Magpie. Reviewed opencover.

2025-02-25 Tue: Sync with Amanda for DEX clarifications and Li for a product deep dive into what sets Harmony apart moving forward. Testing Sonic yields for several applications, [Shadow](https://www.shadow.so/), Rings, SwapX, MagPie, Veda. Insights: all yield pools (most are underdeveloped/early) revolve around incentives and points. I.e. artificial yields. There is a clear gap for simple, abstracted simple one-click DeFi. 

2025-02-24 Mon: Sync with Alaina for marketing and deep dive with Philipp into universal bridge and upcoming product launches. Insight: [Pump.one](https://pump.one) reaching code completion, all marketing materials are go for launch, shifting focus on daily use cross-chain portfolio product.

---

2025-02-23 Sun: (2.0h) Coordination with Alaina for [Pump.one](https://pump.one) launch and following a slightly modified version of [marketing plan](https://www.notion.so/harmonyone/Harmony-2025-Product-Marketing-19ea38fc0487800aa743fdca04c7fd59).

2025-02-22 Sat: (2.0h) Troubleshooting allocation from Community Tx DAO to AthleteFi. Insight: gnosis safe unable to submit transaction, extending issue to Protofire team.

2025-02-21 Fri: [Infinex](https://infinex.xyz) group created with their developer relations to discuss Harmony support. Insight: leveraging a product on top of Infinex may be best for end user satisfaction. No need to switch wallets and keep track of chains.

2025-02-20 Thu: Review of Aeordrome and Drift for further look into cross-chain yield aggregation. Insight: incentives and ties to longer lockups allow for more sustainable yields in volatile markets, incentives aggregator for users may be useful in itself. Scheduled [Holyheld](https://holyheld.com/) integrations call.

2025-02-19 Wed: Outreach for Moralis for potential NFT and chain API. Apple Developer account coordination.

2025-02-18 Tue: Completed [extensive marketing plan](https://www.notion.so/harmonyone/Harmony-2025-Product-Marketing-19ea38fc0487800aa743fdca04c7fd59) for upcoming 5 product launches and ecosystem upgrades and sync with Alaina for product marketing schedule. Submitted [PR](https://github.com/harmony-one/yield-enhancer/compare/main...ONETheo:yield-enhancer-1:patch-2) for Yield Boost Readme.

2025-02-17 Mon: Federal Holiday

---

2025-02-16 Sun: (2.0h) Continued working with agents, using mistral with function calling. Insight: post-action observability is the difference between a quality agent and a lucky LLM.

2025-02-15 Sat: (3.0h) Dive into daily & weekly DeFi uses. Insights: Pull for simple, consistent yield rather than aggressive casino pump and dumps.

2025-02-14 Fri: Continued outreach with Infinex. Research and sync with Alaina for [exchange.one](https://exchange.one).

2025-02-13 Thu: Updates on quote tweets from main account. Product sync with Artem for [Pump.one](https://pump.one) competitions.

2025-02-12 Wed: Group made with Holyheld, continued Infinex conversations. Catch up and sync with Alaina on products and marketing.

2025-02-11 Tue: Testing Hey Anon platform. Insight: still minor automation, not very helpful short term, long term will be how everyone interacts with DeFi, abstracted via agents. Initial planning for bridge revamp with Layerzero.

2025-02-10 Mon: Outreach for Holyheld and Infinex, coordination with Philipp to reach out to all from Delphi Digital year ahead for 2025. Insight: [infinex](https://infinex.xyz) as an abstraction layer, with focus on product seems most promising.

---

2025-02-09 Sun: (2.0h) Continued exploration of Eliza OS integration. Insight: key will be data protection and DeFi guaranteed navigation, there are automation benefits but they remain hard for users to find and access.

2025-02-08 Sat: (3.0h) User behavior trends in multi-chain ecosystems for both manual and automated DeFi processes. Insights: flow follows liquidity, chatGPT-like interaction may be best for end user, navigation via natural language instead of complicated current DeFi navigation.

2025-02-07 Fri: Research into [Monad](https://www.monad.xyz/) launch with testnet announced for February. Insight: similar speed and reduced gas fees, but clear messaging as “if Solana was EVM” matching suggested narratives, user experience and application will continue to be the differentiators.

2025-02-06 Thu: Network outreach for potential additional listing. Continued looking into multi-chain product, stake ONE to use. Reviewed [Pump.one](https://pump.one) and Yield Boost. Insight: simplicity is key, allowing ease of access to create new tokens and motivation to interact with platform.

2025-02-05 Wed: Dive into DEX revenue against bot revenue, as well as path from Uniswap v3 to v4 for Harmony.

2025-02-04 Tue: Team sync for [Pump.one](https://pump.one) and Yield Boost launch. Coordinating with Alaina for marketing.

2025-02-03 Mon: Sync with Philipp for DeFi. Insight: items still needed, liquidity (1sDAI/USDC.e, boostDAI/1sDAI), reward contract automation, boostDAI on LEND, USDC.e Liquidity on LEND

---

2025-02-02 Sun: (2.0h) Using perplexity with Deepseek R1 for reasoning search. Insights: trust remains conversion point between agent completing task vs frontend completing task via manual user interactions. Potential model: stake ONE for use, small platform fee from any token transaction paid in any token used.

2025-02-01 Sat: (2.0h) Reviewing Eliza OS. Insight: manual DeFi interactions will continue to trend to 0 by end of 2025.

2025-01-31 Fri: Finalizing plan for Harmony Gitbook [flag collection](https://www.notion.so/harmonyone/Harmony-GitBook-Flags-189a38fc048780089f07e8660e9a6848), for easier onboarding and AI agent onboarding.

2025-01-30 Thu: Community Tx DAO vote finalized, AthleteFi has completed product and marketing material, multisig vote will be placed tomorrow. Frontend cleanup with Artem for tokens launched beyond guidelines.

2025-01-29 Wed: [Pump.one](https://pump.one) team coordination, and community sync. Insight: users are expecting parity in functionality with [pump.fun](https://pump.fun), solution sync with Yuriy for implementing competition post launch. 

2025-01-28 Tue: Reviewed forum flagged posts. Created notion for Harmony Gitbook [flag collection](https://www.notion.so/harmonyone/Harmony-GitBook-Flags-189a38fc048780089f07e8660e9a6848), sync with Amanda for implementation. Insight: AI runs on data, agents (and users) need quality Harmony data to navigate efficiently.

2025-01-27 Mon: Harmony listed as official [Made in USA](https://www.coingecko.com/en/categories/made-in-usa) category on Coingecko. Next will be Coinmarketcap.

---

2025-01-26 Sun: Continued Deepseek R1 applications for Harmony, code building, dapp building, etc. Insight: safeguards and checks will be important for no-code building in web3.

2025-01-25 Sat: Experiment with Deepseek R1. Insights: reasoning is the main difference, now able to see how the models are interpreting prompts. 

2025-01-24 Fri: UI/UX review for the initial [universal bridge](https://github.com/harmony-one/usdc-converter/pull/1), shared with Artem and Yuriy. Deep dive with Li and team.

2025-01-23 Thu: Submitted pull request for [universal bridge](https://github.com/harmony-one/usdc-converter/pull/1) for usdc.

2025-01-23 Thu: Submitted pull request for [universal bridge](https://github.com/harmony-one/usdc-converter/pull/1) for usdc.

2025-01-22 Wed: Completed first draft for universal bridge UI, sync with Philipp for lecture content. Continued planning for scheduled sync with Alaina tomorrow.

2025-01-21 Tue: Team sync for bridge, yield boost, and universal bridge prioritization. Added questions for Philipp. 

2025-01-20 Mon: Federal holiday

---

2025-01-19 Sun: (3.0h) Deep dive into [AGI formal math](https://i.country) and [Delphi article](https://members.delphidigital.io/reports/the-year-ahead-for-ai-depin-2025#2025-predictions--living-the-inflection-0399https://members.delphidigital.io/reports/the-year-ahead-for-ai-depin-2025#2025-predictions--living-the-inflection-0399) on "The Year Ahead for AI + DePIN 2025".

2025-01-18 Sat: (2.0h) Refined marketing strategy for boostDAI.

2025-01-17 Fri: Docs walkthrough with Alaina and marketing planning. 

2025-01-16 Thu: [Frontend changes](https://github.com/harmony-one/yield-enhancer/pull/2) to Yield Enhancer. Community TX DAO coordination.

2025-01-15 Wed: Researched JSON and xml [AI-optimization](https://www.restack.io/p/ai-data-management-xml-vs-json-answer) for documents. Further conversations with community tx dao for AthleteFi.

2025-01-14 Tue: Reworking boostDAI logo to align with copyright, added marketing copy. 

2025-01-13 Mon: Designed boostDAI logo, sync with Alaina for marketing, and further Yield Enhancer testing. Coordinating with Soph for 0x initiative post yield enhancer launch.

---

2025-01-12 Sun: (2.0h) Spoke with community members. Insights: most in favor of using the [harmony community](https://harmonycommunity.one) site as the main site. Insights: rather than 1-1 switch, best would be to take what cannot be left out and bring it to community page.

2025-01-11 Sat: (2.0h) Market research for best use of exchange.one. Insights: Mobile friendly, intent based design, all in ONE place simple DeFi, remove approvals if possible in a way that is similar to abstract chain.

2025-01-10 Fri: Reviewed listings option and protofire PR for lend. Insight: build failing using deprecated actions.

2025-01-09 Thu: Coordination with Community Transaction DAO and CryptoLandDAO outreach, finalization needed for AthleteFi support.

2025-01-08 Wed: 0x prioritization organization and preparation. Main priority is exchange support for seamless onboarding into Harmony, to optimize for metamask default support for 0x and Harmony EVM compatibility.

2025-01-07 Tue: Sync with Li, Artem, and Yuriy about [Pump.one](https://pump.one) and Yield Enhancer. Suggestions for optional [Pump.one](https://pump.one) “opt-in” functionality: allowing users to have a base version of [Pump.fun](https://pump.fun) as well as be able to opt-in for the [Pump.one](https://pump.one) additional features.

2025-01-06 Mon: Yield Enhancer review and testing. Additional APY still set to launch as industry leading on stablecoins.

---

2025-01-05 Sun: (1.0h) Shared document with Soph again. Insight: 0x work is mostly non-technical, but needs a dedicated push.

2025-01-04 Sat: (2.0h) Reviewed [0x prioritization document](https://harmonyone.notion.site/Prioritizing-0x-Addresses-in-the-Harmony-Ecosystem-8fad1b2a6c054619aff41b9d8f771081).

2025-01-03 Fri: Community call. Prioritization insights from community: “0x” wallet address top priority for seamless entrance to Harmony, and more community representation in 2025 plan.

2025-01-02 Thu: Sync with [Flipguard](https://www.flipguard.xyz/features), discord wallet and bot.

2025-01-01 Wed: New Year’s

2024-12-31 Tue: Read Bitcoin Strategic Reserve documentation, joined Harmony 2025 group.

2024-12-30 Mon: Coordination with Artem for Athletefi rebrand on staking dashboard.

---

2024 Q4 Review:

I architected Harmony's DeFi suite expansion, focusing on accessibility and higher yields, delivering key products to new heights. Swap saw a 300% increase in TVL, and a 4,470% surge in trading volume. Lend followed a similar expansion, reaching a 250% increase in supply.

I led the Yield Enhancer development from strategy to implementation, building the [frontend](https://github.com/ONETheo/yield-enhancer) in typescript and coordinating ERC-4626 vault deployment. The first phase is live with 1sDAI, delivering 12.5% APY through Sky Protocol's yield-bearing stablecoin available within the Harmony ecosystem. I also pioneered [Pump.ONE](https://pump.one)'s innovative concentrated liquidity model with Stephen, optimizing for user collaboration over liquidity fragmentation. I drove the adoption of SimpleSwap, reaching 12.5% conversion rate and enabling seamless ONE acquisition across our ecosystem.

I also strengthened Harmony's market presence by securing Swap listings on DefiLlama and DexScreener, leading our recovery multisig custodian election, and driving community engagement through [ONE Show](https://x.com/harmonyprotocol/status/1865200491476717576) presentations that reached 854 concurrent listeners and generated over 20k post views.

---

2025 Goals: Simple DeFi, "One-Click Yield", Perpetual Innovation

In 2025, my mission is to establish Harmony as the primary destination for DeFi by delivering innovative products that combine accessibility, cutting-edge AI, and simplified financial tools. These goals will drive ecosystem growth and position Harmony as a leader in decentralized finance.

1. One-Click Yield: Simplifying DeFi Strategies  

Launch a flagship one-click yield product that simplifies complex yield farming strategies for stablecoins. This solution will provide industry-leading returns while offering users an effortless and intuitive experience, making Harmony the most user-friendly DeFi platform.

2. Driving Liquidity and Finalizing DeFi Suite

Driving toward $100M in Total Value Locked by leveraging innovative yield strategies and launching the final primitive in Harmony’s DeFi suite: a perpetual exchange. Following swap and lend, this exchange will introduce leverage to the ecosystem, expanding financial offerings and driving adoption. In parallel, I aim to work with the community to deliver more clarity surrounding the proposed community-driven ecosystem treasury, ensuring long-term funding for growth and development.

3. AI-Driven Experiences with Eliza OS

Integrate the [ai16z Eliza OS](https://elizaos.ai/) framework into Harmony1Bot to deliver an AI-powered DeFi experience. By combining conversational interfaces with real-time optimizations, we will simplify user interactions across bridge, swap, lend, and the perpetual exchange, setting a new benchmark for accessibility in decentralized finance.

These goals are designed to empower users, deepen liquidity, and expand Harmony’s ecosystem with precision and purpose. By focusing on simplicity, innovation, and execution, we will ensure Harmony not only remains competitive but becomes the definitive platform for decentralized finance in 2025 and beyond.

---

2024-12-29 Sun: (2.0h) Dive into [Robinhood ux](https://itexus.com/robinhood-ui-secrets-how-to-design-a-sky-rocket-trading-app/) for simplifying DeFi.

2024-12-28 Sat: (2.0h) Dive into updates from [Eliza Repo] (https://github.com/elizaOS/eliza)

2024-12-26 Thu - 12-27 Fri: Paid Time Off

2024-12-25 Wed: Christmas

2024-12-23 Mon - 12-24 Tue: Paid Time Off

2024-12-22 Sun: (2.0h) Promoting Harmony 2025 with others, collecting feedback from non-crypto communities.

2024-12-21 Sat: (1.0h) Review of Harmony 2025

2024-12-20 Fri: Completed Harmony 2025 [draft](https://www.notion.so/harmonyone/Harmony-2025-AI-Agents-DeFi-on-Exchange-one-1-Second-Finality-161a38fc0487806d8592cd4e511dc5c6).

2024-12-19 Thu: Gathering each team member’s 2025, pushed [draft](https://www.notion.so/harmonyone/Harmony-2025-AI-Agents-DeFi-on-Exchange-one-1-Second-Finality-161a38fc0487806d8592cd4e511dc5c6).

2024-12-18 Wed: Team review, yield enhancer parameters, progress on 2025 team blog.

2024-12-17 Tue: Sync with Li and Yuriy for 2025, yield enhancer, and 2024 review. Recorded 2025 goals video.

2024-12-16 Mon: Q4 review, and sync with Alaina for yield enhancer marketing.

--- 

2024-12-15 Sun: (2.0h) Continued search into [Eliza AI](https://elizaos.ai/) initiatives and potential integrations with Harmony.

2024-12-14 Sat: (2.0h) Community questions and sharing details on yield enhancer.

2024-12-13 Fri: Created base frontend for [yield enhancer](https://github.com/ONETheo/yield-enhancer), shared with Artem.

2024-12-12 Thu: Recovery overview, yield enhancer prioritization, sync with a few community members and validators on alternatives to accelerate recovery.

2024-12-11 Wed: Met with Token Terminal, extended integration information internally. Reviewed PumpONE documentation and shared initial timeframe and liquidity threshold.

2024-12-10 Tue: Perpetual exchange sync, initial planning for reducing bridge asset fragmentation. Token Terminal meeting scheduled for tomorrow. (This will concentrate liquidity and allow users to create single pools for their stablecoin pairings rather than opening a pool per chain.)

2024-12-09 Mon: Sync with Matt Barrett on AthleteFi. Selected 5 community members from volunteer list for PumpONE testing. Added completed tasks on [Yield Enhancer](https://www.notion.so/harmonyone/DeFi-Strategy-13fa38fc0487807a8afaefea24c1e1d0) doc.

---

2024-12-08 Sun: (3.0h) [ONE Show](https://x.com/Tenacious_DeFi/status/1865773161746215084) covering yield enhancer, Harmony 2025, bitcoin strategic reserve, and recovery.

2024-12-07 Sat: (1.0h) ONE Show prep with Tenacious and question document.

2024-12-06 Fri: Liquidity planning with Amanda and confirmation with Li for Swap, Lend, and Yield Enhancer liquidity.

2024-12-05 Thu:  Sync in with Yuriy, [erc-4626](https://github.com/harmony-one/erc-4626) deployed on Harmony allowing vault based staking crucial for yield enhancer.

2024-12-04 Wed: Continued discussions on simple DeFi. Team Holiday get-together.

2024-12-03 Tue: Sync with Philipp for Q4 review and 2025 planning.

2024-12-02 Mon: Continued discussions with Chainspect, marketing call scheduled for tomorrow with larger X group. Community outreach for early PumpONE alpha testing. Protofire sync for LEND and 1sDAI strategy.

2024-12-01 Sun: (3.0h) Review of trouble points to onboarding. Insight: potential to incorporate “one-click buy” as “one-click yield” on Harmony.

2024-11-30 Sat: (3.0h) Onboarding to Harmony ecosystem. 

2024-11-29 Fri: Revisited Portfolio and competitive yield bearing to position Harmony as leading in simple DeFi.

2024-11-28 Thu: Thanksgiving

2024-11-27 Wed: Extended yield product requirements to Protofire. Pushing main initiative to make DeFi simple again. Sync with Li.

2024-11-26 Tue: More details on functionality for vault standard. Insight: main narrative will be higher yield on stables on Harmony.

2024-11-25 Mon: Talk forum maintenance for flagged posts. Yield-bearing stablecoin documentation review and sync with Yuriy. Sync with Frank for Harmony1bot API.

2024-11-24 Sun: (1.0h) Jupiter platform troubleshooting, 

2024-11-23 Sat: (2.0h) Elonxai prompt testing, continued interface integration for simple experience.

2024-11-22 Fri: Wrote the frontend for the yield-bearing stablecoin interface, one for traditional finance, and another for native web3 users.

2024-11-21 Thu: Updates to the DeFi Enhanced Savings product. Prompting and testing results for the Elon bot. Sync with Frank for community requests regarding Harmony1bot API for marketplace. Troubleshooting Pear AI issues.

2024-11-20 Wed: Sync with Yuriy for bridge listings, created yield bearing frontend, sync with Philipp for product positioning.

2024-11-19 Tue: Team sync on PumpRoyale or PumpONE (naming not yet finalized), completing strategy for early alpha and community interactions. X space with community covering recovery multisig custodians (RMC) transition. 

2024-11-18 Mon: Swap liquidity discussions and Recovery Multisig Custodian announcement. 

---

2024-11-17 Sun: (2.0h) Continued Pear AI marketing discussions for upcoming Pear AI - AI Fairness campaign.

2024-11-16 Sat: (3.0h) Troubleshooting and resolved recovery multisig issues. Edits to [Harmony DeFi strategy](https://www.notion.so/harmonyone/DeFi-Strategy-13fa38fc0487807a8afaefea24c1e1d0) added simplification.

2024-11-15 Fri: Completing DeFi strategy document. Continuing discussions regarding exchange information.

2024-11-14 Thu: Discussion regarding PumpONE unique mechanics, Artem adding “Get ONE” to page. Insight: pumpdotfun users enjoy the feeling of launching their own coin, important to balance this with having ONE winner. ONE winner with no liquidity, everyone loses. ONE winner allocating liquidity to all users, everyone wins.

2024-11-13 Wed: Sync with Phillipp on yield bearing stablecoin and overall DeFi plan.

2024-11-12 Tue: Meeting with [Chainspect](https://chainspect.app/) to discuss Harmony mainnet listing. Community X space.

2024-11-11 Mon: Veteran’s Day

---

2024-11-10 Sun: (2.0h) Swap live on Coingecko.

2024-11-09 Sat: (2.0h) Recovery Multisig Custodian Year 2 Vote is live. 
2024-11-08 Fri: Continued co-marketing initiative. Insight: team is AI based, would be ideal for us to build out Harmony model with Harmony specific information and Harmony specific actions.

2024-11-07 Thu: Sync with co-marketing opportunity for Harmony. Yield bearing stablecoin planning with Phillipp, and Recovery Multisig elections sync for tomorrow.

2024-11-06 Wed: Continued Recovery Multisig Custodian (RMC) elections, extended due to US elections, RMC vote will open this Friday, Nov. 8 2024. Shared ai16z open source repo with Rika.

2024-11-05 Tue: Deep dive into [ai16z open source documentation](https://github.com/ai16z), review of pumpONE functionality from Artem’s code.

2024-11-04 Mon: Exchange listing continuation following Harmony Improvement Proposal (HIP-32). Completed Swap listings token approval. [ai16z space](https://x.com/shawmakesmagic/status/1848553697611301014) review.

---

2024-11-03 Sun: (2.0h) Continued research into AI fund manager DAOs. Insight: vitality still dependent on human-in-the-loop, people participate and chat with bot in hopes for fund to invest, removing human input removes chances at memetic adoption. Removing human-in-the-loop for twitter and wallet control is the next phase.

2024-11-02 Sat: (2.0h) Research into DAOsdotfun. Insight: clear dominance from ai16z, portfolio less on immediate successful pumpdotfun tokens, but general adoption.

2024-11-01 Fri: Deep dive on ai16z and breakdown of best AI search tooling. Continued community outreach following successful Harmony Improvement Proposal (HIP-32).

2024-10-31 Thu: Updates for Harmony Improvement Proposal (HIP-32) and Binance BEP2. Successful leader rotation decentralization.

2024-10-30 Wed: Stanford AI x Crypto Summit and team sync. Insights: lots of talk about truth terminal, but as hype dies down, accessibility will be the main use case for the intersection of AI x Crypto.

2024-10-29 Tue: Review of Harmony yield-baring stablecoin proposal. Released official Recovery Multisig Custodian [(RMC) Election forum post](https://x.com/theoperisic/status/1851347534536421667).

2024-10-28 Mon: Sync with SimpleSwap, “Get ONE” live across ecosystem for direct transfers from Explorer, Swap, etc. Planning for Harmony1bot marketing into DeFi actions via AI.

---

2024-10-27 Sun: (2.0h) Continuation of AI workflow with Stephen.

2024-10-26 Sat: (3.0h) Continued research into AI use case, especially Claude Agents for DeFi function calling on Harmony.

2024-10-25 Fri:  Setup a Mini Infinite Backroom between two Llama instances. Brief community X space. 

2024-10-24 Thu: xAI api set up with Amanda and Frank. Spoke with machine learning engineer for truth terminal replication. Quick sync with Stephen, telegram and harmony ecosystem is our advantage, best framework for agentic bots able to navigate Harmony on their own and on behalf of users within telegram small groups.

2024-10-23 Wed: Deep dive on Andy and Truth Terminal via media. Insight: will working on intelligence, basic function calling that the bot will use needs to be added first. This means Swaps, Lend, Borrowing, etc.

2024-10-22 Tue: Editas to Recovery Multisig Election document. Team sync and discussions for Harmony1bot. Insight: bringing Harmony DeFi within 1bot would allow easier onboarding and ecosystem navigation.

2024-10-21 Mon: Sync with Recovery Multisig Custodians (RMC) for upcoming elections. Completed RMC elections document, scheduled release this week, election finalization lined up with US elections.

---

2024-10-20 Sun: (2.0h) Continued Meme & AI research. Insight: DeGods founder Frankdegods also posting about this recently. AI creation, posting, adapting to community will be the next wave. 

2024-10-19 Sat: (1.0h) Meme & AI connection research for potential Harmony use cases.

2024-10-18 Fri: Reviewed and provided feedback on first draft of upcoming DeFi developments. Successful [Swap listing](https://dexscreener.com/harmony/swap) on DexScreener.

2024-10-17 Thu: Completed exchange and token dashboard forms for scheduled token release. Reviewed Pump.fun sync between Aaron and Stephen, will convert parts into notion document tomorrow.

2024-10-16 Wed: ETH SF team sync and house of web3 event.

2024-10-15 Tue: Completed forms and tasks associated with various exchanges and platforms. Reviewed differentiating features for pump clone.

2024-10-14 Mon: Federal Holiday

---

2024-10-13 Sun (2.0h): Attend [ONE Show](https://x.com/Tenacious_DeFi/status/1845464372153548897) with community and Soph to discuss upcoming projects and protocol changes.

2024-10-12 Sat (1.0h): Community outreach for token creators, and memecoin enthusiasts. 

2024-10-11 Fri: Continued product testing. Compared pump.fun approach vs snek.fun in concise [analysis](https://www.notion.so/harmonyone/Pump-Analysis-94375b04b7de48d38e0948889d623f05). Insight: Token creation remains main revenue source and is more popular with users than picking winners.

2024-10-10 Thu: Product testing for Pump.fun clones. Tested: [Pump.fun](https://pump.fun/), [Snek.fun](https://www.snek.fun/), [dx.fun](https://www.dx.fun/). Insights: all follow same UI of frequent updates and moving parts. Dx offers a unique pre-buy percentage 0-5% on token creation. 

2024-10-09 Wed: Coordination with some of the Recovery Custodians (RMC) about Modulo and Recovery1 allocations. Ecosystem and project discussions with Li. Get ONE staging for explorer complete for simpleswap.

2024-10-08 Tue: 1bot help for Frank. Testing CLI bridge base to harmony, successfully bridged base USDC to harmony in a single command. 

2024-10-07 Mon: Further dive into potential innovations to pull from pump.fun. Kings & Quest launch.  

---

2024-10-06 Sun (2.0): Reviewed pump.fun marketing & growth strategy before their product launch.

2024-10-05 Sat (1.0h): Communications with Kings & Quests prior to launch, further discussions with Soph.

2024-10-04 Fri: Attempted end to end from Solana assets wrapped to Base and then bridged to Harmony, scheduled call with Yuriy for adding custom bridge tokens as docs were not enough. Researched telegram bots to fix main channel.

2024-10-03 Thu: Meeting with Across for potential bridge expansion. Secured [Swap listing on Defillama](https://defillama.com/protocol/swap-country#information). Coordination with Alaina to resolve Harmony telegram issues.

2024-10-02 Wed: Reached out to protofire again for simpleswap integration on blockscout for easy ONE onboarding. Entered Defillama discord project update to list Swap under Harmony projects. Reviewed Philipp’s initial Harmony ecosystem high-level breakdown and gave feedback.

2024-10-01 Tue: Sync with Philipp for onboarding and harmony ecosystem questions.

2024-09-30 Mon: Scheduled meeting with Across Protocol for bridge expansion. Added 1SY approval for Swap. Testing Solana assets path to Harmony, wrapped Solana tokens to Base, then bridged Base to Harmony.

---

**2024 Q3 Review (49 hours)**

I secured Swap integration with OpenOcean, a leading DEX aggregator with $20B+ in trading volume and 1.2M+ active users. I also released a [Perpetual article](https://blog.harmony.one/p/three-sigmas-research-for-harmonys) with the ThreeSigma Team, incorporating advanced liquidity provider token mechanisms and competitive fee structures, projected to increase trading volume.

I completed comprehensive ecosystem reports to major exchanges, showcasing 45 unique applications built on Harmony. Additionally, I created a dedicated Harmony DeFi group to streamline ecosystem liquidity, project promotion, and user experience. I also prepared for Recovery Multisig Custodian (RMC) elections, creating a [year-in-review](https://harmonyone.notion.site/Recovery-Multisig-Custodians-RMC-fae72d9bbb214620a46bc51578c44591) document with elections planned for Q4, while coordinating the resolution of .country domain issues, resolving the Colossus bug bounty reward, and integrating SimpleSwap to allow seamless cross chain navigation to Harmony with a 0.4% minimum fee collection.

---

2024-09-29 Sun: (2.0h) Coordinating up coming SimpleSwap marketing announcement.

2024-09-28 Sat: (2.0h) Harmony DeFi group communication for updated liquidity on Swap and Lend. Scheduled Across meeting for Thursday.  

2024-09-27 Fri: Completed troubleshooting following feedback from Protofire team. Successfully completed adding liquidity to Lend and Swap pool. Created and sent Frank updated Harmony information document for Harmony1bot. Reviewed Q3 team reports.

2024-09-26 Thu: Extensive troubleshooting for multisig issues with providing liquidity to Lend, will attempt again tomorrow. Reviewed upcoming projects and next steps with Stephen. 

2024-09-25 Wed: Reached out to Across Protocol team for potential bridge expansion. Created relevant Harmony information document for Harmony1bot. Interview with DeFi ecosystem lead candidate.

2024-09-24 Tue: Completed first draft of Q3 review. Outreach to Utility DAO following liquid staking launch, uONE. Rebalancing review for adding more liquidity to Swap.

2024-09-23 Mon: DeFi candidate review, proposed adding telegram mini-app suite to Harmony1bot to make all telegram initiatives easily accessible via intelligent chats. Finalizing Q3 review. 

---

2024-09-22 Sun (3.0h): Harmony1bot testing and community feedback on bot information. Continuation of [Kings & Quests marketing](https://www.notion.so/harmonyone/Kings-Quests-marketing-plan-105a38fc048780fd87fce7df5b2f9c67).

2024-09-21 Sat (2.0h): Reviewed current telegram mini-apps. Insights: current applications are scattered, would benefit from focusing on a single winner for telegram, Prediction Market for example, and gain users first.

2024-09-20 Fri: Liquidity added for ONE on Lend, and USDT <> ONE pair on Swap. Still unable to add USDT, USDC, ETH. Issues with multisig liquidity providing and Lend sent to Protofire.

2024-09-19 Thu: Harmony1bot feature and updates with Frank. Attempted to add liquidity to Lend, and ONE <> USDT pair on Swap.

2024-09-18 Wed: Helped resolve talk forum issues. Created [marketing plan](https://www.notion.so/harmonyone/Kings-Quests-marketing-plan-105a38fc048780fd87fce7df5b2f9c67) for Kings & Quests.

2024-09-17 Tue: Shared Protofire hyperplane bridge proposal. Insight: another bridge solution may dilute our current assets, recommended path forward is focusing on bridge aggregator. Discussion for synthetix use case bringing Aaron’s panoptic cli to telegram client. 

2024-09-16 Mon: Coordinating marketing with [FlappyH1](https://t.me/FlappyH1Bot). Flap-to-earn telegram mini-game. Preparation for Swap and Lend liquidity providing with Amanda.

---

2024-09-15 Sun: (1.0h) Communication with [Ta-da](https://ta-da.io/), a task-to-earn app with 100k users. Worth seeing at Token2049 for Harmony integration.

2024-09-14 Sat: (1.0h) Community transaction dao update, leaning towards using accumulated funds to provide liquidity to Harmony native assets.

2024-09-13 Fri: Sync with Amanda for DeFi liquidity, Swap pool and Lend will be receiving new liquidity. Updated transaction fee DAO with information on potential allocations, current options include using the funds to provide Swap liquidity or supporting community initiatives.

2024-09-12 Thu: Confirmation with [OpenOcean team for Swap listing](https://x.com/Swoop_Exchange/status/1834242828517429447). Important integration that brings Swap to aggregators and meta aggregators like Swoop.

2024-09-11 Wed: Review of sy.country with Artem, synthetix protocol coming soon to Harmony. Bounty invoice confirmed, awaiting confirmation from Colossus, announcement will be made shortly after.

2024-09-10 Tue: [GX technical documentation](https://harmonyone.notion.site/GX-Technical-Documentation-cca26326258d400cab08f6c3d49013eb?pvs=4) contracts added. Still waiting on panoptic demo, sync with Sun for release date.

2024-09-09 Mon: Sync with Li and Alaina for telegram issues brought up by community. Adding moderator. Insight: worth cleaning up as we transition to producing telegram mini-apps, community chat should be a great place to test new products.

---

2024-09-08 Sun: (3.0h) X space with community, covering decentralized finance initiatives, recovery multisig custodian elections, and staking dashboard improvements.

2024-09-07 Sat: (2.0h) Confirmation with Colossus for bug bounty to be sent early next week. 

2024-09-06 Fri: Removed key features not yet implemented from GX technical documentation and added in new features as well as a Fee Distribution section. 1.country domain troubleshooting with Aaron, sent information to Alaina, will help update our documentation on usage. 

2024-09-05 Thu: Twitter space speaker with community, announcing GX progress, panoptic demo, and OpenOcean response for potential integration of Swap for next week. Contacted listings exchange with updated information.

2024-09-04 Wed: Troubleshooting for 1.country notion page support. Reached out to OpenOcean for Swap integration.

2024-09-03 Tue: Review and sync with Yuriy on GX technical documentation, continued preparation for Recover Multisig Custodian (RMC) elections. Started initial Harmony discord revamp with Tenacious, reached out to current mods, and made [official announcement](https://x.com/harmonyprotocol/status/1831117142391144693) with Alaina. Ta-Da (web3 mechanical turk) conversations about Token2049. 

2024-09-02 Mon: Labor Day


---

2024-09-01 Sun (3.0h): Cryptoland DAO twitter space speaker. Recovery and further discussions about Harmony discord were covered.

2024-08-31 Sat (1.0h): Continued conversations in DeFi group. Insights: OpenOcean looking to add Swap integration as a priority and Harmony discord revamp discussions. 

2024-08-30 Fri: Created Harmony DeFi group, aimed at providing the same open discussions as the Harmony Validator group but with a focus on DeFi. This group will streamline ecosystem liquidity, project promotion, and user experience of our DeFi suite. Confirmation from Pablo for release of DeFi article, still no response from Three Sigma marketing, will ping over the weekend for promotion into next week.

2024-08-29 Thu: Sync with Alaina for DeFi article, finaly edits with Stephen. Continued [simpleswap](SimpleSwap.io) integration discussions for simple ONE purchases within new [blockscout explorer](https://explorer.harmony.one/).

2024-08-28 Wed: Review of [Harmony docs](https://docs.harmony.one/home/developers/harmony-stack). Insight: new users are lost when attempting to troubleshoot on their own, or navigate the space for the Harmony Ecosystem. Sent recommendations to Soph.

2024-08-27 Tue: Final edits on [DeFi article](https://www.notion.so/harmonyone/DeFi-Report-df0794d180d3494c9f6ceffa2094c73d), turning our research into a readible copy for better understanding. 

2024-08-26 Mon: Review of Harmster Kombat. Insights: very simple and minimalistic interactions combined with a complex and highly researched plan to make sure each in game action has a positive impact on the team. I.e. ad revenue, user retention, or user actions (subscribing to YouTube)

---

2024-08-25 Sun: (8.0h) Extensive restructuring for [DeFi report](https://www.notion.so/harmonyone/DeFi-Report-df0794d180d3494c9f6ceffa2094c73d#954171edd8544d9184907a422e91026c).

2024-08-24 Sat: (2.0) Continuation of [DeFi article](https://www.notion.so/harmonyone/DeFi-Report-df0794d180d3494c9f6ceffa2094c73d#954171edd8544d9184907a422e91026c).

2024-08-23 Fri: Collected and presented DIA oracle provider price comparison following meeting earlier in the week. Continued discussions with recover multisig custodians, Soph, and Stephen for next steps with Colossus. [Started editing and reformatting](https://www.notion.so/harmonyone/DeFi-Report-df0794d180d3494c9f6ceffa2094c73d) DeFi article.

2024-08-22 Thu: Discussion with Soph for Colossus bug bounty, as well as recovery multisig custodians (RMC).

2024-08-21 Wed: Meeting with DIA oracle provider for price comparison for gmx and DeFi suite. 

2024-08-20 Tue: Edits on 2025 Roadmap document. Sent Swap factory address to Defillama from TEC Viva and Kratos messages. Continued conversations with Pyth team, awaiting internal decision.

2024-08-19 Mon: Spoke with Pyth team for Harmony mainnet integration, added feedback and questions for 2025 roadmap. Reached out to Rome Protocol. Rome Protocol's shared sequencer could enhance Harmony's cross-chain bridges, improving transaction finality, security, and user experience. Added Recovery Multisig Custodian details to document leading up to elections.

---

2024-08-18 Sun: (3.0h) Continued [Recovery Multisig Elections document](https://harmonyone.notion.site/Recovery-Multisig-Custodians-RMC-fae72d9bbb214620a46bc51578c44591?pvs=4).

2024-08-17 Sat: (1.0h) Planned Recovery Multisig Elections document, will include past year of stats regarding the elected individuals.

2024-08-16 Fri: Draft for [recovery progress and marketing plan](https://www.notion.so/harmonyone/Recovery-Marketing-Update-db6bc50b5af1429d86541dafd68cd8d5).

2024-08-15 Thu: [Confirmation from Metamask team](https://github.com/MetaMask/metamask-mobile/pull/10600) for resolving issue with Harmony logo on mobile version. Will be live in version 7.29.0. Reviewed potential telegram mini-app for DeFi.

2024-08-14 Wed: Swap listing approvals for Binance smart chain USDT. Made contact with Pyth developer, moving conversation to a dedicated Pyth <> Harmony channel. Current plan is to integrate Pyth price feeds for our DeFi suite on Harmony mainnet.

2024-08-13 Tue: Reviewed GX from Pablo and suggested fee parity with competitors with % of fees to larger trading competitions rather than rebates, potentially resulting in GMX fee % parity but with more incentives for traders. GXP would remain at 70% fee collection for liquidity providers. Spoke with recovery multisig custodians (RMC) for elections.

2024-08-12 Mon: Sync with Pablo for trader incentives, working through tokenomics for GX platform and GXP. Update marketing with [Harmony 2024 report](https://stse.substack.com/p/harmony-2024-ecosystem-sustainable), Token2049 attendance, and [Mainnet metrics via Blockscout explorer](https://explorer.harmony.one/stats): 8m+ addresses, 800m+ transactions, 143k contracts. 

---

2024-08-11 Sun: (3.0h) Attended [CryptoLandDAO](https://twitter.com/Crypto_LandDAO) community space. Review of fee splits from leading perpetual exchanges.

2024-08-10 Sat: (1.0h) Communications with metamaks representative to fix Harmony mobile logo.

2024-08-09 Fri: Sync with Pablo. Insight: GMX token discussion and alternative path to incentivize traders and liquidity providers further than GMX. Currently GMX only incentivizes liquidity providers and governance.

2024-08-08 Thu: Operations and unboarding. Attended [Harmony X space](https://x.com/harmonyprotocol/status/1821672065247932911). Iterations for [technical documentation](https://www.notion.so/harmonyone/GX-Technical-Documentation-cca26326258d400cab08f6c3d49013eb#551e929924d647e796c82349e09a4802): Oracle explanations and adding How-To guide for GX.

2024-08-07 Wed: [ONEshow](https://x.com/Tenacious_DeFi/status/1821348517753053416) speaker. Sync with David from Swoop for contacts with 4 bridge and DEX aggregators. (Odos, Kyber, Li.Fi, 0x) Prioritizing finalizing Swap listing on OpenOcean.

2024-08-06 Tue: Sync with Colossus staking for bug bounty and institutional staking solutions for Harmony moving forward. Created initial draft of [technical documentation for GX](https://www.notion.so/harmonyone/GX-Technical-Documentation-cca26326258d400cab08f6c3d49013eb#551e929924d647e796c82349e09a4802) and sync with Pablo and Yuriy. Prepared Protofire rate limit update.

2024-08-05 Mon: Working with protofire to include block explorer contracts in csv format for [Artimis support](https://www.artemis.xyz/). Pyth network support for Harmony mainnet outreach.

---

2024-08-04 Sun: (1.0h) Drafted preliminary thoughts on bug bounty for Colossus.

2024-08-03 Sat: (1.0h) Reviewed and refined bullet points version of Harmony 2024 article, focusing on making it more impactful for event attendees.

2024-08-02 Fri: Coinbase submission complete. Harmony 2024 article iterations for different users. Next steps include building out DeFi and GMX technical documentation as we await responses from Coinbase (listings) and Binance (marketing) teams.

2024-08-01 Thu: Reviewed Token2049 events from [list](https://lu.ma/token2049) provided, sync with Alaina with findings. Insights: strong VC and developer showcases to capitalize on. Bullet points for [Harmony 2024 article](https://harmonyone.notion.site/Harmony-2024-Decentralized-Open-Source-Community-Driven-bb89f767d26d4aafa6a27ee08342688d?pvs=4) for event attendees focusing on concise points and top to bottom flow of relevant information.

2024-07-31 Wed: Sent message to Metamask team to fix mobile logo and Wrote Binance marketing response. Sync with Yuriy following Aaron’s audit.

2024-07-30 Tue: [DEX Screener submission.](https://t.co/LKzaFxHEze) Preparing for technical docs with Pablo, Yuriy, and Rika for gmx.

2024-07-29 Mon: Sync with Pablo for Harmony DeFi and gmx fork. Reached out to [Staking Rewards](https://www.stakingrewards.com/) team for Harmony listing. Finalized DEX Screener [listing submission](https://harmonyone.notion.site/Harmony-DEX-Screener-f1c4b90832ec404a9f92fd727f12da9c?pvs=4) with Protofire information. 

---

2024-07-28 Sun: (3.0h) Continued work on Harmony DeFi narrative, breaking down larger vision into actionable weekly goals. Prepared talking points for upcoming sync with Pablo regarding Harmony DeFi and GMX fork.

2024-07-27 Sat: (2.0h) Further review of GMX progress. Started drafting initial ideas for technical documentation structure for GX.

2024-07-26 Fri: Review of gmx progress and sync with Yuriy. [Dex screener listing form](https://harmonyone.notion.site/Harmony-DEX-Screener-f1c4b90832ec404a9f92fd727f12da9c?pvs=4) for Swap, waiting on Protofire for missing information.

2024-07-25 Thu: Prepared [Dex screener listing form](https://harmonyone.notion.site/Harmony-DEX-Screener-f1c4b90832ec404a9f92fd727f12da9c?pvs=4). Sync post meeting with Alaina and breakdown of Pablo's upcoming role.

2024-07 24 Wed: Prep for Alaina's meeting with Yuriy, Pablo and ThreeSigma team.

2024-07-15 Mon - 2024-07-23 Tue: Paid Time Off

2024-07-14 Sun: (1.0h) Refined the structure of the Harmony DeFi document, ensuring a clear progression from current state to future vision.

2024-07-13 Sat: (4.0h) Continued research on GMX v1 vs v2, focusing on potential improvements for Harmony's implementation. Started outlining key points for the Harmony DeFi document, emphasizing innovative approaches.

2024-07-12 Fri: Continuation of [Harmony DeFi document](https://www.notion.so/harmonyone/Harmony-DeFi-1c2e88b425ea48088613c84bf49cd2de) pushing Harmony to evolve from forking primitives to becoming the industry leader in DeFi.

2024-07-11 Thu: Initial work on Harmony DeFi narrative following discussion with Li, current plan is to break down larger vision into 1-3 day chunks. Review of [GMX](https://defillama.com/protocol/gmx-v2#information) v1 vs v2.

2024-07-10 Wed: Organizing yuriy’s progress left for gmx. Supplying Binance with concise recovery information. Current recovery status: 24.55% recovered. Completed initial [GMX launch plan](https://www.notion.so/harmonyone/Launch-Plan-GMX-5544d1d4c88941c087b05f815e35fb51) and coordinated with Alaina, Rika, and Yuriy.

2024-07-09 Tue: Q3 planning with Li, and hand-off sync with Alaina and Yuriy for upcoming paid time off. Reached out again to Binance team for marketing push.

2024-07-08 Mon: Addressing recovery contributors section of LayerZero airdrop. Team sync following recent operation changes.

---

2024-07-07 Sun: (2.0h) Continued research for launch. High-level Insight: prioritizing liquidity provision through fee sharing, competitive pricing, and a platform liquidity token looks to be the best approach to significant growth and user adoption for perpetual exchanges.

2024-07-06 Sat: (2.0h) Dive into previous [launch campaigns](https://harmonyone.notion.site/Launch-Review-Safe-dYdX-GMX-b204075fc0474c99833ed94749495a91?pvs=4), including Safe, DYDX, and GMX.

2024-07-05 Fri: Discussions with Recovery Multisig Custodians about recovery allocations. Currently modulo has not burned recent allocations, whereas Recovery 1 has been able to burn 100%. Over the counter market will potentially be released by modulo to account for this, also giving the ability to prioritize specific pre-hack wallets yet to participate in recovery. Sync with Yuriy, prioritization of assets to be listed for GMX v1 launch.

2024-07-04 Thu: July 4th.

2024-07-03 Wed: Q3 preparation. Top priority: GMX v1. Scheduled sync with Yuriy. X Speaker for [ONEShow](https://x.com/Tenacious_DeFi/status/1805680489581220324). Topics covered: DeFi on Harmony, Lessons from Jupiter, Novel staking initiative from R1 team, and the advantages of decentralized applications that fully leverage a layer 1 infrastructure.

2024-07-02 Tue: Review of [Aperture Finance](https://www.aperture.finance/), as an AI intent based application above Uniswap V3 for potential implementation for an all inclusive ONE platform for Swap, Lend, Bridge, Perp, Options, etc. Additional wallet creation successful for R1 team, issue remains while attempting to claim via wallet connect. 

2024-07-01 Mon: Troubleshooting with Ulad and Recovery1 for multisig claim. Current issue: ZRO claim not recognizing Harmony smart contract address. Modulo claim successful through [metadata work around](https://harmonyone.notion.site/Multi-Chain-Multisig-Address-475080ac0bc84ddbb8c9421897bc8e40?pvs=4). Asked Coingecko for [Swap](https://swap.harmony.one/) verification.

---

**2024 Q2 Review (49 Hours)**

I led the submission of the [LayerZero airdrop](https://commonwealth.im/layerzero/discussion/21730-harmony-bridge-rfp) for 449,000 wallets (users, liquidity providers, and recovery contributors), resulting in ZRO tokens distributed among the Harmony community (~$1.5m at launch). I also crafted a new [perpetual decentralized exchange proposal](https://www.notion.so/d11c3efa2cf6457b96105bc9a5a65dd7?pvs=21) that incorporates liquidity provider tokens to enhance trading dynamics. I re-engaged with 10 key platforms like Coinbase and Moonpay and potential integrations including Stargate, OpenOcean, Synapse, and Li.Fi with the aim of enhancing Harmony’s access to liquidity with industry leading cross-chain bridge and exchange applications.

I participated in 3 community [X spaces](https://x.com/Tenacious_DeFi/status/1794241670621573339?t=TnZXgjcx1cKzkWmx9TXPYg&s=19) and 1 larger space in collaboration with [Swoop](https://swoop.exchange/), one of the leaders in cross-chain aggregation, with 4,600 community members tuning in. Additionally, I managed the completion of comprehensive Coinbase documentation, detailing 38 unique applications utilizing Harmony, from DeFi to essential infrastructure tools; this document is now undergoing internal finalization.

---

2024-06-30 Sun: (4.0hr) Simplified draft for [Harmony DeFi](https://harmonyone.notion.site/Jupiter-Strategy-Harmony-DeFi-0dea5583769c44548c008eb5952d0b23?pvs=4).

2024-06-29 Sat: (1.0hr) Started draft for [Harmony DeFi](https://harmonyone.notion.site/Jupiter-Strategy-Harmony-DeFi-0dea5583769c44548c008eb5952d0b23?pvs=4).

2024- 06-28 Fri: Operations and research on JUP token and [Jupiter platform strategy](https://crypto.news/jupiter-exchange-launches-giant-unified-market-initiative/). Insights: Goal is unified market. Plan: Bring memecoins, real-world assets, decentralized and perpetual exchanges, stocks, and forex into a single market.

2024- 06- 27 Thu: Sourcing AMA from validators, ecosystem developers, and community members for [TGI space](https://x.com/harmonyprotocol/status/1806392237682753644), attended [Validator DAO space](https://x.com/DaoHarmony/status/1806375922905333868).

2024-06-26 Wed: Completion of [Binance Document](https://www.notion.so/harmonyone/Binance-Post-Listing-Team-3f9154522afa46dca46c63f51a2517e5). Operations and community outreach for upcoming AMA.

2024-06-25 Tue: Space [AMA announcement](https://x.com/harmonyprotocol/status/1805681714121130224) and progress on Binance post listings team [form](https://www.notion.so/harmonyone/Binance-Post-Listing-Team-3f9154522afa46dca46c63f51a2517e5).

2024-06-24 Mon: Re-engaged [Stargate](https://stargate.finance/) and submitted application for [Pyth Network](https://pyth.network/) for Harmony integrations.

---

2024-06-23 Sun: (1.0hr) Reached out to LayerZero directly for Harmony support.

2024-06-22 Sat: (3.0hr) Continued looking into smart contract claiming for ZRO.

2024-06-21 Fri: LayerZero troubleshooting, current issue: multisig users unable to claim. Wrote complete guide for [Harmony ZRO claim](https://x.com/theoperisic/status/1804429287472402625). Metric: Harmony community ZRO airdrop valuation ~$1.2m USD (at launch)

2024-06-20 Thu: Completion of ZRO LayerZero Airdrop. Tuned into Timeless Story, Power Perpetuals, Meme Launchpad [X Space](https://x.com/harmonyprotocol/status/1803901043140628754).  

2024-06-19 Wed: Speaker for [Harmony X Space](https://x.com/Tenacious_DeFi/status/1803563071031459934). Highlighted Topics: website updates, gmx/panoptic, R1 [staking proposal and forum post](https://talk.harmony.one/t/expanding-the-r1-ambassador-program-for-enhanced-community-engagement-v2/24724/3), hard fork, overview of current space, DeFi.

2024-06-18 Tue: Discussions with panoptic. Insight: panoptic is looking to launch on all layer 2s which support uniswap v3 this year, should we engage for Harmony layer 1 support, continue with our own implementation, or pursue both? Completed [Binance Marketing review](https://www.notion.so/harmonyone/Binance-Marketing-Trading-Review-cb6fc96845e64bceb478093b0facf31a).

2024-06-17 Mon: [Magic Square](https://magic.store/) confirmed partnership with 3 listed projects upon completion of forms for Swap, Lend, and Timeless or Perpetual (depending on completion date). Tested [squeeth](https://www.opyn.co/strategies/crab?ct=US). Insight: platform navigation is simple and straight forward, two prominent strategies around ETH, including USDC for hedging against ETH and ETH for leveraged bullish positions. *ETH side of squeeth affected by [Euler Finance](https://www.chainalysis.com/blog/euler-finance-flash-loan-attack/) exploit. The simplicity and minimalism should be replicated for our perpetual market.

---

2024-06-16 Sun: (4.0hr) Additional Jupiter testing. Insights: Jupiter now supports swaps, perpetuals, and now [bridging](https://jup.ag/bridge-compare) all within 1 page. We started something similar with Harmony Portfolio, worth looking into to expand and add perpetual market to 1 location for ease of use. 

2024-06-15 Sat: (2.0hr) Testing [panoptic beta](https://deeznuts.panoptic.xyz/) and [Jupiter mainnet](https://jup.ag/perps). Insights: panoptic requires previous knowledge of options or at least following an onboarding flow for how to trade options, Jupiter advantage is you can jump in an trade up or down easily. 

2024-06-14 Fri: X space with community, more deep dive into panoptic. Insights: do we need to separate options from panoptic and perpetuals from dydx, is there a process to include both? Dydx: institutional investor, Jupiter: retail. What is the end user profile for our perpetuals market?

2024-06-13 Thu: Community discussions for integrations and marketing. Attended stephen + zi X space and livestream.

2024-06-12 Wed: Q2 review drafting and discussions with Li.

2024-06-11 Tue: Further Panoptic discussions in discord about PLP (Passive Liquidity Provider). Research on Perpetual exchange liquidity tokens, [GLP](https://gmx-docs.io/docs/tokenomics/rewards/) for GMX, [JLP](https://jup.ag/perps-earn) for Jupiter, and [dydx](https://docs.dydx.exchange/users-rewards/staking_rewards) token for dydx. Insight: of these tokens, dydx requires the token to be staked in order to receive the benefits of fee distribution.

2024-06-10 Mon: Discussions with Panoptic CEO. Research on dapp tokenomics from leading applications: Lido, Wormhole, Aave. Insight: although tokenomics from these and other tokens can be useful, focusing solely on perpetual exchanges and DEXs would be better for our use case.

---

2024-06-09 Sun: (1.0hr) Deliverable realignment, hold on bridge and marketing listing progression, change to Panoptic focus.

2024-06-08 Sat: (1.0hr) Review of [highest TVL bridge](https://defillama.com/protocols/Cross%20Chain). Insight: Stargate highest with ~$240m, average daily volume ~$24m

2024-06-07 Fri: Initialized conversations with [Stargate Foundation](https://stargate.finance/) for integration and [Magic Square](https://magicsquare.io/) for marketing.

2024-06-06 Thu: Wallet management. Reviewed R1 [community engagement proposal](https://talk.harmony.one/t/expanding-the-r1-ambassador-program-for-enhanced-community-engagement-v2/24724). Insight: has the potential to change the grant and milestone paradigm and leverage proof of stake to help bolster the ecosystem as well as promote development and engagement growth. Proposal should be finalized with more concrete milestones and time boxed stake.  

2024-06-05 Wed: Submitted coinmarketcap form for layer 1 category inclusion. [Harmony ONE  X space](https://twitter.com/i/spaces/1zqJVqeAbjXGB) speaker.

2024-06-04 Tue: Submitted coingecko form for layer 1 category. Read through [/options](https://xn--qv9h.s.country/p/on-chain-and-open-source-perpetual) and continued DeFi deep dive.

2024-06-03 Mon: Completed in person wework pass for office work. Continued LayerZero due diligence conversations. Reviewed [panoptic and options](https://threesigma.xyz/blog/defi-options-landscape) report, and dydx [keynote](https://www.youtube.com/watch?v=Nfi0C32xt54). insight: asside from infrastructure, successful perpetual exchanges carve out their target user: i.e. dydx is only concerned with hedge funds and large volume api professional traders, not looking at average retail. 

---

2024-06-02 Sun: (1.0hr) Options review from my time as an options trader prior to moving to crypto. 

2024-06-01 Sat: (1.0hr) Discussions with non-crypto holders. insights: much less maximalism in masses, pushes the narrative that all chains are 1 dapp away from mass adoption.

2024-05-30 Thu - 2024-05-31 Fri: Paid Time Off.

2024-05-29 Wed: More testing of [base.fun](https://www.base.fun/) insight: when chasing quick gains, barriers of entry are the biggest forms of friction, larger than user experience. Started transition to Panoptic focus, tested 1000x leverage on solcasino.  

2024-05-28 Tue: [Commonwealth LayerZero Submission](https://commonwealth.im/layerzero/discussion/21730-harmony-bridge-rfp) published, under review from LayerZero team. Coinbase doc approved by Casey, moving to google docs to add edits from Stephen. Started Stargate communications.

2024-05-27 Mon: Memorial Day

---

2024-05-26 Sun: (3.0hr) Testing [pump.fun](https://pump.fun/board) and [base.fun](https://www.base.fun/), spoke with Matt about potential Harmony fun.country product.

2024-05-25 Sat: (1.0hr) Ideation with Tenacious for ecosystem project marketing and support guidelines.

2024-05-24 Fri: Completed coinbase doc, sent for review to Casey and Soph.

2024-05-23 Thu: Continued communications with layerzero team given the recent update, added to coinbase doc. Metric: 804+ Million transactions since mainnet on Harmony, almost 1 Billion! 

2024-05-22 Wed: ONE Show X space speaker, topics covered: Layerzero, perpetuals, recovery elections, project spotlights, ideation on stake ONE to earn ALL assets (i.e. BTC ETH etc., potential implementation and integration with staking, swap, bridge, etc. to increase utility of staking ONE)

2024-05-21 Tue: Additions to coinbase doc for relevant ecosystem dapps and partners. 35 ecosystem dapps and partners added, will continue with formatting tomorrow.

2024-05-20 Mon: Iterations on Layerzero, no updates on allocation amount from their team, removing core team developer allocation for complete community airdrop. 50% bridge users, 30% liquidity providers, 20% recovery contributors.

---

2024-05-19 Sun: (1.0 hr) Answering community questions for airdrop. No response yet from Layerzero on amount of allocation. 

2024-05-18 Sat: (3.0 hr) Added list of eligible wallets for the current categories and percentage, finalization will occur after community and layer zero review.

2024-05-17 Fri: Completion of LayerZero form, posted to community forum for review, deadline of review May 24th 2024, deadline for submission May 31st 2024.

2024-05-16 Thu: CSV for bridging by May 1st snapshot complete. Current split for the Harmony LayzerZero Airdrop, Note: UNFINALIZED, (45% Users that have bridged OFTs, 30% Liquidity Providers, 15% Recovery Contributors, 10% Developer Account) sharing with Casey and Soph for feedback, and Layer Zero for potential issues.

2024-05-15 Wed: Following sync with Soph and Yuriy, expanded LayerZero allocations to include more than just bridging. (Swap liquidity providing included as well) Metric: 450k unique wallets have interacted with the Harmony LayerZero Bridge.  

2024-05-14 Tue: Completed LayerZero airdrop submission copy, waiting on csv from Yuriy for eligible wallets. Helped Julia with R&D documentation, filled first half of the document, Julia will complete next half by end of day.

2024-05-13 Mon: Sync with Casey for coinbase form and Li for Binance marketing contact, established contact with LI.FI, LayerZero, and OpenOcean.

---

2024-05-12 Sun: (1.0h) Read required messari articles on Synthetix Perpetuals.

2024-05-11 Sat: (1.0h) Continued discussions with David from Swoop, now we have a group with OpenOcean on telegram, next steps will include Swap support, or alternative suggestions on their end.

2024-05-10 Fri: Sync with Julia for OpenOcean integration for larger presence of Harmony on Swoop. Reached out to DIA to start discussions we previously moved on from, again working towards amplifying our ecosystem oracle support for each decentralized application.

2024-05-09 Thu: Continued research on perpetual exchanges to add to current primitive offerings, initial planning of minimal product pulling from Jupiter and dydx.

2024-05-08 Wed: Harmony ONE twitter space with Alaina, Julia, Tenacious with Crypto Land DAO, and David from Swoop. Further website iterations, customization remains limited, webflow may be a better option.

2024-05-07 Tue: Work on new Harmony website. Insights: Super.so customization is extremely limited, but already an improvement on our current site.

2024-05-06 Mon: Draft of DeFi strategy for Q2-Q4 prioritizing perpetual exchange first, building up to complete DeFi narrative that includes cross-chain, and AI to bring all initiatives together.

---

2024-05-05 Sun (1.0h): Reached out to tenacious_defi for Harmony AI data docs.

2024-05-04 Sat (1.0h): Review of Harmony x Swoop doc

2024-05-03 Fri: Sync with Stephen, reassignment of remote engineers based on meeting.

2024-05-02 Thu: Celebration of Stephen’s 6th year dinner. Further talks on Layer 3. Updates to harmony AI data docs. Template search for notion site to update main harmony website. Found quality options for main site upgrade, feedback was the price of the template was too cheap, changing search for expensive templates rather than quality templates.

2024-05-01 Wed: Call with Nagesh and manager for 3 month contract pause, to resume August 6th. Continued work on Coinbase form. ONE Show twitter space.

2024-04-30 Tue: Operations with Li and Q1 review sync with Amanda. 

2024-04-29 Mon: Operations with Amanda, organizing q2 DeFi initiative of copy trading for Frank and Yuri. Q2 prioritizations remain unclear, as we tack on additional tasks others are getting left behind, I.e. coinbase forms. I’ve created and updated Nagesh, Frank, and Yuriy on tasks. Until a clear structure for q2, I will ignore daily tasks until these larger objectives are completed. Notified Encode of our cancellation of the hackathon due to our prioritization of further developing DeFi infrastructure and AI data.

---

2024-04-28 Sun (1.0h): Scheduling call during upcoming week with Amanda.

2024-04-27 Sat (2.0h): Research on intent based contract interactions, looking to bring this to 1bot, or Harmony Portfolio. Harmony users should have a seamless way of navigating DeFi across all chains in ONE location, this is the basis of something we can build based on the tools we have with 1bot on telegram and Harmony Portfolio web app, main worry is prioritization and product direction get in the way of either one reaching completion. 

2024-04-26 Fri: Off boarding Theo with Amanda, finalizing resources for Zi’s layer 3, prepared for twitter space. 

2024-04-25 Thu: Encode funding discussions for web3 + AI hackathon, research and suggestions for Harmony Defi: complete Harmony Portfolio to have the essential defi primitives all in ONE seamless location, then add a perpetual dex with LP tokens for community to earn generated fees as well as trader fees.

2024-04-24 Wed: More research and discussions with Zi for Layer 3 protocol, off boarding Theo with Amanda.

2024-04-23 Tue: New initiative with Zi for an open social graph, a layer 3 protocol concept and early discussions.

2024-04-22 Mon: Meeting with Nagesh for q2 deliverables, scheduled meeting with Zi for timeless integration tomorrow, will sync with Artem and Frank following the meeting.

---

2024-04-21 Sun (1.0h): Harmony AI docs.

2024-04-20 Sat (5.0h): Spent time assigning and detailing Q2 deliverables. As we are now one month into Q2, it's crucial that we have a stable set of objectives to ensure we meet our goals. I suggest that ongoing tasks either be prioritized for completion or clearly identified as discontinued. This approach will help us avoid any ambiguity in our direction and ensure that all products are completed to a higher standard.

2024-04-19 Fri: Clearing offices.

2024-04-18 Thu: Drafted team Q2 assignments. Started 1Bot doc for real-time Harmony information with Tenacious. Coordination with Protofire for Lend. Insight: Lend needs additional liquidity for the automated money market to flow smoother, suggestion 10k USD total split accross each provided token.

2024-04-17 Wed: Meeting with Encode for AI/Crypto hackathon for pricing and potential outcomes. Attended ONE show.

2024-04-16 Tue: Continued Encode discussion for AI and Crypto developments. Updated deliverables. Discussed alternative approach to product development with user focus with Stephen.

2024-04-15 Mon: Started coinbase requirement docs. Coordinated with Soph for social media hires. Backfill and outreach for daily updates.

---

2024-04-14 Sun (3.0h): Research for Bitcoin and Runes. Insights: programmability of bitcoin will continue to increase, chasing bitcoin would not lead to ideal results, better path is building infrastructure that allows people to easily navigate bitcoin as their fees become far too high and the network gets congested.

2024-04-13 Sat (1.0h): Community outreach.

2024-04-12 Fri: Meeting with Encode for developer relations. Insights: Potential inclusion of Harmony in AI and crypto hackathons. PRD for ONE Resume.

2024-04-11 Thu: Elaboration on Joskins support and alignment of merch.

2024-04-10 Wed: Sync with Stephen for continuation of Q2 and alignment for internal and apps team. Set up meeting with Encode for Friday to improve developer relations.

2024-04-09 Tue: Approved listing for Swap. [Stats](https://lend-info-stg-country.safe.protofire.io) for Lend in progress. Emailed Coinbase asset outreach as advised from Coinbase representative.

2024-04-08 Mon: Q1 review for % split. Coordination for /progress, replacing new 2-week deliverables. Check in with Protofire for Blockscout, Lend, and potential for incentivized token for governance on Lend with % fee sharing from my original proposal.

---

2024-04-07 Sun (2.0h): Looked into [open source local](https://clusteredbytes.pages.dev/posts/2024/fully-local-chat-with-pdf-app-using-llamaindex-ollama-nextjs/) frameworks to test for an open source version of ONE Resume without the need of Claude. Insight: not as consistent but with sufficient training this can be solved, cost would be removed.

2024-04-06 Sat (3.0h): Continued testing of Jobscan AI tooling. Insight: not very accurate scoring or ability to reach higher scoring using their suggestions, feels like a worse grammarly but for resumes, focused on keyword additions rather than honest review. 

2024-04-05 Fri: Opened communications with [Ta Da](https://ta-da.io/) to verify “Decentralized workforce enables high-volume, cost-effective, and region-specific data collection”.

2024-04-04 Thu: Sync with Protofire on Blockscout. Update: Cross Shard Transactions, ETA Monday. Staking Transactions, ETA end of next week. Iteration and sync with Stephen for 2-week deliverables.  

2024-04-03 Wed: First iteration for team deliverables due 4/19. Further dive into [CryptoKoryo](https://harmonyone.notion.site/CryptoKoryo-AI-Data-on-Chain-66d1e2bdf6dd4a38a1e9e1b7ef773441?pvs=4) report. Insight: interesting concepts but no sign of adoption yet, also no metrics leading to clear model improvements. 

2024-04-02 Tue: Review of on-chain AI products from @CryptoKoryo report. Story Protocol thread. Notified protofire for adding market data on frontend.

2024-04-01 Mon: Made contact with MoonPay representative, awaiting feedback on their end. Full team review management and weekend hour tracking. Sync with Artem, Yuriy, Theo F, and Sun on OP Stack and Portfolio progress. OP Stack based rollup release on Shard 1 and article scheduled for Friday.

---

Q1 Review:

In Q1, I managed and helped launch 4 distinct projects: Human-Protocol, Quest Lottery, Lend, and Flip. For each project I contributed to the product through UI/UX iterations, userflows, and minor frontend pushes, as well as operations by coordinating 12 individuals, 5 internal, 4 from the apps team, and 3 from protofire. I also extended this coordination to our community, helping the 7 recovery multisig custodians who increased recovery percentage by 6%, the most in a single quarter, and the 60+ eligible validator community for HIP-32 leading to a unanimous YES vote with 3 billion ONE.

I also released the 2024 roadmap, engaged in twitter spaces and EthDenver, promoted 7 ecosystem projects, and onboarded a new infrastructure partner, Envio. The campaign with the OneScription team, led to their sold out inscription token, raising 1.8 million ONE. On my own time, I also attended 5 bi-weekly Harmony Ecosystem Roundup spaces to engage with the community.

7 ecosystem project promotions: Galaxii, a decentralized TikTok alternative; MetaSMS, an encrypted messenger; Joskins, a platform for purchasing merch with ONE tokens; Knights&Peasants, a strategy blockchain game; OneScription, a gateway for converting Harmony inscriptions to ERC-20 tokens; AnotherWorld, a Ready Player One-inspired metaverse; and Coherence, an NFT marketplace.

---

2024-03-31 Sun: Reached out to MoonPay for possible listing. [1hr]

2024-03-30 Sat: Worked on tokenomics for Partie [1hr]

2024-03-29 Fri: Gathering and formatting individual performance in one place. Harmony account tweet and replies. Drafted [community campaign](https://harmonyone.notion.site/Harmony-x-AnotherWorld-gg-2d33bd483f3b4170ae57ea85b5d2be35?pvs=4) with AnotherWorld.

2024-03-28 Thu: Meeting with Partie. Collecting in office and remote Q1 updates.

2024-03-27 Wed: Meetings with team for Q1 review. Covered main X account posts. Continued open source AI summit resource collection.

2024-03-26 Tue: Sync with Artem, Frank, and Yuriy for q1 reviews. Coordination with Mathew Barrett for Standard Protocol and Althlete protocol. Doc review of DIA oracle solution.

2024-03-25 Mon: Meeting with Stephen to realign prioritize on Story Protocol and Portfolio. Started reviewing progress for q1 review. Built and tested resume analyzer using claude 3 api against Julia's resume. Conistent in scoring, short paragraph description, and 3 suggestions based on job description.

---

2024-03-24 Sun: Research on predictions market for salary. Insight: Thales has a simple UX but only supports up/down market. Overtime markets supports only sports betting, but their support for games is extensive. Polymarket covers the widest options with popular categories including elections, box office, sports, ETF approvals, etc. no markets for salary on any platform. [2hr]

2024-03-23 Sat: Changed opus outputs to provide suggestions for resume improvements. Insights: base Claude still needs small adjustments, I.e. “more concise” “single sentences” “follow job description precisely” to yield best results. [3hr]

2024-03-22 Fri: Troubleshooting bridge with Galaxii, sync with protofire for blockscout progress. UI/UX work with Alaina for Buy/Bridge page of Harmony Portfolio.

2024-03-21 Thu: Attended TGI AI. Claude 3 resume testing and Harmony Portfolio iterations. Insights: base model is strong but tends to be verbose, small prompting creates structure consistency, but api structure would be best to deliver consistent match results.

2024-03-20 Wed: Watched NVIDIA panel with “Attention is all you need” authors”. Iterated Harmony Portfolio with Alaina. Tested Claude 3 resume ranking.

2024-03-19 Tue: Attended NVIDIA GTC. Continued monitoring HIP-32, unanimous YES! Research into [Keep3r and KeeperDAO](https://docs.keep3r.network/) project and tokenomics to apply to job recruiters.  

2024-03-18 Mon: Continued research on AiMM, helped Alaina with Harmony Portfolio mocks.

---

2024-03-17 Sun: Market research on [AiMM](harmony.one/aimm). Looking into Ploymarket, specifically prediction market for salary and candidates. Insights: polymarket is banned in the US, decentralized matchmaking for the job industry may be a better solution than prediction markets. [5hr]

2024-03-16 Sat: Continued search for voice first AI products or models. Insight: reinforcement learning is limited to the foundational knowledge base, AGI will need an [abstract layer](https://medium.com/autonomous-agents/enhancing-llms-reasoning-through-jepa-a-comprehensive-mathematical-deep-dive-301ec9c4d6f2). [3hr]

2024-03-15 Fri: Meeting with Li. Formatting for deliverables, Nagesh and Ivan adding shortly. Testing Claude 3 1bot release. Insights: missing web search and subagents that gets the most out of Claude 3 Opus.

2024-03-14 Thu: Concluded 2-week deliverables for team. Helped Rika with smart contracts for story protocol using Julia’s notion.

2024-03-13 Wed: Call with Artem and Frank for 2-week deliverables. Sync with Stephen and Julia for potential voice foundational direction. Contacted Stanford open source AI summit and community members for decks and additional information on crypto AI data companies.

2024-03-12 Tue: Meeting with DIA for alternative oracle solution to add options for dapps. Insight: Their architecture directly provides a solution to the previous oracles issue regarding the bridge hack. Documents will be shared tomorrow EOD. Long meeting with Stephen to align team for next two weeks of deliverables.

2024-03-11 Mon: Moved progress from /x and /s to /h. Scheduled call with DIA for alternative oracle providers to boost support on Harmony. Insight: Investigating JEPA (Joint Embedding Predictive Architecture) for voice synthesis could be valuable following the video of [Lex Fridman with Yann LeCun](https://www.youtube.com/watch?v=5t1vTLU7s40), as its focus on predicting missing segments and learning semantic relationships in the audio signal might lead to improved control over traditional LLMs.

---

2024-03-10 Sun: Further look into providing valuable data for LLMs,resulting in a significant model improvement. Insight: Quality over quantity is the best approach to voice data. [Apple model improvements](https://machinelearning.apple.com/research/personal-voice). We may need to create a new performance benchmark as a standard, Word Error Rate (WER) does not account for natural sounding speech, and Mean Opinion Score (MOS) is an aggregated score of human listeners, quantifying MOS could be great for the entire synthesis space as we move forward. (7hr)

2024-03-09 Sat: Joskins coordination for increased awareness. Shared announcement with Alaina. (1hr)

2024-03-08 Fri: Created content for Envio announcement for partnership.

2024-03-07 Thu: Transition of direction to research specific data providers for models. High level aim is to verify data quality or quantity to achieve 1-10% voice synthesis model performance. Meeting with Envio to plan next week’s announcements and potential twitter spaces.

2024-03-06 Wed: Deep dive into Bittensor architecture and whitepaper, focusing on data component. Insight: End goal of bittensor is decentralized compute for entire model itself, they have a limit at 32 subnets that each consist of a unique model, not strictly at the data collection optimization layer of the model. 

2024-03-05 Tue: Research leading crypto and AI intersections who appeared at EthDenver. Morpheus, Bittensor, 0g, Near, Semiotic Lab, etc.

2024-03-04 Mon: Multiple longer meetings with Stephen and team for Q2 planning and EthDenver recap. Sync with Artem and Yuriy about Bitcoin and AI narratives. 

---

**1. Harmony Shard 1 Data Optimization:**

Analyze how other blockchains make their data readily accessible, focusing on scalability and cost-reduction strategies. Our goal is to adapt these best practices to Harmony Shard 1, resulting in seamless data access and ultra-fast transactions, supercharging the development of powerful dApps on our platform. Zero knowledge proofs may also be implemented to ensure optimal security and privacy.

**3. Social A(G)I for Better Human Connections:**

A concept that makes sense with the Harmony ethos. Embrace the concept of "Social A(G)I" to guide Harmony's future development. This means understanding users' desire for genuine connection in Web2 or Web3 and integrating tools that facilitate meaningful interactions and community building. The goal is a user experience that enhances human connection rather than detracting from it.

**4.  Babylon + Bitcoin:**

Explore how Babylon can provide Harmony users holding Bitcoin the opportunity to earn Harmony yields while simultaneously bolstering our network security. Let's assess the technical feasibility between Bitcoin's hashrate and Harmony's consensus mechanisms for increased resilience. Staking on Harmony should also get an uprgade, auto-restaking, customized reward collection (i.e. rewards collected could be automated directly to liquidity in a Swap liquidity pool), efficient multi-delegration and undelegation, etc.

**5. 'Build on Bitcoin' Expansion:** 

Conceptualize ways to move beyond simple Bitcoin swaps and create a comprehensive Bitcoin platform on Harmony. Think Thorchain on steroids. We should aim for a robust suite of DeFi protocols or portfolio management services, positioning Harmony as a leader in Bitcoin innovation.

**2. cookbook.dev post EthDenver Launch:**

Partner with cookbook.dev to connect their AI-powered documentation platform to Harmony. Pilot this integration within their beta program to gather developer feedback and showcase the benefits to a wider audience. This will make building on Harmony easier, attracting more talent to our ecosystem.

**6. Ecosystem Refinement and User Growth:**

Gather focused feedback from users engaging with Harmony's existing projects to identify pain points and areas for improvement. Prioritize development based on data-driven insights to enhance user experience and satisfaction across the ecosystem. The ultimate goal is to make our existing projects irresistible to a wider audience. (.country, Voice AI, 1Bot, Human Protocol, Swap, Lend, Stacking Dashboard, Explorer, etc.)

---

On-going: One tweet + two replies per day, 365/7 all the time.

---

2024-03-03 Sun: Continued research on post EthDenver initiatives and how we can bring them to Harmony. As well as continuing to improve our current ecosystem. Insight: Lend needs incentivized lending and liquidity, Stacking needs auto-restocking and further rewards customization. (4hr)

2024-03-02 Sat: Updated remote team on changes following EthDenver to continue into Q2.(1hr)

2024-03-01 Fri: Transition into $voice and $map, coordination with Frank to move from h.country onto voice and map data.

2024-02-29 Thu: Event breakdown for team in Denver. Looking into 0g, first modular AI chain, Babylon, bitcoin re-stacking, BoB, build-on-bitcoin EVM.

2024-02-28 Wed: Circle back with Metamask team from EthDenver for Portfolio listing.

2024-02-27 Tue: Flight back from Denver.

2024-02-26 Mon: Extended morning conversations with community members in Denver, covering 2023 products, governance, and ecosystem updates. Participated in conversations with ex-harmony team, side event hackathon for devrel, and evening event at Imperial City.

---

2024-02-25 Sun: Focused on onboarding new projects as well as research into Bitcoin and AI expansion. Partnership with Cookbook.dev for AI smart contract and documentation, free beta. [16hr]

2024-02-24 Sat: First full day in Denver. Onboarding 10+ users to h.country, shared insights with team. [15hr]

2024-02-23 Fri: Travel Day to EthDenver. Mixup with booking, solved with Alaina. Met up with Casey at the buidlathon event.

2024-02-22 Thu: Final sync with Stephen prior to EthDenver, team plan for EthDenver is to push h.country development to showcase and onboard users in Denver.

2024-02-21 Wed: Sync with Yuriy, Artem, and Frank for tasks to implement location updates and most recent UI changes. Implemented front-end only showing the 30 most recent actions and minor copy edits.   2024-02-20 Tue: Completed EthDenver login. 10:30 sync and coordinating front-end logic changes with team.  

2024-02-20 Tue: Completed EthDenver troubleshooting. 10:30 sync, coordinating front-end logic changes with team.

2024-02-19 Mon: Harmony Ecosystem Roundup speaker. Continued Human-Protocol product development. (1hr) Insights for specific UI/UX. Needs: First Hash Page: add wording to tell user what to do, pre-fill links with placeholder names like Twitter and Telegram. We are missing a DRIVE TO ACTION as people use the application and reach the end of the flow they are left wondering “What next?” creating a funnel to a specific use or interaction within or outside of the app will be ideal.  

---

2024-02-18 Sun: Practiced 30-sec walkthrough of Human-Protocol and user flows with outside users. (5hr) Insights: Current flow is heavily dependent on someone looking over their shoulder, without it user is quickly lost. With help the user understands the flow, but when left alone to continue using it there is a drop-off. Resolution: SIMPLIFY. When explained to the user, the core features make sense, but when left alone it is clear the UI/UX needs changes to ease the user through the product.

2024-02-17 Sat: [Brief product requirement document](https://harmonyone.notion.site/Stripped-Down-PRD-for-Human-Protocol-30e7a6aa2fdf4e12a7fd2432969087f7?pvs=4) to show stripped down core functionality of Human-Protocol. (1hr)

2024-02-16 Fri: Detailed authentication, urls, and UI updates for remote team.

2024-02-15 Thu: Hand-off to Artem and Yuriy, completed project outline for team sync following morning meetings. Completed mock for main page with user flow. 

2024-02-14 Wed: Internal team meetings throughout the day.

2024-02-13 Tue: Merge from Julia’s project with Human-Protocol. Color definitions listed as green for verified, blue for self-endorsement, and yellow for other users, giving us a dynamic social profile.

2024-02-12 Mon: Draft for shard 0 consensus down announcement. Detailed Front-end tasks for Franks and Artem.

---

2024-02-11 Sun: Added elements UI, and [pop-up implementation](https://github.com/harmony-one/human-protocol/pull/8). [3hr]

2024-02-10 Sat: Updated Artem on new direction for human-protocol. Green for user self update, Blue for external user update. $ for links, # for interests. OAuth user interface same as interests page. [1hr]

2024-02-09 Fri: Coordinating launch of Lend, meeting with Protofire. Started implementing periodic elements UI for human-protocol.

2024-02-08 Thu: Completed list of 32 logos to be featured on interests page. 

2024-02-07 Wed: Sync with Casey for Lend launch. Pushed front-end changes for interests demo, [logic](https://github.com/harmony-one/human-protocol/pull/2) and [assets](https://github.com/harmony-one/human-protocol/pull/3).

2024-02-06 Tue: Approved PR for Envio gitbooks listing.

2024-02-05 Mon: Coordinating with protofire and casey for lend launch, html GitHub control for .country.

---

2024-02-04 Sun: Preparation for HER 16 [1hr]

2024-02-03 Sat: Research on in-person event products, Cove, Whoa, Bizzabo, BizConnect, HiHello, Blinq. Insight: all revolve around current methods of connecting, I.e. business cards and profiles, burden of building the connection still on user. [2hr]

2024-02-02 Fri: Lottery conclusion and hand-off. Product finalization shift to human-protocol for ethdenver. 

2024-02-01 Thu: Launch of Knights&Peasants lottery. Insights: lottery brought new users to 1bot (source Discord), viable option to expose users to products across the Harmony Ecosystem.

2024-01-31 Wed: Completion of OneScription lottery, sync with Knights&Peasants for lottery process

2024-01-30 Tue: Launch of OneScription lottery. Sync with Frank, Yuriy, Artem for 1bot lottery.

2024-01-29 Mon: Confirmation with OneScription for lottery and matching prize.

--- 

2024-01-28 Sun: Continued review of TheArena and [tippin.me](https://tippin.me/) a platform that allows anyone to tip and receive tips in Bitcoin on twitter posts for potential sofi on Harmony. Coordination for Tuesday and Thursday lotteries with ONES and Knights&Peasants. [2hr]

2024-01-27 Sat: Added documentation for Flip group. [1hr]

2024-01-26 Fri: Completed product requirement document for lottery inscriptions via telegram with 1bot interactions. Reviewed Social Finance applications: TheArena, Tomo, Alpha, and DeSoc.

2024-01-25 Thu: Completion of first Quest, completed sql query for stats. Inscriptions: 957, Wallets: 35, Entries: (Highest = 470, Winning = 104).

2024-01-24 Wed: Launch of first Quest: [Inscription Lottery](https://q.country), monitoring launch and guiding users through process. Started group for Flip.

2024-01-23 Tue: Testing for Inscription Lottery, added [copy for the launch](https://github.com/harmony-one/inscription.demo/commit/6db76eab71f4c7a86d6cf767e669e8415fc5739e).

2024-01-22 Mon: Finalized product requirements document for Minimal Quest Lottery for Yuriy and Artem set to launch Wednesday. 1000 ONE + 100 HOG prize. [Flip thread](https://x.com/theoperisic/status/1749632934154313951?s=20).

---

2024-01-21 Sun: Initial product requirements document for Minimal Quest Lottery for Yuriy and Artem. [2hr]

2024-01-20 Sat: Research and testing for solana inscriptions. Insights: strong nft community from solana is what is carrying inscriptions, some token generations as well but nothing yet in terms of strong utility. Main tool, [LiberPlex](https://www.libreplex.io/) lacking in quality, UI/UX. Main volume from Tensor and MagicEden.  [3hr]

2024-01-19 Fri: Early morning on-call assisting with mint. SQL analytics for onescription mint. Ecosystem lottery implementation discussions. Further inscription plans and personnel allocation for 2024 roadmap tasks.

2024-01-18 Thu: Prototyped pool-based flip architecture for optimized liquidity and decentralization with Julia.  

2024-01-17 Wed: Technical calls with partners. Speaker for [twitter space with Gateway X](https://x.com/GatewayX_one/status/1747825674524704880?s=20).

2024-01-16 Tue: Launch plan and coordination with internal team and external partners. Continued development for [inscription tools](https://hmy-inscription.web.app/) and eventually [i.country](https://i.country).

2024-01-15 Mon: Federal Holiday

---

2024-01-14 Sun: EthDenver content for applications. [1hr]

2024-01-13 Sat: Flip custodians allocation and discussions. [2hr]

2024-01-12 Fri: Released 2024 roadmap and twitter threads.

2024-01-11 Thu: Completed Roadmap 2024, ready for substack release. 

2024-01-10 Wed: Completed successful OneBitFlip proof-of-concept with Julia. Inscribed x.1 and 1.country. Reached out to potential Flip custodians. iOS Safe Multisig development underway.

2024-01-09 Tue: Ran Tuesday Dev call, sync for prioritization, native USDC (Base) and ONE (Harmony) swap or “flip” as it contains no smart contract signing or bridging will be the first release. Completed a draft of 2024 announcement and site copy for USDC/ONE flip. Coded template for 1bot landing page, helped Alaina with walkthrough guide.

2024-01-08 Mon: Roadmapping and interview session with Stephen. Participated in HER space #13.

2024-01-07 Sun: Added metablox to Dapp Overview. Deep dive for Thorchain and Chainflip. Insight: Still early for chainflip, but JIT AMM (Just-in-time automated market maker) currently has the edge on the technical side for capital efficiency. Thorchain currently has millions more in liquidity and volume, chainflip is only just starting having released [pre-release swaps](https://x.com/Chainflip/status/1736796878807683141?s=20) 2 weeks ago ($1k USD single swap limit). Heavy fee hit on BTC, best for larger swaps. [4hr]

2024-01-06 Sat: Updated dapp overview, curated list of active validators, sync with knights&peasants for giveaway. Reviewed delphi digital "year in review" reports. [4hr]

2024-01-05 Fri: Synced with Casey for recovery and lend. Coordinated with custodians for [Round 15](https://x.com/recoveryonefdn/status/1743515190463791354?s=20).

2024-01-04 Thu: Granted access to gnosis group, awaiting response for official integration update. No respponse from Dune, current best option is [data request](https://feedback.dune.com/data-request/p/add-support-for-harmony-protocol).

2024-01-03 Wed: Reached out for Dune listing on [data request form](https://feedback.dune.com/data-request/p/add-support-for-harmony-protocol), discord, and support email. AAG admins figuring out bridge tvl inquiry. Waiting on gnosis contact for official listing. Continued Dapp overview updates and project outreach.

2024-01-02 Tue: Added Knights & Peasants to dapp overview. Handed-off [CreateX deploy](https://github.com/pcaversaccio/createx) issue to Casey. Continued research on Anoma, key insight: heavy burden on author of intents. Anoma and other "intent-centric" projects depend on either quality intents, or the quality of the handling of those intents. Most immediate valuable use case: [Multi-Party Bartering](https://members.delphidigital.io/reports/wtf-is-anoma-part-1-wtf-are-intents#intents-arent-just-limit-orders-e458). 

2024-01-01 Mon: Reviewed Galaxii and updated dapp overview. More testing of uniswap x, centralization risk with more than 70% of fill orders coming from Wintermute or Tokka Labs.

2023-12-31 Sun: Tested Uniswap X. Key insights: Best suited for high liquidity swaps. Most swaps under $10k do not benefit from the gas-free transactions. Uniswap X routing favors trading pairs with significant volume and liquidity. Maximum Extractable Value [(MEV) protection](https://coinmarketcap.com/academy/glossary/front-running) through their [Dutch Limit Order Reactor](https://harmonyone.notion.site/Uniswap-X-2ebfe67b5ccc4c44a7b704f1376c457e?pvs=4), combined with "[fillers](https://docs.uniswap.org/contracts/uniswapx/guides/createfiller)" covering the gas fee, makes Uniswap X optimal for general, high-liquidity swapping and less effective for MEV traders. [2hr]

2023-12-30 Sat: Tested Multibit bridge, bridged $MUBI (ERC-20) very clean UI/UX and smooth transfer. Unknown technicals and poses a risk. Also, 0.03 ETH service fee is quite high. [2hr]

2023-12-29 Fri: Joined telegram groups and conducted market research for [MultiBit](https://multibit.exchange/) and [Ordizk](https://ordizk.io/) for BRC-20 to EVM bridges, will test over the weekend. Initial thoughts: both look promising in what they say they can deliver but their telegram groups, lack of public repos, and lack of technical information is worrisome.

2023-12-28 Thu: Completed initial [Harmony Dapp Overview](https://harmonyone.notion.site/Harmony-Dapp-Overview-fc7a6a82e65540278d3e2951e0262398?pvs=4), drafting tweet to share with community. Used phantom wallet to test and research top wallets, will move to open source to see if anything is comparable.

2023-12-27 Wed: Started initial [Harmony Dapp Overview](https://harmonyone.notion.site/Harmony-Dapp-Overview-fc7a6a82e65540278d3e2951e0262398?pvs=4), will continue to add more tomorrow. 

2023-12-26 Tue: Spoke with Eugene from marscolony about nft marketplace following nftkey's dissolution. Completed review of Avalanche specific inscriptions "avascriptions" compared to the greater space. Still not seeing much in the inscription ultility department but more may come later. Today, 3.4m transactions came solely from an inscription token called "ShenLong" with a 1 mint token limit per transaction. Wary of connecting directly to avascriptions.com but minting directly should be much safer by design of inscriptions (no smart contract signatores needed).

2023-12-25 Mon: Christmas

---

2023-12-24 Sun: Researched different Ordinals projects, joined a free mint for [bitblocks](https://twitter.com/billyrestey) from twitter user "billy". DeFi wave for bitcoin that may follow the memes and brc-20 craze will be interesting to watch. Phantom and other dapps/wallets as well as exchanges like [OKX](https://www.okx.com/web3/hot/inscription) are preparring themselves well for an increase in bitcoin adoption. [2hr]

2023-12-23 Sat: Joined Ethereum, Polygon, Degen, AI, and Arbitrum channels on warpcast. Ethereum has the largest community out of all of them by quite some margin (16k members, closest is AI with ~4k). Insight for today: Quility UI/UX posts explaining the need for simplicity in the web3 space, more is not always better. [1hr]

2023-12-22 Fri: Joined warpcast. Read through inscription posts as well. Warpcast community still wondering about the utility for inscriptions outside of bitcoin. Room for more inscription use cases on evm chains, must be more than memetic oriented for sustained adoption.

2023-12-21 Thu: Posted instcriptions guide on [X](https://x.com/theoperisic/status/1737359794963677462?s=20). Completed NFT [analysis between Moonbirdgs and PudgeyPenguins](https://harmonyone.notion.site/Pudgy-Penguins-vs-MoonBirds-1c8f2ec1bcf5436e83cbf9b4526e56e0?pvs=4), interesting proof of concept that shows "community > product" in web3 business models.

2023-12-20 Wed: Looked over Casey's announcement forum post. Spent today at investors lunch with Stephen. Interesting insights in gamefi coming soon and early alpha on first playstation web3 game. Intersection of crypto and AI still a valuable opportunity. 

2023-12-19 Tue: Continued work with Inscriptions. Completed [image inscriptions guide](https://harmonyone.notion.site/Harmony-Inscription-Process-e3e43a20835c4a3b88cb5d8f22f9b784?pvs=4). Successful inscription using CLI on Sun’s build, waiting for pull request merge for main build.

2023-12-18 Mon: Experimenting with inscriptions on Harmony. Created an [image inscription](https://explorer.harmony.one/tx/0xba7fa5573ad86a69fb980c228d7297c361e3b99b5f56a6ec8ae328aa0f299d89) using metamask and text based json as well. Completed [general analysis](https://harmonyone.notion.site/Inscriptions-f16f5cb08c054cc688ace7673698a4a1?pvs=4) of non-bitcoin inscription projects.

---

2023-12-17 Sun: Catching up on messages and team updates, will continue on Monday. Reached out to metamask contact for metamask portfolio listing. [1hr]

2023-12-16 Sat: Showcased Voice AI app for group of 10, insights: I downloaded most recent version of the app and without internal context I found it to be very confusing to navigate and showcase to people. The app has also taken a turn to becoming overcomplicated. Current structure is a generalized application of openai’s gpt 4 that allows a single app to satisfy many different use cases, an alternative approach may be to highly specialize the app for a single use case. [2hr]

2023-12-11 Mon - 2023-12-15 Fri: Paid time off

---

2023-12-10 Sun: General Harmony overview and communications with the community. [1hr]

2023-12-09 Sat: App testing, insight: noticed I most frequently use the app for a quick inquiry about a fact or interesting information that is lacking in a moment or a conversation. Using the additional feature of “Surprise Me!” far less. [2hr]

2023-12-08 Fri: v1.1208.18 (Updated transcript logs) Mapped full perceived latency benchmarks using [Aaron’s docs](https://github.com/harmony-one/x/blob/main/doc/benchmarking.md), synced with Yuriy for implementation.

2023-12-07 Thu: v1.1207.18 (TimeLogger improvements) Detailed potential focus split for 2024 project roadmap.

2023-12-06 Wed: v1.1206.18 (10MB limit for sharing transcription, “Pause/Play” font alignment and icons update). Updated quickfacts custom instruction [#322](https://github.com/harmony-one/x/pull/322). Reviewed Sudoswap amm nft platform. [Tweeted](https://x.com/harmonyprotocol/status/1732482500482789880?s=20) weekly protocol updates. 

2023-12-05 Tue: v1.1205.18 (Improved haptic feedback for “Press & Hold”). Worked with Alaina for the social media videos.

2023-12-04 Mon: v1.1204.18 (iPhone 15 Action Button support for "Surprise Me!", check implemented for empty "Surprise Me!" result). Completed new x code review.

---

2023-12-03 Sun: Extensive review of x codebase. [6hr]

2023-12-02 Sat: General app testing of latest version. Key insight: "Hey" loses personalization of the app that might draw user back in. Suggested implementation: Additional to "System Settings" or "Custom Instructions", "User Profile" where the user describes themselves and it is added to the context. [1hr]

2023-12-01 Fri: Deployed 1.1201.18 (Updated action sheets, iPad misconfiguration resolved). Created script for finding “[canned responses](https://harmonyone.notion.site/Canned-Responses-08c2a748e67b4da0bf8c05c817c17911?pvs=4)” throughout codebase. 

2023-11-30 Thu: Deployed 1.1130.18 (Context increase 500 -> 8000, Language support now 183). Continued testing smaller models, Mistral and Llama 7b via Ollama. Insights: Llama 7b more verbose but unreliable. Mistral much more consistent at following instructions and fast outputs. GPT-3.5 still the clear winner, but for on-device efficiency and cost optimization, Mistral seems best suited.

2023-11-29 Wed: Deployed 1.1129.18, key change: In-App purchase backend handling improvements. Started [testing Mistral 7b](https://harmonyone.notion.site/Mistral-7b-Testing-4c0512d7106b41ed8321204268d79eb4?pvs=4) locally for upcoming complete on-device build for latency optimization and improved availability. 

2023-11-28 Tue: Deployed 1.1128.18 to TestFlight build, key changes: (Sun) fixed expiration update [bug](https://github.com/harmony-one/x/commit/51c175aaa66b0e460e555d39972b74db1254732a) and (Yuriy) added refactoring [optimization](https://github.com/harmony-one/x/pull/277). Completed set of [3 predefined custom instructions](https://harmonyone.notion.site/3-Predefined-Custom-Instructions-b36546c4ee544aea8168c7f046c476c5?pvs=4).

2023-11-27 Mon: Deployed 1.1127.18 to TestFlight build. Created [Voice AI demo questions](https://harmonyone.notion.site/Voice-AI-Demo-Questions-276e9075c0904d4997c6645557d1b10b?pvs=4) and engineered prompts to output various examples.

---

2023-11-26 Sun: Worked with OpenAIs Assistants API, useful for incorporating our own information, Harmony specific, as well as performing tasks like sending a message or interacting with zappier. Insight: pricing is way too high for the lack of consistency of outputs. Focusing on mastering the quickest smart companion seems to be the best direction at the moment. Potential pivot to smaller LLM to distance from openai and fine tune for use cases specific to a low latency companion needs addressing based on pricing, speed, and dependency on openai. [4hr]

2023-11-25 Sat: Used the app and thought of different ways to increase user retention. Insight: Hand hold the user to a specific app interaction through a specific button. (Daily Trivia, Cooking Assistant, or Quick Ideation) these use cases must highlight the low latency capabilities of the app as this is the main value proposition at the moment. [1hr]

2023-11-24 Fri: Following discussions, drafted simple [gamification elements](https://harmonyone.notion.site/Gamification-for-Voice-AI-3ff4489eb71a42649073e2806a2f939c?pvs=4) and options to improve [user retention](https://harmonyone.notion.site/Improving-User-Retention-2f6b2f3c2c47466b82e93f0b92916e79?pvs=4) as active users has dropped significantly.

2023-11-23 Thu: Thanksgiving, user testing for voice ai app with 20 people. App insight: (12) people were impressed with the speed, (17) don’t like the voice, (11) mentioned they would use it in the kitchen if there was a hands-free mode.

2023-11-22 Wed: Deployed 1.1122.18 to TestFlight build. App insight: current app structure is too broad for user retention, internal users are the only users coming back.

2023-11-21 Tue: Deployed 1.1121.18 to Voice 2 build. Added [Thanksgiving marketing copy](https://harmonyone.notion.site/Thanksgiving-Marketing-Campaign-f4e2ff42dd7e4c78946722e4b64244f2?pvs=4) to Alaina’s graphic. Tested processing logic for [Harmony specific information](https://harmonyone.notion.site/HarmonyGPT-b517a68bce564ac68cebd378b5d420e2?pvs=4) without the need of memory.

2023-11-20 Mon: Deployed 1.1120.18 public TestFlight build. Created and added full [Terms](https://x.country/terms), Privacy, and Copyright for Apple Pay build.

---

2023-11-19 Sun: Completed potential [Thanksgiving marketing campaign](https://harmonyone.notion.site/Thanksgiving-Marketing-Campaign-f4e2ff42dd7e4c78946722e4b64244f2?pvs=4). [1hr]

2023-11-18 Sat: Added and tested [6 scenarios](https://harmonyone.notion.site/AI-Driven-Conversation-d04d358c14ad42d68f35d4799314a838?pvs=4) for AI-driven conversations. [3hr]

2023-11-17 Fri: We deployed 1.1117.18 public TestFlight build. Completed and tested first draft of [AI-Driven Conversations](https://harmonyone.notion.site/AI-Driven-Conversation-d04d358c14ad42d68f35d4799314a838?pvs=4).

2023-11-16 Thu: Added to OpenAI [review](https://harmonyone.notion.site/OpenAI-Implementation-Review-3a44d85cce504066a8fed5690bbc56ef?pvs=4). Helped Sun with custom instruction issues, documented changes [here](https://harmonyone.notion.site/Custom-Instruction-Framework-a61592bd8937490f9e85d527879d9e20?pvs=4).

2023-11-15 Wed: Completed Harmony quiz [demo](https://harmonyone.notion.site/Harmony-Quiz-Exmaple-75a999245f544662906d09ad2838c820?pvs=4). Started [OpenAI implementation review](https://harmonyone.notion.site/OpenAI-Implementation-Review-3a44d85cce504066a8fed5690bbc56ef?pvs=4).

2023-11-14 Tue: Completed Fenwick [Terms](https://harmonyone.notion.site/Terms-33e7f545c9d7407e88201fca0fa5ace3?pvs=4) & sent back Privacy for edits. Also reviewed other [AI premium app](https://harmonyone.notion.site/Competitor-Analysis-2caebf2a984b485db56e53df08a206bd?pvs=4) payment, insight: subscription plans for 1 week and 1 year are the most common payment schedules offered. 

2023-11-13 Mon: User testing for chunking issue with sun, found Apple's text-to-speech as the cause for the unnatural pausing. Reviewed Fenwick Terms update.

---

2023-11-12 Sun: Reviewed Fenwick Terms of Service, sent comments back for changes. [1hr]

2023-11-11 Sat: Continued testing Voice AI, currently heavy burden on user to get value out of usage. [2hr]

2023-11-10 Fri: Completed an initial release usage and [feedback table](https://harmonyone.notion.site/Initial-Release-Usage-and-Feedback-661d427191534b6f9a58e950685e1242?pvs=4) to focus on main blockers to “30 people 30 minutes” goal.

2023-11-09 Thu: Following App Store launch, completed [in-app growth strategies](https://harmonyone.notion.site/App-Growth-Brainstorm-5a776417f42d4c38923bf541a79df413?pvs=4). Continued [app testing](https://harmonyone.notion.site/App-Store-Release-Testing-f4c1cc052fc84d999a6ddd8e218fb27a?pvs=4). 

2023-11-08 Wed: Completed [Product Marketing Strategy](https://harmonyone.notion.site/Voice-AI-Marketing-Product-Strategy-7034a6c564124d23be4f061def94eaff?pvs=4) draft and added [custom instructions](https://harmonyone.notion.site/Custom-Instructions-2-Voice-AI-a14b176b252d4c539f7635c8777c5ece?pvs=4) optimized for user experience. Started competitor analysis page using MobileAction to track App Store Optimization.

2023-11-07 Tue: Completed [v0.9.4 Bug Report](https://harmonyone.notion.site/Bugs-for-v0-9-4-ab3601fe24c5451cb38c4891d82e2c2b?pvs=4) and continued testing v0.9.5 and v0.9.6 builds. Tested OpenAI’s speech api for voice quality and latency during chunk transfer encoding.

2023-11-06 Mon: Completed [Privacy Policy](https://github.com/harmony-one/x/blob/main/doc/privacy.md) for free and non-tracking build. Meeting with Fenwick for Privacy and Terms for Voice AI, shared required materials with team, full documents ready by end of week. Completed a brief [list of alternatives](https://harmonyone.notion.site/Alternatives-for-Skip-5-seconds-Random-Fact-504a80795e1e4484a086c5620ceeb5ad?pvs=4) for “Skip 5 Seconds” and “Random Fact”.

---

2023-11-05 Sun: Started brainstorming alternatives for "Skip 5 seconds" and "Random Fact" will create a notion on Monday. [1hr]

2023-11-04 Sat: Conducted tests on the Voice AI app and demonstrated its functionalities to family members. [1hr]

2023-11-03 Fri: Completed [ideation for improving latency](https://www.notion.so/harmonyone/Ideas-For-Latency-Optimization-7073ab27465146a4a211c7bc1819c7e2) sourcing from y-combinator, twitter, and github repos.

2023-11-02 Thu: Continued product testing for Voice AI with a focus on use cases.

2023-11-01 Wed: Completed [Demo Day suggestions](https://www.notion.so/harmonyone/Demo-Day-Suggestions-8af0f34a47694229b723bc9b33feadbc) for Voice AI. Reached out to Fenwick for terms and privacy. Completed [user study](https://www.notion.so/harmonyone/User-Study-Notes-3adef05e7ad64521bc40dd88e657a7ad) for Voice AI.

---

2023-10-28 Sat to 2023-10-31: Out with injury 

2023-10-27 Fri: Started development log for version increments [here](https://www.notion.so/harmonyone/Kanban-2aff109a6221488081bb99c0d2470d91?p=810178d623804820a8d3b3483a6e6ada&pm=s). Collecting Voice AI internal feedback with Theo.

2023-10-26 Thu: Provided the [updated custom instructions](https://harmonyone.notion.site/Custom-Instructions-2e3ff8d9e9254c039e2d253ad18ec6a1?pvs=4) for Sun to implement in the current Voice AI build. Helped debug [Press Speak recognition issue](https://github.com/harmony-one/x/blob/main/voice/mobile/x/SpeechRecognition/SpeechRecognition.swift) with Sun. Verified Theo’s [pricing excel doc](https://docs.google.com/spreadsheets/d/1s_QkGFYi07__PxPGLIUeIrAB_ZyONa2iq9kpWhF-M-0/edit#gid=0) and updated the [Cost Analysis](https://harmonyone.notion.site/Cost-Analysis-97cd614180164d71a398131a0df545bd?pvs=4) to include end-to-end pricing. Completed a [shortcut guide](https://harmonyone.notion.site/OpenAI-Voice-App-Shortcut-4bb2f7d253854d2a80a1a0cd2de5fb0d?pvs=4) for OpenAI Voice. Found [OpenAI Voice’s default instructions](https://harmonyone.notion.site/OpenAI-Voice-Custom-Instruction-2023-10-26-55789321d05048eeb45a1e245c111f2d?pvs=4) using custom prompt.

2023-10-25 Wed: Started collecting [in-office feedback](https://harmonyone.notion.site/OpenAI-ChatGPT-Voice-Feedback-b92ec110c57548ff93b99d6227103011?pvs=4) for OpenAI ChatGPT voice mode. Went over [marketing strategy and copy](https://voiceai.substack.com/p/voice-ai-talk-with-chatgpt4-on-apple) with Stephen for Voice AI. Continued testing golden paths and added instructions for [interactive storytelling](https://harmonyone.notion.site/Custom-Instructions-2e3ff8d9e9254c039e2d253ad18ec6a1?pvs=4).

2023-10-24 Tue: Added more promotion options to the [Cost Analysis](https://harmonyone.notion.site/Cost-Analysis-97cd614180164d71a398131a0df545bd?pvs=4) including the 5 minute usage with 10 minute break and 10 sessions per day restrictions. Added and tested 6 new model personas through [custom instructions](https://www.notion.so/harmonyone/Custom-Instructions-2e3ff8d9e9254c039e2d253ad18ec6a1).

2023-10-23 Mon: Started the [Cost Analysis](https://harmonyone.notion.site/Cost-Analysis-97cd614180164d71a398131a0df545bd?pvs=4) to see the monthly cost for us to allow different amounts of free Generative Pre-trained Transformer 4 usage. Iterated on the [App Store Copy](https://harmonyone.notion.site/Voice-AI-Talk-with-ChatGPT4-on-Apple-App-Store-a3dcb50d30654c508779b123d278546f?pvs=4) that will be used for the application process.

---

2023-10-22 Sun: Product testing for Chatgpt, Hey Sam, and [Play.ht's new 2.0 launch](https://www.ycombinator.com/companies/playht).

2023-10-21 Sat: Coordinated with Aaron for App Manager access for Hey Sam. Added character lengths for each section and useful links for the [application process](https://harmonyone.notion.site/App-Store-Project-Intro-Product-Details-Screen-Mocks-a3dcb50d30654c508779b123d278546f?pvs=4).

2023-10-20 Fri: Started information compilation for [App Store application process here](https://harmonyone.notion.site/App-Store-Project-Intro-Product-Details-Screen-Mocks-a3dcb50d30654c508779b123d278546f?pvs=4). Wrote [first draft](https://harmonyone.notion.site/App-Store-Description-DRAFT-b56cd5582a134ba192de1fd09cc239c2?pvs=4) of App Store description for “Hey Sam”.  Deep dive with Labhesh on Replika and which knowledge models are best to use for getting past OpenAI guardrails. Mistral and Falcon 7b are potential starting points. Additional concerns with opening doors that we should not be opened was mentioned.

2023-10-19 Thu: Tested Replika, Chatgpt, and Hey Sam. Added to [custom instructions on stephen’s mode](https://harmonyone.notion.site/Stephen-s-Mode-Custom-Instruction-Tuning-70cf17adb61b464abcb97c7f2e735fb8?pvs=4). Started [A/B tests to optimize instructions](https://harmonyone.notion.site/A-B-Testing-for-Custom-Instructions-127fafe300e248c3926a5301157767a8?pvs=4) to make them as concise as possible. 

2023-10-18 Wed: Completed [Apple On-Device Text-To-Speech Comparison](https://harmonyone.notion.site/iOS-On-Device-TTS-Comparison-7381449ec466410fb7097244693369c6?pvs=4) for Julia’s demo. Shared benchmark testing optimization with Sun to include Text-T0-Speech synthesis when the first audio buffer is played rather than waiting for the entire Text-To-Speech to finish. Continued with custom instruction [tuning for Stephen’s mode here](https://harmonyone.notion.site/Stephen-s-Mode-Custom-Instruction-Tuning-70cf17adb61b464abcb97c7f2e735fb8?pvs=4).

2023-10-17 Tue: Moved from external to [internal testing](https://harmonyone.notion.site/Internal-Product-Testing-c03602929dda45c79cf232743301bf4b?pvs=4). Completed first round of [custom instructions for 3 different builds](https://harmonyone.notion.site/Custom-Instructions-2e3ff8d9e9254c039e2d253ad18ec6a1?pvs=4): Concise, Commute, and Funny.

2023-10-16 Mon: Further [custom instruction tuning](https://harmonyone.notion.site/Custom-Instructions-Tuning-2513b72b8524415eb8ec23f13f7bb8dc?pvs=4) in order to produce a concise conversation flow. Started ElevenLabs API [latency testing](https://harmonyone.notion.site/ElevenLabs-Latency-Testing-f6c24bd7a88e4a718b191fd42f36e625?pvs=4), but stopped per /daily Sun and Ivan will compute. Added [Caryn.ai](caryn.ai) to the Voice 2 Voice [comparison page](https://harmonyone.notion.site/Voice2Voice-App-Comparison-0da03ff1a7154802bfbb1e3230e96bb4?pvs=4). Built small [AI GF webapp](https://github.com/harmony-one/x/blob/main/elevenlabs-test/app.py) to test Elevenlabs API's "optimize streaming latency" and "stability" query parameters on voice output.

---

2023-10-13 Fri: Started testing [custom instructions tuning](https://harmonyone.notion.site/Custom-Instructions-Tuning-2513b72b8524415eb8ec23f13f7bb8dc?pvs=4) for GPT-4 voice on ChatGPT mobile app.

2023-10-12 Thu: Completed [Initial Comparison for Voice Apps](https://harmonyone.notion.site/AI-Voice2Voice-App-Comparison-0da03ff1a7154802bfbb1e3230e96bb4?pvs=4) (Device: Iphone 12 Pro)

---


https://www.linkedin.com/in/theoperisic/
https://twitter.com/theoperisic
