---
description: Futaba's Basic Philosophy
---

# Concept

## Why Futaba?

Currently, blockchains are experiencing fragmentation of data including assets due to the rise of new L1 chains such as Aptos and Sui, and Layer2/Layer3 with Ethereum as the base layer. Also, the composability that had been maintained by having a common VM has become loosely coupled due to the diversification of the blockchain, which has greatly impaired the UX.&#x20;

To solve these problems, a number of Bridge protocols have been introduced to move assets to other chains, and messaging protocols that allow arbitrary messages to be sent to other chains as well as assets.&#x20;

However, while the number of protocols for "sending" data to other chains has increased, there are still few protocols for "retrieving" data from other chains.&#x20;

It is possible to retrieve data from other chains by applying Oracle or messaging protocols, but both methods are not necessarily highly secure and often involve extra costs.&#x20;

In other words, there is no optimized method for acquiring data from other chains.&#x20;

Therefore, Futaba provides an optimized method for data acquisition for other chains, facilitating the creation of more seamless cross-chain Dapps.

## Design Philosophy

### Extensibility

Futaba only needs to deploy the endpoint contract only to the chain it wants to request data from, not to each chain. Off-chain actors can also be implemented at a minimum using only Relayer.

This allows us to respond quickly to the increasing number of app-specific rollups that are frequently discussed these days.

### **Aggregativity**

Futaba can collect data from multiple chains at once, not just simple one-to-one data acquisition, such as from one chain to another.

This makes it possible to compare data across multiple chains, expanding the potential of the aggregator protocol, which has traditionally been completed with a single chain.

### Modularity

Futaba allows you to build your own verification logic. This will enable you to choose the verification method that best fits your Dapps and ecosystem and meets your needs.

For example, you can verify using the zk light client for improved security, or between rollups, you can leverage the state root stored in the settlement layer.

In terms of security, each Dapps or ecosystem can have its own contract or off-chain agent, so that even if a hack or other incident were to occur, the entire network would not be affected, minimizing damage.

This will allow for integration as a quick verification method in the future when zkp or better cryptography emerges and will allow us to keep up with the rapidly changing cryptography of the future.
