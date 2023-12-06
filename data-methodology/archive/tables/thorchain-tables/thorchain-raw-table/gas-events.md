---
description: Gas events table provides the summary of the gas events for each block
---

# Gas Events

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.gas_events`

| Field             | Type      | Description                                                                                           |
| ----------------- | --------- | ----------------------------------------------------------------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded                                                         |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded                                                                 |
| `RUNE_E8`         | number    | The total gas amount in rune                                                                          |
| `TX_COUNT`        | number    | The total count of transactions within this block id                                                  |
| `ASSET_E8`        | number    | The asset amount for this fee, using the price table we can calculate the rune amount by asset amount |
| `ASSET`           | text      | Same as pool name, which pool this gas events happens                                                 |
