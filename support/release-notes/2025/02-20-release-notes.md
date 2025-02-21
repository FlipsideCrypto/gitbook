---
description: >-
  This week we released enhanced label support for Ronin & Ink, comprehensive
  price tracking for Stellar, and the full suite of Monad testnet data.
---

# 2025-02-20 | Release Notes

## Highlights

This week we released enhanced label support for Ronin & Ink, and comprehensive price tracking for Stellar.

#### New Testnet Blockchain data available - Monad!

We're excited to announce new Monad testnet data with `blocks`, `transactions`_,_ `event_logs`_,_ `traces`_,_ and `contracts` tables. Start querying this data now in the [studio](https://flipsidecrypto.xyz/studio).

Check out these updates and the rest of the release notes below.

### Ronin & Ink

**New Tables** - Enhanced Label Support

New dimensional tables for labels have been added to both Ronin and Ink chains, enabling more sophisticated data categorization and analysis:

* _core.dim\_labels_

### Stellar

**New Tables** - Comprehensive Price Tracking

Standard pricing tables have been introduced for Stellar, following our established pricing model framework:

* _price.ez\_prices\_hourly_
* _price.ez\_asset\_metadata_
* _price.dim\_asset\_metadata_
* _price.fact\_prices\_ohlc\_hourly_

**New Table** - Network Metrics

A new table for tracking core network metrics has been added:

* _stats.EZ\_CORE\_METRICS\_HOURLY_

### Monad

**New Tables** - Testnet Launch Support

Supporting the launch of the new Monad chain, we've added a complete set of testnet tables for comprehensive blockchain data analysis:

* _testnet.fact\_blocks_
* _testnet.fact\_transactions_
* _testnet.fact\_event\_logs_
* _testnet.fact\_traces_
* _testnet.dim\_contracts_

### Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
