---
description: Retrieve arbitrary values
---

# Custom query

A custom query, unlike [balance-query.md](balance-query.md "mention"), is a feature that allows you to retrieve arbitrary data and emit it as an event. Essentially, you can send a query in a similar manner to a balance query, but the input fields are different.

#### 1. Input the content of the query

To submit a query, you need to specify the choice of chain, the target contract address, the block height, and the storage slot.

You can use tools like [solc](https://docs.soliditylang.org/en/v0.8.19/using-the-compiler.html) or [foundry](https://book.getfoundry.sh/reference/forge/forge-inspect#examples) to determine storage slots. The mapping of storage slots in Solidity is documented in the [official Solidity documentation](https://docs.soliditylang.org/en/v0.8.19/internals/layout\_in\_storage.html).

Additionally, for clearer explanations, you can refer to [the documentation](https://docs.axiom.xyz/developers/sending-a-query/finding-storage-slots) provided by Axiom.

If you don't have data to query, you can use the following sample data to execute the query.\
(You can query the Sepolia USDC held by `0x1aaaeb006AC4DE12C4630BB44ED00A764f37bef8`)

<table><thead><tr><th width="112">Chain</th><th width="129">Block height</th><th width="243">Contract address</th><th>Slot</th></tr></thead><tbody><tr><td>Sepolia</td><td><code>5407197</code></td><td><code>0x91D1a12c16d2Ff1c072069a9d9c90d2c0299B244</code></td><td><code>0xf8a7b40e9f08589bcdc65a6dd287fc853d1877d75bf7422ff09c0651dea732a4</code></td></tr></tbody></table>

#### 2. Submit the queries

Like the balance query, you will need MATIC to send the transaction since it involves sending a transaction.

#### 3. Wait for the query results

You can check the status of the query in the Explorer.

#### 4. Completion of the response transaction

Once the response transaction is completed, you can view the actual transaction from the transaction hash, and you will be able to verify the data queried in the event section.

Here is an example of a transaction: [https://mumbai.polygonscan.com/tx/0x749c8a652131fdc665928d86eb3f8a16d4f1db01bb007c82d1ffb978f42ad688#eventlog](https://mumbai.polygonscan.com/tx/0x749c8a652131fdc665928d86eb3f8a16d4f1db01bb007c82d1ffb978f42ad688#eventlog)
