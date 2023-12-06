---
description: >-
  Your API key to the most comprehensive blockchain data in crypto for analysts,
  developers, and data scientists.
---

# Get Started

## Run your first query in under 2 minutes

### 1. 🔑 Get Your Key

Go to the [Flipside Data Studio](https://flipsidecrypto.xyz/account/api-keys) and click "API" to generate your API key. Every account comes with 5000 free query seconds per month.

### 2. 🛠 Pick Your SDK and Install It

{% tabs %}
{% tab title="Python SDK" %}
```
pip install flipside
```
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
```
yarn add @flipsidecrypto/sdk
```

_or_

```
npm install @flipsidecrypto/sdk
```
{% endtab %}

{% tab title="R SDK" %}
```
install.packages("shroomDK") # from CRAN
```
{% endtab %}
{% endtabs %}

### 3. 🏃‍♀️Execute your First Query

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
<pre class="language-javascript"><code class="lang-javascript">const { Flipside } = require("@flipsidecrypto/sdk");

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

pull_data &#x3C;- auto_paginate_query(
query = query,
api_key = api_key
)
</code></pre>


{% endtab %}
{% endtabs %}

