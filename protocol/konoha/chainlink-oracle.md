# Chainlink Oracle

Chainlink Oracle is currently used as the default module for providing block headers in Futaba. Specifically, it requests a job that can be configured in the Chainlink Node to execute an API to retrieve block headers configured as an External Adapter and return them to the contract.

{% embed url="https://docs.chain.link/chainlink-nodes/external-adapters/external-adapters" %}

```mermaid
graph RL;
	subgraph Src chain
    G[Gateway Contract]<-->|9. verify proofs|L[LightClient Contract];
	end

	subgraph Off-chain
		G-->|1. emit event|R((Relayer));
		L-->|2. emit event|C{Chainlink Oracle};
		C-->|5. return and store state root|L
		R-->|8. return account and storage proof and value|G
	end

	subgraph Destination chain
		C-->|3. query state root|T[Target Contract]
		T-->|4. return state root|C
		R-->|6. query account and storage proof|T
		T-->|7. return account and storage and value|R
	end
```

In the case of Chainlink, the state root is directly obtained and stored, not the block header.
