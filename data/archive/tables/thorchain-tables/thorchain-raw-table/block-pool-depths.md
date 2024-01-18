---
description: >-
  Block Pool Depth table lists all the available pools and its' rune/asset depth
  at each block interval
---

# Block Pool Depths

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.block_pool_depths`

| Field             | Type      | Description                                         |
| ----------------- | --------- | --------------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded       |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded               |
| `RUNE_E8`         | number    | The rune depth for this pool at this block          |
| `ASSET_E8`        | number    | The asset depth for this pool at this block         |
| `POOL_NAME`       | text      | Pool name, which is also asset at some other tables |
