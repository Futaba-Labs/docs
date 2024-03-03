---
description: Relayer is responsible for retrieving data and proof of other chains
---

# Relayer

Relayers act as intermediaries between the source chain and the destination chain. Their main functions are as follows:

* Monitor and receive query requests emitted from the [Gateway Contract](gateway/) on the source chain
* Obtain proof based on the query requests
  * Use `eth_getProof` to obtain account proof and a storage proof
* Send the proof as a transaction to the [Gateway Contract](gateway/) on the source chain

Today, Futaba operates its own Relayer. In the future, we will provide a module to customize Relayer more easily to support Proof of Block Hash when using [konoha](konoha/ "mention"), and aim to build a Permissionless Relayer.

The current Fee for Relayer can be found in [estimate-fee.md](light-client/estimate-fee.md "mention").
