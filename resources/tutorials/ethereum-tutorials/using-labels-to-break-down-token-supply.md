---
description: >-
  In this guide, we're going to look at how supply is distributed across the
  network for particular ERC20 tokens using Flipside's base label system.
---

# Using Labels to Break Down Token Supply

In this guide, we're going to look at how supply is distributed across the network for particular ERC20 tokens.

The question we want to answer is: at any given point in time, who is holding this token?

And because we look at groups of accounts using Flipside's base labels, you can get an aggregate view of the entire network.

Our balances tables are also designed to make answering this question very straightforward:

1. Each date in the table represents a snapshot of "current balances" for all holders, so you only have to query one day to see total supply
2. Labels are already injected into the addresses, so all you have to do is group by existing fields in the table

Let's look at the basic query:

```sql
SELECT
  symbol,
  label_type,
  round(sum(amount_usd)) as total
FROM
  ethereum.erc20_balances
WHERE
  balance_date = '2020-10-31'
  AND amount_usd > 0
  AND contract_address = '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48'
GROUP BY 1,2
ORDER BY symbol, total DESC
```

We want to select:

* `label_type` for the pre-generated Flipside label category,&#x20;
* `symbol` for context in our results set
* a rounded sum of the total usd-converted balance on this first pass, so we can get a sense for the relative sizes of each group

Which returns:

| Symbol | Label Type  | Total      |
| ------ | ----------- | ---------- |
| USDC   |             | 1537642229 |
| USDC   | distributor | 871468974  |
| USDC   | project     | 395089998  |
| USDC   | other       | 5313082    |

Notice that the `label_type` is missing for our largest group. Flipside's base label set identifies accounts like exchanges, foundations, and operators, but not basic user accounts. We leave those accounts to more context- and behavior- specific classification later, so here, a large "unlabeled" set is expected.

In a later guide, we will cover how to start to break down the unlabeled user set into "Top Holders" and "Smaller Wallets", which is useful to analyzing token flows.

If you want to drill down further, you can repeat the query above with `label_subtype` instead of `label_type`:

```sql
SELECT
  symbol,
  label_subtype,
  round(sum(amount_usd)) as total
FROM
  ethereum.erc20_balances
WHERE
  balance_date = '2020-10-31'
  AND amount_usd > 0
  AND contract_address = '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48'
GROUP BY 1,2,3
ORDER BY symbol, total DESC
```

Which returns:

| Symbol | Label Sub Type              | Total      |
| ------ | --------------------------- | ---------- |
| USDC   |                             | 1537642229 |
| USDC   | distributor\_dex            | 544272742  |
| USDC   | project\_token\_contract    | 341612731  |
| USDC   | distributor\_cex            | 228821492  |
| USDC   | distributor\_cex\_satellite | 57614929   |
| USDC   | project\_contract           | 51637001   |
| USDC   | distributor\_dex\_balancer  | 40759810   |
| USDC   | other\_financial            | 4192633    |
| USDC   | project\_other              | 1840265    |
| USDC   | other\_misc                 | 919132     |
| USDC   | other\_single\_use          | 201317     |

As you become more familiar with Flipside's labeling system, you may decide to group certain labels together to express different relationships.

For example, if you wanted to distinguish between centralized and decentralized exchange wallets, you could combine satellite and hot wallet addresses.

Here's a straightforward pattern for playing with combinations in your query using a `CASE` statement:

```sql
SELECT
  symbol,
  CASE
  WHEN label_subtype LIKE 'distributor_cex%' THEN 'centralized exchanges'
  WHEN label_subtype LIKE 'distributor_dex%' THEN 'decentralized exchanges'
  WHEN label_type IS NULL THEN 'user accounts'
  ELSE 'other' END as label,
  round(sum(amount_usd)) as total
FROM
  ethereum.erc20_balances
WHERE
  balance_date = '2020-10-31'
  AND amount_usd > 0
  AND contract_address = '0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48'
GROUP BY 1,2,3
ORDER BY symbol, total DESC
```

Here we:

* distinguished between centralized and decentralized exchanges at the subtype level
* grouped unlabeled address together as "user accounts", which is probably an over-simplification
* grouped all other labels together as "other", which you probably would want to tease apart in your next query, given how large the result set is

Results:

You can see how you can continue to slice and dice the supply based on label types and subtypes and eventually other tags in our system to tease out groups of accounts.

| Symbol | Label Type              | Total      |
| ------ | ----------------------- | ---------- |
| USDC   | user accounts           | 1537642229 |
| USDC   | decentralized exchanges | 585032552  |
| USDC   | other                   | 400403080  |
| USDC   | centralized exchanges   | 286436421  |

The useful feature of Flipside's base label set is that it allows you to characterize the entire network at once. The alternative is zooming in on a specific set of addresses, which can sometimes limit your ability to put your results in a broader context.
