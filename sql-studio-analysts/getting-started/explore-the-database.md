---
description: Navigate the Flipside database to easily find the answers you're looking for
---

# 🔎 Explore the database

The Flipside database contains A LOT of data (several trillion rows, the most comprehensive dataset on the market).&#x20;

But don't worry - **it's actually surprisingly easy to find what you need.**&#x20;

## Access data on 26+ protocols&#x20;

In the left menu of your [Studio](https://flipside.new), you'll find a list of all the chains and protocols we have curated data on - Bitcoin, Ethereum, Solana, Polygon and more.

<figure><img src="../../.gitbook/assets/Screenshot 2023-12-05 at 5.02.32 PM.png" alt=""><figcaption></figcaption></figure>

Click any one of those protocols, and you'll find its tables.&#x20;

**Tables** are curated collections of data that make it easy to find the stats you're interested in. For example, if you click on Base, you'll find:



<figure><img src="../../.gitbook/assets/Screenshot 2023-12-05 at 5.06.13 PM.png" alt=""><figcaption></figcaption></figure>

"Core" includes all block/transaction details, while the rest of the tables are designed to include only what's relevant to the sectors they're titled after.&#x20;

## Flipside data standards

Click one of those tables, and you'll find a list of **views**. Each view is a different grouping of data designed to simplify your query results. Below, we'll talk about how to understand these views.

<figure><img src="../../.gitbook/assets/Screenshot 2023-12-05 at 5.10.57 PM.png" alt=""><figcaption></figcaption></figure>

At Flipside, we organize data into 3 main views (based on the Star Schema):

* Fact
* Dim
* EZ

**Fact** views include observations or events, and can be blocks, transactions, mints, swaps, etc. This is great for a summary of what's happening on chain.

**Dim** views cover _entities_ in a block/tx - labels, prices, decimals, tags, etc. This helps add context to on-chain activity.

**EZ** views make it easy to scan and understand what's happening on chain - they're labeled and tagged views of activity and entities.&#x20;

## Ready to try out some queries?

Keep reading to start working with data in the SQL Studio.
