---
description: Processing performed by Light Client at the time of request
---

# Request Query

{% hint style="info" %}
This function is used when you want to implement your own logic at request time with Light Client Contract.

No need to implement your own if you don't want to.
{% endhint %}

```solidity
function requestQuery(QueryType.QueryRequest[] memory queries) external;
```

<table><thead><tr><th width="133.5">Field</th><th>Description</th></tr></thead><tbody><tr><td><code>queries</code></td><td>An array of <code>QueryRequest</code> data</td></tr></tbody></table>

Our early implementation with Oracle incorporates the following logic:

* Format `QueryRequest` into `dstChainId` and `height` only
* Making a request to Oracle using [Chainlink's Connecting to any API](https://docs.chain.link/any-api/introduction)
