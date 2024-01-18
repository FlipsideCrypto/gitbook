---
description: The table shows the fee paid by each pool at different timestamp
---

# Pool Block Fees

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.pool_block_fees`

| Field                       | Type   | Description                                            |
| --------------------------- | ------ | ------------------------------------------------------ |
| `DAY`                       | date   | The timestamp in day for the recorded of the block fee |
| `POOL_NAME`                 | text   | The asset for the fee events                           |
| `REWARDS`                   | number | The total rewards                                      |
| `TOTAL_LIQUIDITY_FEES_RUNE` | number | The total liquidity fees paid in RUNE                  |
| `ASSET_LIQUIDITY_FEES`      | number | The liquidity fees paid in Asset                       |
| `RUNE_LIQUIDITY_FEES`       | number | The liquidity fees paid in RUNE                        |
| `EARNINGS`                  | number | The total earnings for this pool at this time          |
