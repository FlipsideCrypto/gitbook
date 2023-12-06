# Osmosis Fact Swaps

### Table Schema

`osmosis.core.fact_swaps`

| Field            | Type      | Description                                                                                      |
| ---------------- | --------- | ------------------------------------------------------------------------------------------------ |
| block\_id        | integer   | Unique sequential number that identifies the current block. Called "height" on block explorers.  |
| block\_timestamp | timestamp | The time the block began.                                                                        |
| blockchain       | string    | Cross-chain identifier. In this table, `blockchain` will always be Osmosis.                      |
| chain\_id        | string    | ID of the blockchain to connect to, i.e. Osmosis-1.                                              |
| tx\_id           | string    | A unique key that identifies a transaction. Called "TxHash" on block explorers.                  |
| tx\_status       | string    | "SUCCEEDED" if the transaction went through, "FALSE" if the transaction failed.                  |
| trader           | string    | The wallet address of the user who initiated the swap.                                           |
| from\_amount     | integer   | The quantity of cryptocurrency to be swapped.                                                    |
| from\_currency   | string    | A string identifying the cryptocurrency to be swapped.                                           |
| from\_decimal    | integer   | Divide `from_amount` by POW(10, decimal) to get the actual from\_amount.                         |
| to\_amount       | integer   | The quantity of cryptocurrency received in the swap.                                             |
| to\_currency     | string    | string identifying the cryptocurrency received in the swap.                                      |
| to\_decimal      | integer   | Divide `to_amount` by POW(10, decimal) to get the actual to\_amount.                             |
| pool\_ids        | array     | An array containing integers corresponding to the pools the swap went through.                   |
