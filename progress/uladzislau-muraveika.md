2024-08-16: On the protocol side, as result of previous week work, I've pointed Konstantin work to the harmony-test repo with [go1.22 branch](https://github.com/harmony-one/harmony/pull/4736).

On the infra side: I've set up STORJ snapshots for the shard 1 archival node, it wouldn't sky-rocket our costs(only 6$ per 3 month 120 GB), but give us a reliable shared backup feature. Previously, we had a problem with db corruption on the RPC node, this will mitigate consequences for such scenarios.

Additionally, I'm currently checking the issue with the beacon stuck, that we have from time to time in all our chains.

And finally, there were infra incidents on Wednesday like SnapDB server outage, testnet validators fork, and outages our infra providers which I've fixed.

---

2024-08-12: Small 1 day PTE

---

2024-08-09: On the protocol side, I finished testing the golang version update, discussed results and asked for help from the team - [link](https://github.com/harmony-one/harmony/pull/4722/#discussion_r1702049235).

Additionally,  I've improved our continuous integration for the main repo after discussion with Konstantin about the current setup. It was a problem with hardcoded branches to the `harmony-test` repo, which leads to extra work if you change things like the Golang version update. [My solution](https://github.com/harmony-one/harmony/pull/4730) will help protocol devs to have an easier way to run against any `harmony-test` repo version.

Finally, I'm helping a new devops engineer onboard Harmony. I've helped with localnet setup and guided how to use a watchdog tool.

---

2024-08-02: On the infra side, I've faced DOS attacks(>60K requests/second) on our mainnet RPCs resulting in overloaded nodes thus I've rolled out rate-limits to the mainnet to limit such possibilities and help us provide stable service to our users and partners.

On the protocol side, I continue to help with the golang version update, it has been updated to the latest long time support - 1.22. I've done several compatibility tests in mainnet with all possible libp2p variations, results were differ from the results in devnet, and I need to do more testing.

---

2024-07-26: On the infra side, I rolled out automated, tested rate-limits solution and applied it to devnet - which has whitelisting functionality based on IPv4 CIDR masks, log rate-limited users in a separate log, have a dashboard with a current state of Nginx. We already have excessive rate-limited users in the devnet. Next steps will be to collect our partner IPv4s, whitelist them and only apply this solution to testnet and mainnet.

On the protocol side, I've fixed release CI to have same code version as we have run in CI, previously it was hardcoded `main` branch. Advantage will be the great user experience from our docker image users. [Details](https://github.com/harmony-one/harmony/pull/4716)

Also I've helped Konstantin with the harmony/bootnode golang 1.21 node testing. After several initial testing round node was stabilized. Also We've tested all 6 possible computability cases - (old 1.19 /new 1.21 harmony node vs old 1.19 /new 1.21 bootnode) and of them were passed in the devnet. Waiting for the full devnet/testnet testing, but, probably, 1.21 version will be the following after HIP32 release.

---

2024-07-19: My current week focus was the fixes for ongoing issues and small improvements. There were several topics from the infrastructure side.
Automatic SSL renewal on our internal Grafana, benefit - we wouldn't be doing it manually. Removal of old in-house Explorer infra, benefit - eliminate double spending on infra costs.
I've also applied rate limits on the devnet and load tested how nginx will work under the load, advantage - mitigate load spikes on the RPC endpoints.
And one item, after complaints from on-call engineers, I've added a separate disk usage alarm with a higher threshold for our archival and snapshot nodes, this reduced our monitoring noise.
On the protocol side, I've helped Konstantin with the rollout of the golang 1.21 node to the devnet. It will help us to understand network behavior after the golang and libp2p update.

---

2024-07-12: First of all, I've done migration of the staking backend, thanks to the automation ansible playbook and initial testing end-users haven't faced any downtime. Old expensive infra setup was removed - 88% costs saved. The main focus during this week was the localnet watchdog setup. I've changed both the frontend and backend code to support it. Main advantage - now our protocol dev team now can have full network observability on the localnet via 2 `make` commands.

Finally, I've started preparation for the old explorer infra removal to save money on infra costs.

---

2024-07-05: The main focus during this week is automation for staking backend and new cheaper server setup, now it is in final testing phase. Justification is simple - save money on the traffic and server.

On the security side, I was alarmed team about [RegreSSHion vulnerability in the OpenSSH](https://blog.qualys.com/vulnerabilities-threat-research/2024/07/01/regresshion-remote-unauthenticated-code-execution-vulnerability-in-openssh-server) and helped Soph with infrastructure checks and fixes.

On the community side, I've created and tested new 100 GB SnapDB snapshot, share it with validator community, collected the feedback about the suitable size. This will help our validator community to have predictable snapshot size and timing when the SnapDB snapshot should be created.

Additionally, I was working on the archival RPC 1 node recreation, I've used server with faster NVMe SSD disk, it helped to recreate the RPC in matter of 4 days instead of 3-4 weeks.

---

2024-06-28: The main focus during this week was the removal of the old Tesntet explorer. Result have only one Blockscout explorer and don't pay for the old one. As extra point - it was a great training for the further mainnet explorer removal.

On the protocol side, I've rapidly fixed problems with Travis CI, base image was changed by the Travis. And as consequence this unblocked developers CI builds on the dev branch.

On the community side, I'm creating a fresh SnapDB snapshot which will use around 50 GB instead of 550 GB and help validators to spend less on the storage.

And finally, I'm working on the staking backend migration to the cheaper server. It will save us around 88% on costs.

---

2024-06-21: The main focus during this week was the testnet snapshot service automation and now we have here the mainnet-like disaster recovery approach -  hot copy for the community and extra copies in the STORJ. It will help our community to spin up nodes in matter of 20 minutes instead of 3 days with sync from Genesis.

Additionally, I've standardized the testnet environment - all Harmony managed external validators are managed and monitored from one place now. This action will save our time on the future network support.

And finally, I've done small cleanup of unused test servers. Aftermath - saved money.

---

2024-05-30 to 2024-06-16: Paid Time Off

---

2024-05-29: During 3 days on this week, I found the way how to rate limit users via nginx, with whitelisting feature for our partners. It will helps us to provide stable service for our regular users and mitigate abuse of our nodes.

On the protocol side, I've helped with devnet update to the DNS sync, it will help to rule out a possible streamsync bug.

---

2024-05-24: During this week, I finished Nginx monitoring, now we have a generic solution and the [Grafana dashboard](https://grafana.i.hmny.io/d/ZQAsi-Xiz/nginx-vts) for all networks. It is already give ideas what can be improved, such as removing defaults and deploying proper rate limiting

On the protocol side, I've helped with devnet updates to the latest version with fixed bootnode issue and share my ideas and concerns about further mainnet rollout with Gheis and Soph.

Additionally, I aided a community member with the removal from blacklists.

---

2024-05-17: During this week, I tried different approaches for Nginx monitoring, found the most generic one, and started to roll it out to the devnet. It will help the team understand the current state of our RPC endpoints and how users are using them

On the protocol side, I conducted an initial investigation into the bootnode issue and shared all the information, including Quic protocol usage, incoming IPs, and libp2p troubleshooting manuals, which helped Gheis and Soph with the fix. Additionally, I assisted in spinning up an AWS instance for the bootnode test.

I helped validator users with testnet validator sync issues, which is crucial for the network usage.

---

2024-05-10 Friday: The main focuses on this week(9th of May was a holiday):
* nginx-module-vts -> Prometheus -> Grafana monitoring tool set:
  * created a dashboard in Grafana to show the load state on Nginx
  * created a playbook for the nginx custom build with nginx-module-vts included
* as part of on-call:
  * helped with bootnodes load problem mitigation - enabled logrotate(zip/remove) to run daily against excessive logging
  * keep devnet stabilized through the week - time to time we lost consensus
  * watchdog - updated user-list
  * watchdog - moved threshold for the beacon chain monitoring to the config and updated it to the higher value

---

2024-05-03 Friday: The main focuses on this week:
* snapshot node migration - old one used 100% disk space from 7TB:
  * we created new one with increased 14TB disk space
  * fully setup
  * sync up with network
  * configure automatic snapshots
  * tested against user traffic
  * removed old one
* helped with mitigation of increased load on our bootnodes, together with Kontastantin enabled pprof on nodes, it will help us to understand the root cause of issue
* nginx-module-vts -> Prometheus -> Grafana monitoring tool set:
  * haven't touched it due to load
* as part of on-call:
  * fixed 2 issues in watchdog
    * beacon epoch monitoring - increased previous threshold to 120 seconds
    * fixed devnet test nodes parsing

---

2024-04-26 Friday: The main focuses on this week:
* removed Binance dedicated RPC node after double confirmation.
* added additional Layer Zero monitoring alarm for total transactions absence
* renewed SSL on all mainnet RPC servers, previously created automation for this task works good.
* nginx-module-vts -> Prometheus -> Grafana monitoring tool set:
  * created POC for the devnet RPC instance
  * haven't spent a lot of time due to load
* as part of on-call:
  * Testnet RPC server has issues with the filesystem - decided to switch to the backup node, contacted provider support.
  * Helped to fix problems with watchdog monitoring on the devnet, root cause was in the stopped RPC

---

2024-04-18 Thursday: The main focuses after 1 week vacation:
* I was focused on the Nginx rate-limiting solution and my main concern was how to properly monitor it.
* I've done a research on the possible solutions and stopped on the following tool set:
  *  [nginx-module-vts](https://github.com/vozlt/nginx-module-vts) -> Prometheus -> Grafana
* And on Thursday I've shown the my research to Soph, gotten feedback and started actual implementation

---

2024-04-05 Friday: The main focuses on this week:
* finished setup of two snapshot nodes for the shard 0 and shard 1 in the testnet, users are already using them
* aware team about fresh xz vulnerability - we are safe
* added one more user to the blacklist, user used multiple addresses to burn more than 800K ONE
* added Push-gateway runbook and updated nginx/image to the latest stable
* double checked STORJ backup usage drop by 7 TB from February - this one was expected
* fixed false-positive issue with snapshot creation - code haven't wait for harmony RPC service actual start

---

2024-03-29 Friday: This week I have mostly support activities:
* Our cloud provider - Contabo has a network outage which leads to the various issues in the devnet and tesnet. Patiently check nodes one by and back them back to operational one by one.
* Checked an devnet shard 1 issue connected with harmony node's memdb weird behavior - it started to use the whole disk storage, when the node is in discovery phase
* created two snapshot nodes for the shard 0 and shard 1 in the testnet, [it will help Harmony team and external validators to create new nodes in a matter of minutes, instead of 3 days sync](https://github.com/harmony-one/harmony-ops-priv/issues/175)

---

2024-03-22 Friday: The main focuses on this week:
* one more blacklisted address removed
* working external leader validator hardfork HIP32 on the testnet:
  * created an issue for the testnet shard 0 [invalid merkle root](https://github.com/harmony-one/harmony/issues/4650)
  * synced 8 Shard 0 validator via webdav to avoid syncing issue
  * created 16 total external Validators in total - https://staking.harmony.one/validators/testnet/
  * discussed with Diego the date of HIP32 for the testnet - 11:40 PM UTC 25 March 2024
* finished my on-call this week:
  * added more CPU and RAM for Frankfurt bootnode

---

2024-03-15 Friday: The main focuses on this week:
* one more blacklisted address removed
* working external leader validator hardfork HIP32 on the testnet:
  * shard 0 validators weren't able to sync from the genesis => created a workaround with webdav snaphot solution
  * testing on 2 previous and current version validators to find the root cause
  * all other shard 0 validators are synced
  * shard 1 validators are syncing without problems
  * [one validator was created manually as example what to automate](https://staking.harmony.one/validators/testnet/one1neul965gzqs8pksm2nq5e9ejurscxqm2jdgh2q)
  * main effort automation of external validator creation
* doing my on-call this week

---

2024-03-08 Friday: The main focuses on this week:
* two more blacklisted address removed
* Layer zero alert fixed to be less noisy
* working external leader validator hardfork HIP32 - preparing new setup with 9 external validators per each shard

---

2024-03-01 Friday: The main focuses on this week:
* RPC ansible automation - mainnet shard 0 fulldb and archival RPCs covered and now having latest nginx and security features
* [backup node identification](https://github.com/harmony-one/harmony-ops-priv/issues/171) - number of backup nodes is decreased from 30 to 20
* helped two validators with the proper configuration on the node side
* one more blacklisted address removed

---

2024-02-23 Friday: The main focuses on this week:
* fixed playbook for the new  mainnet automation RPC automation for new SSL
* RPC ansible automation - devnet/testnet/mainnet shard 1 RPC finished, shard 0 fulldb and archival RPCs will be done on the following week
* [backup node identification](https://github.com/harmony-one/harmony-ops-priv/issues/171) - 31 validator were identified with websites/emails
* two more address were removed from blacklist
* finished my first on-call - provided few ideas how to make our monitoring less noisy.

---

2024-02-16 Friday: The main focuses on this week:
* main focus - two new full db RPC up and running == save costs
* RPC ansible automation - devnet/testnet covered and still in progress
* one more address removed from blacklist
* [backup node identification](https://github.com/harmony-one/harmony-ops-priv/issues/171) - backup nodes public keys identified, need to match with validator info

---

2024-02-09 Friday: The main focuses on this week:
* placing automation of the PRC config to the Ansible via nginx reverse proxy, with the latest nginx, certbot, SSL practicies - covered simple case with one node, will integrate it with the Geo-distributed RPC solution - [current progress](https://github.com/mur-me/ansible/tree/put_nginx_RPC_config_to_the_code) - faced several problems here - [certbot don't respect systemd daemon](https://github.com/certbot/certbot/issues/5486#issuecomment-1934756252) - mitigated and on-going [issue with nginx main package repo](https://trac.nginx.org/nginx/ticket/2600)
* preparation task for the upcoming hardfork - [backup node identification](https://github.com/harmony-one/harmony-ops-priv/issues/171) - checked how to get the info and how to remove stale data
---

2024-02-02 Friday: The main focuses on this week:
* blacklist automation - build, tested and rolled out to testnet/mainnet fix from https://github.com/harmony-one/harmony/pull/4623, additionally removed three new redeemed addresses from the blacklist.
* [the second phase of RPC replacement](https://github.com/harmony-one/harmony-ops-priv/issues/166) - first try of the sync up was broken by extra run of rclone, after it files were corrupted and harmony had a [file descriptor leakage issue](https://github.com/harmony-one/harmony/issues/4622),after several tests, that it was indeed rclone, node is synced and running. Rn node is used by Gheis to test the prunning DB config.
* continue refactoring to move the rclone installation/sync as separate playbook - https://github.com/harmony-one/harmony-ops-priv/issues/167 - postponed for now
* checked the [small issue with snapshot service](https://github.com/harmony-one/harmony-ops-priv/issues/170) - it was false-positive, 'cause we don't wait for harmony node to start, but issue can be fixed

---

2024-01-26 Friday: The main focuses on this week:
* blacklist automation - created a bash script to automatically get the redeemed users and remove them from blacklist and allowedtx lists - https://github.com/harmony-one/ansible/pull/110
* [the second phase of RPC replacement](https://github.com/harmony-one/harmony-ops-priv/issues/166) - sync new node via rclone and run our tools, firewall, nginx setup - now it is still in sync
* started refactoring to move the rclone installation/sync as separate playbook - https://github.com/harmony-one/harmony-ops-priv/issues/167

---

2024-01-19 Friday: Two main focuses on this week:
* blacklist automation - there were 2 PRs - https://github.com/harmony-one/ansible/pull/101 and https://github.com/harmony-one/ansible/pull/104 for it and right now blacklisted users can only send ONE to themselves to remove old pending transactions and to dead aka burner address. Huge thanks for Soph for knowledge sharing on the topic.
* [new full db RPC server in the Cherry Cloud Provider instead of Hertzner one](https://github.com/harmony-one/harmony-ops-priv/issues/166) - sync new node via rclone and run our tools, firewall, nginx setup, now it is up and running.
* additionally, it was some small support tasks like restoring mainnet/testnet validators

Focus for the next week - continue with RPC + return back to nginx topics

---

2024-01-11 Thursday: I will be on vacation on the 11th of January. For the rest of the week my main focus was rate-limit for the Nginx and improvement of the monitoring stack - cleaned up the old server and added a way to monitor also devnet-test node automatically via watchdog. Links: [1](https://github.com/harmony-one/ansible/pull/98) [2](https://github.com/harmony-one/ansible/pull/99)

Main focus for the Thursday - blacklist automation and I've created a part for the automatic leader [search](https://github.com/harmony-one/ansible/pull/100)

---
2024-01-05 Friday: I was on vacation on the 1st of January. For the rest of the week my main focus was [Harmony faucet automation](https://github.com/harmony-one/harmony-ops-priv/issues/160):
1. I've spined up whole components locally and started to debug, found the root cause of broken faucet issue(wrong parameters on the start up).
2. After getting the app whole picture, I've started to automate its deployment.
3. I've covered all dependencies like:
   * nodejs from nodesource deb official repo
   * pm2 as global package to control node js service and survive restarts
   * nodemon as global package
   * encrypted secrets
   * backend npm build
   * npm fronted build and copy of static
   * latest stable nginx setup via my previously created role - [nginx_service](https://github.com/harmony-one/ansible/tree/master/playbooks/roles/nginx_service)
   * latest stable certbot setup with best SSL practices  via my previously created role - [certbot_binary](https://github.com/harmony-one/ansible/tree/master/playbooks/roles/certbot_binary)
4. As result - faucet is up and running, users were contacted in the discord about the fix and actively using it
5. I've also added uptime robot monitoring for backend and front-end
6. As final step - I've added a faucet runbook to [documentation](https://app.gitbook.com/o/-LiOowK9lXTPyPxhkAcr/s/-LlYow9k894c-0I26uAc/~/changes/1378/devops-run-book/harmony-mainnet-devops-runbook/harmony-faucet-runbook#all-in-one-deploy)

My main focus on the following week will [RPC nginx config automation](https://github.com/harmony-one/harmony-ops-priv/issues/162) and [rate limits for the RPC](https://github.com/harmony-one/harmony-ops-priv/issues/161)

---
