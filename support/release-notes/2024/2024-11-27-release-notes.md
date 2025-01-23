---
description: >-
  Introducing expanded Aleo data coverage, Jupiter V4/V5 swap updates on Solana,
  plus important table deprecation notices and data latency changes.
---

# 2024-11-27 | Release Notes

## Highlights

This release brings comprehensive data coverage to the Aleo ecosystem with new core transfer tracking, pricing tables, and network metrics. We've also enhanced Solana's Jupiter swap data organization. Plus, we're rolling out major updates to Flipside Studio to transform how you build and share your analysis. Let's dive into what's new!

### 🎨 New Studio Features

1. [**Query Referencing**](https://docs.flipsidecrypto.xyz/data/data-products/data-studio-sql-analysts/studio-in-depth/query-editor/query-referencing) **- Queries in Queries!**
   * Reference results from previous queries directly using $query('query\_id')
   * Streamline your analysis by eliminating complex query rewrites
   * Build more sophisticated analyses by combining query results
   * Learn more about query referencing [here](https://docs.flipsidecrypto.xyz/data/data-products/data-studio-sql-analysts/studio-in-depth/query-editor/query-referencing).
2. **Custom Dashboard Tagging**
   * Create custom tags for your dashboards directly from the sidebar or query editor
   * Increase visibility of your work with better categorization
   * Find and get found more easily with improved tag display across boards
   * Boost your earnings potential through increased dashboard discovery

### ⚠️ [Important Deprecation Notice](https://docs.flipsidecrypto.xyz/support/release-notes/2024-11-27-release-notes#deprecated-tables-action-required)

* Ethereum Chainlink tables will be removed on December 9, 2024
* DeepNFTValue tables will be removed on December 4, 2024
* Please update your queries and dashboards accordingly

[Learn more here](https://docs.flipsidecrypto.xyz/support/release-notes/2024-11-27-release-notes#data-latency-updates)[.](https://docs.flipsidecrypto.xyz/support/release-notes/2024-11-27-release-notes#deprecated-tables-action-required)

### 📊 Data Latency Updates

We're updating the latency for our non-core tables across multiple blockchains to improve data reliability. Tables in non-core schemas like defi/nft/gov/stats/etc. that are not _\[db].core.\[table]_ are subject to changes in their latency. See the full list of blockchains and their freshness targets [here](../../../data/flipside-data/table-freshness-targets.md).

| Blockchain | Current Latency | New Latency |
| ---------- | --------------- | ----------- |
| Aleo       | 1 hour          | 4 hours     |
| Arbitrum   | 2 hours         | 6 hours     |
| Axelar     | 2 hours         | 1 hour      |
| Base       | 2 hours         | 4 hours     |
| BSC        | 2 hours         | 6 hours     |
| Bitcoin    | 2 hours         | 6 hours     |
| Blast      | 1 hour          | 4 hours     |
| CoreDao    | 1 hour          | 4 hours     |
| Eclipse    | 1 hour          | 4 hours     |
| Gnosis     | 2 hours         | 6 hours     |
| Kaia       | 1 hour          | 4 hours     |
| Optimism   | 2 hours         | 6 hours     |
| Polygon    | 2 hours         | 6 hours     |
| Thorchain  | 2 hours         | 4 hours     |

Check out these updates and the rest of the release notes below.

### Aleo

**New Tables** - Core Transfer Tracking

* `aleo.core.fact_transfers`

Track public and private transfers of native Aleo credits between addresses. Foundation for future expansion to include non-native token transfers.

**New Tables** - Price Data Integration

* `aleo.price.dim_asset_metadata`
* `aleo.price.ez_asset_metadata`
* `aleo.price.ez_prices_hourly`
* `aleo.price.fact_prices_ohlc_hourly`

These standard pricing tables integrate data from CoinGecko and CoinMarketCap to provide comprehensive price tracking for Aleo assets.

**New Table** - Network Statistics

* `aleo.stats.ez_core_metrics_hourly`

Core network metrics now available in the stats schema. Aleo metrics integrated into `crosschain.stats.ez_core_metrics_hourly`

### Solana

**Updated Tables -** Jupiter Swap Data Organization

The Jupiter V4 and V5 swap data is being restructured for better analysis and added to Jupiter-specific tables:

* `solana.defi.fact_swaps_jupiter_summary`
  * Aggregated view of Jupiter V4/V5 swaps
* `solana.defi.fact_swaps_jupiter_inner`
  * Detailed routes for individual swaps

{% hint style="warning" %}
**Important Note:** Jupiter V4 and V5 swaps will be removed from `fact_swaps` on December 9th. To query these swaps, use `fact_swaps_jupiter_summary` with the following program IDs:

* Jupiter V4: 'JUP4Fb2cqiRUcaTHdrPC8h2gNsA2ETXiPDD33WcGuJB'
* Jupiter V5: 'JUP5pEAZeHdHrLxh5UCwAbpjGwYKKoquCpda2hfP4u8' and 'JUP5cHjnnCx2DppVsufsLrXs8EBZeEZzGtEK9Gdz6ow'

Since these swaps will exist in both `fact_swaps` and `fact_swaps_jupiter_summary` until December 9th, any union between these tables should exclude the previously mentioned program ID’s from `fact_swaps` to avoid duplicates.
{% endhint %}

### ⚠️ Deprecated Tables - Action Required

#### Ethereum Chainlink Tables (Removing December 9, 2024)

The following tables will be deprecated due to low usage:

* `ethereum.chainlink.dim_oracle_feeds`
* `ethereum.chainlink.ez_oracle_feeds`
* `ethereum.chainlink.fact_oracle_feeds`

#### DeepNFTValue Tables (Removing December 4, 2024)

The following tables will be deprecated due to low usage:

* external.deepnftvalue.fact\_collections
* external.deepnftvalue.fact\_tokens
* external.deepnftvalue.fact\_valuations

Please update any queries or dashboards that reference these tables before their removal dates.

### Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
