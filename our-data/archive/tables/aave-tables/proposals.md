---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Proposals



Votes exists within the `aave` schema, as `aave.proposals`

| **Field**             | **Type** | Description                                                                  |
| --------------------- | -------- | ---------------------------------------------------------------------------- |
| `block_id`            | number   | Block number in which the proposal was created                               |
| `start_voting_period` | number   | Block number in which voting may start                                       |
| `end_voting_period`   | number   | Block number in which voting must conclude                                   |
| `block_timestamp`     | string   | Timestamp of the proposal's creation                                         |
| `governance_contract` | address  | Governance contract used in this vote                                        |
| `proposal_id`         | number   | ID of the proposal, which can be used to join in votes from the voting table |
| `status`              | string   | Current status of the proposal -- Created, Queued, Executed or Failed        |
| `targets`             | array    | Markets that are the target of the vote                                      |
| `proposer`            | address  | Address of the user which issued the proposal                                |
| `proposal_tx`         | string   | Transaction of the initial proposal creation                                 |
| `blockchain`          | string   | Ethereum or Polygon (presently only Ethereum)                                |
