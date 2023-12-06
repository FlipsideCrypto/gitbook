# MakerDAO Tutorials

This guide provides an introduction to exploring Dai related events by using the`ethereum.udm_events` table over a series of simple queries that explore the data.

{% hint style="info" %}
Note: this tutorial uses deprecated Ethereum tables. See the new [Maker DAO](../archive/tables/ethereum-maker-dao-tables.md) curated tables.
{% endhint %}

Let's familiarize ourselves with the table by first looking at the types of events that can be queried for `Dai`

```sql
SELECT 
    event_type, 
    event_name,
    count(1) as event_count
FROM ethereum.udm_events 
WHERE 
  symbol = 'DAI' AND
  block_timestamp >= GETDATE() - interval'8 months'
GROUP BY event_type, event_name
ORDER BY event_count DESC
```

| event\_type     | event\_name          | event\_count |
| --------------- | -------------------- | ------------ |
| erc20\_transfer | transfer             | 3929409      |
| event           | Approval             | 630353       |
| event           | TransferEnabled      | 1            |
| event           | OperatorAdded        | 1            |
| event           | MinterAdded          | 1            |
| event           | OwnershipTransferred | 1            |

From the results of this query we see the majority of events are dominated by `transfer` activity, with the second-highest being, calls to `Approval` on the Dai contract.

{% hint style="info" %}
Note that in the above query, the event names have been decoded into English legible names.&#x20;
{% endhint %}

In our next query let's take a look at the trend of DAI transfers over the prior 30 days:

```sql
SELECT 
  date_trunc('day', block_timestamp) as metric_date,
  sum(amount) as total_amount
FROM ethereum.udm_events
WHERE 
  event_name = 'transfer' AND
  symbol = 'DAI' AND
  amount > 0 AND
  block_timestamp >= GETDATE() - interval'30 days'
GROUP BY metric_date
ORDER BY metric_date ASC
```

![](<../../.gitbook/assets/Screen Shot 2020-11-08 at 8.29.00 PM.png>)

We can break this query down even further by leveraging [Flipside's labels](../labels/). Let's calculate the amount of DAI that is flowing to centralized exchanges using the `distributor_cex` label sub-type.

```sql
SELECT 
  date_trunc('day', block_timestamp) as metric_date,
  sum(amount) as total_amount
FROM ethereum.udm_events
WHERE 
  event_name = 'transfer' AND
  symbol = 'DAI' AND
  to_label_subtype = 'distributor_cex' AND
  amount > 0 AND
  block_timestamp >= GETDATE() - interval'30 days'
GROUP BY metric_date
ORDER BY metric_date ASC
```

![](<../../.gitbook/assets/Screen Shot 2020-11-08 at 8.36.02 PM.png>)

From here, I encourage you to explore our labels even further by breaking down specifically which exchanges DAI is flowing to.

In our next tutorial, we'll explore the amount of activity of DAI that can be attributed to DeFi related activity vs. non DeFi activity and build Flipside's DeFi Activity Ratio metric.
