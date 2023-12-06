---
description: Reserve Events table shows the amount of rune reserved into the network
---

# Reserve Events

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.reserve_events`

| Field             | Type      | Description                                                                                        |
| ----------------- | --------- | -------------------------------------------------------------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded                                                      |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded                                                              |
| `TX_ID`           | text      | The transaction that contained this reserve events, unique id to identify this message information |
| `BLOCKCHAIN`      | text      | The blockchain for this reserve event                                                              |
| `ADDRESS`         | address   | The address reserve the amount to the pool                                                         |
| `E8`              | number    | The rune amount                                                                                    |
| `ASSET_E8`        | number    | The asset amount                                                                                   |
| `FROM_ADDRESS`    | address   | The address reserve the amount to the pool                                                         |
| `TO_ADDRESS`      | address   | Reserve the amount to the address                                                                  |
| `MEMO`            | text      | The memo for the reserve                                                                           |
| `ASSET`           | text      | The reserved asset                                                                                 |
