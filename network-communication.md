## 5. Network Communication

Being distributed in nature, blockchain networks rely heavily on inefficient relayed network communication. The low efficiency of conventional P2P protocols isn’t a significant issue for slow networks, but it was an obstacle for Arcology’s goal of processing millions of transactions per second.

To hit our goal of seven-figure TPS, blocks must be large enough to handle these transactions. Depending on the transaction type, a transaction on the Arcology network uses between 60 and 70 bytes on average. One typical Arcology block contains between 150,000 to 200,000 transactions.

These high numbers require efficient network communication protocols to ensure delay-sensitive information must be delivered on time.

## 5.1. Multi-channel

Consensus process is usually more latency sensitive, while blockchain synchronization is benefited from better throughput. In addition to maximum physical bandwidth, parameters play an important role to make the network either lean toward lower latency or favor better throughput. It is not always possible to maximize both with only one set of parameters.

Arcology refers connections as channels , a channel is a dedicated connection for a special purpose. Each channel has its own connected peer list and network parameters specially tuned for its purpose.

Arcology validator nodes would require two have maintain at least two channels. So it is perfectly possible for two Arcology nodes to be connected through multiple channels at the same time. In this case, while a high throughput channel is busy sending transactions, is low-latency channel is working on exchange consensus information.

## 5.2. Self-adaptive

As explained earlier, the Arcology network will always try to establish direct connection among validators. This accelerates transaction processing and reduces latency as much as possible. Additionally, machine learning algorithms are employed to optimize the network’s topological structures.
