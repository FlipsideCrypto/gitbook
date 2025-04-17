---
description: >-
  New tables for Rise testnet, Movement blockchain, and stablecoin tracking,
  plus expanded Solana DEX coverage and critical EVM standardization timeline
  updates.
---

# 2025-04-17 | Release Notes

This release adds tables for the Rise testnet, Movement blockchain, stablecoin tracking, and expands Solana DEX coverage. It also includes important information about the EVM standardization timeline with specific deprecation dates that require your attention.

## Highlights

* **Rise Testnet Support**: New foundational tables for the Rise testnet including blocks, transactions, event logs, traces, and contracts
* **Movement Blockchain Expansion**: Five new tables providing comprehensive metrics, price tracking, and asset metadata for the Movement blockchain
* **Stablecoin Supply Monitoring**: New table tracking USDT and USDC supply across multiple chains
* **Enhanced Solana DEX Coverage**: Updated fact\_swaps table now includes Pumpswap and Lifinity DEX swaps
* **EVM Standardization Update**: Important deprecation schedule announcement for upcoming EVM table standardization

## ⚠️ Special Notices

#### EVM Standardization Deprecation Timeline

The EVM standardization initiative announced in February 2025 is progressing according to schedule. Please note the following important dates:

<table><thead><tr><th width="232.02734375">Date </th><th>Chain </th></tr></thead><tbody><tr><td>2025-04-22</td><td>Base </td></tr><tr><td>2025-04-28</td><td>Mantle</td></tr><tr><td>2025-04-29</td><td>BOB, Boba, Core </td></tr><tr><td>2025-04-30</td><td>Ink, Ronin, Swell </td></tr><tr><td>2025-05-05</td><td>Ethereum </td></tr><tr><td>2025-05-07</td><td>Arbitrum </td></tr><tr><td>2025-05-08</td><td>Optimism</td></tr><tr><td>2025-05-12</td><td>Gnosis </td></tr><tr><td>2025-05-13</td><td>Avalanche </td></tr><tr><td>2025-05-14</td><td>BSC</td></tr><tr><td>2025-05-15</td><td>Polygon</td></tr></tbody></table>

{% hint style="warning" %}
**Action Required**: Please update your queries to use the new standardized column formats before these dates. The deprecated columns will be removed according to the schedule above. Refer to our [February 6th announcement](https://flipsidecrypto.xyz/blog/2025-02-06-evm-blockchain-standardization) for full details on column changes.
{% endhint %}

## Blockchain Updates

### Stellar

New table providing visibility into trust lines and non-stellar balances on the Stellar network.

* `stellar.core.fact_trust_lines`

### Movement

**New Tables:** comprehensive suite of tables for the Movement blockchain, providing core metrics, price data, and asset information.

* `movement.stats.ez_core_metrics_hourly` : Standard chain statistics with hourly granularity
* `movement.price.dim_asset_metadata` : Dimensional table for Movement asset metadata
* `movement.price.ez_asset_metadata` : Easy-to-use table for Movement asset metadata
* `movement.price.ez_prices_hourly` : Hourly price data for Movement assets
* `movement.price.fact_prices.ohlc_hourly` : Detailed hourly OHLC price data for Movement assets

### Rise (Testnet)

**New Tables:** foundational tables providing comprehensive blockchain data for the Rise testnet.

* `rise.testnet` : A collection of foundational tables including blocks, transactions, event logs, traces, and contracts
* **Note**: Rise testnet data is only accessible in [Flipside Studio](https://flipsidecrypto.xyz/studio/).&#x20;

### External

New table tracking stablecoin supply across multiple chains.

* `defillama.fact_usdt_usdc_supply` : Date and chain-level supply data for USDT and USDC

### Solana

**Updated Table:** enhanced DEX swap coverage with additional protocols.

* `solana.fact_swaps` : Now includes Pumpswap and Lifinity DEX swaps

### EVM Standardization Reminder

As announced on February 6th, we're standardizing column formats across all EVM chains to make cross-chain analysis more intuitive and powerful. This includes:

* **Standardized status tracking**: Using `tx_succeeded` and `trace_succeeded` boolean flags
* **Enhanced error tracking**: With dedicated `revert_reason` columns
* **Flattened topic columns**: Individual `topic_0`, `topic_1`, etc. columns replacing array structures
* **Improved trace data**: Including origin tracking columns

The rollout follows the chain-specific schedule shown in the Special Notices section above. We encourage all users to update their queries well before the deprecation dates to ensure uninterrupted data access.



## Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
