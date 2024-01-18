# Osmosis Fact Governance Proposal Deposits

### Table Schema

`osmosis.core.fact_governance_proposal_deposits`

After a proposal on Osmosis is submitted, it is required that at least 500 OSMO be deposited into the proposal over a two week timeframe.&#x20;

| Field            | Type      | Description                                                                                           |
| ---------------- | --------- | ----------------------------------------------------------------------------------------------------- |
| block\_id        | integer   | Unique sequential number that identifies the current block. Called "height" on block explorers.       |
| block\_timestamp | timestamp | The time the block began.                                                                             |
| blockchain       | string    | Cross-chain identifier. In this table, `blockchain` will always be Osmosis.                           |
| chain\_id        | string    | ID of the blockchain to connect to, i.e. Osmosis-1.                                                   |
| tx\_id           | string    | A unique key that identifies a transaction. Called "TxHash" on block explorers.                       |
| tx\_status       | string    | Transaction status is "SUCCEEDED" if the transaction went through, "FALSE" if the transaction failed. |
| depositor        | string    | The wallet address of the user depositing into a proposal.                                            |
| proposal\_id     | integer   | A sequential number that identifies the proposal.                                                     |
| amount           | integer   | The quantity deposited in the transaction.                                                            |
| currency         | string    | A string identifying the cryptocurrency used in the transaction.                                      |
| decimal          | integer   | Divide `amount` by POW(10, decimal) to get the actual amount.                                         |
