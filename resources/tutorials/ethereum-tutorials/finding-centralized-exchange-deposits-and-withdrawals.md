---
description: >-
  Let's explore using Flipside's base label system to identify Centralized
  Exchange deposits and withdrawals.
---

# Finding Centralized Exchange Flows

Leveraging Flipside's base labeling system and on-chain events, you can easily see deposits and withdrawals from key exchanges.

Let's start by learning about `ethereum.core.dim_labels`.

```sql
select
  distinct label_subtype
from
  ethereum.core.dim_labels
where
  label_type = 'cex'
order by
  label_subtype;
```

As you can see, there are several types of `cex` labels in `dim_labels`. Let's look at flows to deposit wallets of Native ETH in the last week.&#x20;

```sql
select
  block_timestamp :: date as block_date,
  label,
  label_subtype,
  sum(amount) as inflows,
  sum(amount_usd) as inflows_usd
from
  ethereum.core.ez_native_transfers t
  join ethereum.core.dim_labels l on to_address = address
  and label_type = 'cex'
  and label_subtype = 'deposit_wallet'
where
  block_timestamp >= current_date() - 7
group by
  all
order by
  block_date desc,
  inflows desc;
```

Here we can see large flows to popular exchanges such as binance and coinbase. The labels data is extensive and this sample hardly scratches the surface of whats possible with `dim_labels`.
