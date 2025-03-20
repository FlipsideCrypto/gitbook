---
description: >-
  New Solana tables for NFT sales and liquidity pool actions, plus
  external.avalanche schema with Ava Labs data. Legacy Solana tables will be
  deprecated on April 15, 2025.
---

# 2025-03-20 | Release Notes

This release unlocks new data realms across the Solana and Avalanche ecosystems while streamlining access patterns. We're introducing intuitive EZ tables for Solana NFTs and DeFi, plus expanding our coverage through external data partnerships.&#x20;

### Highlights

* **New Solana NFT Sales Table**: Access comprehensive NFT sales data across multiple marketplaces with enriched metadata and pricing information
* **Enhanced DeFi Liquidity Pool Analytics**: New convenience table for Raydium, Orca, and Meteora liquidity pool actions with simplified data structure
* **Avalanche Expansion**: New `external.avalanche` schema with data from Ava Labs
* **Important Deprecation Notice**: Two legacy Solana tables will be deprecated on April 15, 2025

### ⚠️ Special Notices

**DEPRECATION NOTICE - Action Required by April 15, 2025**

The following Solana tables will be deprecated on April 15, 2025. Please update your queries to use the new tables before this date:

* `solana.nft.fact_nft_sales` → Replace with `solana.nft.ez_nft_sales`
* `solana.defi.fact_liquidity_pool_actions` → Replace with `solana.defi.ez_liquidity_pool_actions`

### Solana

**New Tables**

New convenience tables for Solana to enhance data access and usability, offering a more intuitive structure for analyzing DeFi and NFT activities.

* **solana.nft.ez\_nft\_sales**\
  A convenience table containing NFT sales across multiple marketplaces, with comprehensive information on metadata, USD prices, and marketplace details. This table simplifies querying NFT market activity with additional columns for deeper insights.
* **solana.defi.ez\_liquidity\_pool\_actions**\
  Convenience table capturing actions for liquidity pools in Raydium, Orca, and Meteora. This includes deposit and withdrawal events with a significantly improved data structure that consolidates related token information. _Key improvements:_
  * Single actions are represented in a single row, instead of separate records for each mint
  * Contains data for both tokens (A and B) in a single record with properties like `token_a_mint`, `token_b_mint`, `token_a_amount`, `token_b_amount`, etc.
  * Focuses specifically on withdraw and deposit actions for cleaner analysis

**Deprecated Tables**

The following tables are deprecated in favor of the new models above:

* **solana.fact\_nft\_sales**\
  &#xNAN;_&#x52;eplaced with:_ solana.nft.ez\_nft\_sales\
  &#xNAN;_&#x4E;ote:_ No change is required from users as the main difference is additional columns in the new table.
* **solana.fact\_liquidity\_pool\_actions**\
  &#xNAN;_&#x52;eplaced with:_ solana.defi.ez\_liquidity\_pool\_actions\
  &#xNAN;_&#x4E;ote:_ The new ez table contains only withdraw and deposit actions (the previous table had mint/burn actions). Data structure has been improved with single-row representation instead of separate records for each token. _Example:_ For a Meteora deposit:
  * The new EZ table represents the action as one record containing data for both tokens
  * The deprecated table has 2 separate records: one for token A and one for token B

**Deprecation Date: 2025-04-15**

### Avalanche

**New Tables**

New external schema with tables shared from Ava Labs:

*   **avalanche.external.avalanche**\
    A new schema in our external database filled with tables shared directly from Ava Labs. This addition significantly expands our Avalanche ecosystem coverage with authoritative data.&#x20;

    * _Important Note:_ This data is sourced directly from Ava Labs. For technical questions about this dataset, please refer to the Ava Labs Discord community.



### Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
