---
description: Futaba's Basic Philosophy
---

# Concept

## Problem statement

As Ethereum and other blockchain ecosystems continue to evolve, rollups, Layer 1 and Layer 2 blockchain networks are increasing daily. However, these chains and rollups are mostly isolated from one to another. For example, the data of a dApp on Ethereum can only be accessed from within Ethereum - it cannot be accessed from rollups or Layer 2s like Optimism or Arbitrum.

To attempt to solve this, developers deploy a new set of contracts on a Layer 2. However, the data is a new set of data on the Layer 2. Now, they have more work: to manage two sets of data - Ethereum, and Layer 2, instead of just one.

### Current solution

3rd party bridge protocols: Send/push data of asset from 1 chain to another

3rd party messaging protocols: Send/push data of arbitrary message from 1 chain to another

### Current problems with this solution

High cost: Pushing data from Ethereum would incur Ethereum gas fees which are a lot higher than gas fees paid on L2s. 3rd party protocols also incur extra cost to reduce the time taken to complete the transaction.

High latency: Pushing data securely from Ethereum takes 15 minutes or more.

Reduced security: Pushing data relies on the security of a single 3rd party protocol. This is a single point of failure, without any alternative or backup method of security. In the event the protocol is exploited/hacked, the transaction along with its funds are affected.

## Futaba's solution to this problem

Lower cost: Instead of push, pull data from Ethereum from L2s incur minimal fees.

Lower latency: Pulling data bypasses the 15+ minutes needed to push data from Ethereum.

Modular security: Developers can pick any modules of security for the oracles used in Futaba architecture, such as zero-knowledge validation, cryptographically secure cross-chain state proofs, third party oracles. This prevents single point of failure by relying a single 3rd party protocol.



## Why Futaba?

Currently, blockchains are experiencing fragmentation of data including assets due to the rise of new L1 chains such as Aptos and Sui, and Layer2/Layer3 with Ethereum as the base layer.

Besides that, the composability that has been maintained by having a common VM has become loosely coupled because of blockchains are becoming more diverse and increasing in numbers. Thus, the user experience of interacting across many blockchains is inconvenient and tedious.

To solve these problems, a number of Bridge protocols have been introduced to move assets to other chains, as well as messaging protocols that allow arbitrary messages and/or assets to be sent to other chains.&#x20;

However, while the number of protocols for "sending" data to other chains has increased, there are still few protocols for "retrieving" data from other chains.&#x20;

It is possible to retrieve data from other chains by applying Oracle or messaging protocols, but both methods are not necessarily highly secure and often involve extra costs.&#x20;

In other words, there is no optimized method for acquiring data from other chains.&#x20;

Therefore, Futaba provides an optimized method for data acquisition for other chains, facilitating the creation of more seamless cross-chain Dapps.

## Design Philosophy

### Extensibility

**Instead of deploying on all chains, deploy Futaba endpoint contract only from chains you want to request data from. Off-chain actors can also be implemented at a minimum using only Relayer.**

Benefits: Got a new app-specific rollup? Just deploy another Futaba endpoint contract, and request that data right away.&#x20;

### **Aggregativity**

**Collect data from multiple chains at once, not just simple one-to-one data acquisition, such as from one chain to another.**

Benefits: Compare data across multiple chains, expanding the potential of the aggregator protocol, which has traditionally been completed with a single chain.

### Modularity

**Build your own verification logic. This will enable you to choose the verification method that best fits your Dapps and ecosystem and meets your needs.**

For example, you can verify using zk light client for improved security, or between rollups, you can leverage the state root stored in the settlement layer.

In terms of security, each Dapps or ecosystem can have its own contract or off-chain agent, so that even if a hack or other incident were to occur, the entire network would not be affected. Thus, minimizing damage.

This will allow for integration as a quick verification method in the future when zkp or better cryptography emerges and will allow us to keep up with the rapidly changing cryptography of the future.
