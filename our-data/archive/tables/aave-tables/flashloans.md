---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Flashloans



Flashloans exist within the `aave` schema, as `aave.flashloans`

| Field                   | Type      | Description                                   |
| ----------------------- | --------- | --------------------------------------------- |
| `tx_id`                 | string    | Transaction ID for this liquidation           |
| `block_id`              | number    | The block height this event was recorded at   |
| `block_timestamp`       | timestamp | UTC timestamp for this transaction            |
| `event_index`           | number    | Index of this event within the transaction    |
| `aave_market`           | address   | Address of the token                          |
| `aave_token`            | address   | Address of the aToken                         |
| `flashloan_amount`      | number    | Amount of tokens borrowed                     |
| `flashloan_amount_usd`  | number    | USD amount borrowed                           |
| `premium_amount`        | number    | Premium paid on the loan                      |
| `premium_amount_usd`    | number    | USD premium paid on the loan                  |
| `initiator_address`     | address   | Address of the initiator of the loan          |
| `target_address`        | address   | Address of the target of the loan             |
| `lending_pool_contract` | address   | Address of the lending pool contract          |
| `aave_version`          | string    | AAVE version (V1, V2, or AMM for Ethereum)    |
| `token_price`           | number    | Price of the token being borrowed             |
| `symbol`                | string    | Symbol of the token being borrowed            |
| `blockchain`            | string    | Ethereum or Polygon (presently only Ethereum) |



