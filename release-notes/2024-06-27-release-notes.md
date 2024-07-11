---
description: >-
  Major upgrade to Thorchain database impacted by Midgard indexer upgrade
  (v2.22.3), updated NFT tables for Ethereum and NEAR, and the final CORE tables
  have been added to Kaia.
---

# 2024-07-11 | Release Notes

### Highlights

Lots of powerful updates on some of our most popular blockchains. All Kaia CORE tables are now available, Ethereum `ez_nft_sales` table has been revamped so you can query v1 or v2 of Sudoswap NFT marketplace, NEAR `ez_nft_sales` table has been updated with new NFT royalties data, and tons of new Thorchain due to the  Midgard indexer upgrade (v2.22.3).&#x20;

{% hint style="warning" %}
As a reminder on **July 15th** we’re making an update to the solana.core.fact\_transfers table to include both native and wrapped Solana addresses in the mint column. You can learn more about this change on our docs [here](https://docs.flipsidecrypto.xyz/product-special-releases/2024-06-13-solana-native-wrapped-addresses).
{% endhint %}

Check out these updates and the rest of the release notes below.

### [Ethereum](https://flipsidecrypto.github.io/ethereum-models/#!/overview)

**Updated Table**

Sudoswap NFT sales data has been revamped! You can now query the v1 and v2 sales using this filter: platform\_exchange\_version in ('sudoswap v1', 'sudoswap v2')

* `etherum.nft.ez_nft_sales`

### [Kaia](https://flipsidecrypto.github.io/kaia-models/#!/overview)

**New Tables**

All core tables have now been added to our [Kaia](https://klaytn.foundation/say-hello-to-kaia/) database. The following tables have been added this week.

* `kaia.core.ez_native_transfers`
* `kaia.core.dim_contract_abis`
* `kaia.core.dim_contracts`
* `kaia.core.ez_token_transfers`
* `kaia.core.fact_token_transfers`

### [NEAR](https://flipsidecrypto.github.io/near-models/#!/overview)

**Updated Table**

Royalties have been added for those NFT marketplaces that adhere to NEP standards (Mintbase and Paras), along with a detailed breakdown of their platform fees to simplify future calculations.

* `near.nft.ez_nft_sales`

### [Thorchain](https://flipsidecrypto.github.io/thorchain-models/#!/overview/thorchain\_models)

With the Midgard indexer upgrade (v2.22.3) we’ve added 5 new tables and updated our existing fact tables with some columns becoming deprecated. Loan open and repayment events, and streaming swap details are now filled with NULL values in the updated tables. Transaction type has been added to a number of add, bond, outbound, refund, reserve, and swap events, and Thorname change events will have enhanced memo info.

**New Tables**

* `thorchain.defi.fact_scheduled_outbound_events`
* `thorchain.defi.fact_send_messages`
* `thorchain.defi.trade_account_deposit_events`
* `thorchain.defi.trade_account_withdraw_events`
* `thorchain.price.fact_rune_price`

**Updated Tables**

* `thorchain.defi.fact_add_events`
* `thorchain.defi.fact_bond_actions`
* `thorchain.defi.fact_bond_events`
* `thorchain.defi.fact_loan_open_events`
* `thorchain.defi.fact_loan_repayment_events`
* `thorchain.defi.fact_outbound_events`
* `thorchain.defi.fact_refund_events`
* `thorchain.defi.fact_reserve_events`
* `thorchain.defi.fact_streamling_swap_details_events`
* `thorchain.defi.fact_swaps`
* `thorchain.defi.fact_swaps_events`
* `thorchain.defi.thorname_change_events`
* `thorchain.defi.withdraw_events`

#### Useful Resources

Request a smart contract ABI to be decoded:[ https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)

Request a Solana IDL to be decoded:[ https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)

Add labels:[ https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)

\
