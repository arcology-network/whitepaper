## 10. Concurrency Control

Among the factors hindering blockchain’s scalability, low-efficiency transactions are among the most pressing. In other systems, transactions — including smart contract calls — are usually placed and executed in serial order by the systems.

In these serial execution environments, transactions are processed one-by-one. There are two primary  advantages to this design: its linearity intuitively fits in with human perception of sequence and time; and serial programs are easier to design, develop, test and maintain.

Most importantly, however, serial execution guarantees one critically important property: determinism. Any given input will always yield the same set of output. Determinism is thought to be a fundamental requirement for blockchain to function properly.

Serial execution’s downside, of course, is the waste of computational power and its inability to take advantage of modern processors. In serial execution, regardless of how many cores are available, only one of them is busy at any time. It follows that serial execution-based blockchain systems are stuck with these limitations.

Parallelism is the most effective way to improve processing capabilities, and most programming languages have concurrency support. One obvious gain is performance. Most modern computers have multiple cores, allowing them to handle multiple jobs at once.

Particularly in a blockchain environment, designing a good concurrent control framework is not easy. Multiple logic flows may coexist; code logic from multiple threads may interfere with each other; modifying shared variables may cause race conditions or deadlocks. The key to success is properly managing the states of shared resources.

Another challenge is reproducibility — a key requirement in distributed networks. Programs are expected to generate the same results with the same input every time get executed. Due to the timing-dependent nature of concurrent and parallel execution, it is virtually impossible for concurrent programs to reliably reproduce execution results without a deterministic concurrency control mechanism.

Unfortunately, the concurrency frameworks designed for centralized systems usually don’t enforce determinism; transplanting a conventional concurrency solution directly from a centralized system into blockchain is unlikely to be successful.

## 10.1. Arcology’s Concurrency Solution

Arcology offers a very powerful, VM-neutral and easy-to-use deterministic concurrency mechanism that helps developers design and implement concurrent logics in their smart contracts. With Arcology’s concurrent framework, developers can fully utilize the computational power provided by modern multi-thread, multi-core, multi-processor architectures without sacrificing safety.

Transactions can be distributed to multiple cores and multiple processors for parallel processing, making full use of computational power through horizontal scaling.

## 10.2. Benefits

The most obvious benefits of introducing a deterministic concurrency mechanism to blockchain smart contract development is performance. Smart contract executions could be distributed to multiple threads (VMs), multiple cores or even multiple machines. Together with Arcology’s microservice-based architecture, improving the overall throughput is simple as adding more machines to the server cluster.

Arcology’s concurrency control mechanism isn’t just concurrent, but also deterministic. Determinism is critical for distributed networks to reach consensus; a deterministic concurrency control mechanism can help with security as well. With the concurrency framework, all reads and writes to the shared state are under control. The built-in mechanism works in real time to detect and resolve state inconsistency (whether caused by intentional attacks or bad programming practice). Unexpected changes made to shared states can be caught automatically and smart contract execution will be terminated, guaranteeing final state consistency.  

What’s more, Arcology’s concurrency control mechanism works on multiple nodes. It has the ability to connect network-wide computational resources together, turning our network into a supercomputer-like, network-wide computation platform.

## 10.3. Determinism

On a blockchain network, one block is usually proposed by a selected block producer, making other validators responsible for verifying transactions by re-executing them and confirming the same results. Only then will validators confirm the status of the block.

However, as mentioned above, shared states may be updated by different threads in a nondeterministic way. Thus, validators cannot reproduce the producer’s execution results reliably. In this case, a consensus can’t be reached, and the network will come to a complete stop.

Arcology’s design employs a deterministic concurrency management system to guarantee that shared states are accessed and updated in a deterministic way. Developers can fully utilize the computational power of multiple-processor architectures without sacrificing state consistency.

## 10.4. Design Considerations

When it comes to concurrency control mechanism, there are broadly two major strategies: prevention and recovery. The former prevents problems from happening, while the latter tries to recover inconsistent states when they do happen. They are referred to as “optimistic” and “pessimistic” concurrency control.

When used for thread synchronization, so-called “synchronization primitives” usually work well. However, they require developers to pay extra attention when locking and unlocking resources. Furthermore, lock granularity will impact overall network performance: coarse grain locks force much of the code to be executed in serial order (inefficiency), while fine grain locks are harder to design and more prone to deadlocks (dysfunction). This forces design to sacrifice some features for others.

Locking management usually works in a timing-dependent manner: The first thread has the exclusive privilege to update the shared states associated with the lock. Due to the inherent unpredictability of multi-threaded systems, this sequence is broadly nondeterministic. This isn’t a big problem for centralized systems, but it’s incompatible with blockchain architectures.

Another option is software transactional memory (STM). With no locking necessarily required, STM hides the difficulty of assigning properly grained locks from developers. Reads and writes are wrapped into transactions and recorded in independent buffers owned by different threads in isolation as they happen. At commit time, the STM manager collects records from thread buffers and checks for conflicts; any threads that cause conflicts are discarded.

STM is a robust solution that offers the high performance of fine-grain locks — but only when the level of contention is low. When contention level is high, STM will discard a lot of transactions due to conflicts. Ideally, if there is no conflict at all, the overall complexity is **O**(1). While in the worst case, if all the threads need to access some shared states, the whole process will regress to serial execution with complexity of **O**(n).

Arcology’s concurrency framework is a hybrid of both pessimistic and optimistic concurrency control mechanisms and, more importantly, it has a deterministic concurrency model. The framework is composed of a combination of locks, atomic functions, a deterministic synchronization primitive manager and distributed virtual concurrent memory (DVCM) to ensure state consistency and determinism.

