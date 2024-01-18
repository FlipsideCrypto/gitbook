# Osmosis Fact Liquidity Provider Actions

### Table Schema

`osmosis.core.fact_liquidity_provider_actions`

| Field                        | Type      | Description                                                                                          |
| ---------------------------- | --------- | ---------------------------------------------------------------------------------------------------- |
| block\_id                    | intger    | Unique sequential number that identifies the current block. Called "height" on block explorers.      |
| block\_timestamp             | timestamp | The time the block began.                                                                            |
| blockchain                   | string    | Cross-chain identifier. In this table, `blockchain` will always be Osmosis.                          |
| chain\_id                    | string    | ID of the blockchain to connect to, i.e. Osmosis-1.                                                  |
| tx\_id                       | string    | A unique key that identifies a transaction. Called "TxHash" on block explorers.                      |
| tx\_status                   | string    | ransaction status is "SUCCEEDED" if the transaction went through, "FALSE" if the transaction failed. |
| liquidity\_provider\_address | string    | The address of the user interacting with the liquidity pool.                                         |
| action                       | string    | Whether the user is joining or exiting the liquidity pool.                                           |
| pool\_id                     | integer   | A numeric ID that corresponds to the liquidity pool.                                                 |
| amount                       | integer   | The quantity of cryptocurrency in the transaction.                                                   |
| currency                     | string    | A string identifying the cryptocurrency used in the transaction.                                     |
| decimal                      | integer   | Divide `amount` by POW(10, decimal) to get the actual amount.                                        |

