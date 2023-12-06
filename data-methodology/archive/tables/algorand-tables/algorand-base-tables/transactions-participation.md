# Transactions Participation

This is a transaction participation table which lists the addresses involved in a transaction within a block and what intra the address was involved in.

## Table Schema

| Field      | Type   | Description                                                |
| ---------- | ------ | ---------------------------------------------------------- |
| `INTRA`    | number | Offset into the block where this transaction was confirmed |
| `BLOCK_ID` | number | Block                                                      |
| `ADDRESS`  | text   | Wallet address associated with intra and block             |

