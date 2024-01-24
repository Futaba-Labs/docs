---
description: >-
  Konoha is a module for retrieving the appropriate block header for each
  ecosystem
---

# Konoha

<figure><img src="../../.gitbook/assets/konoha.png" alt=""><figcaption></figcaption></figure>

### Motivation

Although this mechanism is scalable, its security is entirely dependent on a single network. Futaba always requires a block header (state root) to verify storage proof. In other words, the problem is how to get the block header to the trustless network to verify the proof, which is not optimized in the existing single network.&#x20;

And now, with the spread of Modular blockchain, Layer 2 with various combinations has appeared. For example, some have the Data Availability Layer as Celestia and the Settlement Layer as Ethereum, some have both the Data Availability Layer and the Settlement Layer as Ethereum, and some have both the Sovereign Rollups with Celestia as the Data Availability Layer have also appeared. Under such circumstances, it is necessary to provide a trustless block header based on the common part (Data Availability Layer and Settlement Layer) to achieve more optimal data acquisition and thus interoperability. Interoperability is achieved.

### Solution - Konoha

For this reason, Futaba offers Konoha as a Modular block header provider, which can be customized to any to retrieve block headers. This allows for the acquisition of block headers that are optimal for each ecosystem and application. This allows for quicker adoption of more optimal cryptographic technologies as they become available in the future.

### How to implement

Currently, Futaba provides a way to access its block headers as part of connecting to the LightClient Contract and adding its verification method. Therefore, it is necessary to implement proof verification and block header access in the same module. However, in the future, a more flexible data retrieval experience can be achieved by separating the verification method (general storage proof or proof in zkp) and the module for block header retrieval. And the current default is to use Chainlink Oracle.

Also, for Relayer, if there are partial modifications such as additional Proof by Konoha, it is necessary to implement Relayer on your own.
