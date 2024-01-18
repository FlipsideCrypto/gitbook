---
description: >-
  The table shows the asset and rune prices in the Thorchain, it will include
  the exchange ratio between rune/asset and the usd price data
---

# Prices

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.prices`

| Field              | Type      | Description                                   |
| ------------------ | --------- | --------------------------------------------- |
| `BLOCK_ID`         | number    | The block number that this block was recorded |
| `BLOCK_TIMESTAMP`  | timestamp | The timestamp this block was recorded         |
| `PRICE_RUNE_ASSET` | number    | How many RUNE can be exchanged by 1 Asset     |
| `PRICE_ASSET_RUNE` | number    | How many Asset can be exchanged by 1 RUNE     |
| `ASSET_USD`        | number    | The Asset price in USD                        |
| `RUNE_USD`         | number    | The RUNE price in USD                         |
| `POOL_NAME`        | text      | The pool this asset in                        |
