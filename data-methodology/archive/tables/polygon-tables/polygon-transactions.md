# Polygon Transactions

{% hint style="warning" %}
These are legacy Polygon tables. See [Polygon 2.0](../polygon-2.0-tables.md) for up-to-date Polygon models.
{% endhint %}

Polygon transactions exist within the polygon schema, as `polygon.transactions` .

Transactions contain top-level summary information not found in `polygon.udm_events`, for example, transaction fees and gas.

## Table Schema

`polygon.transactions`

| Field                | Type                      | Description                                                         |
| -------------------- | ------------------------- | ------------------------------------------------------------------- |
| block\_id            | number                    | The block height this event was recorded at.                        |
| block\_timestamp     | timestamp                 | UTC block timestamp for parent block                                |
| tx\_id               | string                    | The hash (unique identifier) of the transaction.                    |
| tx\_position         | string                    | The position of the transaction in the block.                       |
| nonce                | number                    | The number of transactions sent from the `from_address.`            |
| from\_address        | address                   | The sender/initiator of the transaction.                            |
| from\_address\_name  | [label](../../../labels/) | [(see label's data model for details)](../../../labels/)            |
| from\_label          | [label](../../../labels/) | [(see label's data model for details)](../../../labels/)            |
| from\_label\_subtype | [label](../../../labels/) | [(see label's data model for details)](../../../labels/)            |
| from\_label\_type    | [label](../../../labels/) | [(see label's data model for details)](../../../labels/)            |
| to\_address          | text                      | The recipient of the transaction, or contract being called.         |
| to\_addres\_name     | [label](../../../labels/) | [(see label's data model for details)](../../../labels/)            |
| to\_label            | [label](../../../labels/) | [(see label's data model for details)](../../../labels/)            |
| to\_label\_subtype   | [label](../../../labels/) | [(see label's data model for details)](../../../labels/)            |
| to\_label\_type      | [label](../../../labels/) | [(see label's data model for details)](../../../labels/)            |
| symbol               | text                      | The project symbol (i.e. ERC-20 transaction), if applicable.        |
| function\_signature  | string                    | The function signature of the contract call, if applicable.         |
| function\_name       | string                    | The English decoded name of the function signature, if applicable.  |
| gas\_price           | number                    | The gas price at the time of this transaction.                      |
| gas\_limit           | number                    | The gas limit specified in this transaction.                        |
| gas\_used            | number                    | The amount of gas used by this transaction.                         |
| fee                  | number                    | The transaction fee calculated from the gas price and the gas used. |
| fee\_usd             | number                    | The USD equivalent fee at the time of the transaction.              |
| success              | text                      | The success state of this transaction execution.                    |
| event\_count         | number                    | The number of events contained within this transaction.             |

