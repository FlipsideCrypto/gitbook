# Osmosis Daily Balances

### Table Schema

`osmosis.core.daily_balances`

This table is currently under development and will release in the Velocity App soon. This table only includes balances for addresses that are actively staking or providing liquidity to a liquidity pool. If an address is not doing either of these actions on a given date, it will not be represented in the table on that date.&#x20;

| Field         | Type      | Description                                                |
| ------------- | --------- | ---------------------------------------------------------- |
| date          | timestamp | The day that the balance corresponds to.                   |
| balance\_type | string    | Either "staked" or "liquid."                               |
| address       | string    | The wallet that the balance belongs to.                    |
| currency      | string    | An address that corresponds to the currency in the wallet. |
| decimal       | integer   | Divide "balance" by POW(10, decimal) to get the balance.   |
| balance       | integer   | The amount of currency in the wallet on the given day.     |
