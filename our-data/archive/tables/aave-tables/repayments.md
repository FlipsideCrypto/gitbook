---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Repayments



Repayments exist within the `aave` schema, as `aave.repayments`

| Field                   | Type      | Description                                   |
| ----------------------- | --------- | --------------------------------------------- |
| `tx_id`                 | string    | Transaction ID for this liquidation           |
| `block_id`              | number    | The block height this event was recorded at   |
| `block_timestamp`       | timestamp | UTC timestamp for this transaction            |
| `event_index`           | number    | Index of this event within the transaction    |
| `aave_market`           | address   | Address of the token                          |
| `aave_token`            | address   | Address of the aToken                         |
| `repayed_tokens`        | number    | Amount of tokens repayed                      |
| `repayed_usd`           | number    | USD amount repayed                            |
| `payer`                 | address   | Address of the payer                          |
| `borrower`              | address   | Address of the borrower                       |
| `lending_pool_contract` | address   | Address of the lending pool contract          |
| `aave_version`          | string    | AAVE version (V1, V2, or AMM for Ethereum)    |
| `token_price`           | number    | Price of the token being borrowed             |
| `symbol`                | string    | Symbol of the token being borrowed            |
| `blockchain`            | string    | Ethereum or Polygon (presently only Ethereum) |



