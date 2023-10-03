---
description: Execute simple queries
---

# Quick Start

{% hint style="info" %}
Futaba is still under development and its use may change before its official release.

We do not recommend using Futaba in a production environment at this time.
{% endhint %}

You can easily retrieve data from other chains as long as you implement `send()` and `receiveQuery()`.

The structure of the data and what it actually does is described in the [protocol](broken-reference) section.

Here we will try to implement a contract that gets the balance of any token in any other chain from the src chain and mints a new token of that amount.

The sample code itself is in this [repository](https://github.com/Futaba-Labs/solidity-example) and can be cloned.

## Create new project

In this example we will use hardhat;

```sh
$ npx hardhat
888    888                      888 888               888
888    888                      888 888               888
888    888                      888 888               888
8888888888  8888b.  888d888 .d88888 88888b.   8888b.  888888
888    888     "88b 888P"  d88" 888 888 "88b     "88b 888
888    888 .d888888 888    888  888 888  888 .d888888 888
888    888 888  888 888    Y88b 888 888  888 888  888 Y88b.
888    888 "Y888888 888     "Y88888 888  888 "Y888888  "Y888

👷 Welcome to Hardhat v2.9.9 👷‍

? What do you want to do? …
  Create a JavaScript project
❯ Create a TypeScript project
  Create an empty hardhat.config.js
  Quithe
```

Choose a Typescript project. Choose `y` on all of the prompts.

First, install the OpenZeppelin package;

{% tabs %}
{% tab title="npm" %}
```sh
npm install @openzeppelin/contracts
```
{% endtab %}

{% tab title="yarn" %}
```sh
yarn add @openzeppelin/contracts
```
{% endtab %}
{% endtabs %}

Next, install the relay SDK for gelato;

{% tabs %}
{% tab title="npm" %}
```sh
npm install @gelatonetwork/relay-sdk^4.0.0
```
{% endtab %}

{% tab title="yarn" %}
```sh
yarn add @gelatonetwork/relay-sdk^4.0.0
```
{% endtab %}
{% endtabs %}

Install `dotenv` to protect your private key needed to deploy your contract;

{% tabs %}
{% tab title="npm" %}
```sh
npm install dotenv
```
{% endtab %}

{% tab title="yarn" %}
```sh
yarn add dotenv
```
{% endtab %}
{% endtabs %}

At the root of your project, create a new `.env` file. Here you will store your private key used to deploy your contract.

Update `.env` with the following line:

```
PRIVATE_KEY = <YOUR-PRIVATE-KEY-HERE>
```

## Define the interface

First, we need to define the structs involved in the query;

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;

contract QueryType {
    struct QueryRequest {
        uint32 dstChainId;
        address to;
        // block height
        uint256 height;
        // storage slot
        bytes32 slot;
    }
}
```

Define an `IGateway.sol` to execute the `query()` function;

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;

import "./QueryType.sol";

/**
 * @title Gateway interface
 * @notice This interfece is an endpoint for executing query
 */
interface IGateway {
    /**
     * @notice This contract is an endpoint for executing query
     * @param queries query data
     * @param lightClient The light client contract address
     * @param callBack The callback contract address
     * @param message Data used when executing callback
     */

    function query(
        QueryType.QueryRequest[] memory queries,
        address lightClient,
        address callBack,
        bytes calldata message
    ) external payable;
}

```

Also, create `IReceiver.sol` that defines the `receiveQuery()` function to receive the results of the query;

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;

import "./QueryType.sol";

/**
 * @title Receiver interface
 * @notice This interface is for the user to receive the results of the query
 */
interface IReceiver {
    /**
     * @notice This function is used to receive the results of the query
     * @param results The results of the query
     * @param queries The query data
     * @param message Data to be used in the callback sent at the time of the request
     */
    function receiveQuery(
        bytes32 queryId,
        bytes[] memory results,
        QueryType.QueryRequest[] memory queries,
        bytes memory message
    ) external;
}

```

## Send function

From here, the contract for the actual request is defined. First, define the function that will execute the query request.

```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;

import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "./QueryType.sol";
import "./IReceiver.sol";
import "./IGateway.sol";

/**
 * @title BalanceQuery
 * @notice Example contract to execute and receive queries
 */
contract BalanceQuery is Ownable, ERC20, IReceiver {
    // Gateway Contract endpoint
    address public gateway;

    // Address of contract to verify storage proof
    address public ligthClient;

    constructor(address _gateway, address _lightClient)
        ERC20("Futaba Test Token", "FTB")
    {
        gateway = _gateway;
        ligthClient = _lightClient;
    }

    /** @notice Query execution via gateway contract
    * @param queries Information for doing a query, see QueryType.sol
    * @param decimals Decimals of tokens
    */
    function sendQuery(
        QueryType.QueryRequest[] memory queries,
        uint256[] calldata decimals
    ) public payable {
        // Encode the decimal number of the token and the address to mint the token
        bytes memory message = abi.encode(decimals, msg.sender);
        
        // Check to see if fee has been sent
        require(msg.value > 0, "Insufficient fee");
        
        // Execute query from gateway contract
        IGateway(gateway).query{value: msg.value}(
            queries,
            ligthClient,
            address(this), // callback address
            message
        );
    }
}

```

## Receive function

Create a function that receives the result of the query in the same Contract.

<pre class="language-solidity"><code class="lang-solidity">/** @notice Receive query results
    * @param queryId Unique id that can refer to query results, etc.
    * @param results Results of query in byte format
    * @param queries Information for doing a query, see QueryType.sol
    * @param message Encoded data for non-query use
    */

function receiveQuery(
        bytes32 queryId,
        bytes[] memory results,
        QueryType.QueryRequest[] memory queries,
        bytes memory message
    ) public onlyGateway {
        /* 
        Decode the data stored when requesting the query
        (in this case the decimal number of the token and the address to mint)
        */
        (uint256[] memory decimals, address sender) = abi.decode(
            message,
            (uint256[], address)
        );

        // Mint the total token balance received
        uint256 amount;
        for (uint i = 0; i &#x3C; results.length; i++) {
            uint256 balance = uint256(bytes32(results[i]));
            uint256 decimal = decimals[i];
            amount += balance * (10 ** (18 - decimal));
        }
        _mint(sender, amount);
    }
    
    /** @notice Allow data to be received only from gateway contract
    */
<strong>modifier onlyGateway() {
</strong><strong>    require(msg.sender == gateway, "Only gateway can call this function");
</strong><strong>    _;
</strong>}
</code></pre>

Now that you have finished writing the sample code, compile and deploy it.

Please check [here](../references/contract-addresses.md) for the target network and contract address.

## Executing the Transaction <a href="#executing-the-transaction" id="executing-the-transaction"></a>

Here we create a script to execute the query from the client side.

```typescript
import { ethers } from "hardhat";
import { BigNumber } from "ethers";
import { concat, hexZeroPad, keccak256 } from "ethers/lib/utils";
import { GelatoRelay } from "@gelatonetwork/relay-sdk";
import { QueryType } from "../typechain-types/contracts/BalanceQuery";

// Initialize Gelato
const relay = new GelatoRelay();

async function main() {
  const balanceQuery = await ethers.getContractAt("BalanceQuery", DEPLOYED_ADDRESS)

  // Calculate storage slot for a particular user's token balance
  const slot = concat([
    hexZeroPad(ANY_WALLET_ADDRESS, 32),
    hexZeroPad(BigNumber.from(0).toHexString(), 32),
  ]);

  const slot2 = concat([
    hexZeroPad(ANY_WALLET_ADDRESS, 32),
    hexZeroPad(BigNumber.from(0).toHexString(), 32),
  ]);

  // USDC on Goerli
  const src = "0xA2025B15a1757311bfD68cb14eaeFCc237AF5b43"

  // Struct contains the id of the chain, the target contract, the height of the specific block, and the target storage slot.
  const queries: QueryType.QueryRequestStruct[] = [
    {
      dstChainId: 5, to: src, height:
        8947355, slot: keccak256(slot)
    },
    {
      dstChainId: 5, to: src, height:
        8975344, slot: keccak256(slot2)
    },
  ]


  try {
    // Estimated gas cost to pay for Gelato's relayer
    const fee = await relay.getEstimatedFee(80001, "0xEeeeeEeeeEeEeeEeEeEeeEEEeeeeEeeeeeeeEEeE", BigNumber.from("1000000"), true)
    const tx = await balanceQuery.sendQuery(queries, [6, 6], { gasLimit: 1000000, value: fee.mul(120).div(100) })
    await tx.wait()
    console.log(tx)
  } catch (error) {
    console.error(error)
  }

}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});

```

Then run the script with the following command;

{% tabs %}
{% tab title="npm" %}
```sh
npm hardhat run --network mumbai scripts/requestQuery.ts
```
{% endtab %}

{% tab title="yarn" %}
```sh
yarn hardhat run --network mumbai scripts/requestQuery.ts
```
{% endtab %}
{% endtabs %}
