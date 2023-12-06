# Repayments



Repayments exist within the `compound` schema, as `compound.repayments`

| Field                    | Type      | Description                                                                                                                   |
| ------------------------ | --------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `block_id`               | number    | The block height this event was recorded at                                                                                   |
| `block_timestamp`        | timestamp | UTC block timestamp for parent block                                                                                          |
| `borrower`               | address   | Address of initial borrower                                                                                                   |
| `ctoken`                 | address   | cToken address                                                                                                                |
| `ctoken_symbol`          | string    | cToken symbol                                                                                                                 |
| `payer`                  | address   | Address of user that paid out the loan                                                                                        |
| `repay_contract_address` | address   | Address of token refunded as part of the redemption                                                                           |
| `repay_contract_symbol`  | string    | Symbol of token refunded as part of the redemption                                                                            |
| `repayed_amount`         | number    | Native amount repaid on loan  (decimal adjusted)                                                                              |
| `repayed_amount_usd`     | number    | The equivalent repaid amount in USD. Note this is computed by taking the average hourly price around the time of the tx event |
| `tx_id`                  | string    | Transaction id for this repayment                                                                                             |
