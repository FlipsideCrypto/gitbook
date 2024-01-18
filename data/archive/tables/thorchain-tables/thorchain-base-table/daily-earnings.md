---
description: The earnings information for the whole THORChain network broken down by daily
---

# Daily Earnings

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.daily_earnings`

| Field                   | Type   | Description                                                  |
| ----------------------- | ------ | ------------------------------------------------------------ |
| `DAY`                   | date   | The recorded day                                             |
| `LIQUIDITY_FEE`         | number | The summarized liquidity cost fee within this day            |
| `LIQUIDITY_FEES_USD`    | number | The summarized liquidity cost fee within this day in USD     |
| `BLOCK_REWARDS`         | number | The summarized total block rewards within this day           |
| `BLOCK_REWARDS_USD`     | number | The summarized total block rewards within this day in USD    |
| `TOTAL_EARNINGS`        | number | The summarized total earnings within this day                |
| `TOTAL_EARNINGS_USD`    | number | The summarized total earnings within this day in USD         |
| `EARNINGS_TO_NODES`     | number | The summarized bonding earnings within this day              |
| `EARNINGS_TO_NODES_USD` | number | The summarized bonding earnings within this day in USD       |
| `EARNINGS_TO_POOLS`     | number | The summarized liquidity earnings fee within this day        |
| `EARNINGS_TO_POOLS_USD` | number | The summarized liquidity earnings fee within this day in USD |
| `AVG_NODE_COUNT`        | number | The summarized average node operators number within this day |
