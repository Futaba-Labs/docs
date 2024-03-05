---
description: Aggregate the token balances
---

# Balance query

"Balance query" ([https://testnet.futaba.dev/](https://demo.futaba.dev/)) involves retrieving the balances of tokens from other chains and minting a new token equivalent to their total.\
To submit the query, the following steps are required;

#### 1. Input the content of the query

Please input the choice of `chain` and `token address` to query.

The only tokens that can be queried are those received from [Faucet](https://demo.futaba.dev/faucet). If you wish to query any ERC20 token, use [custom-query.md](custom-query.md "mention").

If you want to add a query, please press "Add Query" and add a form. You can add up to a maximum of 5 queries.

Here are the token addresses that can be used for the balance query;

<table><thead><tr><th width="185">Chain</th><th width="322">Token address</th><th>Explorer</th></tr></thead><tbody><tr><td>Sepolia</td><td><code>0x91D1a12c16d2Ff1c072069a9d9c90d2c0299B244</code></td><td><a href="https://sepolia.etherscan.io/address/0x91D1a12c16d2Ff1c072069a9d9c90d2c0299B244">View on sepolia.etherscan.io</a></td></tr><tr><td>Optimism Sepolia</td><td><code>0x21370CaE272802491CB4115EF4e188Ac3721d992</code></td><td><a href="https://sepolia-optimism.etherscan.io/address/0x21370CaE272802491CB4115EF4e188Ac3721d992">View on sepolia-optimism.etherscan.io</a></td></tr><tr><td>Arbiturm Sepolia</td><td><code>0x0Ea06D21B4163E9C60063e562cBd1739aE7B7015</code></td><td><a href="https://sepolia.arbiscan.io/address/0x0Ea06D21B4163E9C60063e562cBd1739aE7B7015">View on sepolia.arbiscan.io</a></td></tr></tbody></table>

<figure><img src="../../.gitbook/assets/Screenshot 2024-03-03 at 6.54.20 PM.png" alt=""><figcaption></figcaption></figure>

#### 2. Submit the queries

Once you have completed entering the queries, press "Send Query" to submit them. A transaction will occur at this point, so please ensure you have enough MATIC.

You can obtain it from the [Mumbai faucet](https://mumbaifaucet.com/) if you don't have enough.

#### 3. Wait for the query results

After submitting the transaction, you can check it in the explorer ([https://testnet.futaba.dev/explorer](https://demo.futaba.dev/explorer)).

The data you requested will remain in a "Pending" state until the response transaction is completed, at which point it will be displayed in the "Response Transaction" section of the explorer.

#### 4. Completion of the response transaction

Once the response transaction is completed, the transaction hash and status will change to "Delivered." You can navigate to the explorer from the transaction hash link and verify whether the token has been successfully minted.

Here is an example of a transaction: [https://mumbai.polygonscan.com/tx/0x9ca0acb540a5e91e7ea8eb5f45b1a38106d6d07e030cd3a8cb0e8999d27a4ba5](https://mumbai.polygonscan.com/tx/0x9ca0acb540a5e91e7ea8eb5f45b1a38106d6d07e030cd3a8cb0e8999d27a4ba5)
