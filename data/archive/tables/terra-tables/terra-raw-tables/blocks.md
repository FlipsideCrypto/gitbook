# Blocks

Blocks table shows all the basic blocks information in Terra

## Table Schema

**table name:** `terra.blocks`

| `BLOCK_ID`         | number    | The block number that this block was recorded                                                                                                |
| ------------------ | --------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| `BLOCK_TIMESTAMP`  | timestamp | The timestamp this block was recorded                                                                                                        |
| `BLOCKCHAIN`       | text      | The blockchain name for this block                                                                                                           |
| `CHAIN_ID`         | number    | ID of blockchain to connect to, it can be _columbus-3, columbus-4, etc._                                                                     |
| `PROPOSER_ADDRESS` | address   | The address of the block proposer for this block, a _block proposer_ is the validator responsible for building a block during any given slot |
| `TX_COUNT`         | number    | Count of transactions per block, available for Columbus-5 onward.                                                                            |

