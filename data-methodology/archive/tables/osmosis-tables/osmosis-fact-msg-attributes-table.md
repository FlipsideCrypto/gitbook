# Osmosis Fact Msg Attributes Table

### Table Schema

`osmosis.core.fact_msg_attributes`

| Field            | Type      | Descriptions                                                                                     |
| ---------------- | --------- | ------------------------------------------------------------------------------------------------ |
| block\_id        | integer   | Unique sequential number that identifies the current block. Called "height" on block explorers.  |
| block\_timestamp | timestamp | The time the block began.                                                                        |
| blockchain       | string    | Cross-chain identifier. In this table, `blockchain` will always be Osmosis.                      |
| chain\_id        | string    | ID of the blockchain to connect to, i.e. Osmosis-1.                                              |
| tx\_id           | string    | A unique key that identifies a transaction. Called "TxHash" on block explorers.                  |
| msg\_index       | integer   | Short for "message index," the position in which messages occur in a transaction.                |
| msg\_type        | string    | A string containing information about the type of message occurring.                             |
| attribute\_index | integer   | The position in which attributes occur within a message.                                         |
| attribute\_key   | string    | A label of sorts for the attribute\_value.                                                       |
| attribute\_value | string    | Contains critical information such as addresses, amounts, tokens sent, etc.                      |
