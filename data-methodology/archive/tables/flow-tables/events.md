# Events



| Column           | Type           | Description                                                                                                                                                          |
| ---------------- | -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| tx\_id           | TEXT           | ID for the transaction.                                                                                                                                              |
| block\_timestamp | TIMESTAMP\_NTZ | The date and time for when the block was written.                                                                                                                    |
| block\_height    | NUMBER         | The block height the block was recorded at.                                                                                                                          |
| tx\_succeeded    | BOOLEAN        | Transaction status, if it succeeded or failed.                                                                                                                       |
| event\_index     | NUMBER         | The index of the event within the transaction, i.e. in what order the events occurred.                                                                               |
| event\_contract  | TEXT           | The contract called for this event. This is equivalent to the Contract column on Flowscan and is a concatenation of the contract's account address and primary name. |
| event\_type      | TEXT           | The type of method called on the event\_contract. This is equivalent to the Type column on Flowscan.                                                                 |
| event\_data      | OBJECT         | The data passed to the event                                                                                                                                         |

{% embed url="https://flipside-flow.netlify.app/#!/model/model.flow_models.core__fact_events" %}
Full Documentation for Core Events
{% endembed %}
