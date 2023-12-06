# Osmosis Fact Governance Votes

### Table Schema

`osmosis.core.fact_governance_votes`

| Field            | Type      | Description                                                                                      |
| ---------------- | --------- | ------------------------------------------------------------------------------------------------ |
| block\_id        | integer   | Unique sequential number that identifies the current block. Called "height" on block explorers.  |
| block\_timestamp | timestamp | The time the block began.                                                                        |
| blockchain       | string    | Cross-chain identifier. In this table, `blockchain` will always be Osmosis.                      |
| chain\_id        | string    | ID of the blockchain to connect to, i.e. Osmosis-1.                                              |
| tx\_id           | string    | A unique key that identifies a transaction. Called "TxHash" on block explorers.                  |
| tx\_status       | string    | "SUCCEEDED" if the transaction went through, "FALSE" if the transaction failed.                  |
| voter            | string    | The wallet address of the user voting on the proposal.                                           |
| proposal\_id     | integer   | A sequential number that identifies the proposal.                                                |
| vote\_option     | string    | How the user voted on the proposal.                                                              |
| vote\_weight     | float     | The percentage of a user's voting power put towards this vote.                                   |
