---
description: >-
  Flipside launches a new brand identity with major data updates across chains.
  Explore new analytics for Farcaster, Aptos bridges, and improved Solana
  tracking.
---

# 2024-11-14 | Release Notes

## Highlights

We're thrilled to announce a transformative moment at Flipside with the launch of our new brand identity and website experience! This refresh reflects our deepened commitment to fostering blockchain growth through the power of data science and analytics. Our new look embodies our mission of enabling limitless growth for blockchains while continuing to empower the analysts, builders, and users who drive innovation in web3.&#x20;

<figure><img src="../../../.gitbook/assets/1731528003209.jpg" alt="" width="563"><figcaption></figcaption></figure>

> **Take a look at** [**https://flipsidecrypto.xyz**](https://flipsidecrypto.xyz)&#x20;

On the data front, this week brings exciting enhancements across multiple blockchains, with new tables for Farcaster analytics (studio only), improved bridge tracking on Aptos, and enhanced decoded event logs for SEI and Core databases. We've also made significant updates to Solana's Jupiter swaps tracking and governance rewards system, while introducing new mapping capabilities for Flow's EVM addresses.

Check out these updates and the rest of the release notes below.

### Aptos

**New Table** - Streamlined Bridge Activity Tracking

A new convenience table makes analyzing cross-chain bridge activity more intuitive and accessible:

* `aptos.defi.ez_bridge_activity`

### Eclipse

**New Table** - Enhanced Address Labeling

A new dimensional table for comprehensive address labeling:

* `eclipse.core.dim_labels`

### External (Studio Only)

**New Tables -** Extended Farcaster Social Analytics

Two new views enable deeper analysis of social interactions on Farcaster:

* `external.farcaster.fact_blocks`
* `external.farcaster.fact_channel_follows`

### Flow

**New Table** - EVM Address Mapping

A new table bridges the gap between Flow's native and EVM ecosystems:

* `flow.core.dim_address_mapping`
  * Maps Cadence-on-Avalanche (COA) flowEVM addresses to their parent addresses on Flow Mainnet

### SEI

**New Table** - Enhanced Event Log Decoding

New tables provide human-readable format for blockchain events:

* `sei.core_evm.ez_decoded_event_logs`

### Core

**New Table** - Enhanced Event Log Decoding

New tables provide human-readable format for blockchain events:

* `core.core.ez_decoded_event_logs`

### Solana

**Updated Tables** - Jupiter Swaps and Governance Improvements

Enhanced tracking for Jupiter limit orders and streamlined governance rewards identification:

* `solana.defi.fact_swaps_jupiter_summary`
  * Added columns `is_limit_swap` and `limit_requester` to track limit order swaps and initiating addresses
* `solana.gov.fact_rewards_fee`
  * Renamed `vote_pubkey` to `pubkey` for more accurate address identification

{% hint style="info" %}
**Note**: Both columns will remain available until December 3, 2024
{% endhint %}

### Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
