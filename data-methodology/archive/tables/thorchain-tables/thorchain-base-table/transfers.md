---
description: Transfers table shows the transfer action between different address
---

# Transfers

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.transfers`

| Field             | Type      | Description                                   |
| ----------------- | --------- | --------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded |
| `EVENT_ID`        | text      | The flipside internal unique id               |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded         |
| `FROM_ADDRESS`    | address   | The address initiated this transfers          |
| `TO_ADDRESS`      | address   | The address received this transfers           |
| `ASSET`           | text      | The related asset                             |
| `RUNE_AMOUNT`     | number    | The transferred RUNE amount                   |
| `RUNE_AMOUNT_USD` | number    | The transferred RUNE amount in USD            |
