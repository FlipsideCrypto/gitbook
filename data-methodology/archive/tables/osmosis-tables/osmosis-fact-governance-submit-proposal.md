# Osmosis Fact Governance Submit Proposal

### Table Schema

`osmosis.core.fact_governance_submit_proposal`

| Field            | Type      | Description                                                                                           |
| ---------------- | --------- | ----------------------------------------------------------------------------------------------------- |
| block\_id        | integer   | Unique sequential number that identifies the current block. Called "height" on block explorers.       |
| block\_timestamp | timestamp | The time the block began.                                                                             |
| blockchain       | string    | Cross-chain identifier. In this table, `blockchain` will always be Osmosis.                           |
| chain\_id        | string    | ID of the blockchain to connect to, i.e. Osmosis-1.                                                   |
| tx\_id           | string    | A unique key that identifies a transaction. Called "TxHash" on block explorers.                       |
| tx\_status       | string    | Transaction status is "SUCCEEDED" if the transaction went through, "FALSE" if the transaction failed. |
| proposer         | string    | The wallet address of the user that submitted the proposal.                                           |
| proposal\_id     | integer   | A sequential number that identifies the proposal.                                                     |
| proposal\_type   | string    | A descriptor of what the proposal is about. Will be "text" if unknown.                                |
