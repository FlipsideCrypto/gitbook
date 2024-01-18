---
description: Fee events lists all related fees happen in the Thorchain network
---

# Fee Events

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.fee_events`

| Field             | Type      | Description                                                                                           |
| ----------------- | --------- | ----------------------------------------------------------------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded                                                         |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded                                                                 |
| `TX_ID`           | number    | The transaction that contained this fee events, unique id to identify this message information        |
| `ASSET`           | text      | Same as pool name, which pool this fee events happens                                                 |
| `POOL_DEDUCT`     | number    | The amount deduct from the pool related to the fee                                                    |
| `ASSET_E8`        | number    | The asset amount for this fee, using the price table we can calculate the rune amount by asset amount |
