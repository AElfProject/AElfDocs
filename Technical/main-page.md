# Technical documentation for the Ælf project

As the whitepaper already states the AElf kernel will be built in a similar way to the Linux kernel. It will implement the basic building blocks that will allow other developers to build “functionality” on top of it. The whitepaper also states that users can redefine the “core” through interface.

## Table of Contents

* [Data Structures](#1data-structures)
* [Components](#2components)

## Data Structures

## Components

This section describes the components implemented in the kernel. It clarifies the roles that they have in the system.

### **Smart Contracts**

    
  A Smart Contract can be seen as a protocol. It’s implemented as a service (micro-service). For example, this means that since the Consensus Protocol is defined as a Smart Contract, it is in fact a service. When a chain is created, it needs genesis block. This collection can be changed in the future by vote.The contract code will be encapsulated in SmartContractRegistration and registered into AccountZero. Smartcontract object only can be cached in memory by  SmartContractZero from SmartContractRegistration

### **World State**

### **Merkle Tree** 

### **Provider**
- AccountDataProvider provides entries associated with given Account including:
    - DataProvider 
    - AccountDataContext 
    - Address 
- DataProvider provides entries for data related to given Account.

### **Service**
- AccountContextService provides functionality caching AccountDataContext objects in memory. 
    - Return AccountDataContext object in memory if cached
    - Return AccountDataContext object new created if not cached
- ChainCreationService provides functionality creating a new chain including building and appending GenesisBlock.
- ChainContextService provides functionality caching ChainContext objects in memory. 
    - Return ChainContext object in memory if cached
    - Return ChainContext object new created with SmartContractZero if not cached
- BlockValidatingService maintains BlockValidationFilter collection and provides entry of blocks validation
- SmartContractService provides functionality for obtaining SmartContract

### **Manager**

- **_BlockManager_** provides entries(get/set) for **_BlockStore_**
- **_ChainManager_** provides functionality of appending the given Block to specified Chain and entries for **_ChainBlockRelationStrore_**
- **_ChainManager_** provides entries(get/set）for **_ChainStore_**
- **_SmartContractManager_** provides entries(get/set）for **_SmartContractRegistration_** storage
- **_TransactionManager_** provides entries for **_TransactionSotre_**
- **_TransactionExecutingManager_** contains scheduling algorithm and provides functionality of **_Transaction_** executing
- **_WorldStateManager_** provides entry for **_WoldStatestore_** and functionality to obtain **_AccountDataProvider_** objects associated with given **_Account_**

### **Storage**

- **_BlockStore_**
- **_ChainBlockRelationStore_**
- **_ChainStore_**
- **_ChangesStore_**
- **_PointerStore_**
- **_SmartContractRegistrationStore_**
- **_TransactionStore_**
- **_WorldStateStore_**

### **Relation among Service, Manager, Storage**
- Service is processing logic associated with chain state
- Manager provides functions having nothing to do with chain state
- For storage access and persistence, no logic