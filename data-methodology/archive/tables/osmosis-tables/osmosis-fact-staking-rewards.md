# Osmosis Fact Staking Rewards

### Table Schema

`osmosis.core.fact_staking_rewards`

| Field               | Type      | Description                                                                                      |
| ------------------- | --------- | ------------------------------------------------------------------------------------------------ |
| block\_id           | integer   | Unique sequential number that identifies the current block. Called "height" on block explorers.  |
| block\_timestamp    | timestamp | The time the block began.                                                                        |
| blockchain          | string    | Cross-chain identifier. In this table, `blockchain` will always be Osmosis.                      |
| chain\_id           | string    | ID of the blockchain to connect to, i.e. Osmosis-1.                                              |
| tx\_id              | string    | A unique key that identifies a transaction. Called "TxHash" on block explorers.                  |
| tx\_status          | string    | "SUCCEEDED" if the transaction went through, "FALSE" if the transaction failed.                  |
| tx\_caller\_address | string    | The address of the wallet that initiated the transaction.                                        |
| action              | string    | A description of what is occurring in the transaction.                                           |
| delegator\_address  | string    | The wallet address that is delegating their OSMO.                                                |
| validator\_address  | string    | The address of the validator that the delegator is delegating to.                                |
| amount              | integer   | The quantity of cryptocurrency in the transaction.                                               |
| currency            | string    | A string identifying the cryptocurrency used in the transaction.                                 |
| decimal             | integer   | Divide `amount` by POW(10, decimal) to get the actual amount.                                    |

