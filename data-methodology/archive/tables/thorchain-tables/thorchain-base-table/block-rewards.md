---
description: The summarized rewards information for each block per day
---

# Block Rewards

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.block_rewards`

| Field                | Type   | Description                                                  |
| -------------------- | ------ | ------------------------------------------------------------ |
| `DAY`                | date   | The recorded day                                             |
| `LIQUIDITY_FEE`      | number | The summarized liquidity cost fee within this day            |
| `BLOCK_REWARDS`      | number | The summarized total block rewards within this day           |
| `EARNINGS`           | number | The summarized earnings within this day                      |
| `BONDING_EARNINGS`   | number | The summarized bonding earnings within this day              |
| `LIQUIDITY_EARNINGS` | number | The summarized liquidity earnings fee within this day        |
| `AVG_NODE_COUNT`     | number | The summarized average node operators number within this day |
