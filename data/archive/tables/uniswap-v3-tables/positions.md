---
description: uniswapv3.positions
---

# Positions

Positions opened by liquidity providers at a specific tick range (tick\_lower_,_ tick\_upper). Whenever an event is emitted related to a position a new record is added to this table with the latest state of the position.

| Field                          | Type      | Description                                                                                         |
| ------------------------------ | --------- | --------------------------------------------------------------------------------------------------- |
| `block_id`                     | number    | The block number that this position's state was recorded                                            |
| `block_timestamp`              | timestamp | The block timestamp that this position's state was recorded                                         |
| `tx_id`                        | text      | The transaction that triggered this position's state to be recorded                                 |
| `blockchain`                   | text      | The blockchain this position was created on (Ethereum, will support L2s here shortly)               |
| `pool_address`                 | address   | the contract address of the pool                                                                    |
| `pool_name`                    | text      | The name of the Pool (format = "{token0}-{token1} {tick\_spacing} {fee}")                           |
| `is_active`                    | boolean   | Is the position currently active? When a position is closed this is set to false.                   |
| `liquidity_adjusted`           | number    | The liquidity of the position, decimal adjusted.                                                    |
| `liquidity_provider`           | address   | The address of the LP                                                                               |
| `nf_position_manager_address`  | address   | The address of the peripheral nf position manager contract, if used.                                |
| `nf_token_id`                  | number    | The id of the NFT associated with the liquidity position                                            |
| `price_lower_0_1`              | number    | Lower bound of the liquidity position represented as token 0 per token 1                            |
| `price_upper_0_1`              | number    | Upper bound of the liquidity position represented as token 0 per token 1                            |
| `price_lower_0_1_usd`          | number    | Lower bound of the liquidity position represented as token 0 per token 1, converted to USD          |
| `price_upper_0_1_usd`          | number    | Upper bound of the liquidity position represented as token 0 per token 1, converted to USD          |
| `price_lower_1_0`              | number    | Lower bound of the liquidity position represented as token 1 per token 0                            |
| `price_upper_1_0`              | number    | Upper bound of the liquidity position represented as token 1 per token 0                            |
| `price_lower_1_0_usd`          | number    | Lower bound of the liquidity position represented as token 1 per token 0, converted to USD          |
| `price_upper_1_0_usd`          | number    | Upper bound of the liquidity position represented as token 1 per token 0, converted to USD          |
| `tick_lower`                   | number    | Lower tick of the liquidity position                                                                |
| `tick_upper`                   | number    | Upper tick of the liquidity position                                                                |
| `token_0_address`              | address   | Contract address of token 0                                                                         |
| `token_0_symbol`               | text      | Symbol of token 0                                                                                   |
| `token_1_address`              | address   | Contract address of token 1                                                                         |
| `token_1_symbol`               | text      | Symbol of token 1                                                                                   |
| `tokens_owed0_adjusted`        | number    | The uncollected amount of token0 owed to the position as of the last computation.                   |
| `tokens_owed1_adjusted`        | number    | The uncollected amount of token1 owed to the position as of the last computation                    |
| `tokens_owed0_usd`             | number    | The uncollected amount of token0 owed to the position as of the last computation, converted to USD. |
| `tokens_owed1_usd`             | number    | The uncollected amount of token1 owed to the position as of the last computation, converted to USD  |
| `fee_growth_inside0_last_x128` | number    | The fee growth of token0 as of the last action on the individual position.                          |
| `fee_growth_inside1_last_x128` | number    | The fee growth of token1 as of the last action on the individual position.                          |
