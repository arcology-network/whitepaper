---
id: smart-contract
title: Smart Contract
---

## 7 Smart Contract

Put simply, a smart contract allows complex business logic to be executed within virtual machines. There are different kinds of VMs in the blockchain world; they’re designed with different focuses and priorities. Some may put more emphasis on transparency, for example, while others prioritize confidentiality or security.

On all blockchain networks, the smart contract is platform-dependent. This makes it virtually impossible for any given smart contract to be seamlessly transplanted between platforms without explicitly rewriting everything. It is also very difficult for developers to apply their knowledge and development experience accumulated on one platform if they move to another.

Arcology is changing this by introducing the concept of the generic VM container. An Arcology VM container is encapsulated as a stateless transaction execution unit (EU) for processing state transitions.

Smart contracts written for other platforms, in different language, developed in other environments can be seamlessly embedded into Arcology. For example, Arcology supports Ethereum solidity and its development environments transparently. This means that smart contracts written for Ethereum can be used on Arcology with minimal or no modifications.

What’s more, because different smart contract languages may use different interfaces to interact with state data, we designed a generic state storage. Arcology’s state storage module is platform neural and consists two major components:

- **Adaptor:** A VM specific adaptor to separate the VM from Arcology storage component, state queries made to VM’s native state storage will be redirected to the Arcology’s state access layer.
- **Interface:** The uniform state access interface connection to backend database system, query and retrieve data from Arcology state database.   

![Smart Contract](/img/7-smart-contract.png)
