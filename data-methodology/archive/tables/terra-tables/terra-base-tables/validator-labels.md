# Validator Labels

The Validators labels table is based on few different kind of Validator addresses that show up on chain. These individual addresses are matched based on the public\_key of the Validator addresses.

## Table Schema

**table name:** `terra.validator_labels`

| Field               | Type    | Description                                                |
| ------------------- | ------- | ---------------------------------------------------------- |
| `LABEL`             | text    | [(see Labels section for details)](../../../../labels/)    |
| `OPERATOR_ADDRESS`  | address | The validator address (terravaloper)                       |
| `DELEGATOR_ADDRESS` | address | The delegator address of the Validator (terra)             |
| `VP_ADDRESS`        | address | The Validator address used for Voting Power (terravalcons) |

