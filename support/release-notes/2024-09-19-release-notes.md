---
description: >-
  New Polymarket, Flow, and Solana tables, Polygon's MATIC-to-POL update, and
  Ethereum/Optimism lending tables deprecated by Oct 12th, 2024, consolidating
  in DeFi.
layout:
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

# 2024-09-19 | Release Notes

## Highlights

This release enhances blockchain data coverage with updates across multiple ecosystems. A new Polymarket table in Crosschain integrates detailed outcome mappings, while Flow adds transaction actor tagging to improve analytics. Polygon’s NFT sales table now reflects the transition from MATIC to POL, and Solana’s Jupiter swaps table identifies DCA routed swaps with their initiating wallets. Additionally, several Ethereum and Optimism lending tables are deprecated and will be removed by **October 12th, 2024**, consolidating data in the DeFi schema.

{% hint style="warning" %}
**Please Note -** Several tables in the [Ethereum and Optimism schemas are deprecated](2024-09-19-release-notes.md#deprecated-tables) and will be removed by October 12th, 2024, consolidating lending data within the defi schema.
{% endhint %}

### **Studio Updates**

In addition to all the data updates we just released 3 new features to the Data Studio. There are two new chart types: heatmap and candlestick, and you can now add comments to dashboards. Give fellow analysts some praise or leave a question directly on their boards!

Check out these updates and the rest of the release notes below.

### Crosschain - Studio Only

**New Table** - Polymarket mapping outcome tokens

This new table contains curated Polymarket orders combined with Polymarket CLOB API data to map outcome tokens to their human readable descriptions - Question, Outcome, Conditions etc.

* `crosschain.defi.ez_prediction_market_orders`

### Flow

**New Tables** - Transaction actor extraction and tagging

A new model that extracts and tags the actors in a transaction. An actor is an address that is involved within the event execution of a transaction, for example as one of the actors in an NFT Sale, or as a recipient of commission. This model aligns with the new Actor tag on Flowdiver for more enhanced transaction analytics.

* `flow.core.ez_transaction_actors`

### Polygon

**Updated Table** - Polygon symbol change

All references to MATIC (as a currency address and symbol) since September 4th, 2024 has been changed to POL to match the change made by the Polygon ecosystem.

* `polygon.nft.ez_nft_sales`

### Solana

**Updated Table** - Jupiter swaps Dollar Cost Average (DCA)

Jupiter swaps can now be identified as being a part of a Dollar Cost Average (DCA) routed swap, and also shows the original user/wallet that initiated the swap.

* `solana.defi.fact_swaps_jupiter_summary`

### Deprecated Tables

The following tables are deprecated and will be removed by October 12th, 2024. This data is not gone – you can query it in the DeFi schema for the respective chain:

* `ethereum.compound.<tables>`
  * Deprecating all tables in the ethereum.compound schema by October 12. All lending related data (borrows, deposits, etc) of Compound can already be found in the defi schema.
* `ethereum.aave.<tables>`
  * Deprecating all tables in the ethereum.aave schema by October 12. All lending related data (borrows, deposits, etc) of Aave can already be found in the defi schema
* `ethereum.synthetix.ez_snx_staking`
  * Deprecating the synthetix staking table along with the synthetix schema.
* `ethereum.maker.<ez_tables>`
  * Deprecating the ez tables in the ethereum.maker schema by Oct 12. All lending related data (borrows, deposits, etc) of Maker can already be found in the defi schema. All Maker fact tables will remain in the schema.
* `optimism.velodrome.<tables>`
  * Deprecating all tables in the optimism.velodrome schema by October 9th, 2024. All lending related data (borrows, deposits, etc) of Velodrome can already be found in the defi schema

### Useful Resources

Request a smart contract ABI to be decoded:[ https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)

Request a Solana IDL to be decoded:[ https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)

Add labels:[ https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)\
