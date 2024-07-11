---
description: >-
  New and updated tables for Ethereum, Kaia, M1, and Solana. New Olas Network
  schemas added to Crosschain database (studio only).
---

# 2024-06-27 | Release Notes

### Highlights

A ton of new updates and improvements to Ethereum, Kaia (New Chain), and Solana. Plus new devnet data for M1 chain from [Movement Labs](https://movementlabs.xyz/) and Olas Network schemas added to our Crosschain (studio only) database.&#x20;

{% hint style="warning" %}
As a reminder on **July 15th** we’re making an update to the solana.core.fact\_transfers table to include both native and wrapped solana addresses in the mint column. You can learn more about this change on our docs [here](https://docs.flipsidecrypto.xyz/product-special-releases/2024-06-13-solana-native-wrapped-addresses).
{% endhint %}

Check out these updates and the rest of the release notes below.

### [Ethereum](https://flipsidecrypto.github.io/ethereum-models/#!/overview)

**Updated Table**

Added a new refinancing contract from NFTfi v2. This new contract allows users to refinance a loan by closing the existing loan and opening another in the same transaction.

* `ethereum.nft.ez_lending_loans`

### Crosschain (Studio Only)

**New Tables**

These new tables include schemas for olas.network. Learn more about Olas [here](https://olas.network/).

* `crosschain.olas.dim_registry_metadata`
* `crosschain.olas.ez_mech_activity`
* `crosschain.olas.ez_olas_bonding`
* `crosschain.olas.ez_olas_locking`
* `crosschain.olas.ez_olas_staking`
* `crosschain.olas.ez_service_checkpoints`
* `crosschain.olas.ez_service_donations`
* `crosschain.olas.ez_service_evictions`
* `crosschain.olas.ez_service_registrations`
* `crosschain.olas.ez_service_staking`
* `crosschain.olas.ez_unit_registrations`
* `crosschain.olas.fact_mech_activity`
* `crosschain.olas.fact_pol_transfers`
* `crosschain.olas.fact_service_events`

### [Kaia](https://flipsidecrypto.github.io/kaia-models/#!/overview)

**New Tables**

These new tables add decoded event logs.

* `kaia.core.fact_decoded_event_logs`
* `kaia.core.ez_decoded_event_logs`

### M1

**New Tables**

New core tables for the M1 blockchain devnet. These tables match the format of Aptos and are from the M1 devnet. There is no mainnet at this time.

* `m1.core.fact_blocks`
* `m1.core.fact_changes`
* `m1.core.fact_events`
* `m1.core.fact_transactions`
* `m1.core.fact_transactions_block_metadata`
* `m1.core.fact_transactions_state_checkpoint`

### [Solana](https://flipsidecrypto.github.io/solana-models/#!/overview)

**New Tables**

These new tables provide the beginning and ending balances for each account involved in a transaction. Fact\_sol\_balances contains native SOL accounts, and fact\_token\_balances contains information for all token accounts. This table allows for easier analysis into balance changes that occur in transactions, including verifying the balance changes for an account and tracking changes over time.

* `solana.core.fact_token_balances`
* `solana.core.fact_sol_balances`

**Updated Tables**

* `solana.defi.fact_swaps` - This table now contains a more complete record of every individual swap performed on the Raydium dex.
* `solana.defi.ez_swaps` - Analysts no longer have to perform additional joins to get info such as USD amounts or token symbols.

**Reminder Updated Column Data**

The address of native SOL will now be reflected in the 'mint' column. Native SOL is the native token of the Solana blockchain and is used for paying tx fees, staking and participating in governance. [Learn more about this change here](https://docs.flipsidecrypto.xyz/product-special-releases/2024-06-13-solana-native-wrapped-addresses).

* `solana.core.fact_transfers`

#### Useful Resources

Request a smart contract ABI to be decoded:[ https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)

Request a Solana IDL to be decoded:[ https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)

Add labels:[ https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)

\
