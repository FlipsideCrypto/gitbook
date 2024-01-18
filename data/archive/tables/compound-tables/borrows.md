# Borrows

Borrows exist within the `compound` schema, as `compound.borrows`

| Field                      | Type      | Description                                                                                                                   |
| -------------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `block_id`                 | number    | The block height this event was recorded at                                                                                   |
| `block_timestamp`          | timestamp | UTC block timestamp for parent block                                                                                          |
| `borrower`                 | address   | Address that initiated a borrow event                                                                                         |
| `borrows_contract_address` | address   | Address of borrowed token                                                                                                     |
| `borrows_contract_symbol`  | string    | Symbol of borrowed token                                                                                                      |
| `ctoken`                   | address   | Respective cToken address to the borrowed token                                                                               |
| `ctoken_symbol`            | string    | Respective cToken symbol to the borrowed token                                                                                |
| `loan_amount`              | number    | Native amount of borrow (decimal adjusted)                                                                                    |
| `loan_amount_usd`          | number    | The equivalent borrow amount in USD. Note this is computed by taking the average hourly price around the time of the tx event |
| `tx_id`                    | string    | Transaction id for this borrow                                                                                                |

