---
description: This guide will take you through the Ethereum balances tables.
---

# Getting Started with Ethereum Balances

{% hint style="info" %}
If you're looking for a breakdown of the balances tables take a look [here](https://flipsidecrypto.github.io/ethereum-models/#!/overview).
{% endhint %}

In this tutorial, we're going to familiarize ourselves with `ethereum.core.fact_token_balances`

This table is built by doing a balances call for the parties involved in a transfer event, at every block. Because a balance read is conducted at every block of a transfer, this data is very powerful, and can serve as the basis for both daily balances, and block based balances, but more on that later.&#x20;

For now, let's begin by familiarizing ourselves with the table.&#x20;

```sql
select
  block_number,
  block_timestamp,
  user_address,
  contract_address,
  balance
from
  ethereum.core.fact_token_balances b
where
  user_address = '0x88e6a0c2ddd26feeb64f039a2c41296fcb3f5640'
  and block_timestamp >= current_date() - 7
  and contract_address in (
    '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
    '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48'
  )
limit
  500;
```

There are a couple of notable things in the query above:

1. `user_address` is the wallet or contract whose balance we want to analyze, in this case it is a popular [Uniswap V3 USDC - WETH pool](https://etherscan.io/address/0x88e6a0c2ddd26feeb64f039a2c41296fcb3f5640). &#x20;
2. `contract_address` is filtered to USDC and WETH. It is possible this contract could hold other tokens, either by accidental transfer or some other case, but for the purposes of our analysis lets just filter to these two tokens.&#x20;
3. `block_timestamp` is a good filter to include, whenever possible. The balances table is very large, and filters will help your queries' performance. In our example, we are going to look at TVL over the last week.
4. `balance` is the unadjusted balance. Remember from the prior tutorial that tokens on the blockchain often need a decimal adjustment for human-readability.&#x20;

Now let's combine the balances snapshots with `core.dim_contracts` and `price.ez_hourly_token_prices` to look at TVL for the Uniswap pool by block.&#x20;

```sql
with balances as (
  select
    block_number,
    block_timestamp,
    contract_address,
    c.symbol,
    balance / pow(10, c.decimals) as balance_adjusted,
    balance_adjusted * price as balance_usd
  from
    ethereum.core.fact_token_balances b
    left join ethereum.core.dim_contracts c on b.contract_address = c.address
    left join ethereum.price.ez_hourly_token_prices p on p.token_address = b.contract_address
    and p.hour = date_trunc('hour', b.block_timestamp)
  where
    user_address = '0x88e6a0c2ddd26feeb64f039a2c41296fcb3f5640'
    and block_timestamp >= current_date() - 7
    and contract_address in (
      '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
      '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48'
    )
)
select
  block_number,
  block_timestamp,
  sum(balance_usd) as TVL
from
  balances
where
  balance_usd is not null
group by
  block_number,
  block_timestamp
order by
  block_number desc;
```

For native balance data, please use `ethereum.core.fact_eth_balances`. The same approaches learned here apply to the native balances table, there is just no `contract_address` column since it only contains the native asset.&#x20;

Additionally, two `ez_` views exist to help with common balances use cases.

1. `ez_balance_deltas` - this view contains both ETH and token information for a block as well as the previous value for that wallet / token, along with other helpful columns for prices information.&#x20;
2. `ez_current_balances` - this view returns the current balances for a given wallet per token.

In the next section, we will explore how to expand the snapshot data to a block level or daily level.
