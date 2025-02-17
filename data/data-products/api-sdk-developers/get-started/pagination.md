# Pagination

The SDK (and API) expose the ability to request a specific page of the result set by providing both a page number and a dynamically set page size (this means you control the page size).

{% hint style="info" %}
By default the page size is set to 100,000 rows and, the page number is set to 1. If you don't set the page size and just use the default, always remember to check page stats in case the number of rows in the entire query result set exceeds the default page size. In this case, you'd need to use the pagination examples on this page to gather your complete result set. Also, keep in mind that there is a byte limit on the amount of data that can be returned on a single page. There may be cases where 100,000 rows are too big and you will need to decrease the page size to a lower number. More details on [rate limits around page sizing here](rate-limits.md).&#x20;
{% endhint %}

Let's start with the following query to return the last 50k NFT transfers on Ethereum:

```sql
SELECT
  tx_hash,
  nft_address,
  tokenid,
  block_timestamp,
  seller_address,
  buyer_address,
  project_name,
  token_metadata,
  aggregator_name,
  price_usd,
  total_fees_usd,
  platform_fee_usd,
  platform_name,
  creator_fee_usd
FROM ethereum.core.ez_nft_sales
WHERE 
  block_timestamp >= GETDATE() - interval'1 year'
  AND project_name IS NOT NULL
ORDER BY block_timestamp DESC
LIMIT 50000
```

First, we execute the query.

{% hint style="info" %}
Since we know that we are going to page thru the result set after the execution of the query we set the page number and page size to 1 so that we don't attempt to return a very large data set all at once.
{% endhint %}

{% tabs %}
{% tab title="Python SDK" %}
```python
from flipside import Flipside

# Initialize `Flipside` with your API Key and API Url
flipside = Flipside("<YOUR_API_KEY>", "https://api-v2.flipsidecrypto.xyz")

sql = """
SELECT
  tx_hash,
  nft_address,
  tokenid,
  block_timestamp,
  seller_address,
  buyer_address,
  project_name,
  token_metadata,
  aggregator_name,
  price_usd,
  total_fees_usd,
  platform_fee_usd,
  platform_name,
  creator_fee_usd
FROM ethereum.core.ez_nft_sales
WHERE 
  block_timestamp >= GETDATE() - interval'1 year'
  AND project_name IS NOT NULL
ORDER BY block_timestamp DESC
LIMIT 50000
"""

# Run the query against Flipside's query engine and await the results
query_result_set = flipside.query(sql, page_number=1, page_size=1)
```
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
```javascript
const { Flipside } = require("@flipsidecrypto/sdk")

// Initialize `Flipside` with your API key
const flipside = new Flipside(
  "<YOUR_API_KEY>",
  "https://api-v2.flipsidecrypto.xyz"
);

const sql = `
SELECT
  tx_hash,
  nft_address,
  tokenid,
  block_timestamp,
  seller_address,
  buyer_address,
  project_name,
  token_metadata,
  aggregator_name,
  price_usd,
  total_fees_usd,
  platform_fee_usd,
  platform_name,
  creator_fee_usd
FROM ethereum.core.ez_nft_sales
WHERE 
  block_timestamp >= GETDATE() - interval'1 year'
  AND project_name IS NOT NULL
ORDER BY block_timestamp DESC
LIMIT 50000
`

// Send the `Query` to Flipside's query engine and await the results
const queryResultSet = await flipside.query.run({
  sql: sql,
  pageNumber: 1,
  pageSize: 1
});
```
{% endtab %}
{% endtabs %}

After executing the query we can request pages of the results. In this example, we'll specify a page size of 10,000 rows per request.

{% tabs %}
{% tab title="Python SDK" %}
```python
# what page are we starting on?
current_page_number = 1

# How many records do we want to return in the page?
page_size = 1000

# set total pages to 1 higher than the `current_page_number` until
# we receive the total pages from `get_query_results` given the 
# provided `page_size` (total_pages is dynamically determined by the API 
# based on the `page_size` you provide)
total_pages = 2

# we'll store all the page results in `all_rows`
all_rows = []

while current_page_number <= total_pages:
  results = flipside.get_query_results(
    query_result_set.query_id,
    page_number=current_page_number,
    page_size=page_size
  )

  total_pages = results.page.totalPages
  if results.records:
      all_rows = all_rows + results.records
  
  current_page_number += 1
```
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
```javascript
// what page are we starting on?
let currentPageNumber = 1

// How many records do we want to return in the page?
let pageSize = 1000

// set total pages to 1 higher than the `currentPageNumber` until
// we receive the total pages from `getQueryResults` given the 
// provided `pageSize` (totalPages is dynamically determined by the API 
// based on the `pageSize` you provide)
let totalPages = 2


// we'll store all the page results in `allRows`
let allRows = [];

while (currentPageNumber <= totalPages) {
  let results = await flipside.query.getQueryResults({
    queryRunId: queryResultSet.queryId,
    pageNumber: currentPageNumber,
    pageSize: pageSize,
  });

  if (results.error) {
    throw results.error;
  }

  totalPages = results.page.totalPages;
  allRows = [...allRows, ...results.records];
  currentPageNumber += 1;
}
```
{% endtab %}
{% endtabs %}

In the above example, we use the `page` property of the query result set to determine how many pages exist given a page size of 1000 rows. While in this case, we know there is an upper limit of 50k rows, this is particularly useful when we don't know the total number of rows returned by a query in advance.

{% hint style="info" %}
In the next section, we'll walk thru how to sort your results.
{% endhint %}
