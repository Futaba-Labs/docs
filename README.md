---
cover: .gitbook/assets/futaba_cover.png
coverY: 0
layout:
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Introduction

### What is Futaba?

Futaba is a modular omnichain interface enabling communication between contracts, rollups and blockchain networks by querying and pulling data from a single source chain.

<figure><img src=".gitbook/assets/image (1).png" alt="" width="375"><figcaption></figcaption></figure>

### What is Futaba used for?

Futaba **unifies** liquidity, community of users, accounting and management of a dApp or an ecosystem

by **enabling data** to be pulled from one / many chains to one single source chain

while **secured modularly** by [Konoha](https://app.gitbook.com/o/Thz2mfuoktjdE6MeG8yW/s/sOs4pzHyvFKixViaeh5C/\~/changes/26/protocol/konoha), which is made up of multiple validation / security modules that builders can choose to incorporate to optimize their validation method. If one of the modules are exploited, Futaba is still secured by Konoha and its other unaffected modules.



### What does it look like with Futaba integrated?

<table><thead><tr><th width="109">Aspects</th><th width="340">without Futaba integrated (currently)</th><th>with Futaba integrated</th></tr></thead><tbody><tr><td>Fees</td><td>dApp users spend large amounts of gas fees whenever interacting with dApps on Ethereum mainnet</td><td>dApp users can interact with dApps on Ethereum mainnet from dApps/contracts on rollups / L2s, paying only rollups / L2 gas fees</td></tr><tr><td>Security</td><td>To save on fees and time, dApp users bridge to rollups / L2s, at the risk of trusting 3rd party bridges / protocols (single point of failure). </td><td>Futaba's <a href="https://app.gitbook.com/o/Thz2mfuoktjdE6MeG8yW/s/sOs4pzHyvFKixViaeh5C/~/changes/26/protocol/konoha">Konoha</a> ensures dApp users are secure even if one of the 3rd party validators/oracles ie <a href="https://app.gitbook.com/o/Thz2mfuoktjdE6MeG8yW/s/sOs4pzHyvFKixViaeh5C/~/changes/26/protocol/konoha/chainlink-oracle">Chainlink</a>, <a href="https://app.gitbook.com/o/Thz2mfuoktjdE6MeG8yW/s/sOs4pzHyvFKixViaeh5C/~/changes/26/protocol/konoha/lagrange">Lagrange</a>, zk light clients, are exploited.</td></tr><tr><td>Dev Costs</td><td>Whenever a new rollup / chain attracts a lot of liquidity, developers incur a new cost of developer hours and money, as they create a new set of contracts, just to capture market share and users.</td><td>Developers save money and developer hours, by integrating a new rollup/chain via Futaba</td></tr><tr><td>Dev Effort</td><td>Developers have more accounting to do, more data to be managed, and community that is more fragmented to interact with - as their dApp goes live on multiple chains (multi-chain)</td><td>Developers community, data and accounting are accessed and unified from a single source chain, yet accessing data across many chains (omni-chain).</td></tr></tbody></table>



### What are some usecases?

**Reduced transaction fees** - Query and access yield/reward balances on Ethereum mainnet from rollups or Layer 2s at much lower fees, compared to withdrawing the yield balance from mainnet itself.\
**Usecases / dapps:** LST, Perp DEXes, Yield aggregators

**Reduced developer hours to scale to other chains/rollups** - With Futaba integrated, dapp users on chain/rollup X, Y, Z, can access balances on mainnet, instead of deploying another set of contracts and liquidity on another chain/rollup to scale every time.\
**Usecases / dapps:** AMMs, DEXes, Perp DEXes
