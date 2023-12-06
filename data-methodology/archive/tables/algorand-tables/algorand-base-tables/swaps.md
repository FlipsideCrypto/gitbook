# Swaps

The swaps table compiles the swaps from the DEXes(decentralized exchanges) throughout the Algorand ecosystem. This table includes the Tinyman, AlgoFi, PactFi, and Wagmiswap DEX. \
\
**Important Note**: When looking at volume we will look at all rows for swaps. However, when looking at the number of swaps we should only count the number of swaps where swaps have a swap\_from_\__amount > 0. This is due to slippage payouts where a users signs an additional swap transaction to receive additional asset due to a change in price during the swap.\


| Field                   | Type      | Description                                                |
| ----------------------- | --------- | ---------------------------------------------------------- |
| swap\_program           | string    | The DEX or program used to make the swap                   |
| block\_timestamp        | timestamp | The time the block began                                   |
| block\_id               | integer   | Unique sequential number that identifies the current block |
| tx\_id                  | string    | A unique key that identifies a transaction                 |
| swapper                 | string    | Address that initiated the swap                            |
| swap\_from_\__amount    | integer   | Total amount of the token sent in to initiate the swap     |
| swap\__from\_asset\_id_ | string    | Token being sent or swapped from                           |
| pool\_address           | string    | Address of the pool the swap is coming from                |
| swap\_to_\__amount      | integer   | Total amount of the token received in the swap             |
| swap\_to_\_asset\_id_   | string    | Token being received or swapped for                        |
