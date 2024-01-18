---
description: >-
  This guide will take you thru an introduction of the Ethereum ERC20 Balance
  table by exploring the total value locked (TVL) metric.
---

# Getting Started with Ethereum ERC20 Balances

{% hint style="info" %}
If you're looking for a breakdown of the `ethereum.erc20_balances` table take a look [here](broken-reference).
{% endhint %}

In this tutorial, we're going to familiarize ourselves with the ethereum er20 balances table by computing a metric known as Total Value Locked, or TVL for short.

TVL measures the total amount of a token that is locked in a contract.&#x20;

Let's begin by looking at the amount of USDC locked in Curve liquidity pools.

```sql
SELECT 
  date_trunc('day', balance_date) as metric_date,
  symbol,
  amount_usd
FROM ethereum.erc20_balances
WHERE 
  -- the user address is the Curve Liquidty Pool
  user_address = '0xa5407eae9ba41422680e2e00537571bcc53efbfd' AND
  -- the contract address is the USDC proxy contract
  contract_address = '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48' AND
  balance_date >= getdate() - interval '1 month'
```

There are a couple of notable things in the query above:

1. `user_address` in this case, refers to the [Curve liquidity pool](https://etherscan.io/address/0xa5407eae9ba41422680e2e00537571bcc53efbfd) that we'd like to take a balance reading of against the USDC contract.&#x20;
2. `contract_address` is set to the USDC proxy contract. The idea here is that we want to ask for the balance of the user address, the Curve pool, on this contract, USDC.

The results depict a downward-looking trend for the TVL of USDC in this specific Curve liquidity pool.

![](<../../../.gitbook/assets/Screen Shot 2020-11-01 at 11.15.42 PM.png>)

&#x20;Now, instead of looking at the balance locked in a liquidity pool, let's look at the amount of USDC deposited into the Maker eco-system for use in Maker's lending platform.

For this query, we need to look at the balance of USDC on the Maker Gem Join contract. Instead of querying by user\_address or contract address, we're going to leverage Flipside's labels directly:

```sql
SELECT date_trunc('day', balance_date) as metric_date,
       amount_usd
FROM ethereum.erc20_balances 
WHERE 
 -- This is the address name corresponding to the user address 
 -- of the maker gem join contract
 address_name = 'makerdao gem join usdc' AND
 -- This symbol corresponds to the USDC contract address
 symbol = 'USDC' AND
 balance_date >= getdate() - interval '3 months'
```

![](<../../../.gitbook/assets/Screen Shot 2020-11-01 at 11.32.21 PM.png>)

Two things to note from this query:

1. Instead of entering the `user_address` directly, we leveraged Flipside's label to get at the Maker Gem Join contract.
2. Similar to the first point, instead of using the USDC contract address we use the`symbol` here. This symbol has been whitelisted to avoid collision.&#x20;

From here, I encourage you to explore TVL on other platforms such as Balancer, UniSwap, or Aave.&#x20;
