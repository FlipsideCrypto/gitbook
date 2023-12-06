# Transactions

Transactions table shows all the transactions information blocks contains

## Table Schema

**table name:** `terra.transactions`

| Field             | Type      | Description                                                                                                                                                                 |
| ----------------- | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `BLOCK_ID`        | number    | The block number this transaction was recorded                                                                                                                              |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded                                                                                                                                       |
| `BLOCKCHAIN`      | text      | The blockchain for this transaction                                                                                                                                         |
| `CHAIN_ID`        | text      | ID of blockchain to connect to, it can be columbus-3, columbus-4, etc.                                                                                                      |
| `TX_ID`           | text      | The transaction that contained this message, unique id to identify this message information                                                                                 |
| `TX_TYPE`         | text      | Transaction type. Luna can be unbonded (free to move wherever), bonded (ie delegated) and unbonding (21 day freeze to undelegate)                                           |
| `TX_STATUS`       | text      | The transaction status                                                                                                                                                      |
| `TX_STATUS_MSG`   | text      | The transaction status for the message                                                                                                                                      |
| `TX_CODE`         | text      | The Transaction Code                                                                                                                                                        |
| `TX_MODULE`       | text      | Transaction Module for this message                                                                                                                                         |
| `CODESPACE`       | text      | Code space for the transaction                                                                                                                                              |
| `FEE`             | array     | The transaction fee for this transaction, the format is `{ "amount": , "denom":  },` where denom is the currency and the amount is how many token spent on this transaction |
| `GAS_USED`        | number    | The real used gas fee for this transaction, the gas fee is like the gas fee in ETH blockchain                                                                               |
| `GAS_WANTED`      | number    | The requested gas fee for this transaction, the gas fee is like the gas fee in ETH blockchain                                                                               |
