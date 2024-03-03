---
description: Calculate the fees required for query
---

# Estimate fee

## Overview

This function calculates the fees required for the query. If the Gateway contract's `query()` sends less than the required fee, it is reverted as `InvalidFee`.

```solidity
struct QueryRequest {
  uint32 dstChainId;
  address to;
  uint256 height;
  bytes32 slot;
}

function estimateFee(
  address lightClient,
  QueryType.QueryRequest[] memory queries
) public view returns (uint256);
```

<table><thead><tr><th width="174.5">Field</th><th>Description</th></tr></thead><tbody><tr><td><code>lightClient</code></td><td>The address of the contract is to be verified</td></tr><tr><td><code>queries</code></td><td>An array of <code>QueryRequest</code> data</td></tr></tbody></table>

## How to calculate

In `estimateFee()`, the function calculates the sum of the fees for each actor, such as Relayer, Oracle, etc.

There are two main categories of the fee;

* Protocol fee
* Verification fee

Of these, only the Protocol fee is calculated by Gateway contract's `estimateFee()` itself. The verification fee is calculated by [`estimateQueryFee()`](../light-client/estimate-fee.md) of the Light Client Contract.
