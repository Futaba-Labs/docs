---
description: Build your own Light Client Contract
---

# Customize Light Client

As mentioned [here](../protocol/light-client/), Futaba allows you to build the verification logic part at will.

If the target contract extends `ILightClient.sol` and defines `verify()` , `requestQuery()` and `estimateFee()` You can build your own logic at a minimum.

{% code title="ILightClient.sol" %}
```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;

import "../QueryType.sol";

/**
 * @title Light client interface
 * @notice This interface is for the verification of proof
 */

interface ILightClient {
    /**
     * @notice This function is intended to make Light Client do something when a query request is made (mock emit events to Oracle)
     * @param queries request query data
     */
    function requestQuery(QueryType.QueryRequest[] memory queries) external;

    /**
     * @notice This function is for validation upon receipt of query(mock verifies account proof and storage proof)
     * @param message response query data
     */
    function verify(
        bytes memory message
    ) external returns (bool, bytes[] memory);

    /**
     * @notice Estimated fees to be collected on the LightClient Contract side
     * @param queries request query data
     */
    function estimateFee(
        QueryType.QueryRequest[] memory queries
    ) external view returns (uint256);
}

```
{% endcode %}

By default, the block header (state root) supplied by Oracle and the storage proof received from Relayer are verified by Merkle Patricia Trie (MPT).

In the future, we can develop modules using zkp and a block hash Aggregator such as [Hashi](https://github.com/gnosis/hashi).

{% hint style="info" %}
When customizing, it may be necessary to build your own Relayer separate from the current Relayer.
{% endhint %}
