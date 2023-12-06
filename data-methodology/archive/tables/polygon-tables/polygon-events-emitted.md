# Polygon Events Emitted

{% hint style="warning" %}
These are legacy Polygon tables. See [Polygon 2.0](../polygon-2.0-tables.md) for up-to-date Polygon models.
{% endhint %}

Polygon events emitted table contains the information for the Polygon events, it is extracted from the Polygon blockchain and there are some notable features:

* All event inputs are decoded and stored in a fully queryable JSON column called `event_inputs`
* Flipside's labels have been merged in.
* Every contract has an associated name that corresponds 1:1 with the solidity contract code.

## Table Schema

`polygon.events_emitted`

| Field                    | Type      | Description                                                                                                    |
| ------------------------ | --------- | -------------------------------------------------------------------------------------------------------------- |
| block\_id                | number    | The block height this event was recorded at.                                                                   |
| block\_timestamp         | timestamp | UTC block timestamp for parent block                                                                           |
| tx\_id                   | string    | Transaction hash                                                                                               |
| event\_index             | string    | The index/order of the event in the transaction                                                                |
| event\_inputs            | json      | Decoded event inputs (specifically topics/data are decoded)                                                    |
| event\_name              | string    | English decoded name for the event name. This could be a transfer, or any decoded log method or log event name |
| event\_removed           | boolean   | Whether the event get removed or not                                                                           |
| tx\_from\_address        | address   | The initiator of the transaction.                                                                              |
| tx\_from\_address\_name  | string    | [(see Labels section for details)](../../../labels/)                                                           |
| tx\_from\_label          | string    | [(see Labels section for details)](../../../labels/)                                                           |
| tx\_from\_label\_subtype | string    | [(see Labels section for details)](../../../labels/)                                                           |
| tx\_from\_label\_type    | string    | [(see Labels section for details)](../../../labels/)                                                           |
| tx\_to\_address          | address   | The receiver of the transaction or initial contract being called                                               |
| tx\_to\_address\_name    | string    | [(see Labels section for details)](../../../labels/)                                                           |
| tx\_to\_label            | string    | [(see Labels section for details)](../../../labels/)                                                           |
| tx\_to\_label\_subtype   | string    | [(see Labels section for details)](../../../labels/)                                                           |
| tx\_to\_label\_type      | string    | [(see Labels section for details)](../../../labels/)                                                           |
| contract\_address        | address   | The parent contract that is responsible for kicking off this event.                                            |
| contract\_name           | string    | The name of this contract.                                                                                     |
| tx\_succeeded            | boolean   | Was this transaction successful?                                                                               |
