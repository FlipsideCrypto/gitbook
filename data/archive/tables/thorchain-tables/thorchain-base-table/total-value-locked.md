---
description: The table to show the total value locked, bonded and pooled
---

# Total Value Locked

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.total_value_locked`

| Field                | Type   | Description                                                                        |
| -------------------- | ------ | ---------------------------------------------------------------------------------- |
| `DAY`                | date   | The timestamp in day for the recorded of the block fee                             |
| `TOTAL_VALUE_POOLED` | number | The total amount of rune provided by the liquidity provides and pooled in the pool |
| `TOTAL_VALUE_BONDED` | number | The total amount of rune provided by the node operators and bonded in the pool     |
| `TOTAL_VALUE_LOCKED` | number | The total rune value locked in the pool                                            |
