---
description: Rewards events table shows the rewards at each block id
---

# Rewards Events

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.rewards_events`

| Field             | Type      | Description                                             |
| ----------------- | --------- | ------------------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded           |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded                   |
| `BOND_E8`         | number    | The rune amount of the bond for this pool at this block |
