---
description: >-
  Flipside generates the most reliable and comprehensive blockchain data. And we
  have the tools that let you build more with it. All for free.
---

# Welcome to Flipside!

### Getting Started

🌲 **The core Flipside App**: [flipsidecrypto.xyz](http://www.flipsidecrypto.xyz/)\
Analyze blockchain data, visualize it, and share a dashboard instantly. \
Ideal for: data exploration, analytical storytelling, comprehensive dashboard-building.\
\
🍄 **ShroomDK, the developer-friendly API**: [sdk.flipsidecrypto.xyz](https://sdk.flipsidecrypto.xyz/)\
Skip the app, and submit queries directly from your dev or data science environment.\
Ideal for: building a custom analytics app, constructing a trading model, or using Flipside data in R or Python for data science work.\
\
❄️ **Data Shares (via Snowflake)**: [data.flipsidecrypto.xyz](https://data.flipsidecrypto.xyz/)\
Want Flipside's entire database in your stack? We can do that. Just [reach out](https://data.flipsidecrypto.xyz/). \
Ideal for: teams that rely on blockchain data to operate, understand their users, or make applications more web3-connected.

### Important Things to Know

* All our data is accessible via SQL queries, and you'll use the [Snowflake SQL](our-data/using-snowflake-sql.md) dialect to access it.
* Our core app is brand new (launched Feb 2023) and some [documentation](our-app/app-overview.md) is available — we're actively building this out, including both text and video content — if you have questions that aren't answered here, please reach out in [Discord](https://discord.gg/ZmU3jQuu6W).
* Our data structures are and designed for ease of use and efficient querying, and are  [extensively documented](our-data/data-table-documentation.md). We regularly update our data structures to optimize efficiency.
* Latency varies from table to table, but typically lags either 1 hour or 1 day, at most.
* If you run into difficulty getting your queries to run, we provide [a guide for efficient query writing](our-data/writing-efficient-queries.md). Need more assistance? Get help anytime in our [Discord](https://discord.gg/ZmU3jQuu6W).

### What blockchains and projects does Flipside have data on?

If it happens on-chain, we've got it.&#x20;

Data includes core tables (blocks, events, transactions) for every chain, with added 'easy' tables (swaps, prices, etc.) and project-specific tables modeled by the Flipside community.

See our [Data Table Documentation](our-data/data-table-documentation.md) for a current list of supported chains. Don’t see the chain you’re looking for? We add new chains regularly, but you can drop a request in our [Discord](https://discord.gg/ZmU3jQuu6W) anytime.

### **Contract Decoding** <a href="#contract-decoding" id="contract-decoding"></a>

#### Adding a contract for decoding <a href="#adding-a-contract-for-decoding" id="adding-a-contract-for-decoding"></a>

To add a contract for decoding, please visit [here](https://science.flipsidecrypto.xyz/abi-requestor/).

Assuming the submitted ABI is valid, records will be decoded within 24 hours. If records are not decoded within 24 hours, or for any ABI updates, please submit a ticket within our Discord.

#### General Process Overview <a href="#general-process-overview" id="general-process-overview"></a>

The majority of our ABIs have been sourced from Etherscan, and we are constantly asking Etherscan for new ABIs. However, this is not comprehensive, and therefore we must also rely on our users to submit ABIs for decoding. If we are unable to locate an ABI for the contract from either Etherscan or our users, we will attempt to match the contract to a similar ABI. This is done by comparing the contract bytecode to a list of known contract bytecodes. If we are able to match the contract to a similar ABI, we will decode the contract using the similar ABI. You can see the source of each ABI in the `dim_contract_abis` table within the `abi_source` column.

Once ABIs have been verified, events within the last day of blocks will be decoded within approximately 90 minutes. Events older than 1 day will be decoded within 24 hours in the majority of cases. The exception here is if the contract has a massive number of events, in which case it may take longer.
