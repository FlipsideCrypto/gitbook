---
description: Examples to help solve common problems, like paginating through results.
---

# Example Code

### 1. Query Pagination

All queries can return a maximum of 1GB of data. The entire query result set is saved in accordance with the query’s TTL. Subsets of the query results can be retrieved by specifying the page size and page number. All without re-running the initial query and incurring `query_second` usage.

By default, all query runs will be set to the following if pagination is not specified.

| variable   | default value |
| ---------- | ------------- |
| pageSize   | 100k          |
| pageNumber | 1             |

#### Examples:

{% tabs %}
{% tab title="Python" %}
In this query, we will request 200k records from the `ethereum.core.ez_nft_mints` table and return 100 records, starting at page #1.

```python
from flipside import Flipside

sdk = Flipside("<YOUR_API_KEY>")

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
# This SDK function will call `createQueryRun` and poll `getQueryRun` of 
# the Flipside RPC API
page_1_results = sdk.query(
  sql,
  page_size=100,
  page_number=1
)
```

Now if we'd like to access page #2, simply set the `page_number` argument to 2 and re-run the query. This will return the next 100 rows (since we had set the `page_size` to 100).&#x20;

```python
# call `get_query_results` update the page_number to the second page
# This SDK function will call the `getQueryRunResults` method on the Flipside 
# RPC API
page2_results = sdk.get_query_results(
    page_1_results.query_id,
    page_number=2,
    page_size=100
)
```

To retrieve all the results, run the following code:

```python
i = 0
page_number = 1
page_size = 1000
all_rows = []
while i < results.run_stats.record_count:
    results = sdk.get_query_results(
        results.query_id, 
        page_number=page_number, 
        page_size=page_size
    )
    all_rows.append(results.rows)

    i += page_size
    page_number += 1
```
{% endtab %}
{% endtabs %}



_If you have an example you think would be helpful for others: please share with the community by submitting a_ [_pull request_](https://github.com/FlipsideCrypto/gitbook/) _for this page, or sharing in_ [_Discord_](https://discord.gg/ZmU3jQuu6W)_._
