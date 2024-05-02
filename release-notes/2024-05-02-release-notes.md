---
description: >-
  Pricing updates, new tables for Blitz (Blast Protocol), lending tables for
  crosschain, updated nft_sales tables for multiple chains, and now for
  LiveQuery an increased response size and data limit.
---

# 2024-05-02 | Release Notes

### Highlights

Here's what's new at Flipside: Your biweekly roundup of data updates and new releases.&#x20;

This week we released a major upgrade to our pricing data pipelines that enhances our data for most blockchains. This upgrade adds +15,000 tokens to our pricing tables and fills in historical prices. [Read more about this special product release here](broken-reference).

{% hint style="danger" %}
The pricing data upgrade require actions for all users. [See the special release notes ](broken-reference)for more details.
{% endhint %}

In addition to the pricing data upgrade we’ve got new curated tables across lots of different blockchains.&#x20;

Check out these updates and the rest of the release notes below.

### [Blast](https://flipsidecrypto.github.io/blast-models/#!/overview)

**New Table:**

A new table to integrate blast into our crosschain database.

* _blast.stats.ez\_core\_metrics\_hourly_

### [Blitz](https://flipsidecrypto.github.io/blast-models/#!/model/model.blast\_models.blitz\_\_ez\_account\_stats)

**New Table:**

5 new tables that pull data from the Blitz API and on-chain data.

* _ez\_account\_stats_
* _ez\_market\_depth\_stats_
* _ez\_market\_stats_
* _ez\_staking\_actions_
* _ez\_edge\_trades_

### Crosschain (Data Studio Only)

**New Table:**

6 new lending tables to help with crosschain analysis.

* lending.ez\_lending\_borrows
* lending.ez\_lending\_deposits
* lending.ez\_lending\_flashloans
* lending.ez\_lending\_liquidations
* lending.ez\_lending\_repayments
* lending.ez\_lending\_withdraws

### [Ethereum](https://flipsidecrypto.github.io/ethereum-models/#!/overview)

**Updated Table:**

We’ve remodeled Rarible data and updated the data so that all edge cases for Rarible trades are now included.

* _nft.ez\_nft\_sales_

### [Near](https://flipsidecrypto.github.io/near-models/#!/overview)

**New Tables:**

Two new tables to track all NFT transfers and all NFT sales actions on the main Near marketplaces.

* _nft.fact\_nft\_transfers_
* _core.ez\_nft\_sales_

Plus a new table records all native token and NEP-141 token transfers.

* _core.ez\_token\_transfers_

### [Solana](https://flipsidecrypto.github.io/solana-models/#!/overview)

**New Table:**

A new dim\_idls table is added to track IDL decoding. It includes information on the IDL program, status for historical decoding, whether the submission was valid, and more. This new table provides greater observability into our decoding process. Users can now easily see what programs are being decoded, if events have been historically decoded, and whether a submission to request an IDL for decoding was valid.

* _core.dim\_idls_

**Updated Table:**

Updates to nft.fact\_nft\_sales now make it easier to analyze compressed NFT sales on the Tensor marketplace, which has the largest volume of cNFTs. The table now includes relevant columns for compressed NFTs, including columns for merkle\_tree, leaf\_index and tree\_authority. Tensorswap has been added as the first platform for cNFT sales.

* _nft.fact\_nft\_sales_

### Product Updates

#### LiveQuery

LiveQuery now has an increased response size and data limit.

### Useful Resources&#x20;

Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)&#x20;

Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)&#x20;

Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)&#x20;
