---
description: >-
  Ring in the holidays with new DeFi tables on Aleo, enhanced bridge tracking on
  Blast, streamlined NEAR analytics, and THORChain affiliate fee monitoring. 🎄
---

# 2024-12-24 | Release Notes

## Highlights

As we wrap up 2024, we're excited to bring you some holiday gifts in the form of new data! This festive release introduces new tables across multiple chains, including Aleo's DeFi tables, expanded bridge tracking on Blast, and a more intuitive NEAR table schema. We're also spreading some holiday cheer with THORChain affiliate fee tracking.

{% hint style="warning" %}
**Important Update for NEAR Users**: Two tables are being phased out in favor of our new streamlined `core.ez_actions` table. Please migrate your queries by January 30, 2025, to ensure a smooth transition into the new year.
{% endhint %}

Let's unwrap these updates and see what's inside! 🎁

### Aleo

**New Tables** - DeFi Platform Support

Bringing some holiday magic to Aleo with our first set of DeFi tables, supporting Arcane Finance:

* _aleo.core.dim\_token\_registrations_
  * Contains metadata for user-created tokens across DeFi platforms
* _aleo.defi.fact\_swaps_
  * Curated data for token swap transactions
* _aleo.defi.fact\_liquidity\_pool\_actions_
  * Tracks deposits and withdrawals into liquidity pools

### Blast

**New Table** - Enhanced Bridge Tracking

* _blast.defi.ez\_bridge\_activity_
  * Comprehensive tracking of outbound bridge activity
  * Coverage for seven of the top bridge protocols

### NEAR

**New Table** - Simplified Analytics

* _near.core.ez\_actions_
  * Our gift to NEAR analysts: a more intuitive way to analyze transaction data
  * Combines transaction, receipt, and action data at the action level
  * Features decoded FunctionCall data where possible
  * Eliminates the need for complex joins in many queries

**Deprecated Tables** - Retiring January 30, 2025

The following tables are being phased out in favor of `core.ez_actions`:

* _near.core.fact\_actions\_events_
* _near.core.fact\_actions\_events\_function\_call_

Please update your queries to use the new table by January 30, 2025.

### THORChain

**New Table** - Affiliate Fee Tracking

* _thorchain.defi.fact\_affiliate\_fee\_events_
  * Track affiliate fees deducted from transactions
  * Supports fees paid in $RUNE or preferred assets specified via THORName

### Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)

Happy Holidays from the Flipside team! 🎄✨
