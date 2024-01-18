# Osmosis Dim Tokens

### Table Schema

`osmosis.core.dim_tokens`

| Field          | Type   | Description                                                                                                                                                                          |
| -------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| blockchain     | string | In this table, always Osmosis. Used to join to cross-chain tables.                                                                                                                   |
| address        | string | Address unique to the token.                                                                                                                                                         |
| creator        | string | Name of the label creator - for now, this will always be "Flipside."                                                                                                                 |
| label\_type    | string | A broad category that describes what a label is representing.                                                                                                                        |
| label\_subtype | string | Adds more detail to the label type.                                                                                                                                                  |
| label          | string | The label or name of the address.                                                                                                                                                    |
| project\_name  | string | The name of the project the label belongs to.                                                                                                                                        |
| alias          | string | A secondary address for the token, where available                                                                                                                                   |
| decimal        | number | Divide the amount by POW(10, decimal) to get the amount used in the transaction. This value can be NULL, as decimals are hand curated from an outside source and not found on-chain. |
| raw\_metadata  | object | Additional details about the validator or token in json format.                                                                                                                      |
