# Lagrange

The Lagrange Protocol is a cross-chain infrastructure that enables the creation of generalized state proofs across all major blockchains.

Applications that integrate with the Lagrange Protocol can enable applications to submit aggregated proofs of multi-chain states that can be verified in a non-interactive fashion by contracts on other chains.&#x20;

Futaba can use this Lagrange as an Oracle to get the state root of various chains/rollups in a trustless manner.

{% embed url="https://lagrange-labs.gitbook.io/lagrange-labs/overview/what-is-the-lagrange-protocol" %}

```mermaid
graph RL;
	subgraph Src chain
    G[Gateway Contract]<-->|9. verify storage proof|L[LightClient Contract];
	end

	subgraph Off-chain
		G-->|1. emit event|R((Relayer));
		L-->|2. emit event|LG{Lagrange Oracle};
		LG-->|5. return and verify state proof|L
		R-->|8. return storage proof and value|G
	end

	subgraph Destination chain
		LG-->|3. query state proof|T[Target Contract]
		T-->|4. return state proof|LG
		R-->|6. query storage proof|T
		T-->|7. return storage proof and value|R
	end
```

The event received from the [LightClient](../light-client/) contract is used by the Lagrange-based Oracle to obtain the state proof of the Destination chain and return it to the [LightClient](../light-client/) contract, which stores the state root after successful verification and uses it to verify the account proof and storage proof received from the [Relayer](../relayer.md).
