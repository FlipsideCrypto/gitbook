# Get Started in Snowflake

Complex data is now simple. The Snowflake UI has everything you need to integrate Flipside data with your existing architecture, query programmatically, build internal tooling, and more. Get the data you want, in whatever environment you need.&#x20;

Get started by following the demo video or written guide below:

{% embed url="https://flipsidecrypto-1.wistia.com/medias/s0stp0eb0k?wvideo=s0stp0eb0k" %}

1. [How to access my Snowflake account? ](get-started-in-snowflake.md#log-in-to-your-snowflake-account)
2. [Where do I access Flipside's data in Snowflake?](get-started-in-snowflake.md#snowflake-data-tour)
3. [How do I run my first query in Snowflake?](get-started-in-snowflake.md#run-your-first-query)
4. [How to build on top of Flipside's data in Snowflake?](get-started-in-snowflake.md#build-on-top-of-flipside-data)

***

### Log in to your Snowflake Account

1. Access your Snowflake credentials in your account Settings: [https://flipsidecrypto.xyz/settings/snowflake](https://flipsidecrypto.xyz/settings/snowflake)
2. Log in to Snowflake by clicking on the Account URL&#x20;
3. Enter your credentials and click "Sign in"
4. Set a new password for your account&#x20;

***

### Snowflake Data Tour&#x20;

Now that you have your snowflake account set up, let's take a look at the data available.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-01-16 at 11.02.10 AM.png" alt=""><figcaption></figcaption></figure>

1. Navigate to the left-hand side of the screen to find the "Data" section
2. Browse through all of the Flipside Data Shares that have been share with your snowflake account where
   * Each database represents a blockchain. And each database follows a similar schema design pattern to reduce the learning curve for analyzing different chains
3. Now, let's take a look at the "Ethereum" database and expand the "Core" schema. Here you're find:
   * **Fact tables:** akin to primatives of a blockchain. Think blocks, transactions, events, or traces.&#x20;
   * **Dim tables:** dimensions of data that make querying easier. For example, contracts, liquidity pools, or labels that have been developed by Flipside's data science team.&#x20;
   * **Ez tables:** combination of fact and dim tables that allow syou to access highly curated slices of data.&#x20;

***

### Run your First Query&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-01-16 at 11.04.07 AM.png" alt=""><figcaption></figcaption></figure>

1. Navigate to the left-hand side of the screen again to find the "Worksheet" section&#x20;
2. Create a new worksheet by clicking on the "+" button in the top-right corner
3. As an example, let's find the answer to the following question with the example query below:

> Over the past week, how is USD Volume distributed among Decentralized Exchanges (DEXs) across Ethereum, Polygon, Optimism, Arbitrum, Avalanche & BSC?

```sql
-- 1. Aggregate swaps across Ethereum, Polygon,Optimism, Arbitrum, Avalanche, BSC 

WITH dex_swaps AS (
    SELECT 'ethereum' chain, * FROM ethereum.defi.ez_dex_swaps WHERE block_timestamp > current_date - 7
    UNION 
    SELECT 'polygon' as chain, * FROM polygon.defi.ez_dex_swaps WHERE block_timestamp > current_date - 7
    UNION 
    SELECT 'optimism' as chain, * FROM optimism.defi.ez_dex_swaps WHERE block_timestamp > current_date - 7
    UNION
    SELECT 'arbitrum' as chain, * FROM arbitrum.defi.ez_dex_swaps WHERE block_timestamp > current_date - 7
    UNION 
    SELECT 'avalanche' as chain, * FROM avalanche.defi.ez_dex_swaps WHERE block_timestamp > current_date - 7
    UNION 
    SELECT 'bsc' as chain, * FROM bsc.defi.ez_dex_swaps WHERE block_timestamp > current_date - 7
)
-- 2. Aggregate volume and unique users across blockchains

SELECT
    platform as dex_platform,
    count(distinct(origin_from_address)) as total_users, 
    sum(amount_in_usd) as usd_volume
FROM dex_swaps
GROUP BY dex_platform
```

<figure><img src="../../.gitbook/assets/Screenshot 2024-01-16 at 11.09.15 AM.png" alt=""><figcaption></figcaption></figure>

***

### Build On Top Of Flipside Data

In your trial sandbox (that is private to you), you can create any views or tables on top of Flipside's data shares.&#x20;

{% hint style="info" %}
In the dropdown, at the top of the new worksheet, ensure that you've selected your sandbox database so you are operating in this worksheet in the right context.&#x20;
{% endhint %}

1.  Create a new SQL worksheet to write the code to generate a view&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2024-01-16 at 11.11.09 AM (1).png" alt=""><figcaption></figcaption></figure>

```sql
CREATE SCHEMA cross_chain;

CREATE VIEW cross_chain.latest_weekly_dex_volume AS (
WITH dex_swaps AS (
    SELECT 'ethereum' chain, * FROM ethereum.defi.ez_dex_swaps WHERE block_timestamp > current_date - 7
    UNION 
    SELECT 'polygon' as chain, * FROM polygon.defi.ez_dex_swaps WHERE block_timestamp > current_date - 7
    UNION 
    SELECT 'optimism' as chain, * FROM optimism.defi.ez_dex_swaps WHERE block_timestamp > current_date - 7
    UNION    
    SELECT 'arbitrum' as chain, * FROM arbitrum.defi.ez_dex_swaps WHERE block_timestamp > current_date - 7
    UNION 
    SELECT 'avalanche' as chain, * FROM avalanche.defi.ez_dex_swaps WHERE block_timestamp > current_date - 7
    UNION 
    SELECT 'bsc' as chain, * FROM bsc.defi.ez_dex_swaps WHERE block_timestamp > current_date - 7
)
-- 2. Aggregate volume and unique users across blockchains

SELECT
    platform as dex_platform,
    count(distinct(origin_from_address)) as total_users, 
    sum(amount_in_usd) as usd_volume
FROM dex_swaps
GROUP BY dex_platform

)

```

3. Access the last seven days of all major dex volume with one line of SQL&#x20;

```sql
-- Query the newly created view 
SELECT * FROM cross_chain.latest_weekly_dex_volume;
```

3.  Find your newly created view in the Data Explorer:

    * Expand your **sandbox database**&#x20;
    * Expand the **cross\_chain schema**&#x20;
    * Expand **Views**

    <figure><img src="../../.gitbook/assets/Screenshot 2024-01-16 at 11.28.35 AM.png" alt=""><figcaption></figcaption></figure>

