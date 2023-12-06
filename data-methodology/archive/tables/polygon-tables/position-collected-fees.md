---
description: uniswapv3.position_collected_fees
---

# Position Collected Fees

{% hint style="warning" %}
These are legacy Polygon tables. See [Polygon 2.0](../polygon-2.0-tables.md) for up-to-date Polygon models.
{% endhint %}

Fees collected by a Liquidity Provider (LP) on their position. In V3 fees are accrued and collected in each token within the pair. When a pool `Collect` event is emitted a new record is appended to this table. If a `Burn` event is emitted in the same transaction as the `Collect` event the amount of the burn is subtracted from the `Collect` event token1 and token0 amounts. This allows us to arrive solely at the swap fees collected.

| Field                         | Type      | Description                                                                                |
| ----------------------------- | --------- | ------------------------------------------------------------------------------------------ |
| `block_id`                    | number    | The block number that this Collect was recorded                                            |
| `block_timestamp`             | timestamp | The block timestamp that this Collect was recorded                                         |
| `tx_id`                       | text      | The transaction that contained this Collect                                                |
| `blockchain`                  | text      | The blockchain this Collect occurred on (Ethereum, will support L2s here shortly)          |
| `pool_address`                | address   | The contract address of the pool                                                           |
| `pool_name`                   | text      | The name of the Pool (format = "{token0}-{token1} {tick\_spacing} {fee}")                  |
| `liquidity_provider`          | address   | The address of the liquidity provider                                                      |
| `nf_position_manager_address` | address   | The address of the peripheral nf position manager contract, if used.                       |
| `nf_token_id`                 | number    | The id of the NFT associated with the liquidity position                                   |
| `amount0_adjusted`            | number    | The amount of token0 collected for swap fees                                               |
| `amount1_adjusted`            | number    | The amount of token1 collected for swap fees                                               |
| `amount0_adjusted_usd`        | number    | The amount of token0 collected for swap fees, converted to USD                             |
| `amount1_adjusted_usd`        | number    | The amount of token1 collected for swap fees, converted to USD                             |
| `tick_lower`                  | number    | Lower tick of the liquidity position                                                       |
| `tick_upper`                  | number    | Upper tick of the liquidity position                                                       |
| `price_lower`                 | number    | Lower bound of the liquidity position represented as token 1 per token 0                   |
| `price_upper`                 | number    | Upper bound of the liquidity position represented as token 1 per token 0                   |
| `price_lower_usd`             | number    | Lower bound of the liquidity position represented as token 1 per token 0, converted to USD |
| `price_upper_usd`             | number    | Upper bound of the liquidity position represented as token 1 per token 0, converted to USD |







