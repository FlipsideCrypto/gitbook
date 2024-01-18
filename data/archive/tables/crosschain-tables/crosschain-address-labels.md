# Crosschain Address Labels

### Table Schema

`crosschain.address_labels`

Also learn more about labels [here](../../../flipside-data/labels/).

| Field               | Type      | Description                                                                |
| ------------------- | --------- | -------------------------------------------------------------------------- |
| system\_created\_at | timestamp | The time when the label was sent to the table.                             |
| insert\_date        | timestamp | The date the label was inserted into the table.                            |
| blockchain          | string    | The name of the blockchain.                                                |
| creator             | string    | The name of the creator of the label.                                      |
| address             | string    | The address the label belongs to. Use this to join to other tables.        |
| label\_type         | string    | A high-level category describing the addresses main function or ownership. |
| label\_subtype      | string    | A sub-category nested within label type providing further detail.          |
| address\_name       | string    | Name of the address or the label.                                          |
| project\_name       | string    | Name of the controlling entity of the address.                             |
