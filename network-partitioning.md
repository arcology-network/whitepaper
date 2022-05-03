---
id: network-partitioning
title: Network Partitioning
---

## 12 Network Partitioning

Blockchain networks don’t rely on centralized trust. All full-node validators must process all the transactions and store all the data. Though secure, this redundancy can cripple networks as they grow and introduce the following challenges:

-	**Transaction redundancy:** Because all full-node validators must process every transaction, processing power is wasted. Because there’s no economic gain from these superfluous transactions, network costs and fees may increase.
-	**Storage redundancy:** Full nodes must store the network’s entire transaction history if they’re competing for rewards. This is not an issue for smaller, younger blockchain networks, but we’ve already seen the bitcoin and Ethereum ledger grow to enormous size. This forces smaller node operators out of the process, further consolidating hash power in fewer hands.
-	**Communication:** Blockchain networks employ validators (or miners) to produce and validate new blocks. They must communicate to synchronize block transactions, transfer blocks and finally reach consensus. This communication overhead grows exponentially are the network becomes more complex, which can slow down processing speeds, drive up costs and encourage consolidation of hash power.

## 12.1 Sharding

Sharding is the process of horizontally partitioning data within a database into smaller pieces, called shards. This is not new to blockchain; it has been used by centralized networks for decades.

When used in blockchain, sharding divides the whole network into smaller subnets based on certain defined criteria, very often an address. Each shard has its own validator set, and validators are specially designed to process the transactions on their own shards.

### 12.1.1 Benefits

Sharding has certain benefits:

-	**Commutation:** Nodes only need to listen to transactions more relevant to themselves. Messages don’t need to be propagated to the entire network, saving a lot of bandwidth.
-	**Storage:** Sharding can lessen the storage burden on full nodes by limiting data redundancy.
-	**Inter-shard parallelism:** Because sharding divides a network into smaller pieces, multiple shards can work in parallel to independently generate blocks at the same time.

### 12.1.2 Problems
Although sharding is proven to work in centralized systems, serious flaws are introduced when it’s applied to blockchain. In virtually all sharding, nodes are randomly put into shards based on their addresses in the hope that each node will process only those transactions assigned to it.

But because addresses are randomly generated by most blockchain networks, the chance of finding two interacting accounts in the shard is same as finding them in different shards. This creates a situation where a popular smart contract might reside in one shard, but its active users are in other shards. This leads to cross-shard transactions, which are very complicated, inefficient and expensive.

Unless this cross communication is reduced, sharding is not an effective solution for blockchain’s scalability issues.

## 12.2	Self-Organization

Arcology uses a unique partitioning algorithm called Self-Organization (SO), a transparent and intelligent process that dynamically groups accounts based on certain criteria, including historical behavior. This is possible because most transactions are not actually processed in random patterns; over time, many users show tendencies to interact with certain other users. This provides an opportunity to optimize network configuration.

But because these tendencies are not long-lasting, it’s imperative to act dynamically. It’s also important to adapt to trends in user behavior over time.

For example, when a new app catches on with users and becomes wildly popular, it’s possible to increase network efficiencies based on this app’s configuration and transactions. But it’s not worth optimizing one’s resources specifically for this single app. Optimization must be dynamic and adaptable — for any app that may see unexpected use, possibly for a short period of time.

Arcology’s Self-Organization is designed precisely for this. It is:

-	**Adaptive:** a dynamic and ever-happening process;
-	**Dynamic:** active users are grouped into shards to reduce friction;
-	**Efficient:** cross-partition communication is reduced to negligible levels.

Arcology’s Self-Organization is a much more intelligent network partitioning solution, it will significantly reduce cross-partition communication and overhead comes with it.  Self-organizing is the technology designed for scalability.