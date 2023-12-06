---
description: >-
  Message events table shows the message nodes send to the network, it will have
  the block id, timestamp for identification and the action column shows the
  type of message sent
---

# Message Events

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.message_events`

| Field             | Type      | Description                                   |
| ----------------- | --------- | --------------------------------------------- |
| `BLOCK_ID`        | number    | The block number that this block was recorded |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded         |
| `ACTION`          | text      | The type of action of the message             |
| `FROM_ADDRESS`    | address   | The address sends the message to the network  |
