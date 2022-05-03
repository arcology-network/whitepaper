---
id: microservice-architecture
title: Micoservice Architecture
---

## 11	Microservice Architecture

Arcology is a high-performance and general-purpose system that naturally demands a flexible, scalable and loosely coupled system architecture. In Arcology, functional modules can be horizontally scaled and integrated into the existing framework in order to fully harness the computational power that clusters offer.

We chose a microservice architecture for the following benefits:

-	**Cluster computing:** A node on Arcology network can be a cluster of commodity computers with different service modules connected by a high-speed network.
-	**Horizontal scalability:** At times of higher throughput, resources are easily added by simply connecting more servers to the cluster.
-	**Loose coupling:** Microservice architecture allows different services to be developed individually using the technology stack. This means that internal changes to one service are transparent to the others, making development, testing and deployment much easier.
-	**Asynchronous communication:** Every functional module is wrapped in a service; they communicate through a messaging system that increases modularity and throughput.
-	**Computation on demand:** Node operators can fine-tune their cluster setup to meet specific needs on the fly. A typical use case is the transaction execution. One node usually comprises several transaction execution units deployed on different servers, working in parallel for maximum power for heavy workloads. When network demands are lighter, it’s more economical to employ fewer execution units. 
