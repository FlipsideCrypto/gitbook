---
description: uniswapv3.swaps
---

# Swaps

{% hint style="warning" %}
These are legacy Polygon tables. See [Polygon 2.0](../polygon-2.0-tables.md) for up-to-date Polygon models.
{% endhint %}

All swaps that occur on V3 pools.

| Field                | Type      | Description                                                                            |
| -------------------- | --------- | -------------------------------------------------------------------------------------- |
| `block_id`           | number    | The block number that this lp action was recorded                                      |
| `block_timestamp`    | timestamp | The block timestamp that this lp action was recorded                                   |
| `tx_id`              | text      | The transaction that contained this lp action                                          |
| `blockchain`         | text      | The blockchain this lp action was created on (Ethereum, will support L2s here shortly) |
| `pool_address`       | address   | The contract address of the pool                                                       |
| `pool_name`          | text      | The name of the Pool (format = "{token0}-{token1} {tick\_spacing} {fee}")              |
| `sender`             | address   | The address that initiated the swap call, and that received the callback               |
| `recipient`          | address   | The address that received the output of the swap                                       |
| `amount0_adjusted`   | number    | The delta of the token0 balance of the pool, decimal adjusted.                         |
| `amount1_adjusted`   | number    | The delta of the token1 balance of the pool, decimal adjusted.                         |
| `amount0_usd`        | number    | The delta of the token0 balance of the pool, converted to USD                          |
| `amount1_usd`        | number    | The delta of the token1 balance of the pool, converted to USD                          |
| `tick`               | number    | The log base 1.0001 of the price of the pool after the swap                            |
| `liquidity_adjusted` | number    | The liquidity of the pool after the swap, decimal adjusted.                            |
| `price_0_1`          | number    | The amount of token0 per token1 that the swap occurred at                              |
| `price_1_0`          | number    | The amount of token1 per token0 that the swap occurred at                              |
| `token0_address`     | address   | Contract address of token 0                                                            |
| `token0_symbol`      | text      | Symbol of token 0                                                                      |
| `token1_address`     | address   | Contract address of token 1                                                            |
| `token1_symbol`      | text      | Symbol of token 1                                                                      |

