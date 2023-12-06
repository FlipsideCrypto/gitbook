# Swaps



| Column               | Type           | Description                                                                                |
| -------------------- | -------------- | ------------------------------------------------------------------------------------------ |
| tx\_id               | TEXT           | ID for the transaction.                                                                    |
| block\_timestamp     | TIMESTAMP\_NTZ | The date and time for when the block was written.                                          |
| block\_height        | NUMBER         | The block height the block was recorded at.                                                |
| swap\_contract       | TEXT           | The smart contract address of the DEX swap pool.                                           |
| trader               | TEXT           | The account address of the trader performing the swap action.                              |
| token\_out\_amount   | FLOAT          | The amount of the token being swapped that the trader is sending to the pool (selling).    |
| token\_out\_contract | TEXT           | The smart contract address for the token that is being swapped out of the traders wallet.  |
| token\_in\_amount    | FLOAT          | The amount of the token being swapped that the trader is receiving from the pool (buying). |
| token\_in\_contract  | TEXT           | The smart contract address for the token that is being swapped into the traders wallet.    |

{% embed url="https://flipside-flow.netlify.app/#!/model/model.flow_models.core__fact_swaps" %}
Full Documentation for Core Swaps
{% endembed %}
