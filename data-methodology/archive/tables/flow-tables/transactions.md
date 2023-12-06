# Transactions



| Column              | Type           | Description                                                       |
| ------------------- | -------------- | ----------------------------------------------------------------- |
| tx\_id              | TEXT           | ID for the transaction.                                           |
| block\_timestamp    | TIMESTAMP\_NTZ | The date and time for when the block was written.                 |
| block\_height       | NUMBER         | The block height the block was recorded at.                       |
| chain\_id           | TEXT           | The id for the chain of the network on which this block occurred. |
| tx\_index           | NUMBER         | tbd                                                               |
| proposer            | TEXT           | Address of the transaction proposer.                              |
| payer               | TEXT           | Address of the wallet paying for the transaction.                 |
| authorizers         | ARRAY          | Address(es) authorizing the transaction.                          |
| count\_authorizers  | NUMBER         | Number of authorizers                                             |
| gas\_limit          | NUMBER         | Upper gas limit attached to the transaction.                      |
| transaction\_result | VARIANT        | Outcome of the transaction, including events that were called.    |
| tx\_succeeded       | BOOLEAN        | Transaction status, if it succeeded or failed.                    |
| error\_msg          | TEXT           | Error message, if the transaction failed, explaining why.         |

{% embed url="https://flipside-flow.netlify.app/#!/model/model.flow_models.core__fact_transactions" %}
Full Documentation for Core Transactions
{% endembed %}
