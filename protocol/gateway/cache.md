---
description: Reuse data acquired in the past
---

# Cache

This function is used when data retrieved in a previous query is to be used again and does not require access to off-chain agents, allowing for fast data access.

```solidity
function getCache(
	QueryType.QueryRequest[] memory queries
) external view returns (bytes[] memory);
```

<table><thead><tr><th width="136.5">Field</th><th>Description</th></tr></thead><tbody><tr><td><code>queries</code></td><td>An array of <code>QueryRequest</code> data</td></tr></tbody></table>

Here is what the `getCache` function does;

* calculates a key from the `queries`
* get the `QueryData[]` corresponding to the key
  * `QueryData` is made to consist of `height` and `result`
* retrieve the target data from `QueryData[]`
  * If a specific `height` is specified
    * Find the matching `QueryData`
  * If `height = 0`
    * Find the `QueryData` with the largest `height`
* Insert the retrieved data into the array
* Return the data
