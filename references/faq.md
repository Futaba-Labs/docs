---
description: Basic questions about Futaba
---

# FAQ

<details>

<summary>What is Futaba?</summary>

Futaba is a modular omnichain interface enabling communication between contracts, rollups and blockchain networks by querying and pulling data from a single source chain.

</details>

<details>

<summary>How do you execute a query?</summary>

For the architectural aspects of how it is performed, please see [here](../introduction/architecture.md).&#x20;

Also, see the [example contract](https://github.com/Futaba-Labs/solidity-example) for how to request a query

</details>

<details>

<summary>What blockchains are supported?</summary>

Currently, Ethereum Goerli, Polygon Mumbai, Arbitrum Goerli, and Optimism Goerli. A list of contract addresses can be found [here](contract-addresses.md).

</details>

<details>

<summary>When will (insert name) chain / rollup be supported by Futaba?</summary>

We discuss this with our friends and builders in our Discord.&#x20;

If you are building an L1, L2 or rollup, please provide your details [here](broken-reference).\
We will be in touch with you.&#x20;

</details>

<details>

<summary>How can I get involved and build with Futaba?</summary>

Please fill up the details [here](https://b6xxe4i0amr.typeform.com/to/w4wGLvbs), and you'll be added to our Discord.

</details>

<details>

<summary>What is the difference between other approaches ( e.g. Oracle, Messaging)?</summary>

Oracle and Messaging (General Messaging Protocols) can also retrieve on-chain data, but each has its own problems.

**In Oracle**, distributed networks are mostly used, but the problem is that if the off-chain security is low, the security of the chain itself is compromised when communicating between blockchains and working with the off-chain. Therefore, a cryptographic approach is adopted as a form of reducing off-chain third parties as much as possible.

We believe that in the future, infrastructure with minimal trust will be required, like Cosmos IBC or bridge using zkp

**In messaging**, when attempting to retrieve data, it is necessary to deploy the contract to the source and destination chains, as well as to send the messaging back and forth. This results in increased fees and reduced speed.

</details>

<details>

<summary>Is there a possibility of collusion between Oracle and Relayer?</summary>

No. Relayers can be built permissionless. On the other hand, Oracle utilizes Chainlink and depends on Chainlink's network. Therefore, in order to collude, it is necessary to break through Chainlink's security.

</details>

<details>

<summary>What is the difference between the roles of Oracle and Relayer?</summary>

The difference between the two is how they contribute to on-chain validation. Oracle has two roles.&#x20;

One is to supply the latest block headers.

The second is to execute the query. Relayer also has two roles. One is to retrieve the proof contained in the query request. The second is to execute the query.

</details>

<details>

<summary>How much latency will occur?</summary>



Slight latency is incurred because it is necessary to wait for a certain number of blocks to prevent hard forking.

</details>

<details>

<summary>What are future plans for Futaba?</summary>

We are currently live on [Testnet](https://demo.futaba.dev)! Expecting Mainnet in Q1 2024.

Expect some new protocols and dapps to be built powered by Futaba.

</details>

<details>

<summary>What is a Gateway?</summary>

The Gateway is the endpoint on the contract that makes the query request.

See [here](../protocol/gateway/) for more information.

</details>

<details>

<summary>What is a Light Client?</summary>

A light client is a contract that validates the acquired data. The contract can be developed by anyone, allowing you to build your own verification logic for your Dapps and ecosystem.\
See [here](../protocol/light-client/) for more information.

</details>

<details>

<summary>What is a Relayer?</summary>

The relayer is an off-chain agent that receives events from the Gateway Contract and retrieves data.\
See [here](../protocol/relayer.md) for more information.

</details>

<details>

<summary>What is Konoha?</summary>

Konoha is a module for retrieving the appropriate block header for each ecosystem. The default is Chainlink Oracle, with the possibility of using ZK Coprocessors such as Largange or Herodotus in the future.

For more information, please click [here](../protocol/konoha/).

</details>
