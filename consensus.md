## 6. Consensus
- [6. Consensus](#6-consensus)
- [6.1. Various Mechanisms](#61-various-mechanisms)
  - [6.1.1. PoW](#611-pow)
  - [6.1.2. PoS](#612-pos)
  - [6.1.3. Others](#613-others)
- [6.2.	Multifactoring](#62multifactoring)
- [6.3.	Advantages](#63advantages)
  - [6.3.1. Flexibility](#631-flexibility)
  - [6.3.2. Scalability](#632-scalability)
  - [6.3.3. Fairness and Decentralization](#633-fairness-and-decentralization)
  - [6.3.4. Validator Selection](#634-validator-selection)
  - [6.3.5. Activity-based](#635-activity-based)
  - [6.3.6. Anti-cartel](#636-anti-cartel)
  - [6.3.7. Validator shuffling and auto recovery](#637-validator-shuffling-and-auto-recovery)
- [6.4. The Process](#64-the-process)
- [6.5. Engine](#65-engine)
- [6.6. Metadata](#66-metadata)
  - [6.6.1. Validator set](#661-validator-set)
  - [6.6.2. Validator selection](#662-validator-selection)
- [6.7. Validator Quantification](#67-validator-quantification)
The Scalability - Security - Decentralization Trilemma dictates that networks can take their choice of two at any given time. Achieving all three simultaneously has been a practical impossibility. This has plagued the blockchain industry since its inception.

## 6.1. Various Mechanisms

Different consensus algorithms have been developed to address different aspects of this problem. To date, none has successfully addressed scalability,  security  and decentralization.

### 6.1.1. PoW

Since the debut of Bitcoin, the majority of cryptocurrency projects have been reliant on PoW (proof of work) for reaching consensus. PoW has been proven to be effective and reliable.

However, as the size of the network grows, PoW’s inherent problems emerge. Relying on pure hashing power to compete for the winner, all nodes must perform the same hashing jobs; this is an extremely power-thirsty and wasteful process.

As a result, mining bitcoin is no longer economical for average people. What’s more, the centralization of hashing power has pushed PoW-based networks toward centralization, and there’s no mechanism to prevent this from continuing.

### 6.1.2. PoS

Proof-of-stake blockchains rely on each node’s personal “stake” — or, how much of the coin or token they own — to determine the level of likelihood to win the privilege to forge the new blocks. In all existing PoS designs, validators must own a minimum number of coins or tokens to participate.

Though it has many advantages over PoW, PoS inevitably results in network centralization and the “rich get richer” effect, which may alienate users.

### 6.1.3. Others

Delegated Proof-of-Stake (DPoS) was designed to address many problems with proof-of-stake, while proof-of-authority (PoA) is more performance-focused, and therefore less concerned about decentralization. This may carry its own risks to the network and its users.

There are more, but each *proof-of-whatever* algorithm is addressing the same problem: Which node should have the privilege to perform a task and receive the reward?

In focusing on this single question, they fail to take a comprehensive view on nodes in a systematic way. They also lack a mechanism to the adaptor and to cope with temporal changes in network status.

## 6.2.	Multifactoring

Arcology uses a consensus algorithm called “Multifactoring” to determine which participants will earn their fair chance to make block and earn rewards. The algorithm is based on an objective multifaceted evaluation mechanism that quantifies a node’s contribution and commitment in a comprehensive and objective way. Multifactor works on both permissioned and permission-less networks.

Multifactor isn't just a new consensus algorithm, it is a key step toward the goal to unify all consensus algorithms under one general framework. Multifactor builds a positive, inclusive, general purpose, flexible and ever-improving ecosystem in which good players could be rewarded economically.

Over time, many blockchain networks are revealing tendencies toward centralization due to the concentration of certain resources (e.g., hash power in PoW-based networks). To counteract this, Multifactoring has a built-in anti-cartel mechanism that is activated when the issue arises.

As an improvement on other consensus algorithms, Multifactoring offers a smooth and continuous transition to bridge the gap between the centralized and distributed systems.

## 6.3.	Advantages

There are many consensus algorithms that focus on specific qualifications of nodes (**hash power, stake, space, votes, etc.**).

Multifactoring, on the other hand, takes multiple factors into account for a 360-degree, multi-dimensional view on node quality and performance. Nodes are no longer just classified as honest or malicious nodes, Multifactoring also makes distinctions between active and passive participants. (Active participants are rewarded by given extra credibility.)

This helps to ensure that “good” nodes have a better chance to be selected to participate in crucial activities.

### 6.3.1. Flexibility

With Multifactoring, developers don’t have to make the selection among different consensus algorithms for their merits and endure their flaws. In other words, Multifactoring doesn’t require sacrificing one advantage for the other.

What’s more, the Multifactoring consensus algorithm evolves dynamically and automatically in response to network changes. It might even be described as a systematic and sophisticated summation of all other proof of whatever schemes.

### 6.3.2. Scalability

Typical consensus algorithms affect scalability in different ways. For example, a consensus algorithm that works well on a smaller network may be unable to perform efficiently on a larger scale. And vice versa.

Multifactoring can work with both smaller and large-scale networks with millions of nodes without sacrificing performance.

### 6.3.3. Fairness and Decentralization

In Arcology, multiple factors are considered collectively at the same time. The chance of earning transaction fees is proportional to overall quantification results.

To use the PoS analogy, the "stake" is no longer token ownership, but a combination of many factors reflecting the node’s overall quality. Factors are assigned weights to reflect their importance in the calculation; weights can be adjusted dynamically to prompt maximum performance, competition and security.

Those nodes willing to participate in the transaction validation process are required to have scores, and the chance for these nodes to be selected and earn transaction fees is proportional to this DM score. The DM score is a comprehensive aggregation of their qualification, contribution and commitment to the ecosystem.

Multifactoring brings the performance potential of permissioned systems and the openness of permission-less networks together, allowing users to enjoy the benefits of both — without compromising performance.

### 6.3.4. Validator Selection

There are many factors affecting blockchain performance, primarily the number of validators will affect network performance.
In many designs, it’s assumed that more validators mean extra safety. While generally accurate, this introduces greater overhead for communications, which drags on and complicates consensus processing. On the other hand, fewer validators mean faster transaction processing speed — but this, obviously, will decrease network security and decentralization.

Deciding on the appropriate number of validators is a longstanding issue for blockchain developers, and many solutions have been attempted. Some projects choose to select randomly from a large pool of nodes that meet minimum requirements for fairness and security. In many cases, the minimum requirement is a certain stake of coins or tokens. Two obvious drawbacks: large token holders will have an advantage over smaller ones, and there’s no guarantee that a randomly chosen node is the best performer.

Addressing this, Arcology reframed the question as “finding minimum quality validator set" to achieve the right levels of security, decentralization and performance. Our solution is a dynamic mechanism that allows different validator configurations for different circumstances.

In our environment, there is no fixed number of validators or minimum qualification requirements for nodes to become validators. The number of validators and minimum requirements are a function of predefined “equilibrium goals” that solve for scalability, decentralization and security. The total number of validators and minimum requirements to become a validator may vary from time to time.

Validators are selected by a comprehensive score calculated from a set of factors. In PoS systems Staking is the only factor to make a node validator.  By staking a fixed amount coins, a node is guaranteed to be validator.

In Arcology staking is also an important factor but not the only one and there is no fixed lower limit to guarantee a validator membership.  The minimum amount required to become a validator is dependent on how many coins others are willing to stake. Nodes have to compete with each other to win the chance to be a validator.

1.	**Declaration:** A node will broadcast a message wrapped in form of a special transition called self-nominating transition to the network declaring it is willing to become a validator together with its initial qualifications.
2.	**Initial Assessment:** Upon receiving self-nominating transactions, all the full nodes verify it initial qualifications to make sure it meets the minimum requirement at the time.  Once the nodes pass that phase, they become validator candidates.
3.	**Score calculation:** Once these candidates have passed the initial assessment phase, full nodes will retrieve the history data of all the candidates to calculate a score.
4.	**Determination:** Full nodes keep a list of qualified candidates ranked by their scores, a candidate will become a validator if it end up within top N, then the candidate becomes a validator

Under this Multifactoring framework, nodes compete to become validators; economic incentives are given to those who make positive contributions to the network. The result is an ever-competing and ever-improving ecosystem.

### 6.3.5. Activity-based

On the Arcology network, nodes take on multiple roles — at will — and are rewarded based on their performance, thereby encouraging them to work harder and make positive contributions. This results in a fair community of nodes that are incentivized to ensure the network’s long-term performance and security.

### 6.3.6. Anti-cartel

As stated earlier, we’re seeing tendencies for blockchains to shift toward centralization, whether due to consolidation of hash power or inherent unfairness of PoS design.

With this in mind, Arcology has featured an anti-cartel mechanism since day one. On our network, Multifactoring creates an ever-competing, ever-improving ecosystem that helps detect, identify and counterbalance any tendencies toward centralization.

### 6.3.7. Validator shuffling and auto recovery

For many different reasons, a good number of enterprise blockchains have a closed membership. These “permissioned blockchains” ensure that shareholders retain certain controls over the network.

Chief among these controls is recovery. After all, if you’re operating a commercial blockchain network on behalf of paying clients, data security is a top concern.

At Arcology, we have no such concerns. Our built-in validator-shuffling mechanism can auto-recover in the event of a catastrophic breach or other disaster. We constantly monitor and change our validator sets, and even the sudden disconnection of one-third of validators will not stop the network. This allows us to detect, identify and malicious behaviors at their onset, and to replace abnormal validators in real time.

![Validator Shuffling](/img/635-validator-shuffling.png)

## 6.4. The Process

Validators are the special nodes responsible for processing transactions, generating new blocks and signing on new blocks for other nodes to accept. The quality of validators deeply affects the health of the network ecosystem. Arcology has a sophisticated design for validator selection, voting, validator performance evaluation and validator-shuffling and replacement.

## 6.5. Engine

Arcology's dynamic, self-organizing and decentralized consensus is focused on optimal and efficient network partitioning. Our consensus engine verifies the data in the transaction pool and collects statistics related to self-organization by invoking the unified interface of the VM framework. Our network, therefore, does not need any transaction details unrelated to consensus. This design enables Arcology to achieve exceptional scale.

In traditional blockchains, the consensus object is the public ledger that stores all the historical transactions. This is blockchain in its most primitive form.

With the introduction of smart contracts, the public ledger was endowed with complex business logic. Yet, we are still hampered by the limitations of the original blockchain design.

Arcology improves blockchain by introducing the concept of metadata into blockchain. The consensus object is no longer limited to the common ledger but extends to metadata.

## 6.6. Metadata

Arcology records and utilizes not just consensus results, but metadata of the consensus process, including information about self-organizing networks, descriptive information about multiple factors and their weights and other system-level parameter information.

In the absence of metadata consensus, this information is added to either the code or the transaction history, which makes the adjustment and consensus of system-level parameters a very difficult and long process.

Borrowing from traditional databases, Arcology manages system-level metadata independently. This enables finer control of the consensus processes, making governance, optimization, upgrading and other system operations simpler and more efficient.

### 6.6.1. Validator set

In Arcology, an epoch is the time interval generating a fixed number of blocks and a maximum timeout period— whatever is reached first. The size and composition of the validator set may vary from epoch to epoch, but it remains fixed within any given epoch.

Validators have voting powers, and their voting powers are proportional to their summation of multifactor scores and changed dynamically, but deterministically, by the system.

For any block to be accepted by the network, at least 2/3 of voting power and 51% of validators must provide their signature to the block.

### 6.6.2. Validator selection

Unlike Byzantine fault tolerance (BFT) systems, Arcology doesn't need any pre-knowledge or unconditional trust established prior to the validator selection process. Rather:

1.  Nodes are evaluated based on their performance and quality of services they have provided to others
2.	Nodes evaluations in different aspects will be quantified and combined into a single score.
3.	Nodes having higher scores nodes are selected to be the validator candidates set *D*⊂*N*
4.	Out of set *D*, top  *V*⊂*D* nodes are selected to be the validator for the current epoch
5.	One validator *D*∈*V* is randomly selected to be the node producer

![Validator Selection](/img/662-validator-selection.png)

## 6.7. Validator Quantification
To properly evaluate node quality, a set of factors is collected and analyzed.

Below, the set *F* denote all factors to be evaluated.

There are two primary sets of factors: numeric and binary. Numeric factors represent node qualifications with continuous values. Binary factors are 0 or 1. Factors are given weights to reflect their importance. Weights will be changed dynamically from time to time based on circumstances like TPS, node activities, security alerts and so forth.

![Validator Quantification](/img/67-validator-quantification.png)
