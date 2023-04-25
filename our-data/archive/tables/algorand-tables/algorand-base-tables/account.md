# Account

The account table contains all address within the Algorand Ecosystem.

## Table Schema



| Field            | Type   | Description                                                                                    |
| ---------------- | ------ | ---------------------------------------------------------------------------------------------- |
| `ADDRESS`        | text   | The account public key                                                                         |
| `ACCOUNT_CLOSED` | number | Whether or not the account is currently closed                                                 |
| `REWARDSBASE`    | number | Used as part of the rewards computation. Only applicable to accounts which are participating.  |
| `BALANCE`        | number | Total number of ALGOs in the account                                                           |
| `CLOSED_AT`      | number | Block during which this account was most recently closed                                       |
| `CREATED_AT`     | number | Block which account was created                                                                |
| `WALLET_TYPE`    | text   | Wallet type: sig(single signature), msig(multi-signature), lsig(programmatic-signature)        |
| `ACCOUNT_DATA`   | array  | Optional Account data                                                                          |
