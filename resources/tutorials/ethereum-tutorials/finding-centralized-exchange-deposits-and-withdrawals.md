---
description: >-
  Let's explore using Flipside's base label system to identify Centralized
  Exchange deposits and withdrawals.
---

# Finding Centralized Exchange Deposits and Withdrawals



Leveraging Flipside's base labeling system and on-chain events, you can easily see deposits and withdrawals from key exchanges.

Whenever you try to answer a complicated question like this, you're going to have several layers to your query, so it helps to build up small pieces.

{% hint style="info" %}
If you haven't gone through the [Getting Started with Ethereum Events](https://app.gitbook.com/getting-started-with-ethereum-events) guide or worked with labels in the [Using Labels to Break Down Token Supply](using-labels-to-break-down-token-supply.md) guide, yet, we recommend you do that first.
{% endhint %}

Let's start by look at ETH movement into exchanges for a week in October 2020.

```sql
SELECT
    date_trunc('day', block_timestamp) as date,
    to_label_type,
    to_label_subtype,
    round(sum(amount_usd)) as total_inflow
FROM
    ethereum.udm_events
WHERE
    to_label_type = 'distributor'
    AND event_type = 'native_eth'
    AND block_timestamp > '2020-10-01'
    AND block_timestamp < '2020-10-08'
GROUP BY date,to_label_type,to_label_subtype
ORDER BY date, total_inflow DESC
```

In this query, we:

* select label type and subtype because we don't always know which level we need at first
* filter `native_eth` transfers only

Each day give us results that look like this:

| Date                | To Label Type | To Label Subtype            | Total Inflow |
| ------------------- | ------------- | --------------------------- | ------------ |
| 2020-10-01 00:00:00 | distributor   | distributor\_cex            | 358172469    |
| 2020-10-01 00:00:00 | distributor   | distributor\_dex            | 238906080    |
| 2020-10-01 00:00:00 | distributor   | distributor\_cex\_satellite | 157460066    |
| 2020-10-01 00:00:00 | distributor   | distributor\_dex\_balancer  | 3563956      |

Since we are getting several different `to_label_subtype` values, that's a good clue to dig in more.

### Expand Dimensions to See Senders and Receivers

Let's expand the results to see which types and subtypes are sending to exchanges.

```sql
SELECT
    from_label_subtype as sender,
    to_label_subtype as receiver,
    round(sum(amount_usd)) as total
FROM
    ethereum.udm_events
WHERE
    to_label_type = 'distributor'
    AND symbol = 'ETH'
    AND contract_address IS NULL
    AND block_timestamp > '2020-10-01'
    AND block_timestamp < '2020-10-02'
    AND to_label_subtype like 'distributor_cex%'
GROUP BY from_label_subtype,to_label_subtype
ORDER BY to_label_subtype, total desc
```

By adding label categories to the "from" side, we're going to return a lot more rows, so let's modify the query to make the results easier to understand:

* look at a single day
* only look at activity to centralized exchanges `to_label_subtype like 'distributor_cex%'`
* round the total amounts for each pair of senders and receivers
* order the results by `to_label_subtype` and amounts descending

| Sender                      | Receiver                    | Total     |
| --------------------------- | --------------------------- | --------- |
| distributor\_cex\_satellite | distributor\_cex            | 158462305 |
| distributor\_cex            | distributor\_cex            | 142227252 |
|                             | distributor\_cex            | 55712865  |
| other\_single\_use          | distributor\_cex            | 1595028   |
| distributor\_dex            | distributor\_cex            | 94677     |
| operator\_miner             | distributor\_cex            | 77774     |
| operator\_mining            | distributor\_cex            | 1424      |
| project\_contract           | distributor\_cex            | 1076      |
| other\_financial            | distributor\_cex            | 68        |
|                             | distributor\_cex\_satellite | 102552982 |
| distributor\_cex            | distributor\_cex\_satellite | 31853513  |
| other\_single\_use          | distributor\_cex\_satellite | 19357401  |
| operator\_miner             | distributor\_cex\_satellite | 1379866   |
| distributor\_cex\_satellite | distributor\_cex\_satellite | 1216738   |
| other\_financial            | distributor\_cex\_satellite | 609015    |
| distributor\_dex            | distributor\_cex\_satellite | 408611    |
| project\_contract           | distributor\_cex\_satellite | 45839     |
| operator\_mining            | distributor\_cex\_satellite | 25567     |
| project\_other              | distributor\_cex\_satellite | 10368     |
| project\_token\_contract    | distributor\_cex\_satellite | 166       |

By we comparing each combination of sender and receiver, we have created an interaction matrix that can be used to categorize transfer activity.

Here are some possible transaction type examples, with caveats below:

| Sender                      | Receiver                    | Transaction Type                       |
| --------------------------- | --------------------------- | -------------------------------------- |
| any non-distributor label   | distributor\_cex\_satellite | Deposit                                |
| distributor\_cex            | any non-distributor label   | Withdrawal                             |
| distributor\_cex\_satellite | distributor\_cex            | Sweep                                  |
| distributor\_cex            | distributor\_cex            | Inter-exchange transfers for liquidity |
| distributor\_cex            | distributor\_cex            | Intra-exchange hot wallet maintenance  |

### Enrich Categories with Label Names

Now, especially with the last two cases, it may not be obvious what is going on until we expose the names of the exchanges involved.

We can do that with the `from_label` and `to_label` fields:

```sql
SELECT
    from_label as sender,
    to_label as receiver,
    round(sum(amount_usd)) as total
FROM
    ethereum.udm_events
WHERE
    to_label_type = 'distributor'
    AND symbol = 'ETH'
    AND contract_address IS NULL
    AND block_timestamp > '2020-10-01'
    AND block_timestamp < '2020-10-02'
    AND to_label_subtype = 'distributor_cex'
    AND from_label_subtype = 'distributor_cex'
GROUP BY from_label,to_label
ORDER BY from_label, total desc
```

There's a lot to dig into here with the labeled results, but this subset of Binance, Coinbase, and Kraken is representative of the typical patterns we see:

| Sender   | Receiver   | Total    |
| -------- | ---------- | -------- |
| binance  | binance    | 46424958 |
| binance  | coinbase   | 3527514  |
| binance  | coinswitch | 157443   |
| binance  | shapeshift | 18380    |
| coinbase | coinbase   | 32781897 |
| kraken   | kraken     | 6590562  |
| kraken   | coinbase   | 384082   |

Notice that:

1. The largest row in each "from" label set for the most part are transfers within the same exchange, which confirms our "intra-exchange wallet maintenance" category above.
2. When we have cross-exchange activity, that could be exchanges providing each other with liquidity, but you would have drill down further into transactions to try to see that.
3. Hot wallets sending to Coinbase are a little more complicated to classify, since, on Ethereum, Coinbase does not use the same satellite wallet architecture as most other exchanges. In other words, these may be withdrawals to Coinbase user wallets, not inter-exchange transfers for liquidity.
