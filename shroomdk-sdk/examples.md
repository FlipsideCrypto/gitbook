# Examples

### Query Pagination

All query result sets return a maximum of 1,000,000 rows. The entire query result set is cached in accordance with the query’s TTL and subsets can be retrieved by specifying the page size and page number. All without rerunning the initial query and depleting your query run quota.



By default, all query runs will be set to the following if pagination is not specified.

| variable   | default value |
| ---------- | ------------- |
| pageSize   | 100k          |
| pageNumber | 1             |

#### Examples:

{% tabs %}
{% tab title="JavaScript/TypeScript" %}
_Pagination is available by default starting at version 1.1.0 of the JS/TS SDK. Note this is a non-breaking release._&#x20;



In this query, we will request 200k records from the `ethereum.core.ez_nft_mints` table and return 100 records, starting at page #1.

```javascript
// Create a query object for the `query.run` function to execute
// with a page size of 100 rows, starting with page #1.
let query: Query = {
  sql: `
    SELECT
        nft_address,
        mint_price_eth,
        mint_price_usd
    FROM ethereum.core.ez_nft_mints
    LIMIT 200000
  `,
  ttlMinutes: 10,
  pageSize: 100,
  pageNumber: 1,
};

// Send the `Query` to Flipside's query engine and await the results for Page #1
const page1Results: QueryResultSet = await flipside.query.run(query);
```

Now if we'd like to access page #2, simply set `pageNumber` to 2 and re-run the query. This will return the next 100 rows (since we had set the `pageSize` to 100).&#x20;

```javascript
// update the pageNumber to the second page
query = {...query, pageNumber: 2}

const page2Results = await flipside.query.run(query)
```

{% hint style="info" %}
Updating the pageNumber does NOT re-execute the query and therefore does not deduct from your quota. Query results are cached (in accordance with the TTL) up to 1,000,000 records/rows.&#x20;
{% endhint %}
{% endtab %}

{% tab title="Python" %}


In this query, we will request 200k records from the `ethereum.core.ez_nft_mints` table and return 100 records, starting at page #1.

```python
from shroomdk import ShroomDK

sdk = ShroomDK("<YOUR_API_KEY>")

# Create a query object for the `query.run` function to execute
# with a page size of 100 rows, starting with page #1.
sql = """
  SELECT
    nft_address,
    mint_price_eth,
    mint_price_usd
  FROM ethereum.core.ez_nft_mints
  LIMIT 200000
"""

# Run the query on Flipside's Query Engine and await the results...
page_1_results = sdk.query(
  sql,
  page_size=100,
  page_number=1
)
```

Now if we'd like to access page #2, simply set the `page_number` argument to 2 and re-run the query. This will return the next 100 rows (since we had set the `page_size` to 100).&#x20;

```javascript
// update the page_number to the second page
page_2_results = sdk.query(query, page_size=100, page_number=2)
```

{% hint style="info" %}
Updating the `page_number` argument does NOT re-execute the query and therefore does not deduct from your quota. Query results are cached (in accordance with the TTL) up to 1,000,000 records/rows.&#x20;
{% endhint %}
{% endtab %}

{% tab title="REST API" %}
For example, let’s assume this is your query:

```sql
SELECT
  nft_address,
  mint_price_eth,
  mint_price_usd
FROM ethereum.core.ez_nft_mints
LIMIT 200000
```

To access the first 100 records you can issue a GET request with the following URL parameters to `/queries/<query-run-id>`

URL parameters:

`pageSize=100`

`pageNumber=1`

```
https://node-api.flipsidecrypto.com/queries/<query-run-id>?pageSize=100&pageNumber=1
```

To access the next page simply increment pageNumber to 2 and make the same HTTP GET request.

{% hint style="info" %}
Updating the pageNumber does NOT re-execute the query and therefore does not deduct from your quota. Query results are cached (in accordance with the TTL) up to 1,000,000 records/rows.&#x20;
{% endhint %}
{% endtab %}
{% endtabs %}

### Query Pagination - Get All Records

Retrieve all records up to the 1,000,000 row limit.

**Examples:**

{% tabs %}
{% tab title="Python" %}
If the number of records are not known, you can do this to dynamically find out the number of pages that you have to query.



```python
results = []  # All the results will be added to this list
for i in range(10):  # There will be max 10 pages at default 100k per page & 1M record limit
    query_results = sdk.query(
        sql,
        page_number=i + 1,  # i starts with 0 but page number count starts with 1.
    )
    if query_results.run_stats.record_count == 0:  # Check whether the resulting page is empty.
        break
    results += query_results.records


```

_via_ [_jokersden_](https://github.com/jokersden)__
{% endtab %}
{% endtabs %}
