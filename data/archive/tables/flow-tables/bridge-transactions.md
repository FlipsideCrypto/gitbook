# Bridge Transactions



| tx\_id                | TEXT           | ID for the transaction.                                                                                                                                                           |
| --------------------- | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| block\_timestamp      | TIMESTAMP\_NTZ | The date and time for when the block was written.                                                                                                                                 |
| block\_height         | NUMBER         | The block height the block was recorded at.                                                                                                                                       |
| bridge\_contract      | TEXT           | The contract address for the bridge used to move tokens to or from Flow.                                                                                                          |
| token\_contract       | TEXT           | The contract address for a token on the Flow blockchain.                                                                                                                          |
| amount                | FLOAT          | The amount of the asset involved in the transaction.                                                                                                                              |
| flow\_wallet\_address | TEXT           | Address of a FLOW wallet related to the transaction.                                                                                                                              |
| blockchain            | TEXT           | The name of the blockchain for this address or transaction.                                                                                                                       |
| direction             | TEXT           | For bridging transactions, inbound refers to tokens bridged to the Flow blockchain, while outbound indicated tokens were sent from Flow to another (i.e. to Ethereum, BSC, etc.). |
| bridge                | TEXT           | The name of the bridge or protocol used.                                                                                                                                          |

{% embed url="https://flipside-flow.netlify.app/#!/model/model.flow_models.core__fact_bridge_transactions" %}
Full Documentation for Core Bridge Transactions
{% endembed %}
