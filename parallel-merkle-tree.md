---
id: parallel-merkle-tree
title: Parallel Merkle Tree
---

## 9 Parallel Merkle Tree

In cryptography and computer science, a Merkle tree is a data structure where the leaf nodes store hashes of original data entries, while non-leaf nodes store hashes calculated from their child nodes. A Merkle tree can provide cryptographical authentications by verifying data retrieved from a trustless party on blockchain networks.

Arcology’s Merkle tree is a pure hash tree. In other words, it doesn’t contain any state data at all, only the hashes computed from the state data. The leaf nodes are hashes of original data entries, and non-leaf nodes contain hashes calculated from their child. The Merkle tree and original state data are no longer tangled; they are independent from one another other and each has its own dedicated data stores.

Parallel by design, Arcology’s Merkle tree achieves parallelism through a divide and conquer strategy. The entire tree is effectively divided into a number of subtrees, each containing only one part of the whole tree. The subtrees operate independently from each other both in terms of data manipulation and storage.

This design offers several key advantages:

- **Performance:** Because subtrees have their own independent stores, data manipulations (eg, insertion, retrieval, hash calculations) are handled by different database servers in parallel, resulting in huge performance gains.
- **Scalability:** As the network grows, so does the data. It’s much easier to add storage capacities to a distributed tree then keep everything in the same place.
- **Modularity:** Hash proofs are mainly for clients to authenticate state data for external parties. The system has little use for hash proofs internally. Keeping two logically distinctive data structures helps to improve clarity and modularity.

![Parallel Merkle Tree](/img/9-parallel-merkle-tree.png)

## 9.1 Tree Structure

Parallelism is an effective way to achieve the maximum performance. The key is to ensure that all individual processors work in different parts of the tree without interference, allowing each task to be undertaken by an independent processor. Arcology uses a distributed parallel hash tree to provide and store Merkle proofs with no locking required

The total performance is dependent on the number of subtrees: the more subtree there are, better parallelism is achieved. But to make the tree manipulation both parallel and lockless, parallel processing must stop at a certain depth (or, some locking is required to avoid race condition).

The Arcology Merkle tree has a lockless parallelism design, with the tree consisting of two parts. The separation between root and child subtrees is determined by: tree depth, level of expected parallelism and a cutoff value above which nodes will be in the root subtree (and the rest will be in the child subtrees). Nodes in the root subtree point to sub root nodes of child subtrees.

Although, logically, the root subtree and child subtree belong to the same Merkle tree, both root and child subtree have their own storage and can be hosted by different storage servers. This design significantly improves performance, as workload can be distributed to multiple machines simultaneously.

## 9.2 Manipulation

In Arcology, writes are processed in batches. There are several steps in this insertion:

- **Pre-classification:** Hash input is classified into sub groups corresponding to the subtree, based on predefined characteristics. Therefore, independent and unrelated writes are processed independently by different child subtrees.
- **Root subtree:** Insert the pre-grouped hashes into child subtrees. Hashes in the same subgroup are inserted in serial order; hashes belonging to different subgroups are sent to different subtrees in parallel.
- **Child subtrees:** After insertion to child subtrees, child root nodes are returned and added the root subtree as leaf nodes.

![Manipulation](/img/92-manipulation.png)

## 9.3	Tree Storage

It is the user’s responsibility to choose where and how the subtrees will be stored. Generally, storing the subtrees in a distributed database would be an optimal choice performance-wise.

## 9.4	Proof Retrieval  

Reading from Arcology’s Merkle tree is quite straightforward and similar to conventional Merkle trees. The biggest difference is that Merkle proofs and original data entries are stored separately in two services.

Retrieving Merkle proofs is a four-step process:

1.	Calling the data entries from Arcology’s storage service;
2.	Recalculating entry hashes, if necessary, and sending hashes to the Merkle tree service;
3.	Using the hashes to retrieve Merkle tree proof paths from the Merkle tree service; and the Merkle tree service confirms that returned paths match the state data entries before returning them back to the requesting party.
