# Upgrades

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.upgrades`

| Field             | Type      | Description                                   |
| ----------------- | --------- | --------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded         |
| `FROM_ADDRESS`    | address   | The address initiated this transfers          |
| `TO_ADDRESS`      | address   | The address received this transfers           |
| `BURN_ASSET`      | text      | The burned asset                              |
| `RUNE_AMOUNT`     | number    | The transferred RUNE amount                   |
| `RUNE_AMOUNT_USD` | number    | The transferred RUNE amount in USD            |
