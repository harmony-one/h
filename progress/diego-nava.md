---

2023-12-03 Mon: The week kicked off with me migrating two shard 1 validators to a different cloud provider. This move was driven by the need for better cost efficiency and redundancy. I diligently followed the operational checklist, ensuring that monitoring and alerting systems were in place.

Next, I shifted my attention to assisting Adam in setting up a new node for testing state pruning. I cloned the full database and initiated tests. However, we encountered a syncing issue with the node. I took time to address some linting problems in the pull request and had a discussion with Adam about a potential code loss in one of the files during the merge. He agreed to investigate this further.

Towards the week's end, my focus pivoted to researching an issue with the Ethereum JSON RPC, specifically regarding discrepancies in the 'from' field when using the eth_transaction method. I uncovered the root cause: it's related to the method of hash calculation. Armed with this insight, I plan to propose a fix in the coming week.

---

2023-11-05 Sun: Started the week working on a script that would tell us if we had enough validator voting power with the premiage imported before the account migration epoch start, that was important as that could have brought the shards to a halt if case we didn’t. Was in talks with the validators to make sure they have imported the preimage. 

After the initial account migration, worked with Soph in verifying we had imported the balances correctly and worked on a report that would show the affected address along with their balances before and post epoch HIP30-1  the migration went smoothly and was executed correctly.

After the HIP30 epoch worked in fixing the watchdog and created a PR fixing and edge case identified by Soph where validators with the max-rate set to 5% didn’t get the fee upgrade, the fix will have to be part of a future hardfork.
