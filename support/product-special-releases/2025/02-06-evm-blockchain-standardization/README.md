---
description: >-
  Major standardization across EVM databases improves querying with consistent
  column formats, flattened JSON structures, and simplified status tracking.
---

# 2025-02-06 | EVM BlockchainStandardization

## Highlights

Today we're announcing a major standardization effort across our EVM databases to make querying easier and more consistent. These changes will streamline data access across L1s, L2s, and different blockchain architectures while maintaining the unique characteristics that make each chain special.

This update focuses on three key improvements:

1. Standardizing column formats across all EVM chains
2. Ensuring consistency between EVM and non-EVM databases
3. Simplifying queries by flattening JSON structures into dedicated columns

Check out the [specific column changes for each table here.](table-change-overview.md)

### New Columns & Improvements&#x20;

{% hint style="warning" %}
These new columns will become available the week of February  10th, 2025
{% endhint %}

We're adding several new columns to enhance data accessibility:

* New boolean status flags
  * `tx_succeeded` and `trace_succeeded` for clearer transaction state tracking
* Enhanced trace data columns
  * `revert_reason` for detailed error information
  * `tx_position` for improved transaction ordering
  * Origin tracking columns (`origin_to_address`, `origin_from_address`, `origin_function_sig`)
* Flattened topic columns (`topic_0`, `topic_1`, etc.)
  * Replaces the need for complex topic array parsing

### Column Removals & Replacements

{% hint style="warning" %}
These columns will be removed the beginning of March, 2025
{% endhint %}

Several columns are being removed or replaced to improve consistency and usability:

* Removed L1 prefix columns from blocks and transactions tables for `Optimism` stack chains
  * This data will now live in its own dedicated table
* Replaced status columns with boolean flags
  * `tx_status` → `tx_succeeded`
  * `trace_status` → `trace_succeeded`
* Removed and flattened JSON columns
  * `block_header_json` data in blocks will now be available as individual columns
  * `data` column contents in traces table now as separate columns
* Replaced `identifier` in traces with more intuitive `trace_address` column

These updates make our data more accessible while maintaining the deep insights you need for blockchain analysis. The changes will roll out during the month of Feburary.&#x20;

