---
description: Make any RPC call to an EVM Node using LiveQuery
---

# 💡 General EVM Node Queries

In the following examples, we will use the available EVM primitives to make calls directly to an EVM blockchain node. We will use Ethereum Mainnet here, but the same queries will work on any LiveQuery supported chain and network because they use generic EVM RPC methods.&#x20;

We will start small by getting the latest block for Ethereum Mainnet.

{% hint style="warning" %}
If you'd like to follow along in your own Flipside Studio Account please make sure you've added the QuickNode integration to your account. QuickNode [instructions here](../../add-ons/quicknode-setup-guide.md).



Additionally, please see QuickNode for API credit usage per method. You are unlikely to run into credit issues using these functions, unless you are programmatically accessing the data frequently.  &#x20;
{% endhint %}

## Latest Block&#x20;

Using the `udf_rpc` function, we can easily make a [`eth_blockNumber`](https://www.quicknode.com/docs/ethereum/eth\_blockNumber) call to our `ethereum_mainnet` node. This method does not require parameters, so we will just pass a null variant as our parameters. This will return in hexadecimal format, so we will need to apply `utils.udf_hex_to_int` to make it human-readable.&#x20;

```sql
select 
ethereum_mainnet.udf_rpc('eth_blockNumber', [])::STRING AS latest_block_hex,
utils.udf_hex_to_int(latest_block_hex)::int as latest_block_int;
```

## Transactions for a Block

In this example, we will pull the transaction details for a specific block. There are lots of available RPC methods, but here we will use [`eth_getBlockByNumber`](https://www.quicknode.com/docs/ethereum/eth\_getBlockByNumber). In order to return the details of the transactions within the block, we will also need to pass the `transaction detail flag` parameter as `true` alongside our hex block number.&#x20;

```sql
select 
ethereum_mainnet.udf_rpc('eth_getBlockByNumber', 
    [utils.udf_int_to_hex(17000000), --hex block
    true] -- true for tx details
);
```

This returns a large JSON Object, filled with arrays. This block contains 102 transactions, so we'd expect 102 items in our transactions array. We could also flatten this our to look at the details for each transaction. We won't do that here, but if you wanted to, you'd need to use `lateral flatten`. Lets just look at the block details and count the transactions using `array_size()`.

```sql
select 
ethereum_mainnet.udf_rpc('eth_getBlockByNumber', [utils.udf_int_to_hex(17000000), true]) as response,
utils.udf_hex_to_int(response:number::string) as block_number,
to_timestamp_ntz(utils.udf_hex_to_int(response:timestamp::string)) as block_timestamp,
array_size(response:transactions) as block_tx_count;
```

## Logs for a Contract in a Range

Here we will use `udf_rpc_eth_get_logs` to get the emitted event logs for a contract. We will use the USDC contract starting at block 17 million for 100 blocks. We'll have to flatten the result and pull out the relevant columns. This method uses [`eth_getLogs`](https://www.quicknode.com/docs/ethereum/eth\_getLogs) which does have limitations on large ranges. The `toBlock` parameter can also be latest, if you are interested in real-time logs. &#x20;

```sql
WITH base AS (
    SELECT 
        '0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48' AS contract_address,
        17000000 AS start_block_int,
        start_block_int + 100 AS end_block_int,
        utils.udf_int_to_hex(start_block_int) AS start_block_hex,
        utils.udf_int_to_hex(end_block_int) AS end_block_hex
),
raw_logs AS (
    SELECT 
        ethereum_mainnet.udf_rpc_eth_get_logs(OBJECT_CONSTRUCT('address', contract_address, 'fromBlock', start_block_hex, 'toBlock', end_block_hex)) AS eth_logs
    FROM 
        base
)
SELECT 
    value:address::string AS address,
    value:blockNumber::string AS blockNumber,
    value:data::string AS data,
    value:logIndex::string AS logIndex,
    value:topics AS topics,
    value:transactionHash AS transactionHash
FROM 
    raw_logs, 
    LATERAL FLATTEN (input => eth_logs);

```

## Balances for an Address

LiveQuery provides a number of ways to pull balances for an address. In this example, we will use `udf_rpc_eth_get_balance` and `udf_get_token_balance`. Lets find the top 10 trades on Uniswapv3 this week, and look at the ETH balance and the token balance the wallet swapped for.&#x20;

```sql
WITH traders AS (
    SELECT 
        tx_hash,
        origin_from_address AS trader, 
        token_in AS token_address, 
        symbol_in,
        amount_in_usd AS swap_amount
    FROM 
        ethereum.core.ez_dex_swaps
    WHERE 
        block_timestamp >= current_date - 7
        AND platform = 'uniswap-v3'
        AND amount_in_usd IS NOT NULL 
    ORDER BY 
        amount_in_usd DESC 
    LIMIT 10
)
SELECT 
    t.*,
    utils.udf_hex_to_int(ethereum_mainnet.udf_rpc_eth_get_balance(trader, 'latest')::string) / pow(10,18) AS eth_balance,
    ethereum_mainnet.udf_get_token_balance(trader, token_address) / pow(10, decimals) AS token_balance
FROM 
    traders t 
JOIN 
    ethereum.core.dim_contracts
ON 
    token_address = address;
```

We could also look at their balance on block after the swap but giving the functions that block number in hex, like so.&#x20;

```sql
WITH traders AS (
    SELECT 
        tx_hash,
        block_number + 1 AS block_number,
        utils.udf_int_to_hex(block_number + 1) AS block_hex,
        origin_from_address AS trader, 
        token_in AS token_address, 
        symbol_in,
        amount_in_usd AS swap_amount
    FROM 
        ethereum.core.ez_dex_swaps
    WHERE 
        block_timestamp >= current_date - 7
        AND platform = 'uniswap-v3'
        AND amount_in_usd IS NOT NULL 
    ORDER BY 
        amount_in_usd DESC 
    LIMIT 10
)
SELECT 
    t.*,
    utils.udf_hex_to_int(ethereum_mainnet.udf_rpc_eth_get_balance(trader, block_hex)::string) / pow(10,18) AS eth_balance,
    ethereum_mainnet.udf_get_token_balance(trader, token_address, block_number) / pow(10, decimals) AS token_balance
FROM 
    traders t 
JOIN 
    ethereum.core.dim_contracts
ON 
    token_address = address;
```
