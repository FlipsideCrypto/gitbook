---
description: >-
  The release adds new Blast and Eclipse tables, Sei address mapping and updated
  Solana Raydium swaps.
---

# 2024-10-17 | Release Notes

## Highlights

This release introduces new tables for Blast and Eclipse, allowing users to track DEX swaps, liquidity pools, and token mint and burn events. A new Sei table enables analysts to map Sei cosmos addresses to Sei EVM addresses, while Solana's updated swaps table now includes Raydium CPMM swaps.

{% hint style="warning" %}
**As a reminder** several Ethereum and Optimism lending tables were deprecated on October 12th, 2024, with their data consolidated into the DeFi schema. These updates improve tracking and analysis across multiple blockchains.
{% endhint %}

Check out these updates and the rest of the release notes below.

### Blast

**New Tables** - Tracking DEX Swaps & Liquidity Pool

New tables allow you to track DEX Swap and Liquidity Pool creation events, alongside USD prices for Blast.

* `blast.defi.ez_dex_swaps`
* `blast.defi.dim_dex_liquidity_pools`

### Eclipse

**New Tables** - Mint and Burn Events for Tokens

Two new tables enable tracking of every mint and burn event for tokens on eclipse.

* `eclipse.defi.fact_token_mint_action`
* `eclipse.defi.fact_token_burn_actions`

### Sei

**New Table** - Sei Address Mapping&#x20;

This new table enables analysts to map the Sei cosmos address to the Sei EVM address.

* `sei.core.dim_address_mapping`

### Solana

**Updated Table** - Raydium CPMM swaps

Updating the fact\_swaps table to include Raydium CPMM swaps

* `solana.defi.fact_swaps`

## Deprecated Tables

The following tables are deprecated and were removed October 12th, 2024. **This data is not gone** – you can query it in the DeFi schema for the respective chain:

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
