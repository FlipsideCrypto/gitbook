---
description: Daily Pool Stats shows the table for the pool statistics, broken down by daily
---

# Daily Pool Stats

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.daily_pool_stats`

| Field                          | Type   | Description                                                                                                                     |
| ------------------------------ | ------ | ------------------------------------------------------------------------------------------------------------------------------- |
| `DAY`                          | date   | The recorded day                                                                                                                |
| `POOL_NAME`                    | text   | The asset and the pool name                                                                                                     |
| `SYSTEM_REWARDS`               | number | The total daily system rewards in RUNE to the pool                                                                              |
| `SYSTEM_REWARDS_USD`           | number | The total daily system rewards in USD to the pool                                                                               |
| `ASSET_LIQUIDITY`              | number | The total asset liquidity for this pool                                                                                         |
| `ASSET_PRICE`                  | number | Current asset price                                                                                                             |
| `ASSET_PRICE_USD`              | number | Current asset price in USD                                                                                                      |
| `RUNE_LIQUIDITY`               | number | The total RUNE liquidity for this pool                                                                                          |
| `RUNE_PRICE`                   | number | Current RUNE price                                                                                                              |
| `RUNE_PRICE_USD`               | number | Current RUNE price in USD                                                                                                       |
| `ADD_LIQUIDITY_COUNT`          | number | How many times to add liquidity to the pool                                                                                     |
| `ADD_ASSET_LIQUIDITY`          | number | The total amount of asset liquidity added to the pool                                                                           |
| `ADD_ASSET_LIQUIDITY_USD`      | number | The total amount in usd of asset liquidity added to the pool                                                                    |
| `ADD_RUNE_LIQUIDITY`           | number | The total amount of RUNE liquidity added to the pool                                                                            |
| `ADD_RUNE_LIQUIDITY_USD`       | number | The total amount in usd of RUNE liquidity added to the pool                                                                     |
| `WITHDRAW_COUNT`               | number | Time to withdraw from the pool                                                                                                  |
| `WITHDRAW_ASSET_LIQUDITIY`     | number | The total amount of asset withdrawn from the pool                                                                               |
| `WITHDRAW_ASSET_LIQUDITIY_USD` | number | The total amount in USD of asset withdrawn from the pool                                                                        |
| `WITHDRAW_RUNE_LIQUIDITY`      | number | The total amount of RUNE withdrawn from the pool                                                                                |
| `WITHDRAW_RUNE_LIQUIDITY_USD`  | number | The total amount in USD of RUNE withdrawn from the pool                                                                         |
| `IL_PROTECTION_PAID`           | number | Impermanent loss protection cost paid to the network                                                                            |
| `IL_PROTECTION_PAID_USD`       | number | Impermanent loss protection cost in USD paid to the network                                                                     |
| `AVERAGE_SLIP`                 | number | Average slippage                                                                                                                |
| `TO_ASSET_AVERAGE_SLIP`        | number | When swap from RUNE to Asset, the average slippage                                                                              |
| `TO_RUNE_AVERAGE_SLIP`         | number | When swap from Asset to RUNE, the average slippage                                                                              |
| `SWAP_COUNT`                   | number | Total number of swaps                                                                                                           |
| `TO_ASSET_SWAP_COUNT`          | number | Total number of swaps from RUNE TO Asset                                                                                        |
| `TO_RUNE_SWAP_COUNT`           | number | Total number of swaps from Asset TO RUNE                                                                                        |
| `SWAP_VOLUME_RUNE`             | number | The swap amount of RUNE                                                                                                         |
| `SWAP_VOLUME_RUNE_USD`         | number | The swap amount of RUNE in USD                                                                                                  |
| `TO_ASSET_SWAP_VOLUME`         | number | The swap volume from RUNE to Asset                                                                                              |
| `TO_RUNE_SWAP_VOLUME`          | number | The swap volume from Asset to RUNE                                                                                              |
| `TOTAL_SWAP_FEES_RUNE`         | number | Total swap fees in RUNE                                                                                                         |
| `TOTAL_SWAP_FEES_USD`          | number | Total swap fees in USD                                                                                                          |
| `TOTAL_ASSET_SWAP_FEES`        | number | Total asset swap fees in asset                                                                                                  |
| `TOTAL_ASSET_RUNE_FEES`        | number | Total asset swap fees in RUNE                                                                                                   |
| `UNIQUE_MEMBER_COUNT`          | number | All memberships with a rune address. Take the member from rune and asset and then subtract the balance = 0 then get the results |
| `UNIQUE_SWAPPER_COUNT`         | number | The unique swap address for this pool                                                                                           |
| `LIQUIDITY_UNITS`              | number | The amount of units for the liquidity in the pool                                                                               |
