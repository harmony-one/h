2023-11-20 Mon:

---

2023-11-05 Sun: Started the week working on a script that would tell us if we had enough validator voting power with the premiage imported before the account migration epoch start, that was important as that could have brought the shards to a halt if case we didn’t. Was in talks with the validators to make sure they have imported the preimage. 

After the initial account migration, worked with Soph in verifying we had imported the balances correctly and worked on a report that would show the affected address along with their balances before and post epoch HIP30-1  the migration went smoothly and was executed correctly.

After the HIP30 epoch worked in fixing the watchdog and created a PR fixing and edge case identified by Soph where validators with the max-rate set to 5% didn’t get the fee upgrade, the fix will have to be part of a future hardfork.
