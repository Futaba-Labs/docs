# Futaba SDK

Futaba SDK is an npm package for calculating transaction fees and executing queries.

## How to install

To install the package into your DApp as a project dependency, run this command:

```bash
# npm
npm i @futaba-lab/sdk

# yarn
yarn add @futaba-lab/sdk
```

## How to use

### FutabaQueryAPI

FutabaQueryAPI allows you to quote commissions.

In the future, it will be able to perform transaction references, etc.

#### Initialization

To initialize FutabaQueryAPI, the following inputs are required;

* `stage`
  * You can choose between testnet (`ChainStage.TESTNET`) or mainnet (`ChainStage.MAINNET`)
* `chainId`
* `rpc`
  * Specify a JSON-RPC endpoint such as Infura or Alchemy
  * This param is an option since the default endpoint is set
* `lightClient`
  * This param is an option since the default endpoint is set

```typescript
constructor(stage: ChainStage, chainId: ChainId, options?: {
    rpc?: string
    lightClient?: string
})

const chainStage = ChainStage.TESTNET // or MAINNET
const chainId = 80001 // Mumbai
const rpc = "http://localhost:8545" // option
const lightClient = "0x3fab87824ABbe2DC686ed5CbB032d9c62E2fe179" // option

const queryAPI = new FutabaQueryAPI(chainStage, chainId, { rpc, lightClient })
```

#### estimateFee

```typescript
async estimateFee(queries: QueryRequest[], gasLimit?: BigNumber): BigNumber
```

Calculate query fees. Enter the `QueryRequest` array and `gaslimit`. `gasLimit` is set to `1000000` by default.

### FutabaGateway

FutabaGateway can run queries and access caches.

#### Initialization

* `stage`
  * You can choose between testnet (`ChainStage.TESTNET`) or mainnet (`ChainStage.MAINNET`)
* `chainId`
* `provider`
  * Specify `ethers.Wallet`, `ethers.providers.Web3Provider` or `ethers.Signer` in ethers.js.
* `lightClient`
  * This param is an option since the default endpoint is set

```typescript
constructor(stage: ChainStage, chainId: ChainId, provider: Provider, lightClient?: string)

const chainId = 80001
const chainStage = ChainStage.TESTNET
const wallet = new ethers.Wallet(privateKey, new ethers.providers.JsonRpcProvider(providerURL))
const gateway = new FutabaGateway(chainStage, chainId, wallet)
```

#### sendQuery

```typescript
async sendQuery(
    queries: QueryRequest[],
    callBack: string,
    message: string,
    gasLimit?: BigNumber
): Promise<QueryResponse>
```

Sends a Query to the Gateway Contract, entering the `QueryRequest` array, `callback` address, arbitrary `message`, and `gasLimit`. `gasLimit` is set to `1000000` by default.

It then returns a unique `queryId` that contains the `transaction` and query information as a `QueryResponse`.

#### getCache

```typescript
async getCache(queries: QueryRequest[]): Promise<[]>
```

You can retrieve past queries as a cache. Enter an array of `QueryRequest` and the values will be returned in an array.

#### getQueryStatus

```typescript
async getQueryStatus(queryId: string): Promise<QueryStatus>
```

query's current status can be retrieved. If you enter a `queryId`, you can see whether it is `Pending`, `Success`, or `Failed` as the `QueryStatus`.

#### waitForQueryResult

```typescript
async waitForQueryResult(queryId: string): Promise<QueryResult>
```

Wait until the query is returned as a response in the src chain; enter the `queryId` and return the response transaction and the data actually retrieved as the `QueryResult`.
