---
description: >-
  Major updates to NFT tables across all EVM Chains, the launch of Berachain
  (Testnet) data, dedicated Jupiter Dex Swap tables and a new Dashboard builder
  in Flipside Studio.
---

# 2024-07-25 | Release Notes

## Highlights

Today we’re launching in beta our new Flipside studio dashboard builder. With this launch there are tons of new features to help you build, customize and share your Flipside dashboards. Check out all the updates here.&#x20;

In addition we have new tables across Aptos, Ethereum and Solana, and now for a limited time you can query Bearachain testnet data.

{% hint style="warning" %}
**Important update regarding our Solana Jupiter Swaps data.**&#x20;

Starting August 15, the existing solana.defi.fact\_swaps and solana.defi.ez\_dex\_swaps tables will no longer include aggregated Jupiter swaps data. Instead this data can will be stored in two new tables (available now) that better capture Jupiter’s swap transaction structure: solana.defi.fact\_swaps\_jupiter\_inner, solana.defi.fact\_swaps\_jupiter\_summary

* Please update your queries to use the new tables by August 15th.
{% endhint %}

Check out these updates and the rest of the release notes below.

### New Dashboard Builder in Flipside Studio

Redefine data storytelling with the new builder and take your first step to create richer, more interactive narratives. The team launched a ton of new features to make building, customizing and sharing your dashboards so much easier. [Learn more in our docs here.](https://docs.flipsidecrypto.xyz/data/data-products/data-studio-sql-analysts/studio-in-depth/dashboard-v2-beta)

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdoKfjG8usgcTR8LEWsceOeu6T2XmFAU7RPWguyWBy6DFDWaMsjiu1ODDx6SlcAjwK72-EoujumYczVcdZFjx__-_UsqzWD6saM5xaFNL1fSkLFmKYtHFH5PoOmca8uYFS7iSbi9hG_XrOVOjM2g39unmxX?key=3xYmas5blN4HVZOi0ZySqA" alt=""><figcaption></figcaption></figure>

### Aptos

**New Tables**

Two new tables to allow you to easily analyze dex activity on Aptos

* aptos.defi.fact\_dex\_swaps
* aptos.defi.ez\_dex\_swaps

### Berachain (Testnet)

**New Tables**

Berachain public testnet is live, and you can now query the testnet data in these new tables

* berachain.testnet.fact\_blocks&#x20;
* berachain.testnet.fact\_event\_logs
* berachain.testnet.fact\_traces
* berachain.testnet.fact\_transactions

### Ethereum

**New Tables**

With these two new NFT tables you can query how much profit MEV searchers make when making arbitrage NFT transactions, and see which NFTs and marketplaces are involved in the arbitrage transactions.

* ethereum.nft.ez\_mev\_arbitrage
* ethereum.nft.fact\_mev\_arbitrage\_events

### EVM Chains

**Updated Tables for Ethereum, Polygon, Arbitrum, Optimism, Base, Avalanche, and BSC**

You can now query NFT sales data on Element marketplace across all EVM chains.

* \[chain].nft.ez\_nft\_sales

### External / Polymarket (Studio Only)

**New Table**

Map on-chain data to Polymarket metadata: human readable questions, tokens, and descriptions.

* external.polymarket.dim\_markets

### Solana

**New Tables**

Two new Jupiter swap tables have been added to the Solana database. Users can now perform more accurate analysis into swaps. With comprehensive data for Jupiter as well as coverage for top DEX programs, these tables can be used to better evaluate swap activity and avoid issues in double-counting values.&#x20;

* solana.defi.fact\_swaps\_jupiter\_inner
* solana.defi.fact\_swaps\_jupiter\_summary

#### 🚨Important Update

With the release of these two new Jupiter swaps tables, the standard solana.defi.fact\_swaps table and solana.defi.ez\_dex\_swaps will no longer contain aggregated Jupiter swaps data. To query Jupiter swaps, please use the two new Jupiter tables instead.

Please update your queries to reference the two new tables by August 15, at which point the standard swaps tables will no longer contain aggregated Jupiter swaps data.

### Useful Resources

Request a smart contract ABI to be decoded:[ https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)

Request a Solana IDL to be decoded:[ https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)

Add labels:[ https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)

\
