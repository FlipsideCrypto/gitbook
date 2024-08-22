---
description: >-
  New bridging activity and Dex swaps tables for Flow, improved query speeds for
  Solana CORE, DEFI, and PRICE tables, and enhanced NFT sales data on Magic Eden
  AMM.
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 2024-08-08 | Release Notes

## Highlights

Today, we’re excited to introduce new bridging activity and Dex swaps tables for Flow, making tracking easier and more standardized.&#x20;

**Note that `ez_bridge_transactions` and `ez_swaps` will be deprecated by 9/1.**&#x20;

On Solana, we’ve improved query speeds for CORE, DEFI, and PRICE tables and added complete NFT sales data from Magic Eden AMM to `solana.nft.fact_nft_sales`. Explore these updates and enjoy faster, more comprehensive data!

{% hint style="warning" %}
**Reminder regarding our Solana Jupiter Swaps data.**&#x20;

Starting August 15, the existing solana.defi.fact\_swaps and solana.defi.ez\_dex\_swaps tables will no longer include aggregated Jupiter swaps data. Instead this data can will be stored in two new tables (available now) that better capture Jupiter’s swap transaction structure: solana.defi.fact\_swaps\_jupiter\_inner, solana.defi.fact\_swaps\_jupiter\_summary

* Please update your queries to use the new tables by August 15th.
{% endhint %}

Check out these updates and the rest of the release notes below.

### Flow

**New Tables - Bridging Activity**

Two new views to help make tracking bridge activity easier. We’ve designed these views so that the column names match our standards across other blockchains.

* flow.defi.ez\_bridge\_activity&#x20;
* flow.defi.fact\_bridge\_activity

{% hint style="warning" %}
**Table Deprecation:** _ez\_bridge\_transactions_ is deprecating on 9/1.
{% endhint %}

**New Tables - Dex Swaps**

Two new views to help make tracking swaps activity easier. We’ve designed these views so that the column names match our standards across other blockchains.

* flow.defi.ez\_dex\_swaps&#x20;
* flow.defi.fact\_dex\_swaps

{% hint style="warning" %}
**Table Deprecation:** _ez\_swaps_ is deprecating on 9/1.
{% endhint %}

### Solana

**Updated Tables - Query Speed Improvements**

Tables in the CORE/DEFI/PRICE schema have been updated to significantly improve querying speeds. Queries on these tables now run much more efficiently, and users can expect faster results with less time-outs.

* solana.core
* solana.defi
* solana.price

**Updated Table - NFT Sales**

`fact_nft_sales` now contains complete data for NFT sales performed through the Magic Eden AMM marketplace.

* solana.nft.fact\_nft\_sales

#### 🚨Important Update

With the release of these two new Jupiter swaps tables, the standard solana.defi.fact\_swaps table and solana.defi.ez\_dex\_swaps will no longer contain aggregated Jupiter swaps data. To query Jupiter swaps, please use the two new Jupiter tables instead.

Please update your queries to reference the two new tables by August 15, at which point the standard swaps tables will no longer contain aggregated Jupiter swaps data.

### Useful Resources

Request a smart contract ABI to be decoded:[ https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)

Request a Solana IDL to be decoded:[ https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)

Add labels:[ https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)

\
