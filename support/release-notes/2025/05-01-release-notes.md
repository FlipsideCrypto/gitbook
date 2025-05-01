---
description: >-
  TON data now available on Flipside, dedicated Ethereum L2 schema, enhanced
  Solana staking data, and improved Aptos token tracking.
---

# 2025-05-01 | Release Notes

This release launches support for TON blockchain data with 15 new tables, introduces Ethereum L2 schema, enhances Solana staking data, and improves Aptos token tracking. Our EVM standardization efforts continues. Please note the important upcoming deprecation of legacy data shares scheduled for May 15th, which will require action for users still utilizing these resources.

## Highlights

* **15 New TON Tables**: Core blockchain data, DeFi activity, and NFT ecosystem
* **Ethereum L2 Schema**: New dedicated schema with tables for state validation and data availability
* **Solana Staking Data**: Enhanced coverage for moveLamports and moveStake events
* **Aptos Token Metadata**: Improved token data and transfers tracking
* **EVM Standardization continues**: `Core` schema views upgrading to tables. Expect brief interruptions during deprecation workflow migrations&#x20;
* **Legacy Data Shares**: Deprecation scheduled for May 15th, 2025

## ⚠️ Special Notices

### Deprecating legacy Data Shares

Legacy data shares (with `FLIPSIDE_` prefix) will be deprecated on May 15th, 2025. If your data share contains only the blockchain name without this prefix, no action is required.

**How to identify legacy shares**: Legacy shares have the prefix `FLIPSIDE_` (e.g., `FLIPSIDE_SOLANA`). If your data share only contains the name of the blockchain without the prefix (e.g., `SOLANA`), you're already on the latest shares and no action is required.

{% hint style="warning" %}
**Action Required:** If you're still using the legacy shares, please update your queries to use the latest shares. We're happy to help if you need guidance or have questions.
{% endhint %}

### Important EVM Standardization Notices

* **Temporary Downtime** : Brief service interruptions may occur during migrations. Please refer to the [deprecation schedule](https://docs.flipsidecrypto.xyz/support/release-notes/2025/04-17-release-notes#evm-standardization-deprecation-timeline) shared last week for specific timing details.
* **Views → Tables Upgrade**: All views in the <mark style="color:red;">`core`</mark> schema are being upgraded to tables, with a few exceptions on Ethereum (primarily balances-related views), for better performance.

## Blockchain Updates

### TON

**New Tables:** TON blockchain is now fully supported with comprehensive data models covering core blockchain activity, DeFi transactions, and NFT ecosystem data.&#x20;

* `ton.core.fact_account_states`&#x20;
* `ton.core.fact_balances`&#x20;
* `ton.core.fact_blocks`&#x20;
* `ton.core.fact_jetton_events`&#x20;
* `ton.core.fact_jetton_metadata`&#x20;
* `ton.core.fact_messages`&#x20;
* `ton.core.fact_transactions`&#x20;
* `ton.defi.fact_dex_pools`&#x20;
* `ton.defi.fact_dex_trades`&#x20;
* `ton.nft.fact_nft_events`&#x20;
* `ton.nft.fact_nft_items`&#x20;
* `ton.nft.fact_nft_metadata`
* `ton.nft.fact_nft_sales`&#x20;
* `ton.nft.fact_nft_transfers`&#x20;
* `ton.core.dim_labels`&#x20;

### Ethereum

**New Tables:**&#x20;

* `ethereum.l2.ez_state_validation` - Captures state validation events, primarily for optimistic rollups, detailing how L2 chains post and finalize their state on Ethereum L1
* `ethereum.l2.ez_data_availability` - Tracks data availability commitments, including blobs and calldata submissions

### Solana

**Updated Tables:**&#x20;

* `solana.ez_staking_lp_actions` - now includes data for moveLamports and moveStake events, with two new columns: `move_destination` and `move_amount`

### Aptos

**Updated Tables:**

* `aptos.core.dim_tokens` - Enhanced token metadata for fungible tokens
* `aptos.core.fact_transfers` - Improved token transfer tracking



## Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
