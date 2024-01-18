# Deposits

Deposits exist within the `compound` schema, as `compound.deposits`

| Field                       | Type      | Description                                                                                                                      |
| --------------------------- | --------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `block_id`                  | number    | The block height this event was recorded at                                                                                      |
| `block_timestamp`           | timestamp | UTC block timestamp for parent block                                                                                             |
| `ctoken`                    | address   | cToken address                                                                                                                   |
| `ctoken_symbol`             | string    | cToken symbol                                                                                                                    |
| `issued_tokens`             | number    | Amount of cToken issued for providing liquidity                                                                                  |
| `supplied_base_assets`      | number    | Native amount provided as liquidity (decimal adjusted)                                                                           |
| `supplied_base_assets_usd`  | number    | The equivalent liquidity amount in USD. Note this is computed by taking the average hourly price around the time of the tx event |
| `supplied_contract_address` | address   | Address of token provided liquidity for                                                                                          |
| `supplied_symbol`           | string    | Symbol of token provided liquidity for                                                                                           |
| `supplier`                  | address   | Address of liquidity provider                                                                                                    |
| `tx_id`                     | string    | Transaction id for this mint                                                                                                     |

