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
