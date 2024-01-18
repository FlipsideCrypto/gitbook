# Msgs

Message table shows all the message information blocks contains. Please be aware that for now terra msgs table only contains the data for **Columbus-4** and **Columbus-5.**

## Table Schema

**table name:** `terra.msgs`

| Field             | Type      | Description                                                                                                                                           |
| ----------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| `BLOCK_ID`        | number    | Block number for this message been recorded                                                                                                           |
| `BLOCK_TIMESTAMP` | timestamp | The timestamp this block was recorded                                                                                                                 |
| `BLOCKCHAIN`      | text      | The blockchain name for this block                                                                                                                    |
| `CHAIN_ID`        | text      | ID of blockchain to connect to, it can be _columbus-3, columbus-4, etc._                                                                              |
| `TX_ID`           | text      | The transaction that contained this message, unique id to identify this message information                                                           |
| `TX_STATUS`       | text      | Transaction Status for this message                                                                                                                   |
| `TX_MODULE`       | text      | Transaction Module for this message                                                                                                                   |
| `TX_TYPE`         | text      | Transaction Type for this message                                                                                                                     |
| `MSG_INDEX`       | number    | Message index, it is like the different steps for message, one message group can contain multiple message index to deliver many different information |
| `MSG_MODULE`      | text      | Different type of message, it can be _distribution, oracle, etc._                                                                                     |
| `MSG_TYPE`        | text      | The sub type of message module, the format is like _oracle/..._                                                                                       |
| `MSG_VALUE`       | array     | The content of this message, it can be JSON or array and there are many attributes there to identify what kind of message it delivers                 |

