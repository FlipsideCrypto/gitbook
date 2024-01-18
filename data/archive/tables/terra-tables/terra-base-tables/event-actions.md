---
description: >-
  Row based event actions table curated from terra.msg_events event attributes.
  Actions or methods in the 'from_contract' event type are displayed as records
  based on contract address.
---

# Event Actions

## Table Schema

table name: `terra.event_actions`

<table><thead><tr><th width="277.1723384899322">Field</th><th width="154.6185569170212">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>BLOCK_ID</code></td><td>number</td><td>The block number for this event action</td></tr><tr><td><code>BLOCK_TIMESTAMP</code></td><td>timestamp</td><td>The timestamp this block was recorded</td></tr><tr><td><code>BLOCKCHAIN</code></td><td>text</td><td>The blockchain name for this block</td></tr><tr><td><code>CHAIN_ID</code></td><td>text</td><td>ID of blockchain to connect to, it can be <em>columbus-3, columbus-4</em>, <em>columbus-5</em>, etc.</td></tr><tr><td><code>TX_ID</code></td><td>text</td><td>The transaction that contained this event action</td></tr><tr><td><code>ACTION_INDEX</code></td><td>number</td><td>Index for event actions</td></tr><tr><td><code>MSG_INDEX</code></td><td>number</td><td>Message index, it is like the different steps for message, one message group can contain multiple message index values to deliver different information</td></tr><tr><td><code>ACTION_CONTRACT_ADDRESS</code></td><td>text</td><td>Contract address that kicked off this event action</td></tr><tr><td><code>CONTRACT_LABEL</code></td><td>text</td><td><a href="../../../../flipside-data/labels/">(see Labels section for details)</a></td></tr><tr><td><code>ACTION_METHOD</code></td><td>text</td><td>The action or method within an event</td></tr><tr><td><code>ACTION_LOG</code></td><td>object</td><td>The log that provides detail (amounts, to, from, etc.) to an action or method</td></tr></tbody></table>
