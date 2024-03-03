---
description: Calculate the fees required for query
---

# Estimate fee

## Overview

This function calculates the fees required for the query. If the Gateway contract's `query()` sends less than the required fee, it is reverted as `InvalidFee`.

```solidity
function estimateQueryFee(
    QueryType.QueryRequest[] memory queries
) external view returns (uint256);
```

<table><thead><tr><th width="174.5">Field</th><th>Description</th></tr></thead><tbody><tr><td><code>queries</code></td><td>An array of <code>QueryRequest</code> data</td></tr></tbody></table>

## How to calculate

Light Client Contract's `estimateQueryFee()` calculates the Verification fee as explained in the Gateway contract.

Verification fees are divided into the following two categories;

* Relayer fee
* Oracle fee

### **Relayer fee**

Relayer fee is the fee paid to the Relayer and can be divided into two types of fees:

* Gas fee
  * Gas costs include base gas costs plus variable gas costs depending on query size
  * Add 21,000 gas per query
* Rewards for Relayer
  * This is the fee paid to the Relayer
  * At the moment we pay Relayer in Gelato

### **Oracle fee**

This is the fee paid to Oracle, which at this time is accounted for by converting the $LINK paid to Chainlink to the price of the native token by default.

Then use Chainlink's data feed to get the `LINK/Native Token` rate.
