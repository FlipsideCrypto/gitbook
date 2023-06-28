---
description: >-
  Retrieve the TVL for the top 500 UniswapV3 Pools on Polygon using LiveQuery
  and TheGraph
---

# 💡 Query TheGraph

In this example, we'll use LiveQuery to query The Graph.

Here we'll leverage the `udf_api` function to call The Graph directly and retrieve the top 500 Uniswap V3 Liquidity Pools by total value locked USD on Polygon.

**Video Walkthrough:**

{% embed url="https://www.loom.com/share/a91f8524819c415091a5d2006a792115?sid=1805c136-f6f3-40ca-a92e-a0a264d09aed" %}

**Fork It!**

{% hint style="info" %}
Fork the example above [here](https://flipsidecrypto.xyz/edit/queries/8f6042d6-eca4-4d15-9b1b-2a4e72790639).
{% endhint %}

**Step-By-Step**

In the video above we first create our GraphQL query that we'll be sending to TheGraph via LiveQuery:

```graphql
liquidityPools(first: 500, orderBy: totalValueLockedUSD, orderDirection: desc) {
  id
  totalLiquidity
  name  
  inputTokens { 
    id 
    symbol
  }
}
```

We'll issue a `POST` call to the Uniswap V3 Polygon subgraph curated by Messari:

<pre><code><strong>https://api.thegraph.com/subgraphs/name/messari/uniswap-v3-polygon
</strong></code></pre>

Our LiveQuery SQL ([fork it here](https://flipsidecrypto.xyz/edit/queries/8f6042d6-eca4-4d15-9b1b-2a4e72790639)).

```sql
WITH graph_call as (
  SELECT
    livequery.live.udf_api(
      'POST',
      'https://api.thegraph.com/subgraphs/name/messari/uniswap-v3-polygon',
      {'Content-Type': 'application/json'},
      {
       'query': '{
         liquidityPools(first: 500, orderBy: totalValueLockedUSD, orderDirection: desc) {
          id
          totalLiquidity
          name  
          inputTokens { 
            id 
            symbol
          }
         }}',
       'variables':{}
      }
    ) as rawoutput
),
formatted_results as (
  SELECT
   value:id::string as pool_address,
   value:name::string as name,
   value:totalLiquidity::string as total_liquidity,
   value:inputTokens[0]:id::string as token_0_address,
   value:inputTokens[0]:symbol::string as token_0_symbol,
   value:inputTokens[1]:id::string as token_1_address,
   value:inputTokens[1]:symbol::string as token_1_symbol
  FROM graph_call, LATERAL FLATTEN (input => rawoutput:data:data:liquidityPools)
)
SELECT 
* 
FROM formatted_results
```

**Two Call-outs for the above SQL:**

1. Since `udf_api` returns a JSON Variant Object we can call it directly in our SQL select statement (unlike our EVM functions, which return a `table` and must be included in a from clause with a `table(<function>)` wrapper.
2. We use `LATERAL FLATTEN` to extract each liquidity pool from the API response as it's own row.
