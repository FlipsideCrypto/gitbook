# Incremental Table Pattern

As data scales we often need a mechanism beyond views to efficiently materialize our data. In this tutorial, we'll walk through how you can use [Snowflake's Merge command](https://docs.snowflake.com/en/sql-reference/sql/merge) to build a table that incrementally updates.&#x20;

***

**Objective**: To maintain an up-to-date and accurate aggregation of Ethereum transaction counts on an hourly basis in a Snowflake table, using an efficient and automated incremental update process.

**Process Overview**:

1. **Target Table**: A dedicated table named `<db>.<schema>.aggregated_hourly_transactions` stores the hourly aggregated transaction counts. This table is structured with two columns: `hour` (TIMESTAMP) and `transaction_count` (INTEGER).
2. **Incremental Update Strategy**: Our process employs a dynamic and intelligent incremental update mechanism. It is designed to process only the most recent data, thus ensuring efficiency, while also accounting for any updated transactions.
3. **MERGE Command**: We use the SQL [`MERGE`](https://docs.snowflake.com/en/sql-reference/sql/merge) command in Snowflake to seamlessly integrate new data into the target table. This command checks for the latest hour in the target table and reprocesses data starting from four hours before this timestamp, accommodating any data delays or revisions. It is idempotent and can be run as often as you require.

#### Step 1: Create the Target Table

If it doesn't already exist, create a table to store the hourly transaction counts:

```sql
CREATE TABLE IF NOT EXISTS <db>.<schema>.aggregated_hourly_transactions (
    hour TIMESTAMP,
    transaction_count INTEGER
);

```

**Step 2: Merge Query for Incremental Update**

The `MERGE` pattern ensures that the latest transaction counts are accurately reflected, with no duplicates and proper handling of any updates in the source data.

```sql
MERGE INTO <db>.<schema>.aggregated_hourly_transactions AS target
USING (
    -- METRIC LOGIC
    SELECT
        DATE_TRUNC('hour', block_timestamp) AS hour,
        COUNT(*) AS transaction_count
    FROM
        ethereum.core.fact_transactions
    WHERE
        block_timestamp > COALESCE(
            DATEADD(hour, -4, (SELECT MAX(hour) FROM <db>.<schema>.aggregated_hourly_transactions)),
            '1970-01-01' -- Default start date for the first run
        )
    GROUP BY
        DATE_TRUNC('hour', block_timestamp)
) AS source
ON target.hour = source.hour
WHEN MATCHED THEN
    UPDATE SET target.transaction_count = source.transaction_count
WHEN NOT MATCHED THEN
    INSERT (hour, transaction_count)
    VALUES (source.hour, source.transaction_count)
```

**Key Benefits/Features**:

* **Efficiency**: By focusing on a limited and relevant time range, we avoid reprocessing the entire dataset, saving computational resources and time.
* **Data Integrity**: The 4-hour "lookback" window prior to the latest timestamp in the target table ensures we capture any updates to existing records, maintaining high data accuracy.
* **Adaptability**: This process automatically adapts to the data's current state. On the first run, it processes all available historical data. In subsequent runs, it updates based on the most recent, relevant data.
* **Customizability**: The time range for lookback (currently 4 hours) can be adjusted based on your specific data characteristics and update frequency.

## Beyond the tutorial

The above pipeline could be run programmatically on a schedule using [Snowflake's connectors/SDKs](https://docs.snowflake.com/en/developer-guide/drivers) and your favorite scheduler (CRON, Temporal, Dagster, Airflow, etc.)

Alternatively, you can also leverage [DBT](https://www.getdbt.com/), which abstracts away the generic merge mechanics. You can see how Flipside achieves this [here](https://github.com/FlipsideCrypto/ethereum-models/tree/main) using DBT.&#x20;



\
