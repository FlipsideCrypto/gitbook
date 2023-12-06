# Tax Rate

Taxes are essentially a stability fee and range from 0.1% to 1% of transactions capped at 1 TerraSDR. This can be paid in ANY Terra currency (On-chain I don't think we can distinguish between fees for gas vs taxes. They are rolled up into one).\
\
Note: In January 2022 the tax rate on Terra was lowered to 0%. Prior this, there were two kinds of tax on Terra, the default tax rate as the extra percentage paid for transactions on chain, and the effective tax rate which occurred when your transaction's tax value was greater than the capped 1 SDR default tax rate.

## Table Schema

**table name:** `terra.tax_rate`

| Field             | Type      | Description                                                                       |
| ----------------- | --------- | --------------------------------------------------------------------------------- |
| `BLOCK_NUMBER`    | number    | Block number for this message events been recorded, this one equals to block\_id  |
| `BLOCK_TIMESTAMP` | timestamp | Block time stamp for this message events been recorded                            |
| `BLOCKCHAIN`      | text      | The blockchain name for this block                                                |
| `TAX_RATE`        | number    | The tax ratio for at this block and timestamp                                     |
