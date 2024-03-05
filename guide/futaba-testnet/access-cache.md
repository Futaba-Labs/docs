---
description: Access past queries
---

# Access cache

Access cache is a feature that allows you to retrieve data queried in the past. Unlike [balance-query.md](balance-query.md "mention") or [custom-query.md](custom-query.md "mention"), it's a simple view function, so no transaction is generated. You can obtain it through the following steps;

#### 1. Input the content of the query

To access the cache, you will need to specify the choice of chain, contract address, block height, and storage slot, similar to a Custom query.&#x20;

<table><thead><tr><th width="109">Chain</th><th width="131">Block height</th><th width="243">Contract address</th><th>Slot</th></tr></thead><tbody><tr><td>Sepolia</td><td><code>5407197</code></td><td><code>0x91D1a12c16d2Ff1c072069a9d9c90d2c0299B244</code></td><td><code>0xf8a7b40e9f08589bcdc65a6dd287fc853d1877d75bf7422ff09c0651dea732a4</code></td></tr></tbody></table>

Please check [here](custom-query.md#1.-input-the-content-of-the-query) for information about storage slots.

<figure><img src="../../.gitbook/assets/Screenshot 2024-03-05 at 10.29.22 PM.png" alt=""><figcaption></figcaption></figure>

#### 2. Submit the queries

Once you have entered the query form, please press "Get Cache" to submit it.&#x20;

No transaction will occur.

#### 3. Display the query results

You can check the queried data under "Results."

It is displayed in bytes, so you will need to decode it to see the actual data.

<figure><img src="../../.gitbook/assets/Screenshot 2024-03-05 at 10.29.30 PM.png" alt=""><figcaption></figcaption></figure>
