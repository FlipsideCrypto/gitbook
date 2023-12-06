# Asset Freeze Transaction

This is a table for all transactions whose type is Asset Freeze. As the name implies these transactions are made to freeze transactions. Visit here: [ ](https://developer.algorand.org/docs/get-details/transactions/transactions/#asset-configuration-transaction)[https://developer.algorand.org/docs/get-details/transactions/transactions/#asset-freeze-transaction](https://developer.algorand.org/docs/get-details/transactions/transactions/#asset-freeze-transaction)

## Table Schema

All transactions have a distinct intra and block\_id combination. The intra is the transaction # into the block where the transaction was confirmed. Inner transactions(flagged with the inner tx flag) share the tx id of their parent application transactions so you can tie inner transaction to a parent transaction via a tx id. The inner transactions are seen as distinct transactions on the Algorand blockchain, which is signified by their intra and block id combination. One other note on the parent transactions, the parent transaction of inner transaction do not summarize the inner transactions and are seen as their own distinct transaction, which is usually an application call transaction.&#x20;

| Field           | Type    | Description                                                                                                                                                              |
| --------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `INTRA`         | number  | Transaction # into the block where this transaction was confirmed.                                                                                                       |
| `BLOCK_ID`      | number  | Block the transaction was confirmed                                                                                                                                      |
| `TX_GROUP_ID`   | text    | Transaction group ID, can be NULL. Exists when a group of transactions are tied together                                                                                 |
| `TX_ID`         | text    | Transaction ID of the transaction                                                                                                                                        |
| `INNER_TX`      | boolean | A boolean true or false on whether or not this transaction has a parent transaction. The TX\_ID will be the same as the parent transaction but will have it's own intra. |
| `ASSET_ID`      | number  | The asset ID being frozen or unfrozen.                                                                                                                                   |
| `ASSET_ADDRESS` | text    | The address of the account whose asset is being frozen or unfrozen.                                                                                                      |
| `ASSET_FREEZE`  | boolean | True to freeze the asset, otherwise null or false                                                                                                                        |
| `SENDER`        | text    | Address of the wallet creating the transaction                                                                                                                           |
| `FEE`           | number  | Fee associated with the transaction, in ALGOs                                                                                                                            |
| `TX_TYPE`       | number  | Number associated with transaction type                                                                                                                                  |
| `TX_TYPE_NAME`  | text    | transaction type name                                                                                                                                                    |
| `GENISIS_HASH`  | text    | The hash of the genesis block of the network for which the transaction is valid                                                                                          |
| `TX_MESSAGE`    | array   | Encoded JSON message associated with the transaction                                                                                                                     |
| `EXTRA`         | array   | Extra json associated with transaction                                                                                                                                   |
