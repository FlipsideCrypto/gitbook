# Caching (maxAgeMinutes)

Often times we'll write a large query where the underlying results don't change much minute-to-minute or hour-to-hour. In these cases, we don't need to waste unnecessary computational resources (Query Seconds) to re-execute a query that might incur a cost. This is where `maxAgeMinutes` comes in handy.

Let's use the following query as an example. In this example, we're asking for the address of an ENS domain. The results of this query are unlikely to change hour-to-hour.&#x20;

```sql
SELECT
  origin_from_address
FROM ethereum.core.fact_event_logs
WHERE
  contract_address = lower('0x283af0b28c62c092c9727f1ee09c02ca627eb7f5')
  AND event_inputs:name = lower('{ens_domain}')
  AND event_name = 'NameRegistered'
  AND block_timestamp >= GETDATE() - interval'4 year'
```

The first time this query is executed it will trigger a QueryRun. That initial QueryRun saves the results along with the timestamp of when those results were recorded.

<figure><img src="../../../.gitbook/assets/Untitled (7).png" alt=""><figcaption></figcaption></figure>

Now let's attempt to re-run the query, with a `maxAgeMinutes` of 12 hours.&#x20;

<figure><img src="../../../.gitbook/assets/Untitled (5).png" alt=""><figcaption></figcaption></figure>

Since the first query successfully executed and stored a result set within the last 12 hours a new QueryRun will not be triggered.

{% hint style="info" %}
The ceiling for `maxAgeMinutes` is 24 hours or 1440 minutes
{% endhint %}

Under the hood, the API will return the queryRunId of the most recent successful execution. With this queryRunID in hand, the SDKs will call `getQueryRunResults` to retrieve the results for that QueryRun.

Let's take a look at a demo with our SDKs:

{% tabs %}
{% tab title="Python SDK" %}
<pre class="language-python"><code class="lang-python">from flipside import Flipside

# Initialize `Flipside` with your API Key and API Url
flipside = Flipside("&#x3C;YOUR_API_KEY>", "https://api-v2.flipsidecrypto.xyz")

sql = """
SELECT 
  date_trunc('hour', block_timestamp) as hour,
  count(distinct tx_hash) as tx_count
FROM ethereum.core.fact_transactions 
WHERE block_timestamp >= GETDATE() - interval'7 days'
GROUP BY 1
"""
<strong>
</strong># We set `maxAgeMinutes` to 0 to ensure the query re-executes
query_result_set = flipside.query(sql, max_age_minutes=0)

# Now attempt to run the query again with a max age of 5 minutes
# You will notice the first query took a little time to execute
# while this query will return instantly!
query_result_set_cached = flipside.query(sql, max_age_minutes=5)
</code></pre>
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
<pre class="language-javascript"><code class="lang-javascript">const { Flipside } = require("@flipsidecrypto/sdk")

// Initialize `Flipside` with your API key
<strong>const flipside = new Flipside(
</strong>  "&#x3C;YOUR_API_KEY>",
  "https://api-v2.flipsidecrypto.xyz"
);

const sql = `
SELECT 
  date_trunc('hour', block_timestamp) as hour,
  count(distinct tx_hash) as tx_count
FROM ethereum.core.fact_transactions 
WHERE block_timestamp >= GETDATE() - interval'7 days'
GROUP BY 1
`

// We set `maxAgeMinutes` to 0 to ensure the query re-executes
let queryResultSet = await flipside.query.run({sql: sql, maxAgeMinutes: 0});

// Now attempt to run the query again with a max age of 5 minutes
// You will notice the first query took a little time to execute
// while this query will return instantly!
let queryResultSetCached = await flipside.query.run({sql: sql, maxAgeMinutes: 5});
</code></pre>
{% endtab %}
{% endtabs %}



{% hint style="info" %}
In the next section we'll talk about the billable metric, QuerySeconds.
{% endhint %}
