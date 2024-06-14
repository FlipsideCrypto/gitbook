---
description: >-
  New data from Kaia, 9 new Farcaster tables, tons of new core tables for SEI,
  and new dex swap tables for Solana.
---

# 2024-06-14 | Release Notes

### Highlights

This week we added data for a new partner – check out the new Kaia tables in the studio. You can also now query many new Sei core tables that provide the new Sei V2 (EVM) data. Social data from Farcaster is now available, plus upgrades to Solana tables.

{% hint style="warning" %}
On **July 15th, 2024** we’re making an update to the `solana.core.fact_transfers` table to include both native and wrapped solana addresses in the mint column. If you’re querying this data _you will need to update your query_ to include both addresses. You can learn more about this change on our docs [here](https://docs.flipsidecrypto.xyz/product-special-releases/2024-06-13-solana-native-wrapped-addresses).
{% endhint %}

Check out these updates and the rest of the release notes below.

### External (Data Studio Only)

**New Tables:**

Social data from Farcaster is now available in our external database. Analyze casts activity, users and other activity on the social platform.&#x20;

* external.farcaster.dim\_fids
* external.farcaster.dim\_fnames
* external.farcaster.fact\_casts
* external.farcaster.fact\_links
* external.farcaster.fact\_reactions
* external.farcaster.fact\_signers
* external.farcaster.fact\_storage
* external.farcaster.fact\_user\_data
* external.farcaster.fact\_verifications
* external.farcaster.dim\_profile\_with\_addresses

### Kaia

**New Data:**

This week we added the EVM chain, [Kaia](https://klaytn.foundation/say-hello-to-kaia/), to our list of ever growing blockchains. We’re launching with 5 core tables which will include 90 days of data.

* kaia.core.fact\_transactions
* kaia.core.fact\_blocks
* kaia.core.dim\_labels
* kaia.core.fact\_event\_logs
* kaia.core.fact\_traces

### SEI

**New Tables:**

Tons of new core tables for sei launched this week to help analysts query the EVM specific data that is not available on the cosmos/ibc side of the chain.

* sei.core\_evm.fact\_blocks
* sei.core\_evm.fact\_event\_logs
* sei.core\_evm.fact\_traces
* sei.core\_evm.fact\_transactions
* sei.core\_evm.dim\_contracts
* sei.core\_evm.fact\_token\_transfers
* sei.core\_evm.ez\_token\_transfers
* sei.core\_evm.ez\_native\_transfers

### [Solana](https://flipsidecrypto.github.io/solana-models/#!/overview)

**New Tables:**

These tables now contain a more complete record of every individual swap performed on the Raydium dex and now users do not have to do additional joins to get info such as USD amounts or token symbols.

* solana.defi.fact\_swaps
* solana.defi.ez\_swaps

**Updated Column Data:**

The address of native SOL will now be reflected in the 'mint' column. Native SOL is the native token of the Solana blockchain and is used for paying tx fees, staking and participating in governance. [Learn more about this change here](https://docs.flipsidecrypto.xyz/product-special-releases/2024-06-13-solana-native-wrapped-addresses).

* solana.core.fact\_transfers

#### Useful Resources

Request a smart contract ABI to be decoded:[ https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)

Request a Solana IDL to be decoded:[ https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)

Add labels:[ https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
