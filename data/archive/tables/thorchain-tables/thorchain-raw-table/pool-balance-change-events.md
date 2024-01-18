---
description: Pool Balance Change Events shows the change of the pool balance
---

# Pool Balance Change Events

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.pool_balance_change_events`

| Field             | Type      | Description                                                     |
| ----------------- | --------- | --------------------------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded                   |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded                           |
| `REASON`          | text      | The reason for the pool balance change                          |
| `ASSET`           | text      | The related asset or pool name in other table                   |
| `RUNE_AMOUNT`     | number    | The amount of rune for the pool balance change                  |
| `ASSET_ADD`       | boolean   | False or True, if True, then the event is to add asset not rune |
| `ASSET_AMOUNT`    | number    | The amount of asset for the pool balance change                 |
| `RUNE_ADD`        | boolean   | False or True, if True, then the event is to add rune not asset |
