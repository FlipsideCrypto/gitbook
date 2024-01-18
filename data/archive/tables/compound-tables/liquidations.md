# Liquidations

Liquidations exist within the `compound` schema, as `compound.liquidations`

| Field                          | Type      | Description                                                                                                                        |
| ------------------------------ | --------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `block_id`                     | number    | The block height this event was recorded at.                                                                                       |
| `block_timestamp`              | timestamp | UTC block timestamp for parent block                                                                                               |
| `ctoken`                       | address   | Address of cToken                                                                                                                  |
| `ctoken_symbol`                | string    | Symbol of cToken                                                                                                                   |
| `liquidator`                   | address   | Address that initiated the liquidation                                                                                             |
| `ctokens_seized`               | number    | cToken collateral held by the insolvent borrower that is taken by the liquidator                                                   |
| `liquidation_amount`           | number    | Native amount liquidated (decimal adjusted)                                                                                        |
| `liquidation_amount_usd`       | number    | The equivalent liquidated amount in USD. Note this is computed by taking the average hourly price around the time of the tx event. |
| `liquidation_contract_address` | address   | Address of liquidated token                                                                                                        |
| `liquidation_contract_symbol`  | string    | Symbol of liquidated token                                                                                                         |
| `tx_id`                        | string    | Transaction id for this liquidation                                                                                                |
