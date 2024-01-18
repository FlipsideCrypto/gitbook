---
description: Swap event entries table shows the entries for the swaps
---

# Swap Events

| Field                | Type   | Description                                                                     |
| -------------------- | ------ | ------------------------------------------------------------------------------- |
| `_FIVETRAN_ID`       | text   | A unique identifier for the swap event                                          |
| `TO_ADDR`            | text   | The address we are swapping to                                                  |
| `LIQ_FEE_IN_RUNE_E8` | number | The fee in RUNE (divide by 10^8 to get the decimal amount)                      |
| `FROM_ADDR`          | text   | The address we are swapping from                                                |
| `TO_ASSET`           | text   | The asset we are swapping to                                                    |
| `FROM_ASSET`         | text   | The asset we are swapping from                                                  |
| `SWAP_SLIP_BP`       | number | The slippage                                                                    |
| `BLOCK_TIMESTAMP`    | number | The timestamp of when the block was created                                     |
| `LIQ_FEE_E8`         | number | The fee (divide by 10^8 to get the decimal amount)                              |
| `CHAIN`              | text   | The chain we are interacting with                                               |
| `TO_E8`              | number | The asset amount we are swapping for (divide by 10^8 to get the decimal amount) |
| `POOL`               | text   | The name of the pool                                                            |
| `TX`                 | text   | The transaction ID of the swap                                                  |
| `MEMO`               | text   | The transaction memo                                                            |
| `TO_E8_MIN`          | number | The minimum amount the swapper will receive                                     |
| `FROM_E8`            | number | The amount we are swapping from                                                 |

