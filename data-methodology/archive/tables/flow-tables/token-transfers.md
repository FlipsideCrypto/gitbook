# Token Transfers



| Column           | Type           | Description                                              |
| ---------------- | -------------- | -------------------------------------------------------- |
| tx\_id           | TEXT           | ID for the transaction.                                  |
| block\_timestamp | TIMESTAMP\_NTZ | The date and time for when the block was written.        |
| block\_height    | NUMBER         | The block height the block was recorded at.              |
| sender           | TEXT           | Address sending the transferred token.                   |
| recipient        | TEXT           | Address receiving the transferred token.                 |
| token\_contract  | TEXT           | The contract address for a token on the Flow blockchain. |
| amount           | NUMBER         | The amount of the asset involved in the transaction.     |
| tx\_succeeded    | BOOLEAN        | Transaction status, if it succeeded or failed.           |

{% embed url="https://flipside-flow.netlify.app/#!/model/model.flow_models.core__ez_token_transfers" %}
Full Documentation for Core Token Transfers
{% endembed %}
