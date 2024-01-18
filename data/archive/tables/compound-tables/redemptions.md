# Redemptions

Redemptions exist within the `compound` schema, as `compound.redemptions`

| Field                       | Type      | Description                                                                                                                      |
| --------------------------- | --------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `block_id`                  | number    | The block height this event was recorded at                                                                                      |
| `block_timestamp`           | timestamp | UTC block timestamp for parent block                                                                                             |
| `ctoken`                    | address   | cToken address                                                                                                                   |
| `ctoken_symbol`             | string    | cToken symbol                                                                                                                    |
| `received_amount`           | number    | Native amount provided as liquidity (decimal adjusted)                                                                           |
| `received_amount_usd`       | number    | The equivalent liquidity amount in USD. Note this is computed by taking the average hourly price around the time of the tx event |
| `received_contract_address` | address   | Address of token refunded as part of the redemption                                                                              |
| `received_contract_symbol`  | string    | Symbol of token refunded as part of the redemption                                                                               |
| `redeemed_ctoken`           | number    | cToken deposited to redeem                                                                                                       |
| `supplier`                  | address   | Address of liquidity provider                                                                                                    |
| `tx_id`                     | string    | Transaction id for the redemption(s)                                                                                             |
