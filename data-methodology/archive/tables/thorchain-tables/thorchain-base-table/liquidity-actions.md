---
description: >-
  The actions the liquidity providers do in the THORChain, with the amount in
  RUNE/Asset
---

# Liquidity Actions

## Table Schema <a href="#table-schema" id="table-schema"></a>

**table name:** `thorchain.liquidity_actions`

| Field                  | Type      | Description                                                                                                                                                                                                                     |
| ---------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `BLOCK_ID`             | number    | The block number that this block was recorded                                                                                                                                                                                   |
| `BLOCK_TIMESTAMP`      | timestamp | The timestamp this block was recorded                                                                                                                                                                                           |
| `EVENT_ID`             | text      | The flipside internal unique id                                                                                                                                                                                                 |
| `TX_ID`                | text      | The unique transaction id for the this swap                                                                                                                                                                                     |
| `LP_ACTION`            | text      | The direction of the liquidity providers, add or remove the liquidity                                                                                                                                                           |
| `POOL_NAME`            | text      | The asset name                                                                                                                                                                                                                  |
| `FROM_ADDRESS`         | address   | The address of the liquidity provider                                                                                                                                                                                           |
| `TO_ADDRESS`           | address   | The address of the pool                                                                                                                                                                                                         |
| `RUNE_AMOUNT`          | number    | How many RUNE liquidity added/removed                                                                                                                                                                                           |
| `RUNE_AMOUNT_USD`      | number    | How many RUNE liquidity added/removed in USD                                                                                                                                                                                    |
| `ASSET_AMOUNT`         | number    | How many Asset liquidity added/removed                                                                                                                                                                                          |
| `ASSET_AMOUNT_USD`     | number    | How many Asset liquidity added/removed in USD                                                                                                                                                                                   |
| `STAKE_UNITS`          | number    | Stake units are a way of representing how much liquidity an address has in the pool. THORChain converts the raw amounts you are depositing / withdrawing into `stake_units` to represent what % of the pool you own a claim to. |
| `ASSET_TX_ID`          | text      | The transaction id for adding/removing the asset                                                                                                                                                                                |
| `ASSET_ADDRESS`        | address   | The asset address of the liquidity provider                                                                                                                                                                                     |
| `ASSET_BLOCKCHAIN`     | text      | The blockchain the asset is in                                                                                                                                                                                                  |
| `IL_PROTECTION`        | number    | The total impermanent loss protection paid for this pool on this day                                                                                                                                                            |
| `IL_PROTECTION_USD`    | number    | The total impermanent loss protection paid  in USD for this pool on this day                                                                                                                                                    |
| `UNSTAKE_ASYMMETRY`    | number    | Only exists in unstake, or removing the liquidity                                                                                                                                                                               |
| `UNSTAKE_BASIS_POINTS` | number    | The basis points for unstaking, or removing the liquidity                                                                                                                                                                       |
