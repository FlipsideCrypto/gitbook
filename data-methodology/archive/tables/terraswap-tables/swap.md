---
description: terraswap.swaps
---

# Terraswap Swaps

Swaps table contains the information for swap behavior, it involves the sender (trader) and liquidity pool where the swap takes place.&#x20;

**Note**: The terraswap.swaps table is different from terra.swaps. Terraswap swaps are swaps executed by smart contracts in Terraswap liquidity pools. Native swaps (terra.swaps) are on-chain swaps executed by Terra's minting/burning mechanism. For example, when $1 worth of UST is minted, $1 worth of LUNA is burned.&#x20;



## Table Schema



| Field               | Type      | Description                                                                          |
| ------------------- | --------- | ------------------------------------------------------------------------------------ |
| `BLOCKCHAIN`        | text      | The blockchain this swap was created on (Terra)                                      |
| `CHAIN_ID`          | text      | ID of blockchain to connect to, it can be _columbus-3, columbus-4, columbus-5, etc._ |
| `BLOCK_ID`          | number    | The block number that this swap was recorded                                         |
| `MSG_INDEX`         | number    | The message index for this swap                                                      |
| `TX_INDEX`          | number    | The transaction index for this swap, some transactions contain multiple swaps        |
| `BLOCK_TIMESTAMP`   | timestamp | The block timestamp that this swap was recorded                                      |
| `TX_ID`             | text      | The transaction that contained this swap                                             |
| `SENDER`            | address   | Sender (trader) address for this swap                                                |
| `OFFER_AMOUNT`      | number    | Amount to offer for this swap                                                        |
| `OFFER_AMOUNT_USD`  | number    | USD Amount to offer for this swap                                                    |
| `OFFER_CURRENCY`    | text      | Currency to offer for this swap                                                      |
| `RETURN_AMOUNT`     | number    | Amount returned for this swap                                                        |
| `RETURN_AMOUNT_USD` | number    | USD Amount returned for this swap                                                    |
| `RETURN_CURRENCY`   | text      |  The currency returned for the swap                                                  |
| `POOL_ADDRESS`      | text      | The address for the pool where the currencies were swapped                           |
| `POOL_NAME`         | text      | The name of the pool where the currencies were swapped                               |
