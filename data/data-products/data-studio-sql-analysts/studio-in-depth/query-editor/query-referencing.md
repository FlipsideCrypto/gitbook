---
description: Easily reference results from exiting queries!
---

# Query Referencing

Query Referencing allows you to streamline your analysis workflow by reusing the results of previously executed queries as data sources for new queries. This feature enhances query organization, promotes reusability of complex result sets, and significantly boosts query performance.

### Overview

This section will cover:

1. [How to reference a query?](query-referencing.md#syntax)
2. [How to leverage query referencing to speed up parameter runs?](query-referencing.md#leveraging-query-referencing-for-performance-optimization)
3. [How to decide which query to reference?](query-referencing.md#how-to-decide-which-query-to-reference)
4. [How to troubleshoot errors?](query-referencing.md#troubleshooting-errors)
5. [Limitations](query-referencing.md#limitations)

***

### How to reference a query?

1. **Identify the Query:**
   1.  Navigate to the desired query and click **"Copy Reference"** button to obtain the query ID.&#x20;

       <figure><img src="../../../../../.gitbook/assets/Screenshot 2024-11-20 at 10.16.34 AM.png" alt=""><figcaption></figcaption></figure>
   2.  To reference your own query, find the query you want to reference under "My Work". Click the 3-dot menu, and select "Add to Query".

       <figure><img src="../../../../../.gitbook/assets/ezgif.com-video-to-gif-converter (1).gif" alt=""><figcaption></figcaption></figure>
2. **Reference the Query:**
   *   In your new query, use the following syntax to reference the query:

       {% code overflow="wrap" lineNumbers="true" %}
       ```sql
       SELECT * 
       FROM $query('query_id')
       ```
       {% endcode %}
3. **Join with other tables:**
   *   You can join the referenced query with other tables in your dataset:

       {% code overflow="wrap" lineNumbers="true" %}
       ```sql
       SELECT * 
       FROM bitcoin.core.fact_transactions t
       JOIN $query('query_id') AS my_query 
         ON my_query.blockheight = t.blockheight
       ```
       {% endcode %}

***

### Leveraging Query Referencing for Performance Optimization

A significant advantages of Query Referencing is its ability to dramatically improve the performance of parameterized queries.

{% tabs %}
{% tab title="With Query Referencing" %}
1.  Pre-calculate the 100,000 most relevant addresses:

    <pre class="language-sql" data-overflow="wrap" data-line-numbers><code class="lang-sql">select 
    <strong>    from_address,
    </strong><strong>    count(1) as n_tx   -- can safely count(1) b/c this table is 1 row per tx_hash
    </strong>from ethereum.core.fact_transactions 
    where block_timestamp >= '2024-01-01'
    group by from_address
    having n_tx &#x3C; 20001 -- assume > 20k is bots 
    order by n_tx desc 
    limit 100000;
    </code></pre>
2.  Reference the pre-calculated result:&#x20;

    {% code overflow="wrap" lineNumbers="true" %}
    ```sql
    select * from 
    $query('0a0d54ca-f8de-43fe-8e5f-c270272982f9') -- query id taken from studio URL
    where from_address = '{{wallet_address}}';
    ```
    {% endcode %}

{% hint style="success" %}
By pre-calculating the relevant addresses and referencing the result, you can significantly improve query performance, especially when dealing with large datasets and frequent parameter changes.
{% endhint %}
{% endtab %}

{% tab title="Without Query  Referencing " %}
This approach requires the query to be re-executed for each user, leading to potential performance bottlenecks.

```sql
select 
from_address, 
count(tx_hash) as n_tx 
from base.core.fact_transactions
where block_timestamp >= '2024-01-01'
and from_address = '{{wallet_address}}'
```
{% endtab %}
{% endtabs %}

***

### How to decide which query to reference?

1. **Do Your Own Research (DYOR):** Always verify the logic and accuracy of the referenced query.

{% hint style="info" %}
Since all public queries can be referenced, make sure you trace query dependencies! Hover over any `$query('query_id')` and click on the query title in the popover to view all information about the underlying query.&#x20;
{% endhint %}

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-11-14 at 2.38.11 PM.png" alt="" width="563"><figcaption></figcaption></figure>

2. **Consider Query Refresh Rates:** Ensure that the referenced query is refreshed at an appropriate interval to provide up-to-date results.

{% hint style="info" %}
* To ensure up-to-date results, set a "Refresh Rate" on your base query
* Any new query referencing the results will automatically use the refreshed data
* Refreshes follow standard query refresh capabilities
{% endhint %}

3. **Understand Cache Expiration:** Be aware of the cache duration and expiration rules for referenced queries.

{% hint style="warning" %}
* Results are cached and available for 24 hours by default
* Each reference within the 24-hour window extends availability by another 24 hours
* Maximum cache duration is 31 days


{% endhint %}

***

### Troubleshooting Errors&#x20;

#### Error: `Result for query {ID} has expired.`

This error occurs when the results of a referenced query has expired.&#x20;

How to resolve:

1.  **If you own the referenced query:**

    1. Set a refresh rate of at least once every 24 hours on the referenced query. This ensures that its results are consistently available to access.&#x20;


2. If you _**do NOT**_ own the referenced query:
   1. Hover over the query ID in your SQL to see the details of the referenced query, click on the query title to open it.&#x20;
   2. Fork the referenced query to create a copy under your ownership and set a refresh rate of at least once every 24 hours.
   3. Update the query ID in your current query with the ID of the forked query to ensure uninterrupted access to the results.

***

### Limitations

Base queries that utilize parameters will always execute with their default values when referenced. Currently, there’s no mechanism to dynamically pass parameters into the $query() function. It is best to avoid using parameters in your base queries.

