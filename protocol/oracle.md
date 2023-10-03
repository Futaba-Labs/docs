---
description: Oracle is responsible for providing block headers for the destination chain
---

# Oracle

{% hint style="info" %}
Oracle is the component used for validation in Light Client Contract. Therefore, depending on the logic of the Light Client Contract, it may not need to be used (e.g., when using another on-chain Ligth Client).
{% endhint %}

Oracles function as follows:

* Monitor and receive query request events emitted by the Light Client Contract of the src chain.
* Acquire the block header corresponding to the designated block height in advance.
* Obtain only the state root from it and send it to the Light Client Contract.

These functions need to be defined using Chainlink Node Operator's Job.
