# Labels

The labels table is based on the Flipside Event label data, currently we included 4 different projects for the labels: `terraswap`, `chai`, `mirror`, `anchor`

[(see Labels section for details)](../../../../labels/)

## Table Schema

**table name:** `terra.labels`

| Field           | Type    | Description                                             |
| --------------- | ------- | ------------------------------------------------------- |
| `BLOCKCHAIN`    | text    | The blockchain name for this block                      |
| `ADDRESS`       | address | The label address                                       |
| `LABEL_TYPE`    | text    | [(see Labels section for details)](../../../../labels/) |
| `LABEL_SUBTYPE` | text    | [(see Labels section for details)](../../../../labels/) |
| `LABEL`         | text    | [(see Labels section for details)](../../../../labels/) |
| `ADDRESS_NAME`  | text    | The name of this address                                |

