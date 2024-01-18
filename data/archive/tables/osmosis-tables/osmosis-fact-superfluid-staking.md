# Osmosis Fact Superfluid Staking

### Table Schema

`osmosis.core.fact_superfluid_staking`

| Field                              | Type      | Description                                                                                                                                                                          |
| ---------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| block\_id                          | integer   | The block height the block was recorded at.                                                                                                                                          |
| block\_timestamp                   | timestamp | The date and time at which the block began.                                                                                                                                          |
| blockchain                         | string    | In this table, always Osmosis. Used to join to cross-chain tables.                                                                                                                   |
| chain\_id                          | string    | The name and version of the blockchain.                                                                                                                                              |
| tx\_id                             | string    | A unique key that identifies a transaction. Called "TxHash" on block explorers.                                                                                                      |
| tx\_status                         | string    | Transaction status is "SUCCEEDED" if the transaction went through, "FALSE" if the transaction failed.                                                                                |
| tx\_caller\_address                | string    | The wallet address of the individual who initiated the transaction.                                                                                                                  |
| action                             | string    | The action taken in the msg group. For staking this includes delegate, undelegate, redelegate, withdraw\_rewards.                                                                    |
| delegator\_address                 | string    | The wallet address of the individual who owns the delegated asset.                                                                                                                   |
| amount                             | integer   | The amount that was used in the transaction message.                                                                                                                                 |
| currency                           | string    | The currency that was used in the transaction message.                                                                                                                               |
| decimal                            | integer   | Divide the amount by POW(10, decimal) to get the amount used in the transaction. This value can be NULL, as decimals are hand curated from an outside source and not found on-chain. |
| validator\_address                 | string    | The wallet address of the validator related to the staking action.                                                                                                                   |
| lock\_id                           | integer   | An ID corresponding to the locking step of the transaction.                                                                                                                          |
| original superfluid delegate tx id | string    | The transaction id when the user initialized the superfluid stake.                                                                                                                   |

