---
description: uniswapv3.pools
---

# Pools

Pool records are appended to this table whenever a `PoolCreated` event is emitted by the UniswapV3 Factory Contract.

| Field             | Type      | Description                                                                       |
| ----------------- | --------- | --------------------------------------------------------------------------------- |
| `block_id`        | number    | The block number that this Pool record was created at                             |
| `block_timestamp` | timestamp | The block timestamp that this Pool record was created at                          |
| `tx_id`           | text      | The transaction that this Pool was created at                                     |
| `blockchain`      | text      | The blockchain this Pool was created on (Ethereum, will support L2s here shortly) |
| `factory_address` | address   | The address of the UniswapV3 factory that initialized this Pool                   |
| `fee_percent`     | number    | The fee expressed as a decimal percentage                                         |
| `init_price_1_0`  | number    | The initial price of the Pool (converted from sqrtPriceX96)                       |
| `init_tick`       | number    | The initial tick of the Pool                                                      |
| `pool_address`    | address   | The address of the Pool                                                           |
| `pool_name`       | text      | The name of the Pool (format = "token0-token1 fee tick\_spacing")                 |
| `tick_spacing`    | number    | The minimum number of ticks allowed between each tick.                            |
| `token0_address`  | address   | The contract address of token0                                                    |
| `token0_decimals` | number    | The number of decimals for token0 (used for decimal adjustments)                  |
| `token0_name`     | text      | The name of token0                                                                |
| `token0_symbol`   | text      | The symbol of token0                                                              |
| `token1_address`  | address   | The contract address of token1                                                    |
| `token1_decimals` | number    | The number of decimals for token1 (used for decimal adjustments)                  |
| `token1_name`     | text      | The name of token1                                                                |
| `token1_symbol`   | text      | The symbol of token1                                                              |

