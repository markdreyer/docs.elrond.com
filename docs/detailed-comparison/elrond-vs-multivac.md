---
id: elrond-vs-multivac
title: Elrond vs. Multivac
---

One of the main differences between Elrond and Multivac, is how Multivac manages cross shard operations, there is a larger overhead in communication compared to the Elrond architecture, as it is required to broadcast all shard headers to all shards. This also makes the processing harder for any shard and every node. If a node wants to validate a given header from another shard, it needs the relevant data from that shard. Whereas Elrond has the metachain shard aggregating this information and broadcasting only the aggregation, which leads to less communication.

Multivac employs an UTXO model, while Elrond uses an account model. Multivac seems to not even mention about shard merges, which in fact is harder to solve than shard splits, Elrond already has a solution designed for this. For consensus group sampling Multivac employs VRFs, which would lead to slower consensus, because forming the groups will be harder.

Multivac mentions that they are doing resharding - which actually means reshuffling of miners among shards, and in best case the described process includes some liveness penalties, due to communication involved between new miners and old storage nodes when synchronizing the state.

Elrond is also doing validators reshuffling between shards of up to 1/3 of validators but this is buffered, so it doesn’t incur any liveness issues. Because there is no shard merging, a malicious group could do some discouragement attack, making honest nodes leave a certain shard. By doing this, they will become a majority in that shard and could do any type of transactions. Elrond solves the shard takeover attack by nodes shuffling, shard merges when the number of nodes decreases under the security threshold, and with a "fisherman challenge" where any honest node from the shard could raise a challenge against a bad block.
