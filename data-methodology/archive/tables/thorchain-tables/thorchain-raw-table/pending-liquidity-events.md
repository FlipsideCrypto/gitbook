---
description: >-
  The pending liquidity events table shows the pending liquidity actions, there
  are different types of pending liquidity, can be 'add' or 'withdraw'
---

# Pending Liquidity Events

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.pending_liquidity_events`

| Field              | Type      | Description                                                                                                                     |
| ------------------ | --------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `BLOCK_ID`         | number    | The block number that this block was recorded                                                                                   |
| `BLOCK_TIMESTAMP`  | timestamp | The timestamp this block was recorded                                                                                           |
| `RUNE_TX_ID`       | text      | The unique transaction id for the rune event, the liquidity type can be add/remove the rune/asset, if the event related to rune |
| `POOL_NAME`        | text      | The pool name for the liquidity                                                                                                 |
| `PENDING_TYPE`     | text      | The type of liquidity, can be 'add' or 'withdraw'                                                                               |
| `RUNE_E8`          | number    | The amount of rune for the liquidity events                                                                                     |
| `ASSET_TX_ID`      | text      | The unique transaction id for the rune event, the liquidity type can be add/remove the rune/asset, if the event related to rune |
| `ASSET_E8`         | number    | The amount of asset for the liquidity events                                                                                    |
| `RUNE_ADDRESS`     | address   | The address of rune                                                                                                             |
| `ASSET_ADDRESS`    | address   | The address of asset                                                                                                            |
| `ASSET_BLOCKCHAIN` | text      | The blockchain of the asset                                                                                                     |
