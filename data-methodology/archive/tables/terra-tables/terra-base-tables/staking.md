# Staking

Staking table listed the information about the users who staked the tokens into the chain and it contains the information of the amount of the staking token, price and the validator and delegator address.&#x20;

## Table Schema

**table name:** `terra.staking`

| Field                     | Type      | Description                                                   |
| ------------------------- | --------- | ------------------------------------------------------------- |
| `BLOCKCHAIN`              | text      | Blockchain name, here is Terra                                |
| `CHAIN_ID`                | text      | The type of Blockchain                                        |
| `TX_STATUS`               | text      | The transaction status for the staking                        |
| `BLOCK_ID`                | number    | Block number for this message events been recorded            |
| `BLOCK_TIMESTAMP`         | timestamp | Block time stamp for this message events been recorded        |
| `TX_ID`                   | text      | The unique transaction id                                     |
| `ACTION`                  | text      | The action taken for this transaction                         |
| `DELEGATOR_ADDRESS`       | address   | The address of the delegator for this staking event           |
| `DELEGATOR_LABEL_TYPE`    | text      | [(see Labels section for details)](../../../../labels/)       |
| `DELEGATOR_LABEL_SUBTYPE` | text      | [(see Labels section for details)](../../../../labels/)       |
| `DELEGATOR_ADDRESS_LABEL` | text      | [(see Labels section for details)](../../../../labels/)       |
| `DELEGATOR_ADDRESS_NAME`  | text      | Delegator name linked to the address                          |
| `VALIDATOR_ADDRESS`       | address   | The validator is the addresses to validate the delegation     |
| `VALIDATOR_LABEL_TYPE`    | text      | [(see Labels section for details)](../../../../labels/)       |
| `VALIDATOR_LABEL_SUBTYPE` | text      | [(see Labels section for details)](../../../../labels/)       |
| `VALIDATOR_ADDRESS_LABEL` | text      | [(see Labels section for details)](../../../../labels/)       |
| `VALIDATOR_ADDRESS_NAME`  | text      | Validator name linked to the address                          |
| `EVENT_AMOUNT`            | number    | The amount of currency for this event                         |
| `PRICE_USD`               | number    | The price of the token at current timestamp for this currency |
| `EVENT_AMOUNT_USD`        | number    | Event amount in USD                                           |
| `CURRENCY`                | text      | The currency for this token                                   |
