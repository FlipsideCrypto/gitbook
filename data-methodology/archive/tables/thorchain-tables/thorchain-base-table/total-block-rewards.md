---
description: The total block rewards for each pool
---

# Total Block Rewards

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.total_block_rewards`

| Field             | Type      | Description                                    |
| ----------------- | --------- | ---------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded  |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded          |
| `REWARD_ENTITY`   | text      | The asset or named as pool name                |
| `RUNE_AMOUNT`     | number    | The rewards measured in RUNE amount            |
| `RUNE_AMOUNT_USD` | number    | The rewards measured in RUNE amount in the USD |
