---
description: Inactive Vault Events lists the events triggered by the churning activities
---

# Inactive Vault Events

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.inactive_vault_events`

| Field             | Type      | Description                                        |
| ----------------- | --------- | -------------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded      |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded              |
| `ADD_ASGARD_ADDR` | address   | The asgard address in the vault which are inactive |
