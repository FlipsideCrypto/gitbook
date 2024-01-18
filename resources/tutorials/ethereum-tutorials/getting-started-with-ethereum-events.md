---
description: This guide will take you thru an introduction of the Ethereum events table.
---

# Getting Started with Ethereum Events

This guide provides an introduction to the `ethereum.udm_events` table via a series of simple queries that explore the data.

{% hint style="info" %}
For a breakdown of the Ethereum Events table schema [go here.](broken-reference)
{% endhint %}

Let's familiarize ourselves with the table by first looking at the types of events that can be queried.

```sql
SELECT distinct(event_type) FROM ethereum.udm_events 
```

| event\_type     | description                                      |
| --------------- | ------------------------------------------------ |
| function        | A function call                                  |
| event           | An event emitted from a function call.           |
| erc20\_transfer | An event involving a transfer of an ERC20 token. |
| native\_eth     | A native eth transfer.                           |

This tells us there are 4 types of events that get recorded in the ethereum events table. Let's take a closer look at the decoded on-chain event names for USDC over the past 30 days.

```sql
SELECT 
  event_type,
  event_name as event_name,
  count(event_name)
FROM ethereum.udm_events
WHERE 
  -- USDC contract address
  contract_address = '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48' AND
  block_timestamp >= GETDATE() - interval'30 days'
GROUP BY 1,2
ORDER BY 3 DESC
```

| event\_type     | event\_name      | count     |
| --------------- | ---------------- | --------- |
| erc20\_transfer | transfer         | 1,142,589 |
| event           | Approval         | 167,014   |
| event           | Mint             | 525       |
| event           | Burn             | 514       |
| event           | MinterConfigured | 15        |

These results provide a more granular breakdown of the events surrounding the USDC contract. Specifically, this shows us the number of Approval, Mint, Burn, and MinterConfigured events that were emitted by the USDC contract. It appears that the greatest number of events are related to transfers of the USDC token. In our next query let's look at the trend of USDC transfers of the past 30 days.

```sql
SELECT 
  date_trunc('day', block_timestamp) as metric_date,
  sum(amount) as total_amount
FROM ethereum.udm_events
WHERE 
  event_type = 'erc20_transfer' AND
  symbol = 'USDC' AND
  amount > 0 AND
  block_timestamp >= GETDATE() - interval'30 days'
GROUP BY metric_date
ORDER BY metric_date DESC
```

![](<../../../.gitbook/assets/Screen Shot 2020-11-01 at 10.30.54 PM.png>)

We see a big spike in USDC transfers on October 26th. This just happens to coincide with the Harvest.finance attack on the same date. Let's take a closer look at the exchanges that USDC was being sent to at that time by leveraging Flipside's Exchange labels.

```sql
SELECT 
  to_label,
  sum(amount) as total_amount
FROM ethereum.udm_events
WHERE
  -- the 'distributor' label type = exchanges 
  to_label_type = 'distributor' AND
  event_type = 'erc20_transfer' AND
  symbol = 'USDC' AND
  amount > 0 AND
  block_timestamp >= '2020-10-26T00:00:00Z' AND
  block_timestamp <= '2020-10-27T00:00:00Z'
GROUP BY to_label, to_label_type
ORDER BY total_amount DESC
LIMIT 5
```

| to\_label    | total\_amount    |
| ------------ | ---------------- |
| curve fi     | 2,786,908,380.42 |
| yearn        | 1,431,392,778.53 |
| ftx exchange | 168,161,544.95   |
| binance      | 82,280,347.55    |
| uniswap      | 44,740,268.63    |

Here we see that Curve saw the largest influx at \~2.7B, followed closely by Yearn.&#x20;

From here I encourage you to dig deeper by exploring the inflows and outflows on each of these exchanges, perhaps even looking at individual pool activity on curve or uniswap by leveraging the project labels.
