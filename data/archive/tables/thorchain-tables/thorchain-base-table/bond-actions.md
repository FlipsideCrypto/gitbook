---
description: The clean bond action table to record the node operators' behaviors
---

# Bond Actions

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.bond_actions`

| Field             | Type      | Description                                                                                     |
| ----------------- | --------- | ----------------------------------------------------------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded                                                   |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded                                                           |
| `TX_ID`           | number    | The transaction that contained this bond events, unique id to identify this message information |
| `FROM_ADDRESS`    | address   | The sending address for this bond event                                                         |
| `TO_ADDRES`       | address   | The receiving address for this bond event                                                       |
| `ASSET`           | text      | Same as pool name, which pool this bond events happens                                          |
| `BLOCKCHAIN`      | text      | The blockchain for this event, here is "THOR"                                                   |
| `BOND_TYPE`       | text      | There are 4 different types of bond:`bond_reward, bond_paid, bond_cost, bond_returned`          |
| `ASSET_AMOUNT`    | number    | The asset amount for this bond event                                                            |
| `ASSET_USD`       | number    | Used the price table to calculate the asset in the usd                                          |
