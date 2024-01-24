---
description: Access past queries
---

# Access cache

Access cache is a feature that allows you to retrieve data queried in the past. Unlike [balance-query.md](balance-query.md "mention") or [custom-query.md](custom-query.md "mention"), it's a simple view function, so no transaction is generated. You can obtain it through the following steps;

#### 1. Input the content of the query

To access the cache, you will need to specify the choice of chain, contract address, block height, and storage slot, similar to a Custom query.&#x20;

<table><thead><tr><th width="97">Chain</th><th width="131">Block height</th><th width="243">Contract address</th><th>Slot</th></tr></thead><tbody><tr><td>Goerli</td><td>8947360</td><td><code>0xA2025B15a1757311bfD68cb14eaeFCc237AF5b43</code></td><td><code>0xac94f423a384a9d9a46ae4ac92c45b0aac171c967c618e74db0938ae8eb3d349</code></td></tr></tbody></table>

Please check [here](custom-query.md#1.-input-the-content-of-the-query) for information about storage slots.

<figure><img src="../../.gitbook/assets/cache_query" alt=""><figcaption></figcaption></figure>

#### 2. Submit the queries

Once you have entered the query form, please press "Get Cache" to submit it.&#x20;

No transaction will occur.

#### 3. Display the query results

You can check the queried data under "Results."

It is displayed in bytes, so you will need to decode it to see the actual data.

<figure><img src="../../.gitbook/assets/cache_result" alt=""><figcaption></figcaption></figure>
