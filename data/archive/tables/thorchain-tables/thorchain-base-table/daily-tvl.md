---
description: The table shows the total valued locked and the total value bonded/pooled
---

# Daily TVL

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.daily_tvl`

| Field                    | Type   | Description                                                                            |
| ------------------------ | ------ | -------------------------------------------------------------------------------------- |
| `DAY`                    | date   | The recorded day                                                                       |
| `TOTAL_VALUE_POOLED`     | number | The total amount of rune provided by the liquidity provides and pooled in the pool     |
| `TOTAL_VALUE_POOLED_USD` | number | The total USD amount of rune provided by the liquidity provides and pooled in the pool |
| `TOTAL_VALUE_BONDED`     | number | The total amount of rune provided by the node operators and bonded in the pool         |
| `TOTAL_VALUE_BONDED_USD` | number | The total USD amount of rune provided by the node operators and bonded in the pool     |
| `TOTAL_VALUE_LOCKED`     | number | The total rune value locked in the pool                                                |
| `TOTAL_VALUE_LOCKED_USD` | number | The total USD value locked in the pool                                                 |
