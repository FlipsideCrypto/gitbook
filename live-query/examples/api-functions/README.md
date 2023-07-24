---
description: >-
  Primitive functions that allow you to access API data within Flipside with
  Snowflake SQL
---

# 🤖 API Functions

API functions serve as a low-level primitive that enables you to query any API (or Node RPC) and bring those results into Flipside. This is particularly useful for 3rd Party Data APIs or blockchain nodes/networks not yet supported by higher-level functions such as our EVM Functions.

<details>

<summary>Allowlisted APIs</summary>

The following APIs are queryable with LiveQuery. If you interested in having your API added, please submit an issue [here](https://github.com/FlipsideCrypto/livequery-models/issues/new/choose).&#x20;

* api.chainbase.online
* api.deepnftvalue.com
* api.footprint.network
* api.helius.xyz
* api.thegraph.com
* api.zapper.xyz
* api.zksync.io
* avax.network
* blockchainnodeengine.com
* credmark.com
* flipsidecrypto.xyz
* g.alchemy.com
* gateway.credmark.com
* gateway.thegraph.com
* helius.xyz
* hub.snapshot.org
* ipfs.io
* llama.fi
* playgrounds.network
* quiknode.pro
* rest.stargaze-apis.com
* services.blockpour.com
* solscan.io
* subnets.avax.network
* thegraph.com

</details>

## **API Function Examples**

{% content-ref url="query-thegraph.md" %}
[query-thegraph.md](query-thegraph.md)
{% endcontent-ref %}

{% content-ref url="query-defi-llama.md" %}
[query-defi-llama.md](query-defi-llama.md)
{% endcontent-ref %}

## UDF\_API Documentation

### Syntax

```
live.udf_api(
  [method,]
  url,
  [headers,]
  [data,]
  [secret_name]
)
```

### Arguments

**Required:**

* `url` (string): The URL to call. If you are doing a GET request that does not require authentication, you can pass the URL directly. Otherwise, you may need to pass in some or all of the optional arguments below. You may also need to pass a secret value into the URL if you are using an API that requires authentication.

**Optional:**

* `method` (string): The HTTP method to use (GET, POST, etc.)
  * Default: `GET`, unless `data` is passed, in which it will default to `POST`
* `headers` (object): A JSON object containing the headers to send with the request.
  * Default: `{'Content-Type': 'application/json'}`
* `data` (object): A JSON object containing the data to send with the request. Batched JSON RPC requests are supported by passing an array of JSON RPC requests.
  * Default: `null`
* `secret_name` (string): The name of the secret to use for authentication.&#x20;