The framework covers a broad area of issues in concurrent programing and determinism required by blockchain systems. Developers are given freedom to choose between fine-grain blocks, built-in atomic functions or concurrent containers to develop their smart contracts.

At its core, this framework is a standalone module. It is not a part of any particular smart contract programming language or virtual machine. It is VM- and language-neutral, and it can be deployed as an independent network service with just some language-specific adaptation needed.

## 10.5. Arcology Concurrency Framework

Arcology is capable of supporting parallel transaction processing on a cluster of a few thousand machines, and our concurrency framework provides a high-level deterministic concurrency mechanism that’s generic enough to cover all key aspects of coordinating shared state accesses.

The concurrency framework is designed to work in heterogeneous environment and has the following features:

-	**Multithreading support:** Spreading transaction processing tasks to all processor cores in a single machine
-	**Cluster support:** Spreading transaction processing tasks to all processing cores on a computer cluster
-	**Transparency:** Physical configuration of the cluster should be transparent to developers. Developers only need to specify the maximum level concurrency required.
-	**Consistency:** Developers have a consistent experience. All computational resources are abstracted behind a consistent interface. Developers should not be able to tell if the computational resources are on local computers or other machines in cluster (though this information is fully available to them).
-	**Deterministic:** The framework is strictly deterministic.
-	**Built-in Protection:** The framework has internal mechanism to prevent intentional or unintentional misuse that cause race conditions or state inconsistency.
-	**Ease of use:** Arcology’s concurrency framework is very user-friendly. Developers can focus on building their apps, not configuring their environment.
-	**Platform neutrality:** The framework can potentially be used on all platforms.
-	**Flexibility:** Arcology has a collection of synchronization primitives such as locks, atomic function, deferred functions and lockless concurrent containers for developers to choose from, based on use cases.
- **Performance:** Fully utilize computational power to execute smart contracts in full parallel mode with minimum overhead.

## 10.6. Synchronization Primitives

Synchronization primitives help protect shared states. Proper use of these primitives ensures that, at any given moment, just one thread has the chance to modify the lock-protected shared resources. This prevents them from being modified by multiple threads in concurrent execution environments. Among all primitives, locking is the most common: a thread must set a lock to a shared variable before making any changes, and the lock is released only for the second thread. This process inevitably introduces network overhead.

Arcology’s concurrency framework includes a language- and VM-neutral locking system that protects shared states with minimum overhead. It is mainly aimed at facilitating synchronization among smart contracts running in heterogeneous virtual machines attempting to access some shared resources.

Smart contracts can run on different VMs within the same machine or even VMs hosted by different physical servers. On Arcology, it is perfectly reasonable for multiple smart contracts to run in heterogeneous virtual machines while trying to access shared states concurrently.

We also provide a consistent interface that developers can use without worrying about the underlying inter-VM communications and synchronization. Arcology takes care of all these details behind the scenes.

## 10.7. Distributed Virtual Concurrent Memory (DVCM)

Distributed virtual concurrent memory (DVCM) is a key part of Arcology concurrency framework for managing shared states generated from concurrent smart contract executions, detecting potential state conflicts and recovering state consistency, if needed.

DVCM stores temporary state transitions and provides a set of interfaces in a language-neutral way for developers to declare shared containers and variables and read/update them without explicitly using locks. DVCM is responsible for maintaining final consistency of all shared states in its virtual container by analyzing state transitions generated from all execution units, detecting conflicts and merge nonconflicting states at the end of each processing cycle.

The entire process is transparent to developers.

DVCM doesn’t exclude the use of locks. Rather, it minimizes the need for locks whenever possible. DVCM and locking can work perfectly together to achieve outstanding performance.

### 10.7.1. Concurrent Containers
For developers to fully utilize the concurrency mechanism, Arcology provides a collection of thread-safe containers that allow concurrent updates from multiple smart contract instances running in different VMs. Concurrent containers can be used in both lock or lock-free way.
Declared containers have their own unique identifiers. All variables are globally visible and accessible under the same DVCM manager. Currently, Arcology provides two different types of concurrent containers: Concurrent Array and Concurrent Hashmap.

### 10.7.2. Concurrency Manager

Concurrency manager keeps a list of all concurrent arrays created by the smart contracts. The concurrent array manager connects to the DVCM through a concurrent library. Once a concurrent container is registered, all subsequent manipulation to the array is versioned and recorded.

### 10.7.3. Concurrent Array

Concurrent array is a fixed-length, sequence container. As with a conventional array, elements are accessed by their indices and can be manipulated in a thread-safe way. This means that multiple threads running in different VMs can read and write concurrent arrays simultaneously without causing state inconsistencies.

The interface to access concurrent containers is provided through a set of carefully designed system level smart contract calls deployed at reserved addresses. Every smart contract has its own dedicated virtual memory for concurrent variable and containers. When the array manager receives a request, queries the register if a container has been created or not. If it doesn’t exist, the manager creates a new one.

### 10.7.4. Concurrent Hashmap

Hashmap keeps a collection of key-value pairs. It is a concurrency-safe container for a number of elements, and it supports simultaneous operations such as concurrent append, and update and delete by multiple threads running in different VM containers.

### 10.7.5. Deferred Functions

Deferred functions are invoked when call functions are returned. They are system-provided lockless mechanisms offering highly efficient alternatives to lock-protected access. Using deferred calls is a convenient way to handle post-processing after concurrent smart contract executions are completed.

For many applications, it is a common requirement that the program be able to count invocations. For instance, a web application’s smart contract may need to count the number of visits in a certain time frame. This can be implemented in Arcology as a lock-guarded shared variable or a deferred function.
