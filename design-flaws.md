---
id: design-flaws
title: Design Flaws
---

## 2 Design Flaws

Of the many issues mentioned above, scalability is the most imperative for the blockchain industry today. Without high-speed, low-cost scale, DLT cannot compete with traditional centralized offerings. Widespread adoption of blockchain technology is thereof unlikely.

Putting it mildly, scalability is a complicated issue. Over the years, we’ve seen many proposals, but few successes. This, we believe, is a result of deeply rooted design problems that haven’t been addressed. Specifically:

- Transaction processing
- Network communication
- Consensus
- Storage

## 2.1 Transaction Processing

Nodes are the building blocks of blockchain networks. Generally, a node is an independent entity that is responsible for processing transactions, broadcast blocks, storing state data and so forth. The efficiency There are two types of separate but closely related performance issues.

### 2.1.1 Inter-node

A blockchain network may consist of a few thousand nodes, yet due to the trustless nature of permissionless networks, all the full-node validators are expected to reprocess all the transactions in the blocks. This, by definition, precludes collaboration between nodes. While this competitive feature ensures security, fault tolerance and is key to decentralization, there are some issues as well:

- **Low Throughput:** The network throughput is not greater than that of a full-node validator, on average.
- **Over-Redundancy:** Having all full-node validators process the same transactions is a profound waste of processing capacity that could be used elsewhere.

### 2.1.2 Intra-node

Conventionally, a node means one copy of client software installed on a single machine. Virtually all blockchain systems adopt this all-in-one design concept. Apart from simplicity, this type of system architecture has some very serious limitations:

- **Limited Resources:** The resources available to support network throughput wouldn’t be pathetically more than one machine can offer on average.  It is questionable that if the whole infrastructure can be built on resources of just a machine
- **Vertical scaling:** This type of design only allows vertical scaling. When system is running out resources the only option is to upgrade the machine by adding more RAM, CPU etc. Vertical scaling is no longer mainstream because of its obvious fallbacks.

## 2.2 Communication

Current blockchain networks relay their communications among nodes. The reliability and communication efficiency have critical impact on network throughput. Current communication design and implementation limit efficiency of transaction speed per second (TPS), which in turn limits scalability.

In the typical block consensus process, after a new block is proposed, the proposer node needs to send the block to other validators for verification and collect the votes. In the worst-case scenario, the overall network bandwidth required equals the size of block multiple by the total number of validators.  Any attempts to improve efficient of this process will inevitably face a dilemma:

- **Throughput:** Cutting the block size down will certainly help with saving bandwidth and make communication faster, but smaller blocks result in low throughput.
- **Security:** Having fewer validators will ease the problem, but may compromise security, fault tolerance and decentralization.

## 2.3 Consensus

Consensus also play a big part in scalability. Depending on choice of consensus algorithm used. Ranges from seconds to minutes. Although these consensus algorithms look different from each other, they all share some similarities.

Apart from the CAP trilemma,  all consensus algorithms lack the mechanism to incentivizing positive contributions to help blockchain networks scale up. Neither staking or hashing power is subjectively linked to contributions to the network scalability itself. Mining and Staking will help with improving network security but they don’t directly contribute to improving transaction throughput.

For example, on PoW networks, with the same amount of financial resources, it will be better off for nodes to upgrade their mining rigs rather than upgrading hardware configurations to processing more transactions. Basically PoW networks reward nodes by their mining capacity not transaction processing speed. Nodes wouldn’t get any credit for being able to process more transactions. Unfortunately, mining power is not connected to transaction processing throughput in any direct way.

A healthy network needs various types of voluntary contributions. For example, when a new node comes online, it would make requests to other existing nodes on the network for synchronizing blocks and state data etc. The decision whether to answer these requests is purely made on a voluntary basis. Although it would certainly consume network bandwidth and CPU resources, answering nodes wouldn’t get any reward for actively answering these requests or doing anything “unselfish”. Consensus protocol like PoS is having similar issues. On PoS network it will be a much better economic option to stake more coins than to invest in upgrading hardware or software to achieve better throughout. Again, nodes are rewarded for staking more but not processing fast.

Both PoW and PoS were designed for security not scalability. Without having an economical rewarding and punishing design in place to stimulate nodes to improve their transaction process capability, individuals or organizations who are running nodes have no apparent reasons to upgrade network bandwidth, computational power, storage capacity or software architecture to improve network throughput.

## 2.4 Storage

Blockchain can be imagined as a special type of distributed database system. The data storage is critically important to blockchain systems. At the moment , the blockchain storage is probably the biggest bottleneck for virtually all platforms.

### 2.4.1	Excessive Redundancy

Most centralized, cloud-based storage providers grow capacity by adding more servers. In the past few years, this ongoing process has driven down prices dramatically. Cloud storage has never been cheaper thanks to economies of scale.

On blockchain networks, the arrow moves in the other direction. Storage becomes more expensive as more nodes join. This has, so far, been unavoidable due to blockchain’s trustless nature: Full-node validators must store the entire ledger, at all times, no matter how large and unwieldy.

As stated earlier, this redundancy is a fundamental feature of blockchain network, but we can no longer ignore its wasteful nature.

### 2.4.2	Embedded DB

Virtually all blockchain client software uses embedded key-value (KV) database systems such as LevelDB and RocksDB. These databases operate on the same computer as all others. Overall storage capacity, therefore, is limited to that of just one computer.

To perform and compete in the real world, a blockchain network needs a sustainable storage strategy that balances capacity, cost and security.
Embedded database systems do not meet these requirements.

### 2.4.3	Hash Root Calculation

Computing hash proof offers a way to retrieve and verify state data received from trustless parities on a blockchain network. It is one of blockchain’s cornerstones.

Yet a majority of implementations have performance problems when dealing with frequent updates. This issue is often ignored due to the fact that many projects either haven’t reached the throughput level where the effect starts to show up, or they simply skip this step for slightly improved performance.

## 2.5 VM Compatibility

Similar to centralized platforms, blockchain networks need to support real-world applications that allow end users to conduct business by accessing and exchanging digital assets. These transactions are handled by smart contracts.

Perhaps because it’s a relatively young technology, or perhaps because market conditions required it, the smart contract ecosystem is very fragmented. By and large, each platform has its own language for smart contracts, which developers must learn before they can build and launch their apps.

Arcology is designed to be compatible with multiple virtual machines (VM) and smart contract languages. This allows developers to work in their preferred language and get started immediately. They can also move their smart contracts from other platforms, to Arcology, with no modification required.  
