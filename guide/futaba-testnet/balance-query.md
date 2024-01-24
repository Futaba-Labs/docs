---
description: Aggregate the token balances
---

# Balance query

"Balance query" ([https://demo.futaba.dev/](https://demo.futaba.dev/)) involves retrieving the balances of tokens from other chains and minting a new token equivalent to their total.\
To submit the query, the following steps are required;

#### 1. Input the content of the query

Please input the choice of `chain` and `token address` to query.

The only tokens that can be queried are those received from [Faucet](https://demo.futaba.dev/faucet). If you wish to query any ERC20 token, use [custom-query.md](custom-query.md "mention").

If you want to add a query, please press "Add Query" and add a form. You can add up to a maximum of 5 queries.

Here are the token addresses that can be used for the balance query;

<table><thead><tr><th width="185">Chain</th><th width="322">Token address</th><th>Explorer</th></tr></thead><tbody><tr><td>Goerli</td><td><code>0x30D3C07CEB71553CABe5FA4d29fe4Ce2Aead38e5</code></td><td><a href="https://goerli.etherscan.io/address/0x30D3C07CEB71553CABe5FA4d29fe4Ce2Aead38e5">View on goerli.etherscan.io</a></td></tr><tr><td>Optimism Goerli</td><td><code>0x73969C83706a2aED1D5CB242CA365EdFe679DFE3</code></td><td><a href="https://goerli-optimism.etherscan.io/address/0x73969C83706a2aED1D5CB242CA365EdFe679DFE3">View on goerli-optimism.etherscan.io</a></td></tr><tr><td>Arbiturm Goerli</td><td><code>0xD3BbB5f1269e8Cd3677C951722dA5597D450D121</code></td><td><a href="https://goerli.arbiscan.io/address/0xD3BbB5f1269e8Cd3677C951722dA5597D450D121">View on goerli.arbiscan.io</a></td></tr></tbody></table>

<figure><img src="../../.gitbook/assets/balance_query" alt=""><figcaption></figcaption></figure>

#### 2. Submit the queries

Once you have completed entering the queries, press "Send Query" to submit them. A transaction will occur at this point, so please ensure you have enough MATIC.

You can obtain it from the [Mumbai faucet](https://mumbaifaucet.com/) if you don't have enough.

#### 3. Wait for the query results

After submitting the transaction, you can check it in the explorer ([https://demo.futaba.dev/explorer](https://demo.futaba.dev/explorer)).

The data you requested will remain in a "Pending" state until the response transaction is completed, at which point it will be displayed in the "Response Transaction" section of the explorer.

#### 4. Completion of the response transaction

Once the response transaction is completed, the transaction hash and status will change to "Delivered." You can navigate to the explorer from the transaction hash link and verify whether the token has been successfully minted.

Here is an example of a transaction: [https://mumbai.polygonscan.com/tx/0x9ca0acb540a5e91e7ea8eb5f45b1a38106d6d07e030cd3a8cb0e8999d27a4ba5](https://mumbai.polygonscan.com/tx/0x9ca0acb540a5e91e7ea8eb5f45b1a38106d6d07e030cd3a8cb0e8999d27a4ba5)
