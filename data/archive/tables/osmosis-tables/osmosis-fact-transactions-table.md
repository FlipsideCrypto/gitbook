# Osmosis Fact Transactions Table

### Table Schema

`osmosis.core.fact_transactions`

| Field            | Type      | Description                                                                                                                                                   |
| ---------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| block\_id        | integer   | Unique sequential number that identifies the current block. Called "height" on block explorers.                                                               |
| block\_timestamp | timestamp | The time the block began.                                                                                                                                     |
| blockchain       | string    | Cross-chain identifier. In this table, `blockchain` will always be Osmosis.                                                                                   |
| chain\_id        | string    | ID of the blockchain to connect to, i.e. Osmosis-1.                                                                                                           |
| tx\_id           | string    | A unique key that identifies a transaction. Called "TxHash" on block explorers.                                                                               |
| tx\_from         | string    | Address of the individual that initiated the transaction.                                                                                                     |
| tx\_status       | string    | Transaction status is "SUCCEEDED" if the transaction went through, "FALSE" if the transaction failed.                                                         |
| fee              | integer   | The fee is paid by the initiator of the transaction. Fee = gas \* gas price.                                                                                  |
| gas\_used        | integer   | The amount of gas consumed by the transaction.                                                                                                                |
| gas\_wanted      | integer   | Amount of gas requested for a transaction. It is provided by users when the transaction is generated.                                                         |
| codespace        | string    | Namespace for the code.                                                                                                                                       |
| tx\_code         | integer   | A number that corresponds to various error codes. When "0", the transaction is successful. Non-zero numbers signify different types of transaction failures.  |
| msgs             | json      | A json structure that includes information about the message attributes and attribute types.                                                                  |
