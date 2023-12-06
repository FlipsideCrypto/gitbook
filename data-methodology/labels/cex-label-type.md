# Centralized Exchange Label Type

Centralized Exchanges are referred to as `cex` in the Flipside label system.&#x20;

`label_type` = `cex`

### Label Subtypes

| Subtype             | Description                                                                                                                                                         |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `hot_wallet`        | Centralized exchange hot wallets -- addresses that collect funds from deposit wallets, send withdrawals to customers, and hold the majority of the exchange’s funds |
| `deposit_wallet`    | Centralized exchange deposit wallets                                                                                                                                |
| `cold_wallet`       | A wallet used to hold rarely used funds belonging to the exchange                                                                                                   |
| `chadmin`           | A administration address belonging to the exchange                                                                                                                  |
| `contract_deployer` | A contract belonging to the exchange that is used to create other contracts                                                                                         |
| `general_contract`  | A general use contract belonging to the exchange                                                                                                                    |
| `multisig`          | A general use multisig wallet belonging to the exchange                                                                                                             |
| `token_contract`    | Contract of a token owned by the exchange                                                                                                                           |

