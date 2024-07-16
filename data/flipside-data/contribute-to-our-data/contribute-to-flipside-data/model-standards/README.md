# Model Standards

## Style Standards

Our general model and style standards are derived from the best practices guide put forth by dbt Labs:

{% embed url="https://github.com/dbt-labs/corp/blob/main/dbt_style_guide.md" %}

All code that is submitted for a PR should be formatted according to [this dbt autoformatter](https://github.com/henriblancke/dbt-formatter), available as an extension on the VS Code extension marketplace.

The primary needs with a Flipside dbt model (will be explained in greater detail below):

1. [Star schema](./#dimensional-modeling-and-star-schema)
2. [Tests and full documentation](./#model-properties)
3. [Appropriate materialization](./#materialization)
4. [Consistent column names](./#column-names)

## Dimensional Modeling & Star Schema

### Table Layers

#### Bronze

1. Blockchain data that has been indexed and piped into Snowflake under `chainwalkers` schema. This includes all core data characterizing what occurs on a chain (e.g. blocks, transactions, function calls, state changes, etc). Chainwalkers 2.0 decodes log data, but does no other transformation.&#x20;
2. The only data that has been added to this is `_inserted_timestamp`. This has been added a requirement for all blockchains for efficiency and data integrity reasons.
3. Any ingested data should be in the bronze layer.
4. This layer is a view on the source, as such it is the only layer where `{{ source() }}` should be called and no transformations shall happen in bronze.

#### Silver

1. Filtered, cleaned and transformed data.
2. Silver models should de-duplicate bronze, as chainwalkers may re-ingest a block at a later date.
3. The models in this layer are incremental as to reduce compute time and cost.
4. Fact and dimension tables which are completely decoded (where we can), are additive (no replacing data), deduped, have not been joined to other tables. We can expose silver tables in the public facing app as a gold view.&#x20;
5. Can be a combination of data sources.

#### Gold (Core)

1. Curated models exposed to the public front-end.
2. [Fact and dimension](https://docs.google.com/document/d/1sdtchIcnkzMyP0HLQkA-c3BtE4AWgNFjiGFnhX3YzAs/edit#heading=h.snh3fvv82vz1) **tables should never be combined in tables ie: no joining transactions and labels**. They can be combined in views, where the logic is done in the underlying queries.&#x20;
3. Views that can ease the burden for analysts. The wide array of data-users include some new to SQL, new to analytics, and/or new to blockchain technology. Incorporating off-chain metadata, and even aggregations (e.g. daily summaries of key transactions) can help new users understand the ecosystem as a whole.&#x20;
   1. This also eases the burden on the underlying systems, and facilitates “Easy” bounty programs.&#x20;
   2. Facilitates learning for new users.
   3. Examples include: labels, transfers, event logs, swaps, liquidity provision/removal, daily balances of holders, prices and decimals, daily transfer summary.
4. Models that accelerate analytics for a particular protocol (e.g. compound, uniswapv3, anchor, mirror schemas).

### Core Naming Conventions

#### 3 Primary Types of Views

All views should have a prefix of what type of data is within (based on [star schema](https://docs.google.com/document/d/1GxWCUBkMB55h1Qb8-t42JW7s2yJWe57nsElzE4gMSyc/edit)).

All names should\_be\_snake\_case. Abbreviations should be avoided when possible. Abbreviations should match an iso standard ie: currency or country names, etc.

1. Facts (`fact_`)
   1. Fact table contains measurements, metrics, and facts. Anything that is measurable, summing, averaging, anything over time.
2. Dimensions (`dim_`)
   1. Dimension table is a companion to the fact table which contains descriptive attributes to be used as query constraining.
3. Convenience Views (`ez_`)
   1. Convenience Views can combine facts and dimensions for reasons above. This should only be views in the gold layer.
   2. Where curation is doing more of the “lift” for the view.

## Model Properties

SQL models do not dance alone! Each `sql` file should have an accompanying `yml` of the same name. This is the model properties file and we use it, primarily, to document the model and columns and to test data in the model, at the column level.

{% embed url="https://docs.getdbt.com/reference/model-properties" %}

### Testing

The model properties allow us to test the model output to ensure the data flowing through meets expectations. Some common [generic tests](https://docs.getdbt.com/docs/build/tests#generic-tests) we use are:

* unique
* not null
* accepted values

There are also [packages](https://github.com/dbt-labs/dbt-utils) with utility functions that enhance the available tests to plug into a model, or you can write [custom tests](https://docs.getdbt.com/guides/best-practices/writing-custom-generic-tests) that apply to the model.

### Documentation

The `yml` file is also where tables and columns are [documented](https://docs.getdbt.com/docs/collaborate/documentation#adding-descriptions-to-your-project). These should be clear and concise for users to understand what data the model contains. As several columns might be used across models, we utilize the [doc block](https://docs.getdbt.com/reference/dbt-jinja-functions/doc) to define the column in a markdown file, rather than in each individual model property file.

## Materialization

dbt Models can be configured to run using one of a number of strategies. The two most common materializations in our models are [incremental](https://docs.getdbt.com/docs/build/incremental-models) and [view](https://docs.getdbt.com/terms/view).

### Incremental

True to the name, incremental models load data based on some incremental filter. In silver, just about every model will be incrementally built, based on `_inserted_timestamp`.&#x20;

### View

Views persist as SQL transformations without actually storing data, like a table. Every `core` (gold) model is a view on a silver incremental model. This is done to:

* drop any internal columns that need not be exposed to end users (like `_inserted_timestamp`)
* rename the model to follow star schema

{% embed url="https://docs.getdbt.com/docs/build/materializations" %}

## Column Names

When building a model, be sure to check how columns are already named in the blockchain's data tables. Within a database, one model should not refer to `tx_id` while another `tx_hash`. A more comprehensive naming standard will be published soon™️.
