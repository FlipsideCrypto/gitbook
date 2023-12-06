# Oracle Prices

The Oracle Prices table contains the information for the token price per timestamp

## Table Schema

**table name:** `terra.oracle_prices`

| Field                | Type      | Description                                                                                                                                                                                                                                 |
| -------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `BLOCKCHAIN`         | text      | Blockchain name, here is Terra                                                                                                                                                                                                              |
| `BLOCK_TIMESTAMP`    | timestamp | Block time stamp for this message events been recorded                                                                                                                                                                                      |
| `CURRENCY`           | text      | The currency for this token                                                                                                                                                                                                                 |
| `SYMBOL`             | text      | The token symbol                                                                                                                                                                                                                            |
| `LUNA_EXCHANGE_RATE` | text      | The exchange ratio to change this token for `LUNA` token. How many this token you can get when you transfer it with 1`LUNA`, for example, for `MNT`, `LUNA_EXCHANGE_RATE` is 2600, which means you can use 1 `LUNA` to exchange 2600 `MNT`  |
| `PRICE_USD`          | number    | The price for this token at this timestamp                                                                                                                                                                                                  |
| `SOURCE`             | text      | The source for the price                                                                                                                                                                                                                    |
