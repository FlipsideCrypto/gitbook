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
{% endtabs %}
