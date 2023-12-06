# Transitions

Transitions table shows all the Transitions information blocks contains

## Table Schema

**table name:** `terra.transitions`

| Field              | Type      | Description                                                                           |
| ------------------ | --------- | ------------------------------------------------------------------------------------- |
| `BLOCK_ID`         | number    | The block number this transaction was recorded                                        |
| `BLOCK_TIMESTAMP`  | timestamp | The timestamp this transaction was recorded                                           |
| `BLOCKCHAIN`       | text      | The blockchain for this transaction                                                   |
| `CHAIN_ID`         | text      | ID of blockchain to connect to, it can be _columbus-3, columbus-4, etc._              |
| `TRANSITION_TYPE`  | text      | The type of this transition                                                           |
| `INDEX`            | number    | The position/index for this transition                                                |
| `EVENT`            | text      | The name of the event for this transition record                                      |
| `EVENT_ATTRIBUTES` | array     | It contains the information for this transition, the format will be JSON array format |
