# dbt Tips

## Naming Convention

As noted in the model standards, we segment steps into bronze/silver/core layers and these are organized via schemas within a database. The directory structure within `models/` is not what determines database structure! Our models include a pre-written macro that handles this database organization based on the model name! A double underscore in the file-name will be parsed as a schema break.

So, `silver__blocks` compiles to a table `blocks` in schema `silver`.

## Table Materialization

A table is materialized as incremental via the model config. Flipside does this in each model by using a config block. There are three properties in the config block to note for setting an incremental model.

```
{{ config(
    materialized = 'incremental',
    incremental_strategy = <strategy>,
    unique_key = <unique_key_column>,
    ...
) }}
```

* [`materialized`](https://docs.getdbt.com/reference/resource-configs/materialized) sets the type of model
* [`incremental_strategy`](https://docs.getdbt.com/docs/build/incremental-models#about-incremental_strategy) determines the build approach. On Snowflake, the default is `merge` but you may also see `delete+insert`
* [`unique_key`](https://docs.getdbt.com/reference/resource-configs/unique_key) is a required parameter, regardless of incremental or table, but is used in the `incremental_strategy` to identify records.

When creating models with incremental materialization, we need to write an incremental logic within the model. It is important for the incremental logic to be based on `_inserted_timestamp` and not on the `block_timestamp`_._ This is important especially when the data encounters gaps on certain dates. This enables the model to heal itself because gaps are associated with `block_timestamp` and when they get-inserted later, they get captured by _`_inserted_timestamp`._

```sql
 {% if is_incremental() %}
WHERE _inserted_timestamp >= (
    SELECT
        MAX(_inserted_timestamp) :: DATE - 1
    FROM
        {{ this }}
)
{% endif %}
```

