---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Votes



Votes exists within the `aave` schema, as `aave.votes`

| **Field**             | **Type** | Description                                                                  |
| --------------------- | -------- | ---------------------------------------------------------------------------- |
| `block_timestamp`     | string   | Block timestamp of the vote                                                  |
| `governance_contract` | address  | Governance contract used in this vote                                        |
| `proposal_id`         | number   | ID of the proposal, which can be used to join in votes from the voting table |
| `support`             | string   | Does the voter support the proposal? True/False                              |
| `voting_power`        | number   | Voting power, which depends on the voter's AAVE and stkAAVE balances         |
| `voter`               | address  | voter's address                                                              |
| `tx_id`               | string   | Transaction of the vote                                                      |
| `blockchain`          | string   | Ethereum or Polygon (presently only Ethereum)                                |
