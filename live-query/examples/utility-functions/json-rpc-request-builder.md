---
description: >-
  This functions helps you build JSON RPC Requests to be passed to an node or
  other API
---

# 💡 JSON RPC Request Builder

## UDF\_JSON\_RPC\_CALL()

### Syntax

```
utils.udf_json_rpc_call(
  method,
  params
  [,id]
)
```

### Arguments

**Required:**

* `method` (string): The method to call
* `params` (array or object): The parameters to pass to the method. This can be an array or an object.

**Optional:**

* `id` (string): The ID of the request. This parameter is optical.&#x20;
  * Default: `random number`

### Sample Queries

```sql
-- Creates a JSON RPC Request to fetch the latest block using the `eth_blockNumber` method
   SELECT utils.udf_json_rpc_call('eth_blockNumber',[]) AS rpc_request;
   
-- Creates a JSON RPC Request use the `eth_call` method to fetch the balance of a wallet for a token
 WITH inputs AS (
     -- input function_sig, token_address, wallet_address
     -- format data for eth call, should be 64 chars long (32 bytes) + 10 chars for function sig (including 0x)
     SELECT
            LOWER('0xae7ab96520DE3A18E5e111B5EaAb095312D7fE84') AS token_address,
            -- stETH
            LOWER('0x66B870dDf78c975af5Cd8EDC6De25eca81791DE1') AS wallet_address,
            --a16Z
            '0x70a08231' AS function_sig,
            --balanceOf(address)
            CONCAT(
                   function_sig,
                   LPAD(REPLACE(wallet_address, '0x', ''), 64, 0)
            ) AS DATA
) -- creates a formatted json rpc eth_call request that is ready to be sent to a node
SELECT
     utils.udf_json_rpc_call(
            'eth_call',
            [{ 'to': token_address, 'from': null, 'data': data },'latest']
     ) AS rpc_request
FROM
     inputs;
```
