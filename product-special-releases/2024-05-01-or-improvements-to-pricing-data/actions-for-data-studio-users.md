---
description: >-
  Pricing data updates and actions required for queries and dashboards build in
  the data studio.
---

# Actions for Data Studio Users

### Update #1: Get CoinGecko token prices

To pull pricing data from 15,000+ tokens from CoinGecko into your queries, analysts use the `Crosschain` data set and query `select * from crosschain.price.ez_hourly_token_prices` to select any token from the available list.

### Update #2: Replace old tables and column with optimized tables

Leverage our new pricing tables and deprecate the old ones. The old ones will be deprecated on **June 3rd, 2024**. You need to change these table and column names in your queries so they don’t break. This affects 2 tables and 1 column for 11 databases.

The chains affected:

* Aptos
* Arbitrum
* Avalanche
* Base
* Blast
* BSC
* Crosschain
* Ethereum
* Gnosis
* Optimism
* Polygon

The table and column names that need to be deprecated for those 11 chains:&#x20;

<table data-full-width="true"><thead><tr><th width="341">Type</th><th width="235">Current name</th><th>New name</th></tr></thead><tbody><tr><td>TABLE NAME CHANGE</td><td><mark style="color:red;">fact_hourly_token_prices</mark></td><td><mark style="color:green;">fact_prices_ohlc_hourly</mark></td></tr><tr><td>TABLE NAME CHANGE</td><td><mark style="color:red;">ez_hourly_token_prices</mark></td><td><mark style="color:green;">ez_prices_hourly</mark></td></tr><tr><td>COLUMN NAME CHANGE<br>- in <code>ez_asset_metadata</code></td><td><mark style="color:red;">id</mark></td><td><mark style="color:green;">asset_id</mark></td></tr><tr><td>COLUMN NAME CHANGE<br>- in <code>dim_asset_metadata table</code></td><td><mark style="color:red;">id</mark></td><td><mark style="color:green;">asset_id</mark></td></tr><tr><td>COLUMN DEPRECATION <br>- in <code>dim_asset_metadata table</code></td><td><mark style="color:red;">decimals</mark></td><td><mark style="color:red;">No replacement, column is being deprecated</mark></td></tr></tbody></table>

{% hint style="warning" %}
Remember, you must update these tables and column name by **Jun 3rd, 2024** or your queries will break.&#x20;
{% endhint %}
