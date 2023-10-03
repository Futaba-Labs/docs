---
description: Endpoints that receive query results from Relayer
---

# Receive

This function is the endpoint from which Relayer obtains the proof and returns it to the src chain.

```solidity
struct QueryResponse {
  bytes32 queryId;
  bytes proof;
}

function receiveQuery(QueryResponse memory response) external;
```

<table><thead><tr><th width="148.5">Field</th><th>Description</th></tr></thead><tbody><tr><td><code>response</code></td><td><code>QueryResponse</code> data</td></tr></tbody></table>

What the `receiveQuery` function does:

* Verify if Gelato's Relayer executed the function
* Verify the proof and extract the acquisition data
  * Done through the interface by the Light Client Contract
* Pay fees to the Relayer
* Return data to the user

To return data to the User Contract, the User Contract must inherit the following interface:

```solidity
interface IReceiver {
    function receiveQuery(
        bytes32 queryId,
        bytes[] memory results,
        QueryType.QueryRequest[] memory queries,
        bytes memory message
    ) external;
}
```
