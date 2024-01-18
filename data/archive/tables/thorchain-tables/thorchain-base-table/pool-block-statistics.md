---
description: >-
  The overall pool block statistics broken by day, it lists most important
  metrics for the pools
---

# Pool Block Statistics

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.pool_block_statistics`

| Field                              | Type   | Description                                                                                                                     |
| ---------------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------- |
| `DAY`                              | date   | The timestamp in day for the recorded of the block fee                                                                          |
| `ADD_ASSET_LIQUIDITY_VOLUME`       | number | How many asset liquidity has been added to the pol at this time for this pool                                                   |
| `ADD_LIQUIDITY_COUNT`              | number | How many times there are transactions to add liquidity                                                                          |
| `ADD_LIQUIDITY_VOLUME`             | number | The asset volume of liquidity added to the pool                                                                                 |
| `ADD_RUNE_LIQUIDITY_VOLUME`        | number | The rune volume of liquidity added to the pool                                                                                  |
| `ASSET`                            | text   | Asset name or pool name                                                                                                         |
| `ASSET_DEPTH`                      | number | The current pool depth, which is the total Rune pooled in the asset                                                             |
| `ASSET_PRICE`                      | number | The asset price (how many rune) at this time                                                                                    |
| `ASSET_PRICE_USD`                  | number | The asset price in USD                                                                                                          |
| `AVERAGE_SLIP`                     | number | The average slip point for this block within the day                                                                            |
| `IMPERMANENT_LOSS_PROTECTION_PAID` | number | The total impermanent loss protection paid for this pool on this day                                                            |
| `RUNE_DEPTH`                       | number | The pool depth                                                                                                                  |
| `STATUS`                           | text   | The pool status, which is active or not                                                                                         |
| `SWAP_COUNT`                       | number | Total swap transactions count                                                                                                   |
| `SWAP_VOLUME`                      | number | Total swap volume                                                                                                               |
| `TO_ASSET_AVERAGE_SLIP`            | number | If the transaction is from Rune to Asset, the average slip point                                                                |
| `TO_ASSET_COUNT`                   | number | How many swaps happen from Rune to Asset                                                                                        |
| `TO_ASSET_FEES`                    | number | The total swap fees paid to transfer from Rune to Asset                                                                         |
| `TO_ASSET_VOLUME`                  | number | The total volume transferred from Rune to Asset                                                                                 |
| `TO_RUNE_AVERAGE_SLIP`             | number | If the transaction is from Asset to Rune, the average slip point                                                                |
| `TO_RUNE_COUNT`                    | number | How many swaps happen from Asset to Rune                                                                                        |
| `TO_RUNE_FEES`                     | number | The total swap fees paid to transfer from Asset to Rune                                                                         |
| `TO_RUNE_VOLUME`                   | number | The total volume transferred from Asset to Rune                                                                                 |
| `TOTAL_FEES`                       | number | The total fees paid for the swaps                                                                                               |
| `UNIQUE_MEMBER_COUNT`              | number | All memberships with a rune address. Take the member from rune and asset and then subtract the balance = 0 then get the results |
| `UNIQUE_SWAPPER_COUNT`             | number | The unique swap addresses for this pool                                                                                         |
| `UNITS`                            | number | The swap units                                                                                                                  |
| `WITHDRAW_ASSET_VOLUME`            | number | How many assets get withdrawn from the liquidity pools                                                                          |
| `WITHDRAW_COUNT`                   | number | How many times the withdraw events happens                                                                                      |
| `WITHDRAW_RUNE_VOLUME`             | number | How many rune volume get withdrawn from the pool                                                                                |
| `WITHDRAW_VOLUME`                  | number | How many asset volume get withdrawn from the pool                                                                               |
