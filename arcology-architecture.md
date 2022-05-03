## 4. Arcology Architecture

To achieve the Arcology’s design goals, it naturally demands a flexible, scalable and loosely-coupled system architecture for client software.  At the core of Arcology client software is a microservice base architecture.

The only way to enhance blockchain infrastructure to a level that it could support millions of transactions is through horizontal scaling.  In this type of design, functional modules are individually deployed on multiple machines connected by high speed network.

## 4.1. Microservice Architecture

Microservice architecture is inherently suitable for this. In Arcology, all key functional modules are encapsulated into services and deployed on different machines to spread the workload. All services communicate asynchronously via a message queue system. We chose this architecture model for the following reasons:

1. Easy integration
2. Loose coupling
3. Cluster computing
4. Flexibility

### 4.1.1. Easy Integration

As any software designer will admit, introducing new features during active production can introduce unknown technical risks that may affect and impede development. With Arcology’s microservice architecture, we abstracted all key functional modules into discrete functions so they can be developed, tested and integrated individually.

### 4.1.2. Loose Coupling

Some modules in Arcology require good performance, whiles others need greater productivity. Arcology’s microservice architecture allows different services to be developed using different technology stacks.

Services are loosely coupled and communicate through a messaging system. Any internal changes happened to one service is transparent to others.

### 4.1.3. Flexibility

It’s not unusual for any network or system to run out computational power when faced with unusual high volumes of user requests. Some current blockchain networks are well-designed to handle this, but they’re far from perfect.

Arcology’s architecture maximizes efficiency during moments of high demand by automatically adding resources only when the workload is high. This is especially helpful for cloud-computing environments, where deployed nodes are charged by actual usage.

## 4.2. Cluster Computing

On Arcology, a node is no longer is a single machine but is a cluster of commodity computers with different functional modules deployed. Connected by high speed network, all the machines can work collaboratively to process transactions in full parallel.

Cluster computing is proven to be an effective, cost-efficient way to boost computation power. In fact, computer clusters represent more than 80% of all top 500 commercial systems.

However, existing cluster computing facilities are designed for centralized systems. They lack many of the fundamental features necessary for blockchain network.

We have developed a deterministic concurrency framework to manage shared computational resources in a node cluster. On Arcology, a node is no longer a single machine, but a cluster of commodity computers with different functional modules deployed. Connected by a high-speed network, all machines work collaboratively to process transactions in full parallel. Developers can access these shared resources through a set of user-friendly APIs.

This gives Arcology unlimited scalability: Improving the overall throughput could be as simple as adding more machines to the server cluster. There is no theoretical limit to the amount of resources to a cluster.

![Cluster Computing](/img/42-cluster-computing.png)

## 4.3. Structure Diagram

![Structure Diagram](/img/43-structure-diagram.png)
