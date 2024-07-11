---
description: >-
  New NFT Mint tables for Aptos. Base decoded event logs just got added. And we
  made a suite of upgrades to Ethereum. Plus a new discover page allows you to
  search queries
---

# 2024-03-18 | Release Notes

## Highlights

New NFT Mint tables for Aptos. Base decoded event logs just got added. And we made a suite of upgrades to Ethereum and L2 data for the Ethereum Dencun and Optimism Ecotone updates: new blob sidecar table, new columns in block and transaction tables, and new `tx_fee` calculation for L1 fees.  The full list of updates is below.

Plus, check out the makeover our [Discover](https://flipsidecrypto.xyz/discover/dashboards) page got! Discover queries, ecosystems, and more to help you get started or unstuck in your analysis.

<figure><img src="https://lh7-us.googleusercontent.com/iaRZN0lO2ZqVHenmDn_cRsqa56YjTVskJCIxaTwBXLmD7KP8Sve6vz33AFdu0MWmBTpqyQuBnRiOFGz5fhlOocZpJx5UKkoTY221j2zQHoYeiBb_P1wzx1LPU-No-PMULfWIigMlPWl59qSxrWXy1HU" alt=""><figcaption></figcaption></figure>

### [Aptos](https://flipsidecrypto.github.io/aptos-models/#!/overview)

Analyze Aptos NFT mints with these newly added tables.

**New Tables:**

* _nft.fact\_nft\_mints_
* _nft.ez\_nft\_mints_

### [Base](https://flipsidecrypto.github.io/base-models/#!/overview)

**New Tables:**

Delve into Base decoded event logs with these newly added tables.

* _core.fact\_decoded\_event\_logs_
* _core.ez\_decoded\_event\_logs_

**Updated Tables:**

We updated the `tx_fee` calculation, making our L1 fees data compatible with the Ethereum Dencun and Optimism Ecotone upgrades. &#x20;

* _core.fact\_transactions_

### [Blast](https://flipsidecrypto.github.io/blast-models/#!/overview)

Updated the `tx_fee` calculation, making our L1 fees data compatible with the Ethereum Dencun and Optimism Ecotone upgrades&#x20;

**Updated Tables:**

* _core.fact\_transactions_

### [Ethereum](https://flipsidecrypto.github.io/ethereum-models/#!/overview)

Our Ethereum tables are up to speed with the Dencun upgrade! A new table got added for blob sidecars, and the fact blocks and transactions tables have new columns added.

**New Table:**

* _beacon\_chain.fact\_blob\_sidecars_

**Updated Tables:**

* _core.fact\_blocks_: new columns `excess_blob_gas` and `blob_gas_used`
* _core.fact\_transaction_s: new columns `blob_versioned_hashes`, `max_fee_per_blob_gas`, `blob_gas_used`, `blob_gas_price`
* _beacon\_chain.fact\_blocks_: new columns `blob_kzg_commitments`, `blob_gas_used`, `excess_blob_gas`

### [NEAR](https://flipsidecrypto.github.io/near-models/#!/overview)

We’ve enhanced your ability to analyze NEAR’s DeFi ecosystem with this new table, which maps out the lending platform Burrow (withdrawals, deposits, and collateral actions).

**New Table:**

* _defi.fact\_lending_

### [Optimism](https://flipsidecrypto.github.io/optimism-models/#!/overview)

We updated the `tx_fee` calculation, making our L1 fees data compatible with the Ethereum Dencun and Optimism Ecotone upgrades.&#x20;

**Updated Tables:**

* _core.fact\_transactions_

### [Vertex](https://flipsidecrypto.github.io/arbitrum-models/#!/model/model.arbitrum\_models.vertex\_\_dim\_products)

Delve into DeFi analytics with these newly added Vertex protocol tables.

**New Tables:**

* _arbitrum.vertex.dim\_products_
* _arbitrum.vertex.ez\_clearing\_house\_events_
* _arbitrum.vertex.ez\_liquidations_
* _arbitrum.vertex.ez\_perp\_trades_
* _arbitrum.vertex.ez\_spot\_trades_

### Data Studio Updates for Analysts and Teams

**Available Now:**

#### 📋 [Your Query History](https://flipsidecrypto.xyz/settings/plan)

A new feature in your settings! View your history and usage of query and API seconds, see where your usage accumulates, and how it matches your plan (Free, Builder, or Pro). You can also adjust each query refresh rate directly from this page: [https://flipsidecrypto.xyz/settings/plan](https://flipsidecrypto.xyz/settings/plan) &#x20;

#### 🌐 [Community Query Discovery](https://flipsidecrypto.xyz/discover)

As part of Flipside’s commitment to public good data in web3, any user can discover community SQL queries and dashboards. This makes it super easy to get started, find great analysis, and get inspired to create your own. You can explore and filter 100k+ dashboards, and now also search and discover the 800k+ queries created by our analyst community: [https://flipsidecrypto.xyz/discover](https://flipsidecrypto.xyz/discover) &#x20;

#### 🔐 [Private Queries & Dashboards](https://flipsidecrypto.xyz/pricing)

On the Builder and Pro plans, our new privacy settings let you make your work completely private, or only share it with specific users on your team. Try it out with a Builder or Pro subscription: [https://flipsidecrypto.xyz/pricing](https://flipsidecrypto.xyz/pricing)&#x20;
