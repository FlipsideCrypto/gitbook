---
description: >-
  This update includes EVM chain swaps USD value improvements, new Avalanche
  Dexalot trace data, Ethereum NFT lending support for Arcade XYZ, and new Lava
  staking models.
---

# 2024-08-22 | Release Notes

## Highlights

This release brings updates across multiple blockchains. EVM chain swaps tables now include USD values for native assets, even when one side of the swap is NULL, effective **August 26, 2024**. Avalanche gets a new table for Dexalot's internal contract trace data, and Ethereum's NFT lending tables now support Arcade XYZ. Additionally, Lava introduces two new models to enhance staking and staking rewards tracking, and we’ve added a Farcaster table for Warpcast power users.

{% hint style="warning" %}
**Reminder:** Flow `ez_swaps` and `ez_bridge_transactions` is deprecating on 9/1. \
**Please update your queries to reference the** [**new swaps and bridging tables Flow**](https://docs.flipsidecrypto.xyz/support/release-notes/2024-08-08-release-notes#flow)**.**
{% endhint %}

Check out these updates and the rest of the release notes below.

### All EVM Chains

**Updated Tables - EVM Chain Swaps Tables**

Updates `amount_in_usd` and `amount_out_usd` to have USD values for the native chain's asset, even if the other side of the swap is NULL. Previously, both `amount_in_usd` and `amount_out_usd` were set to NULL if any side of the swap had a NULL USD value. This is put in place to avoid overstating volumes on low-liquidity swaps. **Going live August 26, 2024.**&#x20;

* _**CHAIN**.defi.ez\_dex\_swaps_

### Avalanche

**New Table - Avalanche Subnet - Dexalot**&#x20;

This table contains flattened trace data for internal contract calls on the Dexalot Blockchain. Hex encoded fields can be decoded to integers by using the `utils.udf_hex_to_int()` function.

* _avalanche.dexalot.fact\_traces_

### Ethereum

**Updated Tables - Bridging Activity**

The team updated three NFT lending tables to include Arcade XYZ DeFi protocol curation.

* _ethereum.nft.ez\_lending\_loans_
* _ethereum.nft.ez\_lending\_repayments_
* _ethereum.nft.ez\_lending\_liquidations_

### External (Studio Only)

**New Table - Farcaster Warpcast Power Users**

Represents data associated with power users, based on Warpcast power badges.

* _external.farcaster.fact\_warpcast\_power\_users_

### Lava

**New Tables - Staking**

Two new curated models for both staking and staking rewards. Lava staking is non-standard due to the functionality of staking to providers.

* _lava.gov.fact\_staking_
* _lava.gov.fact\_staking\_rewards_

### Useful Resources

Request a smart contract ABI to be decoded:[ https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)

Request a Solana IDL to be decoded:[ https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)

Add labels:[ https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)\
