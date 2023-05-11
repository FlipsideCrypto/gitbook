---
description: Examples to help solve common problems, like paginating through results.
---

# Example Code

### 1. Query Pagination

All queries can return a maximum of 1GB of data. The entire query result set is saved in accordance with the query’s TTL. Subsets of the query results can be retrieved by specifying the page size and page number. All without re-running the initial query and incurring `query_second` usage.

By default, all query runs will be set to the following if pagination is not specified.

| variable   | default value           |
| ---------- | ----------------------- |
| pageSize   | 100k (Python), 1000 (R) |
| pageNumber | 1                       |

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

{% tab title="R" %}
In this query, we will request 200k records from the `ethereum.core.ez_nft_mints` table.\
\
This code is for the shroomDK R Package version 0.2.0, versions 0.1.0 and 0.1.1 are deprecated as of 2023-05-31. Note, the R package default page size is 1,000, not 100,000 like python. As upgrades occur, argument `api_url` is flexible. \
\
Always gitignore your API key!

<pre><code>if(!require(shroomDK)){
install.packages("shroomDK")
library(shroomDK)
}

# recommended method for easy gitignore 
# see: github.com/fsc-data-science/RMarkdown-template/#topic-rmarkdown-template
api_key &#x3C;- readLines("api_key.txt") 

# Simplified
<strong>nft_mints_query &#x3C;- {
</strong>"
SELECT
    nft_address,
    mint_price_eth,
    mint_price_usd
  FROM ethereum.core.ez_nft_mints
  LIMIT 200000
"
}

nft_mints &#x3C;- shroomDK::auto_paginate_query(query = nft_mints_query,
                                            api_key = api_key,
                                            page_size = 100000, #default 1,000
                                            page_count = 2) #default 1
</code></pre>

`auto_paginate_query()` will return execution errors and wait for QUERY\_STATUS\_SUCCESS, but remember you need the `queryRunId` to cancel queries.\
\
The manual process for debugging, testing, and managing execution time is to create tokens, check their status, cancel if needed (see: `?cancel_query`), request the results, clean each page into a data frames and combine the pages.

```
# Full (for debugging & key query execution details)

nft_mints_token <- create_query_token(
  query = nft_mints_query,
  api_key = api_key,
  ttl = 1, # default 1HR time to live (query result available)
  mam = 10, # default 10 minute cache lifespan (query result refresh timer)
  api_url = "https://api-v2.flipsidecrypto.xyz/json-rpc" # default endpoint
)

## Query Run ID

nft_mints_run_id <- nft_mints_token$result$queryRequest$queryRunId

## looking for QUERY_STATE_SUCCESS
## note: implicitly checked within get_query_from_token()
status_check <- get_query_status(
 query_run_id = nft_mints_run_id, # yes, a bit long
 api_key = api_key)
 
# 2 pages of 100,000 each (30MB max per page)

nft_mints_request1 <- get_query_from_token(
  query_run_id = nft_mints_run_id,
  api_key = api_key,
  page_number = 1, 
  page_size = 100000, #default 1,000
  result_format = "csv", # default 
  api_url = "https://api-v2.flipsidecrypto.xyz/json-rpc" # default
)

nft_mints_100k <- clean_query(nft_mints_request1)

# clean_query turns the request into a data frame. 
# Note, if a json column is present, each columns will be a list to conform 
# to the same # rows rule for columns in data frames.
 

nft_mints_request2 <- get_query_from_token(
  query_run_id = nft_mints_run_id,
  api_key = api_key,
  page_number = 2, 
  page_size = 100000
)
# clean_query
nft_mints_200k <- clean_query(nft_mints_request2) 

# combine 
nft_mints_fullmethod <- rbind(nft_mints_100k, nft_mints_200k)

# same result 
identical(nft_mints, nft_mints_fullmethod)
```
{% endtab %}
{% endtabs %}



_If you have an example you think would be helpful for others: please share with the community by submitting a_ [_pull request_](https://github.com/FlipsideCrypto/gitbook/) _for this page, or sharing in_ [_Discord_](https://discord.gg/ZmU3jQuu6W)_._
