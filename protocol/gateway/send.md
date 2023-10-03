---
description: Endpoint to request query
---

# Send

Execute this function via an interface from a User-defined contract In this case, it is necessary to send the fee to be paid to Relayer as `msg.value`.

```solidity
struct QueryRequest {
  uint32 dstChainId;
  address to;
  uint256 height;
  bytes32 slot;
}

function query(
  QueryRequest[] memory queries,
  address lightClient,
  address callBack,
  bytes calldata message
) external;
```

<table><thead><tr><th width="174.5">Field</th><th>Description</th></tr></thead><tbody><tr><td><code>queries</code></td><td>An array of <code>QueryRequest</code> data</td></tr><tr><td><code>lightClient</code></td><td>The address of the contract is to be verified</td></tr><tr><td><code>callBack</code></td><td>The address of the contract to return the data to</td></tr><tr><td><code>message</code></td><td>Data to be returned, in addition to the query</td></tr></tbody></table>

What the `query` function does:

* Encode the query data
* Calculate the query Id
* Execute the light client process as necessary
  * Currently, sending a request to Chainlink's Node Operator
* Emit a request event
* Pay fees to Relayer
  * Calculate the transaction fee off-chain and send the token based on it

#### Calculate the query Id

```solidity
bytes memory encodedPayload = abi.encode(
	callBack,
	queries,
	message,
	lightClient
);
bytes32 queryId = keccak256(abi.encode(encodedPayload, nonce));
```

Encode each field and the nonce again and hash it as `queryId`.

#### Emit a request event

Events are emitted with the following structure;

```solidity
event Packet(
	address indexed sender,
  	bytes32 indexed queryId,
	bytes packet,
	bytes message,
	address lightClient,
	address callBack
);
```

<table><thead><tr><th width="187">Field</th><th>Description</th></tr></thead><tbody><tr><td><code>sender</code></td><td>An user who executed the contract</td></tr><tr><td><code>queries</code></td><td>An array of <code>QueryRequest</code> data</td></tr><tr><td><code>packet</code></td><td><code>callBack</code>, <code>queries</code>, <code>message</code>, <code>lightClient</code> encoded</td></tr><tr><td><code>message</code></td><td>Data to be returned, in addition to the query</td></tr><tr><td><code>lightClient</code></td><td>The address of the contract is to be verified</td></tr><tr><td><code>callBack</code></td><td>The address of the contract to return the data to</td></tr></tbody></table>
