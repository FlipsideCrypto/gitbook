---
description: >-
  Secrets Manager allows you to securely store your secrets, such as API keys,
  to be used in LiveQuery's primitive functions.
---

# Secrets Manager

### 1. **Define your secret**

Start by creating a container that corresponds with the API you want to use and then populate key/value pairs within it&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-12-12 at 11.16.47 AM.png" alt=""><figcaption></figcaption></figure>

### 2. Reference your secret\_name

Pass in the `secret_name` as an argument in the `live.udf_api` function

```sql
live.udf_api(
  [method,]
  url,
  [headers,]
  [data,]
  [secret_name]
)
```

#### **More on arguments**

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
