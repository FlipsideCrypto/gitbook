# Osmosis Fact Blocks Table

### Table Schema

`osmosis.core.fact_blocks`

| Field             | Type      | Description                                                                                                     |
| ----------------- | --------- | --------------------------------------------------------------------------------------------------------------- |
| block\_id         | integer   | Unique sequential number that identifies the current block. Called "height" on block explorers.                 |
| block\_timestamp  | timestamp | The time the block began.                                                                                       |
| blockchain        | string    | Cross-chain identifier. In this table, `blockchain` will always be Osmosis.                                     |
| chain\_id         | string    | ID of the blockchain to connect to, i.e. Osmosis-1.                                                             |
| tx\_count         | integer   | Number of transactions that occurred on the block.                                                              |
| proposer\_address | string    | The address of the validator that proposed this block and is the validator responsible for building the block.  |
| validators\_hash  | string    | The root hash of the new validator set.                                                                         |
