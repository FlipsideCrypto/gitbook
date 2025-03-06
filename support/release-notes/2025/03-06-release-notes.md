---
description: >-
  Introducing a new contract events table for Stellar, enhanced intent data for
  NEAR, and important deprecation notices for NFT mint tables on Ethereum and
  Polygon.
---

# 2025-03-06 | Release Notes

## Highlights

This week we're expanding our Stellar data coverage with a new table for transaction and smart contract events. NEAR users will find enhanced intent data with comprehensive token labeling and price information. Please note important deprecation notices for NFT mint tables on Ethereum and Polygon, as well as NEAR's NFT series metadata table.

Check out these updates and the rest of the release notes below.

### Stellar

**New Table** - Transaction and Smart Contract Events

A new table provides detailed event-level data for transactions and smart contracts on Stellar:

* _stellar.core.fact\_contract\_events_

### NEAR

**New Table** - Enhanced Intent Data with Token Labels

A significant enhancement to the existing fact\_intents table that includes comprehensive labeling for native NEAR tokens and bridged tokens, complete with price data where available:

* _near.defi.ez\_intents_

**Deprecated Table** - NFT Series Metadata

The following table is deprecated and will be removed by the end of March 2025:

* _near.defi.dim\_nft\_series\_metadata_

This table relied on an API from Pagoda which has shut down. Access will be removed by the end of the month.

### Ethereum & Polygon

**Deprecated Tables** - NFT Mint Tracking

The following tables are deprecated and will be removed by March 10, 2025:

* _ethereum.nft.ez\_nft\_mints_
* _polygon.nft.ez\_nft\_mints_

Mint prices in these tables may not be accurate. Users should use the `nft_transfers` table to filter for nft mint transactions instead.

### Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
