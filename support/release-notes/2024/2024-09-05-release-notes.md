---
description: >-
  The latest update adds Flow EVM core models, new Lava pricing tables, and
  Thorchain Rune Pool event tracking tables.
---

# 2024-09-05 | Release Notes

## Highlights

This release introduces new Flow EVM core models for the Crescendo network upgrade, including blocks, transactions, and event logs tables. Lava now has four new pricing tables aligned with our standard blockchain pricing models. Thorchain gains two new tables to track deposit and withdrawal events for the Rune Pool product. These updates enhance data coverage and analysis across Flow, Lava, and Thorchain networks.

Check out these updates and the rest of the release notes below.

### Flow

**New Tables - Flow’s Crescendo Network Upgrade**

New core models supporting EVM on Flow with Flow's Crescendo network upgrade.

* flow.core\_evm.fact\_blocks
* flow.core\_evm.fact\_transactions
* flow.core\_evm.fact\_event\_logs

### Lava

**New Table - Pricing Tables**

Four new pricing tables for Lava were released. These new tables follow our standard pricing models for most blockchains.&#x20;

* lava.price.ez\_asset\_metadata
* lava.price.fact\_prices\_ohlc\_hourly
* lava.price.ez\_prices\_hourly
* lava.price.dim\_asset\_metadata

### Thorchain

**New Tables - Pool Events**

Two new tables to track deposit and withdrawal events for Rune Pool product.

* thorchain.defi.fact\_rune\_pool\_deposit\_events
* thorchain.defi.fact\_rune\_pool\_withdraw\_events

### Useful Resources

Request a smart contract ABI to be decoded:[ https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)

Request a Solana IDL to be decoded:[ https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)

Add labels:[ https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)\
