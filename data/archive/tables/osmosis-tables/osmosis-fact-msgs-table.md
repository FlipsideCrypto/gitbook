# Osmosis Fact Msgs Table

### Table Schema

`osmosis.core.fact_msgs`

| Field            | Type      | Description                                                                                            |
| ---------------- | --------- | ------------------------------------------------------------------------------------------------------ |
| block\_id        | integer   | Unique sequential number that identifies the current block. Called "height" on block explorers.        |
| block\_timestamp | timestamp | The time the block began.                                                                              |
| blockchain       | string    | Cross-chain identifier. In this table, `blockchain` will always be Osmosis.                            |
| chain\_id        | string    | ID of the blockchain to connect to, i.e. Osmosis-1.                                                    |
| tx\_id           | string    | A unique key that identifies a transaction. Called "TxHash" on block explorers.                        |
| tx\_status       | string    | Transaction status is "SUCCEEDED" if the transaction went through, "FALSE" if the transaction failed.  |
| msg\_index       | integer   | Short for "message index," the position in which messages occur in a transaction.                      |
| msg\_type        | string    | A string containing information about the type of message occurring.                                   |
| msg              | json      | A block of json that contains the message attributes in base64 encoding.                               |
