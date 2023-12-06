---
description: >-
  Bond Events table lists all the information about the Bond activities.
  THORChain uses a spinoff of the Proof of Stake consensus mechanism called
  Proof of Bond.
---

# Bond Events

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.bond_events`

| Field             | Type      | Description                                                                                            |
| ----------------- | --------- | ------------------------------------------------------------------------------------------------------ |
| `BLOCK_ID`        | number    | The block number that this block was recorded                                                          |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded                                                                  |
| `TX_ID`           | number    | The transaction that contained this bond events, unique id to identify this message information        |
| `TO_ADDRES`       | address   | The receiving address for this bond event                                                              |
| `FROM_ADDRESS`    | address   | The sending address for this bond event                                                                |
| `MEMO`            | text      | Memo for this bond event                                                                               |
| `ASSET`           | text      | Same as pool name, which pool this bond events happens                                                 |
| `BLOCKCHAIN`      | text      | The blockchain for this event, here is "THOR"                                                          |
| `BOND_TYPE`       | text      | There are 4 different types of bond:`bond_reward, bond_paid, bond_cost, bond_returned`                 |
| `E8`              | number    | The rune amount for this bond event                                                                    |
| `ASSET_E8`        | number    | The asset amount for this bond, using the price table we can calculate the rune amount by asset amount |
