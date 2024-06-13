---
description: >-
  Launching July 15th, 2024 - The address of native SOL or wrapped SOL will now
  be reflected in the 'mint' column. This change can impact query results.
---

# 2024-06-13 | Solana native and wrapped addresses

## Solana fact\_transfers mint column updated

On July 15th, 2024 the mint column in the `solana.core.fact_transfers` table will be updated to reflect the difference between native SOL and wrapped SOL (wSOL). Currently there is no way to distinguish between the two in our transfers table.&#x20;

**Why are we making this change:**

We're making this update to enable users to analyze and differentiate between SOL and wSOL. Differentiating between the two enables analysts to conduct more accurate analyses for transaction patterns and usage trends of wrapped versus native assets.

{% hint style="info" %}
Table names and columns will stay the same and will only impact user querying the mint column in `solana.core.fact_transfers`.&#x20;
{% endhint %}

**What will happen if I don't do anything?**

If you have a query referencing the native SOL address in the `fact_transfers` table you may see a decrease in your results.

**How do I account for this change?**

To get full scope of volume, users will have to add in `So11111111111111111111111111111111111111111` to their queries. Here is an example:

```sql
// CURRENT QUERY
SELECT *
FROM solana.core.fact_transfers
WHERE mint = 'So11111111111111111111111111111111111111112'
AND block_timestamp >= CURRENT_DATE - 1
LIMIT 100 
```

```sql
// UPDATE TO 
SELECT *
FROM solana.core.fact_transfers
WHERE mint IN ('So11111111111111111111111111111111111111112','So11111111111111111111111111111111111111111')
AND block_timestamp >= CURRENT_DATE - 1
LIMIT 100 
```

**Useful Details:**

Native SOL is the native token of the Solana blockchain and is used for paying tx fees, staking and participating in governance. Wrapped SOL (wSOL) is a SPL token that represents SOL, and is used to interact with a majority of dApps which do not directly support native SOL.

* Native SOL Address: `So11111111111111111111111111111111111111111`
* Wrapped wSOL Address: `So11111111111111111111111111111111111111112`
  * You can read more about wSOL [here](https://docs.meteora.ag/getting-started/what-is-wrapped-sol) and [here](https://station.jup.ag/guides/general/wrapped-sol)
