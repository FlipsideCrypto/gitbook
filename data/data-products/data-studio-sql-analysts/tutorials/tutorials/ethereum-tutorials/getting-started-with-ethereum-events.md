---
description: >-
  This guide will take you through some sample queries working with decoded
  ethereum events.
---

# Getting Started with Decoded Ethereum Events

This guide provides an introduction to the `ethereum.core.ez_decoded_event_logs` table via a series of simple queries that explore the data.

{% hint style="info" %}
For a breakdown of the Ethereum tables [go here.](https://flipsidecrypto.github.io/ethereum-models/#!/overview)
{% endhint %}

Let's familiarize ourselves with the table by first looking at the types of events emitted by the USDC contract in the last week.&#x20;

```sql
select
  event_name,
  count(*) as events
from
  ethereum.core.ez_decoded_event_logs
where
  block_timestamp >= current_date() - 7
  and contract_address = '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48' -- USDC
group by
  event_name
order by
  events desc;
```

As you would expect, the most common event for the USDC token is the `Transfer` event. Let us dig a big deeper into the `Transfer` event. The human-readable arguments for this event can be found in the `decoded_log` column. This column is an `object` and must be queried using a specific syntax, demonstrated below.&#x20;

```sql
select
  decoded_log,
  decoded_log:from :: string as from_address,
  decoded_log:to :: string as to_address,
  decoded_log:value :: integer as value
from
  ethereum.core.ez_decoded_event_logs
where
  block_timestamp >= current_date() - 7
  and contract_address = '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48'
  and event_name = 'Transfer'
limit
  5;
```

Now that we know how to work with this data, let's analyze it.

```sql
select
  block_timestamp :: date as block_date,
  sum(decoded_log:value :: int) / pow(10, 6) as amount
from
  ethereum.core.ez_decoded_event_logs
where
  block_timestamp >= current_date() - 7
  and contract_address = '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48'
  and event_name = 'Transfer'
group by
  block_date
order by
  block_date desc;
```

The query above totals the transfer volume by day, for the last week, for USDC. Token amounts on the blockchain almost always require a decimal transformation, which for USDC is 6 places. We'll learn how to pull this in programmatically in the next section where we dig into who is receiving USDC in the last week.&#x20;

```sql
with raw_transfers as (
  select
    block_timestamp :: date as block_date,
    contract_address,
    decoded_log:to :: string as to_address,
    decoded_log:value :: int as value
  from
    ethereum.core.ez_decoded_event_logs events
  where
    block_timestamp >= current_date() - 7
    and contract_address = '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48'
    and event_name = 'Transfer'
)
select
  block_date,
  ifnull(address_name, 'Unknown') as address_name,
  to_address,
  decimals,
  sum(value) / pow(10, decimals) as amount
from
  raw_transfers e
  left join ethereum.core.dim_labels l on e.to_address = l.address
  left join ethereum.core.dim_contracts c on e.contract_address = c.address
group by
  all
order by
  block_date desc,
  amount desc;
```

This query utilizes a common-table-expression (CTE) to first pull in the relevant transfers in the last week. Next, we take advantage of the metadata in `dim_labels` and `dim_contracts` to enrich our analysis. `dim_contracts` is the home of decimals and symbols for smart contracts, as well as other metadata. `dim_labels` is useful for tagging addresses with human readable names, as well.&#x20;
