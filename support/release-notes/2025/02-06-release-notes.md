---
description: >-
  Major EVM standardization, new Ronin blockchain data available in studio, and
  enhanced Solana data coverage.
---

# 2025-02-06 | Release Notes

## Highlights

This release brings transformative updates across our data ecosystem. We're rolling out a major standardization initiative for our EVM databases, launching core Ronin blockchain tables, and enhancing our Solana data coverage.

{% hint style="info" %}
Starting February 10th, we're introducing significant improvements to standardize data access across all EVM chains. This update brings new columns for better transaction tracking, enhanced trace data visibility, and simplified topic parsing. Key improvements include new boolean status flags, detailed error tracking, and flattened topic columns replacing complex array structures. As part of this standardization, some legacy columns will be deprecated beginning March 2025. [Learn more here](../../product-special-releases/2025/02-06-evm-blockchain-standardization/).
{% endhint %}

#### New Blockchain data available - Ronin!&#x20;

We're excited to announce new Ronin data with `core`, `NFT`. and `price` tracking tables. Built by the team behind Axie Infinity, Ronin is the benchmark for mass adoption in gaming. Now you can query Ronin tables on Flipside and discover your sharpest insights about Onchain Gaming. &#x20;

Lastly you'll see new a new AI 🤖 feature on dashboards and studio. More AI stuff coming soon ![:eyes:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/apple-medium/1f440.png)!

Check out these updates and the rest of the release notes below.

### Solana

**Updated Tables**

Two key Solana tables have been enhanced to provide deeper insights into transaction ordering and NFT marketplace dynamics:

* _solana.core.fact\_transactions_
  * Added `TX_INDEX` column to precisely track transaction ordering within blocks, enabling more accurate sequence analysis
* _solana.nft.fact\_nft\_sales_
  * Added `CURRENCY_ADDRESS` column to capture multi-token payment support across NFT marketplaces
  * Enhanced coverage of NFT sales data, particularly for Magic Eden and Tensor marketplaces
  * This update reflects the evolving NFT marketplace landscape where platforms increasingly support payments in tokens beyond SOL

### Ronin

**New Tables**

We're thrilled to announce the release of Ronin chain in studio, introducing a comprehensive set of core, NFT and pricing tables that unlock new analytical possibilities:

Core Infrastructure:

* _ronin.core.fact\_event\_logs_
* _ronin.core.fact\_traces_
* _ronin.core.fact\_transactions_
* _ronin.core.fact\_blocks_
* _ronin.core.dim\_contract\_abis_
* _ronin.core.dim\_contracts_
* _ronin.core.ez\_decoded\_event\_logs_
* _ronin.core.ez\_token\_transfers_
* _ronin.core.ez\_native\_transfers_

NFT Activity:

* _ronin.nft.ez\_nft\_transfers_

Price Tracking:

* _ronin.price.ez\_prices\_hourly_
* _ronin.price.ez\_asset\_metadata_
* _ronin.price.dim\_asset\_metadata_
* _ronin.price.fact\_prices\_ohlc\_hourly_

### Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
