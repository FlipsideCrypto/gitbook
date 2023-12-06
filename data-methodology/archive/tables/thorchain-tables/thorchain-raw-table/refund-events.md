# Refund Events

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.refund_events`

| Field             | Type      | Description                                   |
| ----------------- | --------- | --------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded         |
| `TX_ID`           | text      |                                               |
| `ASSET_E8`        | number    |                                               |
| `MEMO`            | text      |                                               |
| `REASON`          | text      |                                               |
| `ASSET_2ND_E8`    | number    |                                               |
| `CODE`            | number    |                                               |
| `BLOCKCHAIN`      | text      |                                               |
| `ASSET`           | text      |                                               |
| `ASSET_2ND`       | text      |                                               |
| `TO_ADDRESS`      | address   |                                               |
| `FROM_ADDRESS`    | address   |                                               |
