---
description: >-
  Introducing data on the largest DEX on Base – Aerodrome Slipstream, a Solana
  CPI (Cross-Program Invocations) table, plus example queries for new Crosschain
  Polymarket order data.
---

# 2024-10-03 | Release Notes

## Highlights

This release introduces data on Aerodrome Slipstream, the largest DEX on Base, added to the `base.defi.ez_dex_swaps` and `base.defi.dim_dex_liquidity_pools` tables. A new `solana.core.fact_events_inner` table enables faster querying of the inner instructions of a Solana event instruction. In the Crosschain database, the Polymarket `crosschain.defi.ez_prediction_market_orders` table launched last week, and in this release you will find helpful query examples for using it.

{% hint style="warning" %}
**Please Note** - Several tables in the Ethereum and Optimism schemas are deprecated and will be removed by October 12th, 2024, consolidating lending data within the defi schema.
{% endhint %}

Check out these updates and the rest of the release notes below.

## Base

**Updated Tables** - Added Aerodrome Slipstream DEX data

These DeFi tables now include data on Aerodrome Slipstream, the largest DEX now on Base.

* `base.defi.ez_dex_swaps`
* `base.defi.dim_dex_liquidity_pools`

## Solana

**New Table** - A faster way to query CPI (Cross-Program Invocations)&#x20;

Contains each event that occurs within the inner instructions of an instruction. These are also known as CPI (Cross-Program Invocations), where a program makes a call to another. The new table enables much faster querying without needing to separately parse the events in the fact\_events table.

* `solana.core.fact_events_inner`

## Crosschain - Studio Only

**New Table** - Polymarket mapping outcome tokens

This new table, launched last week, contains curated Polymarket orders combined with Polymarket CLOB API data to map outcome tokens to their human readable descriptions - Question, Outcome, Conditions, etc. Use [**this dashboard**](https://flipsidecrypto.xyz/MasterChETH/polymarket-candlestick-djEzEw) for example Polymarket analytics made possible by the new table.&#x20;

* `crosschain.defi.ez_prediction_market_orders`

## Deprecated Tables

The following tables are deprecated and will be removed by October 12th, 2024. This data is not gone – you can query it in the DeFi schema for the respective chain:

* `ethereum.compound.{tables}`
  * Deprecating all tables in the ethereum.compound schema by October 12. All lending related data (borrows, deposits, etc) of Compound can already be found in the defi schema.
* `ethereum.aave.{tables}`
  * Deprecating all tables in the ethereum.aave schema by October 12. All lending related data (borrows, deposits, etc) of Aave can already be found in the defi schema
* `ethereum.synthetix.ez_snx_staking`
  * Deprecating the synthetix staking table along with the synthetix schema.
* `ethereum.maker.{ez_tables}`
  * Deprecating the ez tables in the ethereum.maker schema by October 12. All lending related data (borrows, deposits, etc) of Maker can already be found in the defi schema. All Maker fact tables will remain in the schema.
* `optimism.velodrome.{tables}`
  * Deprecating all tables in the optimism.velodrome schema by October 12. All lending related data (borrows, deposits, etc) of Velodrome can already be found in the defi schema

### Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
