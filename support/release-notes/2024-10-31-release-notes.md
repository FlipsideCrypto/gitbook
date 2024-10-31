---
description: >-
  The release adds 4 new SEI Pricing tables, and unused Osmosis tables get ready
  for deprecation.
---

# 2024-10-31 | Release Notes

## Highlights

This week the team has released 4 new SEI pricing tables to track prices hourly on the SEI network.&#x20;

{% hint style="warning" %}
**Please Note** several Osmosis tables will be deprecated on November 5th, 2024. This is due to lack of usage.
{% endhint %}

Check out these updates and the rest of the release notes below.

### SEI

New Tables - SEI Pricing Tables

New tables allow you to track prices hourly on the SEI network.

* `sei.price.dim_asset_metadata`
* `sei.price.ez_asset_metadata`
* `sei.price.ez_prices_hourly`
* `sei.price.fact_prices_ohlc_hourly`

### Deprecating Osmosis Tables - November 5th, 2024

The following tables will be deprecated on November 5th, 2024. These are being removed due to limited usage.&#x20;

* `osmosis.core.ez_icns`
* `osmosis.core.fact_daily_balances`
* `osmosis.core.fact_token_day`
* `osmosis.defi.fact_liquidity_provider_actions`
* `osmosis.defi.fact_locked_liquidity_actions`
* `osmosis.defi.fact_pool_hour`
* `osmosis.defi.fact_superfluid_staking`
* `osmosis.gov.dim_liquidity_pools`
* `osmosis.gov.fact_staking`
* `osmosis.gov.fact_staking_rewards`
* `osmosis.gov.fact_validators`
* `osmosis.gov.fact_validator_commission`
* `osmosis.mars.ez_liquidity_provider_actions`
* `osmosis.mars.ez_pool_fee_day`
* `osmosis.mars.ez_pool_hour`
* `osmosis.mars.ez_redbank_actions`
* `osmosis.mars.ez_redbank_balance_changes`
* `osmosis.mars.ez_redbank_reward_claims`
* `osmosis.mars.ez_redbank_reward_distributions`
* `osmosis.mars.ez_swaps`
* `osmosis.mars.ez_token_day`

### Useful Resources

* Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)
* Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)
* Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)
