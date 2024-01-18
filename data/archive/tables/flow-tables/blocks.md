# Blocks



| Column           | Type           | Description                                                       |
| ---------------- | -------------- | ----------------------------------------------------------------- |
| block\_height    | NUMBER         | The block height the block was recorded at.                       |
| block\_timestamp | TIMESTAMP\_NTZ | The date and time for when the block was written.                 |
| network          | TEXT           | The blockchain network the block or transaction occurred on.      |
| chain\_id        | TEXT           | The id for the chain of the network on which this block occurred. |
| tx\_count        | NUMBER         | The number of transactions in the block.                          |
| id               | TEXT           | The block hash.                                                   |
| parent\_id       | TEXT           | The block hash for the parent block.                              |

{% embed url="https://flipside-flow.netlify.app/#!/model/model.flow_models.core__fact_blocks" %}
Full Documentation for Core Blocks
{% endembed %}
