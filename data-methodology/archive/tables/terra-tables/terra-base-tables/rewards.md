# Reward

`Reward` table shows the behaviors about how does supply enter / exist the Terra ecosystem. Staking rewards are made up of **gas (computer fees)**, **taxes**, and **seigniorage rewards**:

* **Gas fee:** Similar concept as the Gas fee in Ethereum network, the fee paid for the transaction in the Network.&#x20;
* **Taxes:** Taxes are essentially a stability fee and range from 0.1% to 1% of transactions capped at 1 TerraSDR, the taxes can be paid in ANY Terra currency&#x20;
* **Seigniorage rewards:** Seigniorage rewards are given to validators for participating in the Luna exchange rate oracle process. Rewards come from the seigniorage pool.

## Table Schema

**table name:** `terra.rewards`

| Field                     | Type      | Description                                                                                                                  |
| ------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `BLOCKCHAIN`              | text      | Blockchain name, here is Terra                                                                                               |
| `CHAIN_ID`                | text      | The type of Blockchain                                                                                                       |
| `TX_STATUS`               | text      | The status of this transaction, either `success` or `failure`                                                                |
| `BLOCK_ID`                | number    | Block number for this message events been recorded                                                                           |
| `BLOCK_TIMESTAMP`         | timestamp | Block time stamp for this message events been recorded                                                                       |
| `TX_ID`                   | text      | Unique transaction id for the reward                                                                                         |
| `MSG_INDEX`               | number    | The index of message, within one message there are many messaged wrapped up and index will show the position of the message  |
| `ACTION`                  | text      | Different actions for the reward, it can be `withdraw_validator_commission`or `withdraw_delegator_rewards`                   |
| `VALIDATOR`               | address   | Validator address                                                                                                            |
| `VALIDATOR_LABEL_TYPE`    | text      | [(see Labels section for details)](../../../../labels/)                                                                      |
| `VALIDATOR_LABEL_SUBTYPE` | text      | [(see Labels section for details)](../../../../labels/)                                                                      |
| `VALIDATOR_ADDRESS_LABEL` | text      | [(see Labels section for details)](../../../../labels/)                                                                      |
| `VALIDATOR_ADDRESS_NAME`  | text      | Validator name linked to the address                                                                                         |
| `DELEGATOR`               | address   | The address for the recipient to receive the reward                                                                          |
| `DELEGATOR_LABEL_TYPE`    | text      | [(see Labels section for details)](../../../../labels/)                                                                      |
| `DELEGATOR_LABEL_SUBTYPE` | text      | [(see Labels section for details)](../../../../labels/)                                                                      |
| `DELEGATOR_ADDRESS_LABEL` | text      | [(see Labels section for details)](../../../../labels/)                                                                      |
| `DELEGATOR_ADDRESS_NAME`  | text      | The recipient name linked to the address                                                                                     |
| `EVENT_AMOUNT`            | number    | The amount of currency for this event                                                                                        |
| `PRICE_USD`               | number    | The price of the token at current timestamp for this currency                                                                |
| `EVENT_AMOUNT_USD`        | number    | Event amount in USD                                                                                                          |
| `CURRENCY`                | text      | The currency for this token                                                                                                  |
