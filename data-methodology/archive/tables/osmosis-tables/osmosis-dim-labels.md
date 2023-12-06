# Osmosis Dim Labels

### Table Schema

`osmosis.core.dim_labels`

| Field          | Type   | Description                                                                                     |
| -------------- | ------ | ----------------------------------------------------------------------------------------------- |
| blockchain     | string | Cross-chain identifier. In this table, `blockchain` will always be Osmosis.                     |
| address        | string | Address that the label is associated with.                                                      |
| creator        | string | Name of the creator of the label.                                                               |
| label\_type    | string | A high-level category describing the addresses main function or ownership (eg validator).       |
| label\_subtype | string | A sub-category nested within label type providing further detail (e.g. exchange deposit wallet) |
| label          | string | The name of the entity that controls the address (e.g. Cosmostation)                            |
| project\_name  | string | A description of the use of the address by the controlling entity.                              |
| raw\_metadata  | json   | A json structure containing additional information about the label where available.             |
