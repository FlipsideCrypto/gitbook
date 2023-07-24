---
description: Get TVL Data from DeFi Llama
---

# 💡 Query Defi Llama

We can post a simple `get` request to DeFi Llama's `chains` endpoint. Because this API call is a get and requires no authentication or headers, our query is very simple.&#x20;

```sql
SELECT
  livequery.live.udf_api('https://api.llama.fi/chains') as response;
```
