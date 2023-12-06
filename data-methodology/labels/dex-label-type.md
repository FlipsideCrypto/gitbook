# Decentralized Exchange Label Type

The `dex` label type represents any foundation controlled address.

`label_type` = `dex`

### Label Subtypes

| Subtype              | Description                                                                                |
| -------------------- | ------------------------------------------------------------------------------------------ |
| `swap_contract`      | The contract used by the dex to facilitate token exchanges                                 |
| `token_contract`     | Contract of a token belonging to the decentralized exchange                                |
| `pool`               | Any type of pool address, i.e. farming, staking, liquidity etc.                            |
| `vault`              | A vault controlled by the decentalized exchange                                            |
| `fee_wallet`         | Wallet for fees collected by the decentalized exchange                                     |
| `dao`                | An address controlling a DAO controlled by the decentalized exchange                       |
| `chadmin`            | Addresses used for administrative purposes controlled by the decentalized exchange         |
| `contract_deployer`  | A contract controlled by the decentralized exchange that is used to create other contracts |
| `foundation`         | Foundation addresses where the decentralized exchange has a foundation                     |
| `governance`         | Governance addresses where the decentralized exchange has governance                       |
| `rewards`            | Addresses used to distribute rewards                                                       |
| `strategy`           | Addresses used to control strategy                                                         |
| `token_distribution` | Addresses used to distribute supply                                                        |
| `token_sale`         | Addresses used in initial token sales and distributions                                    |
| `general_contract`   | A contract belonging to the exchange                                                       |
| `multisig`           | A multisig contract belonging to the decentralized exchange                                |
