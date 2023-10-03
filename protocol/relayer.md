---
description: Relayer is responsible for retrieving data and proof of other chains
---

# Relayer

Relayers act as intermediaries between the source chain and the destination chain. Their main functions are as follows:

* Monitor and receive query requests emitted from the Gateway Contract on the source chain
* Obtain proof based on the query requests
  * Use `eth_getProof` to obtain account proof and a storage proof
* Send the proof as a transaction to the Gateway Contract on the source chain

Currently using [Gelato](https://www.gelato.network/), including the risk of private key management and simplification of the fee system. However, we may build our own Relayer in the future.

Click [here](https://docs.gelato.network/developer-services/relay/payment-and-fees#gelatos-fees) for a list of fees collected by Gelato.
