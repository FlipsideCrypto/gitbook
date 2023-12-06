# Msg\_events

Message events table shows all the message events information blocks contains. Please be aware that for now terra msgs table only contains the data for **Columbus-4** and **Columbus-5.**

## Table Schema

**table name:** `terra.msg_events`

| Field              | Type      | Description                                                                                                                                           |
| ------------------ | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| `BLOCK_ID`         | number    | Block number for this message been recorded                                                                                                           |
| `BLOCK_TIMESTAMP`  | timestamp | The timestamp this block was recorded                                                                                                                 |
| `BLOCKCHAIN`       | text      | The blockchain name for this block                                                                                                                    |
| `CHAIN_ID`         | text      | ID of blockchain to connect to, it can be _columbus-3, columbus-4_, etc.                                                                              |
| `TX_ID`            | text      | The transaction that contained this message, unique id to identify this message information                                                           |
| `TX_STATUS`        | text      | Transaction Status for this message events                                                                                                            |
| `TX_MODULE`        | text      | Transaction Module for this message events                                                                                                            |
| `TX_TYPE`          | text      | Transaction Type for this message events                                                                                                              |
| `MSG_INDEX`        | number    | Message index, it is like the different steps for message, one message group can contain multiple message index to deliver many different information |
| `MSG_MODULE`       | text      | Different type of message, it can be distribution, oracle, etc.                                                                                       |
| `MSG_TYPE`         | text      | The sub type of message module, the format is like oracle/...                                                                                         |
| `EVENT_INDEX`      | number    | Event happens within message, it can be seen as the steps of message. Event Index defines the index of this event within the message                  |
| `EVENT_TYPE`       | text      | For each event, there will be a type linked to that                                                                                                   |
| `EVENT_ATTRIBUTES` | array     | The information contained within each event, it can be a JSON array format                                                                            |
