---
description: >-
  In this guide, we're going to look at how to create a view of balances at a
  block level and daily level.
---

# Block Level and Daily Balances

By using the snapshot data in `ethereum.core.fact_token_balances` we can create a block level view of balances or a daily view. The approach for both methods is similar, but we can start at a block level.&#x20;

{% hint style="info" %}
Please note: Balances data is very large. Queries without where filters on `block_number` of `block_timestamp` may take a long time. Please do your best to only query what you really need. However, we do realize that some use cases require full history.
{% endhint %}

We are going to use the same USDC-WETH Uniswap v3 pool from the prior example. We'll start by pulling the decimal transformed balances for the pool from the last 7 days.

```sql
select
  block_number,
  block_timestamp,
  user_address,
  contract_address,
  c.symbol,
  balance / pow(10, c.decimals) as balance
from
  ethereum.core.fact_token_balances b
  left join ethereum.core.dim_contracts c on b.contract_address = c.address
where
  user_address = '0x88e6a0c2ddd26feeb64f039a2c41296fcb3f5640'
  and block_timestamp >= current_date() - 7
  and contract_address in (
    '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
    '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48'
  )
```

The next step involves filling all the gaps in blocks with the prior value. This pool has a lot of volume as of writing, so there is not much filling to do, as there is already almost a swap every block. However, something like an EOA (wallet) will have much less volume, and therefore has more filling to do. We will fill by `block_number` here, but if you only needed daily balances, you could fill by `block_timestamp::date`.&#x20;

Once we have our spine of `block_number`, `user_address`, `contract_address`, and `symbol`, we can left join in our balances data, and fill the gaps with the prior valid value. Let's do this with a few CTEs.

```sql
with balances as (
  select
    block_number,
    block_timestamp,
    user_address,
    contract_address,
    c.symbol,
    balance / pow(10, c.decimals) as balance
  from
    ethereum.core.fact_token_balances b
    left join ethereum.core.dim_contracts c on b.contract_address = c.address
  where
    user_address = '0x88e6a0c2ddd26feeb64f039a2c41296fcb3f5640'
    and block_timestamp >= current_date() - 7
    and contract_address in (
      '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
      '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48'
    )
),
-- create a spine of all the possible combos
spine as (
  select
    block_number,
    block_timestamp,
    user_address,
    contract_address,
    symbol
  from
    ethereum.core.fact_blocks b
    join (
      select
        distinct contract_address,
        user_address,
        symbol
      from
        balances
    ) on 1 = 1
  where
    block_number between (
      select
        min(block_number)
      from
        balances
    )
    and (
      select
        max(block_number)
      from
        balances
    )
),
-- join all options with transfer based data and fill gaps 
block_level_balances as (
  select
    s.block_number,
    s.block_timestamp,
    s.user_address,
    s.contract_address,
    s.symbol,
    b.balance,
    LAST_VALUE(b.balance ignore nulls) over(
      PARTITION BY s.user_address,
      s.contract_address
      ORDER BY
        s.block_number ASC rows unbounded preceding
    ) as balance_filled
  from
    spine s
    left join balances b using (block_number, user_address, contract_address)
)
select
  *
from
  block_level_balances;
```

This gives us the WETH and USDC balance, per block, for the Uniswap V3 pool. We could take this a step further by filtering to just the last balace per day using the following final step.

```sql
select
  block_timestamp :: date as block_date,
  block_number,
  user_address,
  contract_address,
  symbol,
  balance_filled as balance
from
  block_level_balances qualify (
    row_number() over (
      partition by user_address,
      contract_address,
      block_date
      order by
        block_number desc
    ) = 1
  )
order by
  block_date,
  user_address,
  contract_address
```

If you wanted to analyze the total supply of a token, you would want to remove the `user_address` filter. There are many possibilities with these tables, but remember to use as many filters as possible for optimal performance.&#x20;
