# Concept

## 1. Problem statement

As Ethereum and other blockchain ecosystems continue to evolve, rollups, Layer 1 and Layer 2 blockchain networks are increasing daily. However, these chains and rollups are mostly isolated from one another. For example, the data of a dApp on Ethereum can only be accessed from within Ethereum - it cannot be accessed from rollups or Layer 2s like Optimism or Arbitrum.

To attempt to solve this, developers deploy a new set of contracts on a Layer 2. However, the data is a new set of data on the Layer 2. Now, they have more work: to manage two sets of data - Ethereum, and Layer 2, instead of just one.

### Current solution

3rd party bridge protocols: Send/push data of asset from 1 chain to another

3rd party messaging protocols: Send/push data of arbitrary message from 1 chain to another

### Current problems with this solution

High cost: Pushing data from Ethereum would incur Ethereum gas fees which are a lot higher than gas fees paid on L2s. 3rd party protocols also incur extra cost to reduce the time taken to complete the transaction.

High latency: Pushing data securely from Ethereum takes 15 minutes or more.

Reduced security: Pushing data relies on the security of a single 3rd party protocol. This is a single point of failure, without any alternative or backup method of security. In the event the protocol is exploited/hacked, the transaction along with its funds are affected.

### Futaba as a solution

**Lower cost:** Instead of push, pull mainnet Ethereum data from L2s to incur minimal fees.

**Lower latency:** Pulling data bypasses the 15+ minutes needed to push data from Ethereum.

**Modular security:** Developers can pick any modules of security for the oracles used in Futaba architecture, such as zero-knowledge validation, cryptographically secure cross-chain state proofs[ (Lagrange)](https://app.gitbook.com/o/Thz2mfuoktjdE6MeG8yW/s/sOs4pzHyvFKixViaeh5C/\~/changes/26/protocol/konoha/lagrange), third party oracles. This prevents single point of failure by relying a single 3rd party protocol.

**Data available AND interoperable:** Data unique to each rollup / chain is no longer siloed, no longer just available - it is now interoperable. Users can access it by pulling from 1 single source chain.



## 2. Design

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

This will allow for integration as a quick verification method in the future when zkp or better cryptography emerges and will allow us to keep up with the rapidly changing cryptography of the future. This is achieved with a Modular block header provider called [konoha](../protocol/konoha/ "mention").
