---
description: A guide to data curation with Flipside.
---

# Community Curation

## Open Source Models

Flipside Crypto is a data analytics and research firm that provides data-driven insights and analysis for the cryptocurrency market. Our data models are open source and available on GitHub, and anyone can contribute to them. We use [dbt](https://www.getdbt.com/), a command-line tool for working with data, to transform raw Blockchain data ingested through RPC nodes or an indexer into clean and easy-to-use data. These transformations are transparent to users, so they can see exactly how the data is being processed and can even contribute to the development of the models themselves. By making our data models open source and transparent, we are enabling our partners and users to collaborate with us and help improve the accuracy and reliability of our data.

The models for each chain that we offer can be reviewed and contributed to on our Github. Repositories follow the following naming convention for each blockchain: `<chain>-models`.

{% embed url="https://github.com/orgs/FlipsideCrypto/repositories" %}

## Contribute&#x20;

### Tags & Labels

See [How to Add Tags](../our-data/featured-tags-and-sql-examples/how-to-add-your-own-tags.md) on the address tags & labels data model page.\
Add a label by submitting through our [label submission form](https://science.flipsidecrypto.xyz/add-a-label/).

### SQL Models

The Flipside community uses [dbt](https://www.getdbt.com/) to model data in a [Snowflake](https://www.snowflake.com/) database. The following page on our [Analytics Stack for Community Curation](broken-reference) will go into further depth about the tech stack. If you are familiar with these tools, skip to [Getting Started](getting-started/) for instructions on access and setting up your dev environment.

#### What and why?

In its most simple form, dbt allows for reproducible SQL in the form of data models where the queries are used to build tables. In the analyst workflow, there is likely a lot of data transformation required to parse transaction and event data down to the activity of interest. You likely factor this work out into one or many CTEs. Think of building a data model via dbt as simply one more abstraction, factoring that transform into a table analysts can select from, rather than a single-use CTE.

If you find yourself reproducing code, maybe you use the same set of CTEs to filter transactions down to just one DEX or marketplace, that could be a perfect example of a community-built model.&#x20;

Community contributions do not need to be full-blown models. Protocols are constantly evolving and our models must adapt to these changes. If you spot something out-of-date or that needs attention, suggested revisions are welcome PRs.

#### Note

This guide will be updated as the community curation process evolves. Please feel free to provide feedback to us on Discord!
