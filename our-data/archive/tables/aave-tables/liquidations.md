---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Liquidations



Liquidations exist within the `aave` schema, as `aave.liquidations`

| Field                      | Type      | Description                                   |
| -------------------------- | --------- | --------------------------------------------- |
| `tx_id`                    | string    | Transaction ID for this liquidation           |
| `block_id`                 | number    | The block height this event was recorded at   |
| `block_timestamp`          | timestamp | UTC timestamp for this transaction            |
| `event_index`              | number    | Index of this event within the transaction    |
| `collateral_asset`         | address   | Address of the collateral asset               |
| `collateral_aave_token`    | address   | Address of the collateral aToken              |
| `liquidated_amount`        | number    | Amount liquidated (decimal adjusted)          |
| `liquidated_amount_usd`    | number    | USD amount liquidated (decimal adjusted)      |
| `debt_asset`               | address   | Address of the debt asset                     |
| `debt_aave_token`          | address   | Address of the debt aToken                    |
| `debt_to_cover_amount`     | number    | Amount of debt to cover                       |
| `debt_to_cover_amount_usd` | number    | USD amount of debt to cover                   |
| `liquidator`               | address   | Address of the liquidator                     |
| `borrower`                 | address   | Address of the borrower                       |
| `aave_version`             | string    | AAVE version (V1, V2, or AMM for Ethereum)    |
| `collateral_token_price`   | number    | Price of the collateral token                 |
| `collateral_token_symbol`  | string    | Symbol of the collateral token                |
| `debt_token_price`         | number    | Price of the debt token                       |
| `debt_token_symbol`        | string    | Symbol of the debt token                      |
| `blockchain`               | string    | Ethereum or Polygon (presently only Ethereum) |

