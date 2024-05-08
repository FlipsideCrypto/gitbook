---
description: >-
  Pricing data updates and actions required for users leveraging the Flipside
  API.
---

# Actions for API Users

There are **two** key actions API Users need to take during Flipside’s pricing updates period. They are outlined below in [Action #1](actions-for-api-users.md#action-1-replace-old-tables-and-column-with-optimized-tables) and [Action #2](actions-for-api-users.md#action-2-monitor-modified\_timestamp-on-june-3rd) sections.&#x20;

### Action #1: Replace old tables and column with optimized tables

Leverage our new pricing tables and deprecate the old ones by **June 3rd, 2024**. You need to change these table and column names in your queries so they don’t break. This affects 2 tables and 3 columns for 19 databases.

The following chains are affected:

<table data-header-hidden><thead><tr><th></th><th></th><th data-hidden></th></tr></thead><tbody><tr><td>Aptos</td><td>Ethereum</td><td></td></tr><tr><td>Arbitrum </td><td>Flow </td><td></td></tr><tr><td>Avalanche </td><td> Gnosis </td><td></td></tr><tr><td>Aurora </td><td>Near </td><td></td></tr><tr><td>Axelar</td><td>Optimism </td><td></td></tr><tr><td>Base </td><td>Osmosis </td><td></td></tr><tr><td>Bitcoin </td><td>Polygon </td><td></td></tr><tr><td>Blast </td><td>SEI</td><td></td></tr><tr><td>BSC</td><td>Solana</td><td></td></tr><tr><td>Crosschain</td><td></td><td></td></tr></tbody></table>

The table and column names that need to be deprecated for those 19 chains:&#x20;

<table data-full-width="true"><thead><tr><th width="341">Type</th><th width="235">Current name</th><th>New name</th></tr></thead><tbody><tr><td>TABLE NAME CHANGE</td><td><mark style="color:red;">fact_hourly_token_prices</mark></td><td><mark style="color:green;">fact_prices_ohlc_hourly</mark></td></tr><tr><td>TABLE NAME CHANGE</td><td><mark style="color:red;">ez_hourly_token_prices</mark></td><td><mark style="color:green;">ez_prices_hourly</mark></td></tr><tr><td>COLUMN NAME CHANGE<br>- in <code>ez_asset_metadata</code></td><td><mark style="color:red;">id</mark></td><td><mark style="color:green;">asset_id</mark></td></tr><tr><td>COLUMN NAME CHANGE<br>- in <code>dim_asset_metadata table</code></td><td><mark style="color:red;">id</mark></td><td><mark style="color:green;">asset_id</mark></td></tr><tr><td>COLUMN DEPRECATION <br>- in <code>dim_asset_metadata table</code></td><td><mark style="color:red;">decimals</mark></td><td><mark style="color:red;">No replacement, column is being deprecated</mark></td></tr></tbody></table>

{% hint style="warning" %}
Remember, you must update these tables and column names by **June 3rd, 2024** or your queries will break
{% endhint %}

### Action #2: Monitor data pipeline for refreshed data on June 3rd, 2024

Any table that includes the _amount\_usd_ column will be refreshed on **June 3rd, 2024** to include historical pricing. This will cause the modified\_timestamp column to update.

If you are incrementally loading data utilizing the _modified\_timestamp_ column, you could see larger than normal data loading on **June 3rd**. Please make necessary preparations and keep an eye on your data pipelines on this day.

The following chains are affected:

<table data-header-hidden><thead><tr><th></th><th></th><th data-hidden></th></tr></thead><tbody><tr><td>Aptos </td><td>Crosschain</td><td></td></tr><tr><td>Arbitrum </td><td>Ethereum</td><td></td></tr><tr><td>Avalanche</td><td>Gnosis</td><td></td></tr><tr><td>Base </td><td>Optimism </td><td></td></tr><tr><td>Blast</td><td>Polygon</td><td></td></tr><tr><td>BSC</td><td></td><td></td></tr></tbody></table>

{% hint style="info" %}
We will send you an email as we get closer to remind you.&#x20;
{% endhint %}

### Bonus: How to get improved token prices

To pull pricing data from 15,000+ tokens from CoinGecko, CoinMarketCap, and various other sources into your queries, analysts use the Crosschain data set and query `select * from` `crosschain.price.ez_prices_hourly` to select any token from the available list.

\
