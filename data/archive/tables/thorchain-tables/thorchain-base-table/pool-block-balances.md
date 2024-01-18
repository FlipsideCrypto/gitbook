---
description: The table shows the pool block balances based on the rune and asset amount
---

# Pool Block Balances

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.pool_block_balances`

| Field              | Type      | Description                                                    |
| ------------------ | --------- | -------------------------------------------------------------- |
| `BLOCK_ID`         | number    | The block number that this block was recorded                  |
| `BLOCK_TIMESTAMP`  | timestamp | The timestamp this block was recorded                          |
| `POOL_NAME`        | text      | The pool name for the balance, it can be asset in other tables |
| `RUNE_AMOUNT`      | number    | The rune amount balance for this pool name                     |
| `RUNE_AMOUNT_USD`  | number    | The rune amount balance in USD for this pool name              |
| `ASSET_AMOUNT`     | number    | The asset amount balance for this pool name                    |
| `ASSET_AMOUNT_USD` | number    | The asset amount balance in USD for this pool name             |
| `SYNTH_AMOUNT`     | number    | The synth amount balance for this pool name                    |
| `SYNTH_AMOUNT_USD` | number    | The synth amount balance in USD for this pool name             |
