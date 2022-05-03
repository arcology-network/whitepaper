## 8. Data Storage

Arcology users are given more freedom and finer control over where and how the data should be stored, based primarily on frequency of usage. Instead of throwing everything into one data store, Arcology is flexible: Different data types can be stored in different manners, increasing performance and driving down costs.

## 8.1. Issues

Data storage is one of the key roadblocks faced by blockchain technology on the road to scale. Today’s blockchains predominantly use embedded key-value data stores like LevelDB and RocksDB. Embedded key-value databases are easier to use; very little configuration is required and they’re faster than many other databases. They work just fine for smaller applications.

But this architecture isn’t designed for large-scale applications. The total storage capacity is limited to what a single server can provide, and it’s very difficult to add capacity. This storage architecture is diverging from the mainstream way of maximum capacity scalability and performance.

### 8.1.1. Indiscrimination of Data

Because varying data types require different treatments, there is no universal solution for storage. In-memory databases are capable of offering top storage access performance, but they’re generally expensive. Cloud storage, on the other hand, is generally slower but more competitively priced.

## 8.2. Tight Coupling

Lacking many key features that are widely available on other standalone databases, developers are forced to couple their code to the underlying systems. For example, SQL cannot be used to query databases within smart contracts. This hampers both adoption and innovation.

### 8.2.1. Low Performance

Famously, the data stored on a blockchain network is irreversible and immutable. This is achieved by building a Merkle tree for the source data entries. Most blockchain projects choose to store both data entries and the Merkle tree in the data store, even though they are logically different types of data.

In such a Merkle tree, the leaf nodes store original data entries, while non-leaf nodes store hashes calculated from their child nodes. This inefficient design drags down performance at large scale.

### 8.2.2. Storage Scalability

When the server runs out of storage space or performance deteriorates at high volume, scaling capabilities become critical. One popular option is horizontal scaling. That is, just add more servers to the network, laterally, with little or no additional effort.
Embedded databases cannot do this.

### 8.2.3. Cost

In most industries — indeed, with most technologies — economies of scale show that costs are reduced when capacity and performance are increased. Blockchain moves in the opposite direction: Greater network scale demands more redundant computational cycles, which drags down overall performance and drives up transaction costs. This is an unavoidable reality of proof-of-work’s fundamental security model, and other *proof-of* networks are coming up against this reality.

Eventually, such systems will reach a point where having every full node store the entire ledger is no longer profitable for smaller nodes. We’re seeing this already on the bitcoin network, where maintaining the full ledger profitably is reserved for the large cartels. This has many worried that bitcoin is, ironically, becoming a centralized network controlled by a small group of large miners.

By allowing large and small nodes to compete for rewards, Arcology’s Multifactoring consensus algorithm is a remedy for this.

## 8.3. Arcology Storage solution

Arcology’s data store is abstracted into storage layers running in clusters. Our carefully designed tiered storage framework achieves maximum performance while keeping cost low, offering users the freedom to choose their storage configurations based on access frequencies.

To accelerate data access, a local cache sits in every service needing fast access to the storage. State transitions are recorded in local cache, before persisting to permanent storage. The process is transparent to data storage users, and the local cache talks to the permanent storage only when there is a cache miss.

Local state cache is updated at the end of the blocking cycle. When consensus has been reached for a new block, storage service pushes all state updates to the other services, holding a local state cache in an Arcology cluster.

These execution units access local state cache through a VM-specific data access adaptor, which is responsible for translating communications between the VMs and state cache.

### 8.3.1. Tiered Storage

Functional modules in Arcology access storage through an abstracted storage access layer. Therefore, the underlying storage is completely transparent to data users. They know, for instance, if the requested data is from a local embedded database or a remote cloud-based storage service.

To further increase efficiencies, Arcology clusters can connect to multiple database systems. Rather than throwing everything into one embedded store, data is assigned to different databases based on its characteristics. For instance, frequently used data is kept in a memory database like Redis, while less frequently accessed data goes to more affordable cloud storage or shared with other nodes.

### 8.3.2. Data Manipulation Language

Arcology’s design allows developers to use their SQL in the smart contract code to query state database directly.

### 8.3.3. EVM Example

The Ethereum Virtual Machine plugin (EVM) is a part of Arcology’s standard release. The default configuration categorizes data into three general types:

- **Hot Data:** The mostly frequently used data. Because EVMs need the latest state information to process transactions and provide account updates, “hot data” includes the latest account states and some of the most popular smart contracts. The recommended database system for hot data is a Redis cluster, whose in-memory databases offer the best general performance
- **Warm Data:** Often but not frequently accessed data. “Warm data” may include less popular smart contracts and historical account states. When accessing warm data, one might expect slightly longer wait times.
- **Cold data:** Information and records that aren’t frequently accessed or queried. Because it’s not typically used for processing  transactions, “cold data” requests don’t negatively impact network overall performance.

![Validator Quantificationn](/img/832-evm-example.png)

### 8.3.4. Storage Sharing

In Arcology, the delicate balance between minimizing costs while maximizes data safety is maintained through storage sharing. This allows nodes to share the responsibility of storing any given piece of data or record, rather than require every node to perform redundant functions. For example, five full nodes might share one copy of block data stored on an AWS S3 server.

Not every data type is suited for data sharing. For instance, that data directly related to processing transactions processing, and other types of “hot data”, should be stored locally and redundantly. In practical terms, this is only possible with tiered storage, which allows users to configure their storage according to their own needs.

### 8.3.5. Storage Server Node

A storage node isn’t necessarily a full node. Although it still plays some roles of a full node, it actually works like a storage server, providing data services to other nodes and earning rewards for its clients on the network. Code data storage is the best candidate for storage sharing these objects and records are less likely to be in frequent use.

### 8.3.6. Storage Sharing Protocol

Storage sharing protocol defines the following:

- How data is held on storage nodes,
-	How storage nodes are discovered,
-	The communication between storage nodes other their client nodes,
-	How data is to be transferred,
-	How prices are negotiated; and
-	How to maintain the balance between redundancy and decentralization.
