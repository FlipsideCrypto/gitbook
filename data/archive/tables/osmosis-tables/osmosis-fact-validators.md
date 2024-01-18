# Osmosis Fact Validators

### Table Schema

`osmosis.core.fact_validators`

| Field                 | Type    | Description                                                                                                              |
| --------------------- | ------- | ------------------------------------------------------------------------------------------------------------------------ |
| address               | string  | Address unique to an individual wallet, validator, or token.                                                             |
| blockchain            | string  | In this table, always Osmosis. Used to join to cross-chain tables.                                                       |
| creator               | string  | Name of the label creator - for now, this will always be "Flipside."                                                     |
| label\_type           | string  | A broad category that describes what a label is representing.                                                            |
| label\_subtype        | string  | Adds more detail to the label type.                                                                                      |
| label                 | string  | The label or name of the address.                                                                                        |
| project\_name         | string  | The name of the project the label belongs to.                                                                            |
| account\_address      | string  | The osmosis address of the user / entity that operates the validator.                                                    |
| delegator\_address    | string  | The number of tokens staked to the validator.                                                                            |
| jailed                | boolean | FALSE when a validator is not jailed, TRUE when a validator is jailed.                                                   |
| max\_change\_rate     | number  | The maximum rate at which a validator can change their commission per day.                                               |
| max\_rate             | number  | The maximum commission rate that the validator can charge.                                                               |
| min\_self\_delegation | number  | The minimum number of OSMO tokens that the operator must be staking with their own validator.                            |
| rank                  | number  | The rank of the validator in the validator set. Rank is determined by the number of OSMO tokens staked to the validator. |
| missed\_blocks        | number  | The number of blocks the validator has been down for during it's lifetime.                                               |
| raw\_metadata         | object  | Additional details about the validator or token in json format.                                                          |

