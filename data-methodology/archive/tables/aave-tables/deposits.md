---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Deposits



Deposits exist within the `aave` schema, as `aave.deposits`

| Field                   | Type      | Description                                                    |
| ----------------------- | --------- | -------------------------------------------------------------- |
| `tx_id`                 | string    | Transaction ID for this supply                                 |
| `block_id`              | number    | The block height this event was recorded at                    |
| `block_timestamp`       | timestamp | UTC timestamp for this transaction                             |
| `aave_market`           | address   | Address of the AAVE market/underlying contract                 |
| `aave_token`            | address   | aToken address                                                 |
| `issued_tokens`         | number    | Amount of tokens issued for providing liquidity                |
| `supplied_usd`          | number    | USD amount provided as liquidity (decimal adjusted)            |
| `depositor_address`     | address   | Address of liquidity provider                                  |
| `lending_pool_contract` | address   | Address of the lending pool contract used for this transaction |
| `aave_version`          | string    | AAVE version (V1, V2, or AMM for Ethereum)                     |
| `token_price`           | number    | Current price of the market token                              |
| `symbol`                | string    | Symbol of the market asset                                     |
| `blockchain`            | string    | Ethereum or Polygon (presently only Ethereum)                  |

