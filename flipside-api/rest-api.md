---
description: Lower-level Direct HTTP Access
---

# API

_**To skip the walkthrough and go straight to dedicated API Documentation,**_ [_**click here**_](https://api-docs.flipsidecrypto.xyz/)_**.**_

{% hint style="info" %}
Don't see an SDK for your language of choice? Interact directly with the API endpoints below! If you're feeling adventurous feel free to build an SDK library -- we'd be happy to point the community to it.
{% endhint %}

The Query API uses an RPC interface instead of REST for its client-server communication. This is because RPC can provide more efficient communication and support for batch/multi-calls, which is useful for dashboards that have lots of queries powering them. Future functionality will make use of the RPC architecture to enable more efficient/scalable application use cases.

### Getting Started

There are three RPC methods you must interact with to execute a query:

1. `createQueryRun`: used to queue up the execution of a query.
2. `getQueryRun`: used to retrieve the status of a query run.
3. `getQueryRunResults`: used to retrieve the results of the query run once it has completed executing.

### Step 1: Create a Query

The following call to the API will queue up the execution of a query. If results already exist the query will not be executed. The endpoint returns a `token` that can be plugged into the `Get Query Results` endpoint to retrieve your data.

{% tabs %}
{% tab title="cURL Example" %}


```bash
curl --location -g 'https://api-v2.flipsidecrypto.xyz/json-rpc' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {{api_key}}' \
--data '{
    "jsonrpc": "2.0",
    "method": "createQueryRun",
    "params": [
        {
            "resultTTLHours": 1,
            "maxAgeMinutes": 0,
            "sql": "SELECT date_trunc('\''hour'\'', block_timestamp) as hourly_datetime, count(distinct tx_hash) as tx_count from ethereum.core.fact_transactions where block_timestamp >= getdate() - interval'\''1 month'\'' group by 1 order by 1 desc",
            "tags": {
                "source": "postman-demo",
                "env": "test"
            },
            "dataSource": "snowflake-default",
            "dataProvider": "flipside"
        }
    ],
    "id": 1
}'
```
{% endtab %}

{% tab title="JS Example" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "{{api_key}}");

var raw = JSON.stringify({
  "jsonrpc": "2.0",
  "method": "createQueryRun",
  "params": [
    {
      "resultTTLHours": 1,
      "maxAgeMinutes": 0,
      "sql": "SELECT date_trunc('hour', block_timestamp) as hourly_datetime, count(distinct tx_hash) as tx_count from ethereum.core.fact_transactions where block_timestamp >= getdate() - interval'1 month' group by 1 order by 1 desc",
      "tags": {
        "source": "postman-demo",
        "env": "test"
      },
      "dataSource": "snowflake-default",
      "dataProvider": "flipside"
    }
  ],
  "id": 1
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api-v2.flipsidecrypto.xyz/json-rpc", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endtab %}

{% tab title="Python Example" %}
```python
import requests
import json

url = "https://api-v2.flipsidecrypto.xyz/json-rpc"

payload = json.dumps({
  "jsonrpc": "2.0",
  "method": "createQueryRun",
  "params": [
    {
      "resultTTLHours": 1,
      "maxAgeMinutes": 0,
      "sql": "SELECT date_trunc('hour', block_timestamp) as hourly_datetime, count(distinct tx_hash) as tx_count from ethereum.core.fact_transactions where block_timestamp >= getdate() - interval'1 month' group by 1 order by 1 desc",
      "tags": {
        "source": "postman-demo",
        "env": "test"
      },
      "dataSource": "snowflake-default",
      "dataProvider": "flipside"
    }
  ],
  "id": 1
})
headers = {
  'Content-Type': 'application/json',
  'x-api-key': '{{api_key}}'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```
{% endtab %}

{% tab title="R Example" %}
```r
library(RCurl)
headers = c(
  "Content-Type" = "application/json",
  "x-api-key" = "{{api_key}}"
)
params = "{
  \"jsonrpc\": \"2.0\",
  \"method\": \"createQueryRun\",
  \"params\": [
    {
      \"resultTTLHours\": 1,
      \"maxAgeMinutes\": 0,
      \"sql\": \"SELECT date_trunc('hour', block_timestamp) as hourly_datetime, count(distinct tx_hash) as tx_count from ethereum.core.fact_transactions where block_timestamp >= getdate() - interval'1 month' group by 1 order by 1 desc\",
      \"tags\": {
        \"source\": \"postman-demo\",
        \"env\": \"test\"
      },
      \"dataSource\": \"snowflake-default\",
      \"dataProvider\": \"flipside\"
    }
  ],
  \"id\": 1
}"
res <- postForm("https://api-v2.flipsidecrypto.xyz/json-rpc", .opts=list(postfields = params, httpheader = headers, followlocation = TRUE), style = "httppost")
cat(res)
```
{% endtab %}
{% endtabs %}



### Step 2: Poll for the Status of the Query Run

This endpoint takes as input a query run id returned by the `createQueryRun` rpc call.

{% tabs %}
{% tab title="cURL Example" %}
```bash
curl --location -g 'https://api-v2.flipsidecrypto.xyz/json-rpc' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {{api_key}}' \
--data '{
    "jsonrpc": "2.0",
    "method": "getQueryRun",
    "params": [
        {
            "queryRunId": "{{queryRunId}}"
        }
    ],
    "id": 1
}'
```
{% endtab %}

{% tab title="JS Example" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "{{api_key}}");

var raw = JSON.stringify({
  "jsonrpc": "2.0",
  "method": "getQueryRun",
  "params": [
    {
      "queryRunId": "{{queryRunId}}"
    }
  ],
  "id": 1
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api-v2.flipsidecrypto.xyz/json-rpc", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endtab %}

{% tab title="Python Example" %}
```python
import requests
import json

url = "https://api-v2.flipsidecrypto.xyz/json-rpc"

payload = json.dumps({
  "jsonrpc": "2.0",
  "method": "getQueryRun",
  "params": [
    {
      "queryRunId": "{{queryRunId}}"
    }
  ],
  "id": 1
})
headers = {
  'Content-Type': 'application/json',
  'x-api-key': '{{api_key}}'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```
{% endtab %}

{% tab title="R Example" %}
```r
library(RCurl)
headers = c(
  "Content-Type" = "application/json",
  "x-api-key" = "{{api_key}}"
)
params = "{
  \"jsonrpc\": \"2.0\",
  \"method\": \"getQueryRun\",
  \"params\": [
    {
      \"queryRunId\": \"{{queryRunId}}\"
    }
  ],
  \"id\": 1
}"
res <- postForm("https://api-v2.flipsidecrypto.xyz/json-rpc", .opts=list(postfields = params, httpheader = headers, followlocation = TRUE), style = "httppost")
cat(res)
```
{% endtab %}
{% endtabs %}

Once the `getQueryRun` has returned a state of `QUERY_STATE_SUCCESS` call the `getQueryRunResults` RPC method to retrieve the result set in Step3.

### Step 3: Get the Query Run Results

This endpoint takes as input a query run id used in the previous two steps.

{% tabs %}
{% tab title="cURL Example" %}
```bash
curl --location -g 'https://api-v2.flipsidecrypto.xyz/json-rpc' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {{api_key}}' \
--data '{
    "jsonrpc": "2.0",
    "method": "getQueryRunResults",
    "params": [
        {
            "queryRunId": "{{queryRunId}}",
            "format": "csv",
            "page": {
                "number": 1,
                "size": 1
            }
        }
    ],
    "id": 1
}'
```
{% endtab %}

{% tab title="JS Example" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("x-api-key", "{{api_key}}");

var raw = JSON.stringify({
  "jsonrpc": "2.0",
  "method": "getQueryRunResults",
  "params": [
    {
      "queryRunId": "{{queryRunId}}",
      "format": "csv",
      "page": {
        "number": 1,
        "size": 1
      }
    }
  ],
  "id": 1
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api-v2.flipsidecrypto.xyz/json-rpc", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endtab %}

{% tab title="Python Example" %}
```python
import requests
import json

url = "https://api-v2.flipsidecrypto.xyz/json-rpc"

payload = json.dumps({
  "jsonrpc": "2.0",
  "method": "getQueryRunResults",
  "params": [
    {
      "queryRunId": "{{queryRunId}}",
      "format": "csv",
      "page": {
        "number": 1,
        "size": 1
      }
    }
  ],
  "id": 1
})
headers = {
  'Content-Type': 'application/json',
  'x-api-key': '{{api_key}}'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```
{% endtab %}

{% tab title="R Example" %}
```r
library(RCurl)
headers = c(
  "Content-Type" = "application/json",
  "x-api-key" = "{{api_key}}"
)
params = "{
  \"jsonrpc\": \"2.0\",
  \"method\": \"getQueryRunResults\",
  \"params\": [
    {
      \"queryRunId\": \"{{queryRunId}}\",
      \"format\": \"csv\",
      \"page\": {
        \"number\": 1,
        \"size\": 1
      }
    }
  ],
  \"id\": 1
}"
res <- postForm("https://api-v2.flipsidecrypto.xyz/json-rpc", .opts=list(postfields = params, httpheader = headers, followlocation = TRUE), style = "httppost")
cat(res)
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Detailed documentation on Flipside's RPC API can be [found by clicking here](https://api-docs.flipsidecrypto.xyz).
{% endhint %}
