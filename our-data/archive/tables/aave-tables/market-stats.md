---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Market Stats



Market Stats exists within the `aave` schema, as `aave.market_stats`

| **Field**                        | **Type** | Description                                                                                                                                                  |
| -------------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `block_hour`                     | string   | Market stats are aggregated by hour in UTC. `date_trunc(‘hour’,block_timestamp)` for joins on other tables                                                   |
| `lending_pool_add`               | string   | Lending pool contract associated with the AAVE market (used for interacting with on-chain)                                                                   |
| `data_provider`                  | string   | Data Provider contract associated with the AAVE market (used for interacting with on-chain)                                                                  |
| `reserve_name`                   | string   | Name/symbol of the underlying contract (i.e. USDT)                                                                                                           |
| `atoken_address`                 | address  | Address of the atoken the market serves (i.e. aUSDC). Given to suppliers proportional to how much they supply to this market                                 |
| `stable_debt_token_address`      | address  | Address of the stable debt token the market serves. Given to borrowers proportional to how much debt of this type from this market they hold                 |
| `variable_debt_token_address`    | address  | Address of the variable debt token the market serves. Given to borrowers proportional to how much debt of this type from this market they hold               |
| `underlying_contract`            | address  | Address of the underlying contract, i.e. USDC's address                                                                                                      |
| `reserve_price`                  | number   | Price of the underlying token contract                                                                                                                       |
| `atoken_price`                   | number   | Price of the aToken the market uses                                                                                                                          |
| `total_liquidity_token`          | number   | Total liquidity/total supplied. Includes amounts currently out on loans                                                                                      |
| `total_liquidity_usd`            | number   | Total liquidity converted to USD values as of the hour recorded                                                                                              |
| `total_stable_debt_token`        | number   | Total debt out at a stable borrow rate from this market                                                                                                      |
| `total_stable_debt_usd`          | number   | Total Stable Debt converted to USD values as of the hour recorded                                                                                            |
| `total_variable_debt_token`      | number   | Total debt out at a variable borrow rate from this market                                                                                                    |
| `total_variable_debt_usd`        | number   | Total Variable Debt converted to USD values as of the hour recorded                                                                                          |
| `utilization_rate`               | number   | The percentage of the reserve’s total capital which is borrowed at any given time, calculated as total borrows divided by total liquidity                    |
| `supply_rate`                    | number   | The supplier's APY. It depends on the current 'utilization rate', the proportion borrowed from/supplied to the market.                                       |
| `borrow_rate_stable`             | number   | The borrower's stable APY. It depends on the current 'utilization rate', the proportion borrowed from/supplied to the market.                                |
| `borrow_rate_variable`           | number   | The borrower's variable APY. It depends on the current 'utilization rate', the proportion borrowed from/supplied to the market.                              |
| `aave_price`                     | number   | The current price of the AAVE governance token                                                                                                               |
| `aave_version`                   | string   | The version of the AAVE market (can be V1, V2 or AMM for Ethereum)                                                                                           |
| `blockchain`                     | string   | Ethereum or Polygon (presently only Ethereum)                                                                                                                |
| `stkaave_rate_supply`\*          | number   | The APR for liquidity mining distributions. Calculated as pool emissions per second times seconds per year times AAVE price divided by total pool liquidity. |
| `stkaave_rate_variable_borrow`\* | number   | The APR for liquidity mining distributions. Calculated as pool emissions per second times seconds per year times AAVE price divided by total pool liquidity. |

\*AAVE price and total pool liquidity values used are USD equivalents instead of ETH, and therefore some small differences may exist vs. current rates on AAVE v2.

