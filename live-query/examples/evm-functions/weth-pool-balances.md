# 💡 WETH Pool Balances

In this example, we'll use the LiveQuery table function `latest_token_balance` to retrieve the real-time balance of Uniswap Pools.

{% hint style="warning" %}
If you'd like to follow along in your own Flipside Studio Account please make sure you've added the QuickNode integration to your account. QuickNode [instructions here](../../add-ons/quicknode-setup-guide.md).&#x20;
{% endhint %}

Let's start with a simple example, retrieve the balance of WETH and USDC on the WETH/USDC pool.

Pool Address: `0x88e6a0c2ddd26feeb64f039a2c41296fcb3f5640`

WETH Token Address: `0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2`

USDC Token Address: `0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48`

```sql
SELECT 
 *
FROM table(
  ethereum_mainnet.latest_token_balance(
    -- pool address
    '0x88e6a0c2ddd26feeb64f039a2c41296fcb3f5640',
    -- an array of addresses we want to know the pool's balance of
    [                                              
     '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2', -- WETH
     '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48'  -- USDC
    ]                                   
  )
)
```

{% hint style="danger" %}
Note you must wrap the call to the function in `TABLE()` since this function returns a table structure.&#x20;
{% endhint %}

This function will always return a table with the following columns:

| Column          | Type    |
| --------------- | ------- |
| blockchain      | varchar |
| network         | varchar |
| wallet\_address | varchar |
| token\_address  | varchar |
| symbol          | varchar |
| raw\_balance    | varchar |
| balance         | float   |

The function supports a few overloads. An overload means the function can take different combinations of inputs.  Here are a few overload examples:

### **Query a Pool's Balance for a Single Token**

```sql
SELECT 
 *
FROM table(
  ethereum_mainnet.latest_token_balance(
    '0x88e6a0c2ddd26feeb64f039a2c41296fcb3f5640', -- pool address
    '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2', -- WETH address
  )
)
```

### **Query Multiple Pool Balances Simultaneously using Dynamic Inputs**

In this example, we'll pull the latest WETH balance for all WETH pools that have done greater than $10 million in volume over the past week.&#x20;

We will first fetch the pools using Flipside's `ethereum.core.ez_dex_swaps` table and then use the table function `ethereum_mainnet.latest_token_balance()` to retrieve the balance for each pool involving WETH.

```sql
WITH pools AS (
  SELECT 
    contract_address as pool_address, 
    sum(amount_out_usd) as volume_usd 
  FROM ethereum.core.ez_dex_swaps
  WHERE 
    -- filter to only pools involving `WETH`
    (token_out = lower('0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2') OR token_in = lower('0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2'))
    AND block_timestamp >= GETDATE() - interval '1 week' 
    AND amount_out_usd IS NOT NULL
  -- filter to only pools with greater than $10m in USD volume
  GROUP BY pool_address HAVING volume_usd >= 10000000
)
SELECT
  *
FROM table(ethereum_mainnet.latest_token_balance(
  -- generate an array of pool addresses to pass to the function
  (SELECT array_agg(distinct pool_address) FROM pools),
  -- WETH token address
  '0xC02aaA39b223FE8D0A0e5C4F27eAD9083C756Cc2'
))
```

The above query will return the WETH balance for every pool that has had over $10 million in trading volume over the past week.
