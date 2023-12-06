---
description: The swaps table to show the swap activity in the Thorchain
---

# Swaps

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.swaps`

| Field               | Type      | Description                                                         |
| ------------------- | --------- | ------------------------------------------------------------------- |
| `BLOCK_ID`          | number    | The block number that this block was recorded                       |
| `BLOCK_TIMESTAMP`   | timestamp | The timestamp this block was recorded                               |
| `TX_ID`             | text      | The unique transaction id for the this swap                         |
| `BLOCKCHAIN`        | text      | The blockchain for the swap transaction                             |
| `POOL_NAME`         | text      | The pool name where the swaps happen                                |
| `FROM_ADDRESS`      | address   | The user address that initiates the swap                            |
| `NATIVE_TO_ADDRESS` | address   | The user address that is receiving the result of the swap           |
| `TO_POOL_ADDRESS`   | address   | The pool address that processes the swap                            |
| `FROM_ASSET`        | text      | Initial asset to swap                                               |
| `TO_ASSET`          | text      | The asset swap to                                                   |
| `FROM_AMOUNT`       | number    | Amount of the asset to swap from                                    |
| `TO_AMOUNT`         | number    | Amount of the asset to swap for                                     |
| `MIN_TO_AMOUNT`     | number    | Minimal amount to swap for                                          |
| `FROM_AMOUNT_USD`   | number    | Amount in USD of the asset to swap from                             |
| `TO_AMOUNT_USD`     | number    | Amount in USD of the asset to swap for                              |
| `TO_AMOUNT_MIN_USD` | number    | Minimal amount in USD to swap for                                   |
| `SWAP_SLIP_BP`      | number    | The slippage during the swap process                                |
| `LIQ_FEE_RUNE`      | number    | The amount of RUNE liquidity fee paid in RUNE for the swaps         |
| `LIQ_FEE_RUNE_USD`  | number    | The amount of RUNE in USD liquidity fee paid in RUNE for the swaps  |
| `LIQ_FEE_ASSET`     | number    | The amount of Asset liquidity fee paid in RUNE for the swaps        |
| `LIQ_FEE_ASSET_USD` | number    | The amount of Asset in USD liquidity fee paid in RUNE for the swaps |
