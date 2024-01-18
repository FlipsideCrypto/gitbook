---
description: Joining industry standards with innovative, user-first architectures
---

# Data Modeling Approach

### Our Data Modeling Approach

If it happens on-chain, we've got it for 26+ blockchains and protocols.&#x20;

At a high level for a blockchain you'll see 3 - 5 schemas:&#x20;

* Core
* DeFi
* Gov
* NFT
* Price&#x20;

and some custom curations for some large protocols like AAVE.&#x20;

The goal is to align ecosystems to a consistent pattern, e.g., `<chain>.<core>.fact_transactions`

<figure><img src="../../.gitbook/assets/Screenshot 2023-10-26 at 4.38.47 PM.png" alt=""><figcaption></figcaption></figure>

The [STAR schema](https://en.wikipedia.org/wiki/Star\_schema) classifies tables as either **dimension** or **fact** tables.

### **Fact tables**

_**Fact tables**_ store observations or events, and can be blocks, transactions, transfers, logs, etc.&#x20;

A transfer transaction would have facts like the transaction hash, the token being transferred, and the amount. It would not have the _reason_ a transfer is occurring, e.g., that the transfer is actually part of a trade. But it would have the recipient address, which contains clues (it may be a liquidity pool address, for example).&#x20;

### Dimension tables

_**Dimension ("dim") tables**_ describe entities — the things you analyze.&#x20;

Entities can include labels, prices, decimals, tags, etc. The liquidity pool the swap uses involves smart contracts with dimensions like the platform (e.g., Uniswap), the fee the pool charges (e.g., 0.3%), and details about the tokens in the pool (e.g., AAVE and ETH).&#x20;

The key here is that:

* _**Facts**_ support summarization ("what is the amount of ETH transferred to the pool address in this transaction?")
* _**Dimensions**_ support filtering and grouping ("Which pool address is which DEX platform?")

### EZ tables

We also create new **curated** tables we call "_**EZ".**_

* _**EZ**_ combine Facts and Dimensions to make _easy_ to filter and aggregate tables for common insights ("What is the Estimated USD Volume of swaps involving Wrapped Ether across Uniswap v3 vs Curve over the last 30 days?")

```sql
SELECT 
     platform,
     sum(amount_in_usd) as usd_volume
FROM ethereum.defi.ez_dex_swaps 
WHERE platform IN ('uniswap-v3', 'curve')
     -- Wrapped Ether
 AND (token_in = '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2'
     OR 
     token_out = '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2'
     )
 AND block_timestamp >= current_date - 30
GROUP BY platform
ORDER BY usd_volume DESC;
```
