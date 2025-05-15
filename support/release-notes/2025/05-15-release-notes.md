---
description: >-
  Introducing UnifAi schema in the crosschain database, Uniswap v4 integration
  in Ethereum DeFi tables, and improvements across Solana, Ethereum, and NEAR.
---

# 2025-05-15 | Release Notes

This release introduces a new schema for UnifAi in our Crosschain database, Uniswap v4 integration in Ethereum DeFi tables, and important data improvements across Solana, Ethereum, and NEAR.&#x20;

## Highlights

* **New UnifAi Schema**: Introducing crosschain.unifai schema with dedicated tables for tracking crosschain swaps and purchases.
* **Uniswap v4 Integration**: Enhanced Ethereum DeFi tables now include Uniswap v4.
* **NEAR Bridge Improvements**: Added bridge activity tracking with Omni bridge contracts as Omni bridge is replacing Rainbow as NEAR's primary bridge protocol.
* **Solana Transaction Enhancements**: Improved transaction ordering and expanded DEX coverage.



## Blockchain Updates

### UnifAi

Introducing a new schema in the Crosschain database for UnifAi, containing tables for tracking swap and purchase transactions across multiple chains:

* `crosschain.unifai.fact_purchases`
* `crosschain.unifai.fact_swap`

### Solana

**Improved Balance Tracking** — these tables now include a `tx_index` field to accurately track transaction ordering.

* `solana.core.fact_sol_balances`
* `solana.core.fact_token_balances`

**Enhanced DEX Coverage** — updated with comprehensive Saber swap data and new support for Meteora bonding program swaps.

* `solana.core.fact_swaps`
* `solana.defi.ez_dex_swaps`

### Ethereum

**Uniswap v4 Integration** — these DeFi tables now include Uniswap v4&#x20;

* `ethereum.defi.ez_dex_swaps`
* `ethereum.defi.dim_dex_liquidity_pools`

### NEAR

**Updated Tables** — Omni bridge contracts have been mapped and added to the bridge activity tables as Omni bridge is replacing Rainbow bridge as NEAR's primary bridge protocol.

**Bridge Activity Tracking**

* `near.defi.fact_bridge_activity`
* `near.defi.ez_bridge_activity`



## Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
