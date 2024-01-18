# Swaps

Swaps table contains the information for the swap behavior, it involves the two parties to swap different tokens within the chain

## Table Schema

**table name:** `terra.swap`

| Field                 | Type      | Description                                                                      |
| --------------------- | --------- | -------------------------------------------------------------------------------- |
| `BLOCKCHAIN`          | text      | The blockchain this swap was created on (Terra)                                  |
| `CHAIN_ID`            | text      | The version of the Terra Core (now is **Columbus-4**)                            |
| `BLOCK_ID`            | number    | The block number that this swap was recorded                                     |
| `BLOCK_TIMESTAMP`     | timestamp | The block timestamp that this swap was recorded                                  |
| `TX_STATUS`           | text      | The transaction status for the staking                                           |
| `TX_ID`               | text      | The transaction that contained this swap                                         |
| `SWAP_FEE_AMOUNT`     | number    | The amount of fee for this swap                                                  |
| `SWAP_FEE_AMOUNT_USD` | number    | The USD amount of fee for this swap                                              |
| `SWAP_FEE_CURRENCY`   | text      | The currency of fee for this swap                                                |
| `TRADER`              | address   | Trader address for this swap                                                     |
| `ASK_CURRENCY`        | text      |  The currency asked for the swap                                                 |
| `OFFER_AMOUNT`        | number    | Amount to offer for this swap                                                    |
| `OFFER_AMOUNT_USD`    | number    | USD Amount to offer for this swap                                                |
| `OFFER_CURRENCY`      | text      | Currency to offer for this swap                                                  |
| `TOKEN_0_AMOUNT`      | number    | The swap token 0 amount, in other word, use how many `token_0` to swap `token_1` |
| `TOKEN_0_AMOUNT_USD`  | number    | Amount of token\_0 in USD                                                        |
| `TOKEN_0_CURRENCY`    | text      | The currency of token\_0                                                         |
| `TOKEN_1_AMOUNT`      | number    | The swap token 0 amount, in other word, use how many `token_0` to swap `token_1` |
| `TOKEN_1_AMOUNT_USD`  | number    | Amount of token\_1 in USD                                                        |
| `TOKEN_1_CURRENCY`    | text      | The currency of token\_1                                                         |
| `PRICE0_USD`          | number    | The price for token\_0                                                           |
| `PRICE1_USD`          | number    | The price for token\_1                                                           |
| `SWAP_PAIR`           | text      | The concat field for the combination of `token_0` and `token_1`                  |
