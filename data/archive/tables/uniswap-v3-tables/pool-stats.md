---
description: uniswapv3.pool_stats
---

# Pool Stats

Statistics for each pool, appened each time a transaction triggers a Pool Event (i.e. 'Initialize', 'Mint', 'Collect', 'Burn', 'Swap', 'Flash', 'IncreaseObservationCardinalityNext', 'SetFeeProtocol', 'CollectProtocol', etc.).&#x20;

**A new record is appended each time this occurs.** These stats are read from the Pool contract state leveraging Flipside's fully archival Ethereum cluster.

| Field                              | Type      | Description                                                                                                 |
| ---------------------------------- | --------- | ----------------------------------------------------------------------------------------------------------- |
| `block_id`                         | number    | The block number at which stats computed/read.                                                              |
| `block_timestamp`                  | timestamp | The block timestamp at which stats were computed/read.                                                      |
| `blockchain`                       | string    | The blockchain this pool was created on (Ethereum, will support L2s here shortly)                           |
| `pool_address`                     | address   | The contract address of the pool                                                                            |
| `pool_name`                        | string    | The name of the pool                                                                                        |
| `price_0_1`                        | number    | The price of token 0 in terms of token 1                                                                    |
| `price_1_0`                        | number    | The price of token 1 in terms of token 0                                                                    |
| `tick`                             | number    | The tick of the pool according to the last tick transitions that was run                                    |
| `protocol_fees_token_0_adjusted`   | number    | The amount of token0 owed to the protocol, decimal adjusted                                                 |
| `protocol_fees_token_1_adjusted`   | number    | The amount of token1 owed to the protocol, decimal adjusted                                                 |
| `token0_address`                   | address   | The contract address of token0                                                                              |
| `token1_address`                   | address   | The contract address of token1                                                                              |
| `token0_symbol`                    | text      | The symbol of token0                                                                                        |
| `token1_symbol`                    | text      | The symbol of token1                                                                                        |
| `token_0_balance`                  | number    | The balance of token0 locked in the pool contract as of this block                                          |
| `token_1_balance`                  | number    | The balance of token1 locked in the pool contract as of this block                                          |
| `token_0_balance_adjusted`         | number    | The balance of token0 locked in the pool contract as of this block, decimal adjusted                        |
| `token_1_balance_adjusted`         | number    | The balance of token1 locked in the pool contract as of this block, decimal adjusted                        |
| `unlocked`                         | boolean   | Whether the pool is currently locked to reentrancy                                                          |
| `virtual_liquidity_adjusted`       | number    | The virtual liquidity of the pool                                                                           |
| `virtual_reserves_token0_adjusted` | number    | The virtual reserves of token0, decimal adjusted, in the pool                                               |
| `virtual_reserves_token1_adjusted` | number    | The virtual reserves of token1, decimal adjusted, in the pool.                                              |
| `virtual_reserves_token0_usd`      | number    | The virtual reserves of token0, converted to USD.                                                           |
| `virtual_reserves_token1_usd`      | number    | The virtual reserves of token1 converted to USD.                                                            |
| `fee_growth_global0_x128`          | number    | The fee growth as a Q128.128 fees of token0 collected per unit of liquidity for the entire life of the pool |
| `fee_growth_global1_x128`          | number    | The fee growth as a Q128.128 fees of token1 collected per unit of liquidity for the entire life of the pool |
