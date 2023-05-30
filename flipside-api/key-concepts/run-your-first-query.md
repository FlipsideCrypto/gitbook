# Run Your First Query

This tutorial assumes you have already signed up for a Flipside Account and generated an API key [here in Flipside's Data Studio](https://flipsidecrypto.xyz/account/api-keys).&#x20;

### 1. Install the SDK (or skip to #2 if using the API directly)

{% tabs %}
{% tab title="Python SDK" %}
```
pip install flipside
```

{% hint style="info" %}
_Python 3.7 and above, is required to use `flipside`_
{% endhint %}
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
```
yarn add @flipside/sdk
```

_or_

```
npm install @flipside/sdk
```
{% endtab %}

{% tab title="R SDK" %}
```
install.packages("shroomDK") # from CRAN
```
{% endtab %}
{% endtabs %}

### 2. Execute your Query

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
</strong># Run the query against Flipside's query engine and await the results
query_result_set = flipside.query(sql)
</code></pre>
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
<pre class="language-javascript"><code class="lang-javascript">const { Flipside } = require("@flipsidecrypto/sdk")

// Initialize `Flipside` with your API key
const flipside = new Flipside(
  "&#x3C;YOUR_API_KEY>",
  "https://api-v2.flipsidecrypto.xyz"
);

<strong>const sql = `
</strong>SELECT 
  date_trunc('hour', block_timestamp) as hour,
  count(distinct tx_hash) as tx_count
FROM ethereum.core.fact_transactions 
WHERE block_timestamp >= GETDATE() - interval'7 days'
GROUP BY 1
`

// Send the `Query` to Flipside's query engine and await the results
const queryResultSet = await flipside.query.run({sql: sql});
</code></pre>
{% endtab %}

{% tab title="R SDK" %}
<pre><code><strong>library(shroomDK)
</strong><strong>
</strong><strong>api_key = readLines("api_key.txt") # always gitignore your API keys!
</strong>
query &#x3C;- { 
"
SELECT 
  date_trunc('hour', block_timestamp) as hour,
  count(distinct tx_hash) as tx_count
FROM ethereum.core.fact_transactions 
WHERE block_timestamp >= GETDATE() - interval'7 days'
GROUP BY 1
"
 }

# auto_paginate_query is a wrapper to all other steps. 
pull_data &#x3C;- auto_paginate_query(
query = query,
api_key = api_key
)

# otherwise step 1 is to run the query and get a Run ID
qtoken &#x3C;- create_query_token(
query = query,
api_key = api_key)
</code></pre>
{% endtab %}
{% endtabs %}

### 3. Paginate over the Results

{% tabs %}
{% tab title="Python SDK" %}
```python
# what page are we starting on?
current_page_number = 1

# How many records do we want to return in the page?
page_size = 100

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
let pageSize = 100

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
  allRows = [...allRows, ...results.records!];
  currentPageNumber += 1;
}
```
{% endtab %}

{% tab title="R SDK" %}
```
q_id <- qtoken$result$queryRequest$queryRunId
page_size = 100
page_count = 2

# auto_paginate_query() overrides size & count to get all available data. 

# otherwise you can manually paginate with get_query_from_token()
# ?get_query_from_token waits for query to finish via ?get_query_status

 results <- lapply(1:page_count, function(i){
    temp_page <- get_query_from_token(q_id,
                                api_key = api_key,
                                page_number = i,
                                page_size = page_size)

    if(length(temp_page$result$rows) < 1){
      df <- data.frame()
    } else {
  # See ?clean_query for conversion to a data frame.
    df <- clean_query(temp_page)
      }
    return(df)
  })

 # drop empty pages just in case.
   results <- results[unlist(lapply(results, nrow)) > 0]

# combine into a single data frame.
   results <- do.call(rbind.data.frame, results)
```


{% endtab %}
{% endtabs %}
