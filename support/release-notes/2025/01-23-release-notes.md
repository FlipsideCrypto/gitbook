---
description: >-
  Major updates across NEAR, INK, and Solana ecosystems, plus significant EVM
  fact_traces enhancements coming next week with new transaction data columns.
---

# 2025-01-23 | Release Notes

## Highlights

This release brings new tables and schemas across the NEAR, INK, and Solana ecosystems, while also streamlining our data architecture through strategic deprecations. We're introducing comprehensive native balance tracking for NEAR addresses, expanding INK's data coverage with new schema implementations, and enhancing Solana's DeFi capabilities with detailed Marinade protocol tracking. Plus major `fact_traces`  table updates across all EVM blockchains.

{% hint style="info" %}
Starting next week, we will be enhancing the `fact_traces` table across all EVM blockchains with additional columns to provide more detailed transaction data.

**Key Changes:**

**New Columns (where not already present):**

* `origin_from_address`: Transaction's original sender
* `origin_to_address`: Transaction's original recipient
* `origin_function_signature`: Function signature at transaction level
* `revert_reason`: If applicable, reason for transaction revert
* `trace_address`: Simplified version of the identifier field
* `tx_succeeded`: Boolean equivalent of `tx_status`
* `trace_succeeded`: Boolean equivalent of `trace_status`
* `tx_position`: Transaction's position within its block
* `value_hex`: Raw hexadecimal value of the trace

Important Notes:

* Column ordering within the table may change
* If you use SELECT \* queries, your applications may be affected
* Specific column selection in queries (SELECT column1, column2...) will not be impacted

**Bug Fix:** We're also resolving an issue where a small number of failed traces were incorrectly marked as successful when their parent trace failed.

**Timeline:** These changes will begin rolling out next week. We recommend reviewing any SELECT \* queries before the upgrade.

For detailed documentation or questions about these changes, please reach out.
{% endhint %}

Check out these updates and the rest of the release notes below.

### NEAR

**New Table** - Native Balance Tracking&#x20;

A new table enables comprehensive tracking of native token balances across NEAR addresses:

* _near.core.ez\_native\_daily\_balances_

{% hint style="warning" %}
**Deprecated Schemas** - Atlas and Horizon Consolidation

The NEAR Atlas schema will be deprecated in early February 2025. To maintain continuity of service, the EZ\_SUPPLY table will be migrated to the core schema. This strategic consolidation reflects the evolution of the NEAR ecosystem, as the Atlas webpage is no longer in operation.
{% endhint %}

{% hint style="warning" %}
The NEAR Horizon schema will be deprecated by February 1st, 2025, as part of our ongoing efforts to streamline data accessibility.
{% endhint %}

### INK

**New Tables** - Core Infrastructure and Pricing

A comprehensive suite of new schemas and tables has been introduced to enhance data coverage across contracts, transfers, event logs, and pricing:

Core Tables:

* _ink.core.dim\_contract\_abis_
* _ink.core.dim\_contracts_
* _ink.core.ez\_decoded\_event\_logs_
* _ink.core.ez\_token\_transfers_
* _ink.core.ez\_native\_transfers_

NFT Tables:

* _ink.nft.ez\_nft\_transfers_

Pricing Tables:

* _ink.price.ez\_prices\_hourly_
* _ink.price.ez\_asset\_metadata_
* _ink.price.dim\_asset\_metadata_
* _ink.price.fact\_prices\_ohlc\_hourly_

### Solana

**New Tables** - Marinade Protocol Integration

A new schema dedicated to the Marinade protocol introduces tables for comprehensive tracking of pools, staking actions, and token activities:

* _marinade.dim\_pools_
* _marinade.ez\_liquid\_staking\_actions_
* _marinade.ez\_liquidity\_pool\_actions_
* _marinade.ez\_native\_staking\_actions_
* _marinade.ez\_swaps_

These tables provide detailed insights into Marinade protocol activities, including pools, swaps, staking, and actions related to MNDE/MSOL tokens.

### Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
