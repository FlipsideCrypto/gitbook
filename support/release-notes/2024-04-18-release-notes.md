---
description: >-
  New tables on Vertex and Solana. Plus updates to Arbitrum and BSC supporting
  Seaport 1.6.
---

# 2024-04-18 | Release Notes

## Highlights

The team just released 5 new tables for Vertex that give you the ability to dig into account stats, market depth stats, market stats, staking actions and edge trades.

We also released a new Solana table `core.fact_token_account_owners` that provides a comprehensive view of token account ownership, enabling users to track the ownership history of token accounts. As the owner of an account can change over time, and transactions more commonly display the token account over the actual owner, this table makes it easier to analyze the main parties that are executing transactions on-chain, to get insight into user behavior, network connections, and market correlations.

Check out the rest of the release notes below.

### [Arbitrum](https://flipsidecrypto.github.io/arbitrum-models/#!/overview)

**Updated Table:**

Seaport 1.6 added to ez\_nft\_sales table

* _nft.ez\_nft\_sales_

### [Binance Smart Chain](https://flipsidecrypto.github.io/bsc-models/#!/overview)

**Updated Table:**

Seaport 1.6 added to ez\_nft\_sales table

* _nft.ez\_nft\_sales_

### [Solana](https://flipsidecrypto.github.io/solana-models/#!/overview)

**New Table:**

This new table provides a comprehensive view of address ownership, enabling users to track the ownership history of an account. Because the owner of an account can change over time, and transactions more commonly display the token account over the actual owner — this table enables easier analysis into the main parties that are executing transactions on-chain, and insight into user behavior, network connections, market correlations, etc.

* _core.fact\_token\_account\_owners_

**Updated Table:**

These tables now contain all events related to mints, where previously they only contained the actual minting of the token/nft. This is useful in situations where the first mint and initialization do not occur in the same transactions.

* _nft.fact\_nft\_mint\_actions_&#x20;
* _defi.fact\_token\_mint\_actions_

### [Vertex](https://flipsidecrypto.github.io/arbitrum-models/#!/model/model.arbitrum\_models.vertex\_\_dim\_products)

**New Tables:**

We recently added new tables to integrate Vertex API and on-chain data. You can find this data under the Arbitrum database.

* _arbitrum.vertex.ez\_account\_stats_
* _arbitrum.vertex.ez\_market\_depth\_stats_
* _arbitrum.vertex.ez\_market\_stats_
* _arbitrum.vertex.ez\_staking\_actions_
* _arbitrum.vertex.ez\_edge\_trades_

### Useful Resources&#x20;

Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)&#x20;

Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)&#x20;

Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)&#x20;
