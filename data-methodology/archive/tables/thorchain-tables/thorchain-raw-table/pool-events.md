---
description: Pool events table shows that the status of the pool at each block id
---

# Pool Events

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.pool_events`

| Field             | Type      | Description                                   |
| ----------------- | --------- | --------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded         |
| `ASSET`           | text      | The asset/pool name                           |
| `STATUS`          | text      | The current status for this pool              |
