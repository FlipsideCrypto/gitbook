---
description: >-
  Blast data now available! Plus new tables for Aptos and Axelar, and an updated
  `ethereum.nft.ez_nft_sales` table that now includes Art Blocks and Magic Eden
  among the available NFT platforms.
---

# 2024-03-05 | Data Updates

## [Blast - _NEW_](https://flipsidecrypto.github.io/blast-models/#!/overview)

**New Tables:**

`core.fact_token_transfers`, `core.dim_contracts`, `core.ez_native_transfers`, `core.ez_token_transfers`

Gain access to essential data on native and Ethereum transfers, as well as token transactions. Additionally, dive into a dimensional table for contract creations.

**Price Tables:**

`price.fact_hourly_token_prices`, `price.ez_hourly_token_prices`, `price.dim_asset_metadata`, `price.ez_asset_metadata`

Comprehensive price data sourced from Coingecko and CoinMarketCap.

## [Aptos](https://flipsidecrypto.github.io/aptos-models/#!/overview)&#x20;

**New Tables:**

`fact_nft_sales`, `ez_nft_sales`

Delve into Aptos NFT sales data with these newly added tables.

## [Axelar](https://flipsidecrypto.github.io/axelar-models/#!/overview)&#x20;

**New Tables:**

`axelscan.fact_gmp`, `axelscan.fact_transfers`

Explore data retrieved directly from the Axelscan API.

## [Ethereum](https://flipsidecrypto.github.io/ethereum-models/#!/overview)

**Updated Data**

`ez_nft_sales`

Added support for Art Blocks in the EZ NFT Sales table. Now filterable with platform\_name = 'art blocks', including all collections and collaboration projects listed on the Art Blocks website.

Added Magic Eden in the EZ NFT Sales table. Now filterable with platform\_name = 'magic eden'.



Stay tuned for more updates and enhancements to our data offerings!
