# Osmosis Dim Liquidity Pools

### Table Schema

`osmosis.core.dim_liquidity_pools`

| Field      | Type    | Description                                                        |
| ---------- | ------- | ------------------------------------------------------------------ |
| blockchain | string  | In this table, always Osmosis. Used to join to cross-chain tables. |
| module     | string  | Module used to create liquidity pool                               |
| pool\_id   | integer | Identifier for the pool within the module                          |
| assets     | object  | List of 2 or more asset addresses belonging to the pool            |

