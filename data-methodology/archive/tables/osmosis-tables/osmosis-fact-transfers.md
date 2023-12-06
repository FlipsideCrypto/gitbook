# Osmosis Fact Transfers

### Table Schema

`osmosis.core.fact_transactions`

| Field            | Type      | Field                                                                                            |
| ---------------- | --------- | ------------------------------------------------------------------------------------------------ |
| block\_id        | integer   | Unique sequential number that identifies the current block. Called "height" on block explorers.  |
| block\_timestamp | timestamp | The time the block began.                                                                        |
| blockchain       | string    | Cross-chain identifier. In this table, `blockchain` will always be Osmosis.                      |
| chain\_id        | string    | ID of the blockchain to connect to, i.e. Osmosis-1.                                              |
| tx\_id           | string    | A unique key that identifies a transaction. Called "TxHash" on block explorers.                  |
| tx\_status       | string    | "SUCCEEDED" if the transaction went through, "FALSE" if the transaction failed.                  |
| transfer\_type   | string    | The type of transfer that occurred (i.e. IBC transfer)                                           |
| sender           | string    | The wallet address of the user that sent the transfer.                                           |
| amount           | integer   | The quantity of cryptocurrency sent in the transfer.                                             |
| currency         | string    | A string identifying the cryptocurrency sent in the transfer.                                    |
| decimal          | integer   | Divide `amount` by POW(10, decimal) to get the actual amount.                                    |
| receiver         | string    | The wallet address of the user that received the transfer.                                       |
