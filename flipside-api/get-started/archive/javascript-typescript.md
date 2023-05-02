# \[LEGACY] JavaScript / TypeScript

{% hint style="danger" %}
_The JS/TS SDK is currently undergoing an upgrade to be compatible with V2 of Flipside's API. Until that update rolls out, the JS/TS SDK can only be used by legacy ShroomDK users._

_**For Legacy ShroomDK users:** once the upgrade is complete you will be able to seamlessly upgrade to the latest version of the SDK without any changes to your existing code._&#x20;
{% endhint %}

[![](https://github.com/flipsidecrypto/sdk/actions/workflows/ci\_js.yml/badge.svg)](https://github.com/flipsidecrypto/sdk/actions/workflows/ci\_js.yml/badge.svg)

_**To skip the walkthrough and go straight to dedicated API Documentation,**_ [_**click here**_](https://api-docs.flipsidecrypto.xyz/)_**.**_

### 💾 Install the SDK

```javascript
yarn add @flipsidecrypto/sdk
```

or if using npm

```javascript
npm install @flipsidecrypto/sdk
```

### 🦾 Getting Started

```typescript
import { Flipside, Query, QueryResultSet } from "@flipsidecrypto/sdk";

// Initialize `Flipside` with your API key
const flipside = new Flipside(
  "<YOUR_API_KEY>",
  "https://node-api.flipsidecrypto.com"
);

// Parameters can be passed into SQL statements via simple & native string interpolation
const myAddress = "0x....";

// Create a query object for the `query.run` function to execute
const query: Query = {
  sql: `select nft_address, mint_price_eth, mint_price_usd from flipside_prod_db.ethereum_core.ez_nft_mints where nft_to_address = LOWER('${myAddress}')`,
  ttlMinutes: 10,
};

// Send the `Query` to Flipside's query engine and await the results
const result: QueryResultSet = await flipside.query.run(query);

// Iterate over the results
result?.records?.forEach((record) => {
  const nftAddress = record.nft_address
  const mintPriceEth = record.mint_price_eth
  const mintPriceUSD = record.mint_price_usd
  console.log(`address ${nftAddress} minted at a price of ${mintPriceEth} ETH or $${mintPriceUSD} USD`);
});
```

####

### The Details

**The `Query` Object**

The `Query` object contains both the sql and configuration you can send to the query engine for execution.

```typescript
type Query = {
  // SQL query to execute
  sql: string;

  // The number of minutes to cache the query results
  ttlMinutes?: number;

  // An override on the query result cahce.
  // A value of false will re-execute the query.
  cached?: boolean;

  // The number of minutes until your query run times out
  timeoutMinutes?: number;
  
  // The number of rows to return from the query result set.
  // If not specified this defaults to 100k. A max of 1m rows/records 
  // will be cached and can be paged thru using the pageNumber parameter.
  pageSize?: number;
  
  // The page to retrieve cached query results from.
  // The default (if not specified) is 1.
  pageNumber?: number;
};
```

Let's create a query to retrieve all NFTs minted by an address:

```typescript
const yourAddress = "<your_ethereum_address>";

const query: Query = {
  sql: `select nft_address, mint_price_eth, mint_price_usd from flipside_prod_db.ethereum_core.ez_nft_mints where nft_to_address = LOWER('${myAddress}')`,
  ttlMinutes: 60,
  cached: true,
  timeoutMinutes: 15,
  pageSize: 1000,
  pageNumber: 1
};
```

Now let's execute the query and retrieve the results.

```
const result: QueryResultSet = await flipside.query.run(query);
```

The results of this query will be cached for 60 minutes, given the `ttlMinutes` parameter.



**The `QueryResultSet` Object**

After executing a query the results are stored in a `QueryResultSet` object.

```typescript
interface QueryResultSet {
  // The server id of the query
  queryId: string | null;

  // The status of the query (`PENDING`, `FINISHED`, `ERROR`)
  status: QueryStatus | null;

  // The names of the columns in the result set
  columns: string[] | null;

  // The type of the columns in the result set
  columnTypes: string[] | null;

  // The results of the query
  rows: Row[] | null;

  // Summary stats on the query run (i.e. the number of rows returned, the elapsed time, etc)
  runStats: QueryRunStats | null;

  // The results of the query transformed as an array of objects
  records: QueryResultRecord[] | null;

  // If the query failed, this will contain the error
  error:
    | QueryRunRateLimitError
    | QueryRunTimeoutError
    | QueryRunExecutionError
    | ServerError
    | UserError
    | UnexpectedSDKError
    | null;
}
```

Let's iterate over the results from our query above.\
\
Our query selected `nft_address`, `mint_price_eth`, and `mint_price_usd`. We can access the returned data via the `records` parameter. The column names in our query are assigned as keys in each record object.

```
result?.records?.forEach((record) => {
  const nftAddress = record.nft_address
  const mintPriceEth = record.mint_price_eth
  const mintPriceUSD = record.mint_price_usd
  console.log(`address ${nftAddress} minted at a price of ${mintPriceEth} ETH or $${mintPriceUSD} USD`);
});
```



**Rate Limits**

Every API key is subject to a rate limit over a moving 5-minute window, as well as an aggregate daily limit.\
\
If the limit is reached in a 5-minute period, the SDK will exponentially backoff and retry the query up to the `timeoutMinutes` parameter set on the `Query` object.\
\
This feature is quite useful if leveraging the SDK client-side and your web application sees a large spike in traffic. Rather than using up your daily limit all at once, requests will be smoothed out over the day.y\
\
Rate limits can be adjusted per key/use case.



**Client-Side Request Requirements**

All API Keys correspond to a list of hostnames. Client-side requests that do not originate from the corresponding hostname will fail.

**Pagination**

More details on how pagination works can be found here:
