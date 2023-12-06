---
description: Rewards event entries table shows the entries for the rewards
---

# Rewards Event Entries

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.rewards_event_entries`

| Field             | Type      | Description                                                |
| ----------------- | --------- | ---------------------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded              |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded                      |
| `POOL_NAME`       | text      | The pool name for the rewards                              |
| `RUNE_E8`         | number    | The rune amount of the rewards for this pool at this block |
