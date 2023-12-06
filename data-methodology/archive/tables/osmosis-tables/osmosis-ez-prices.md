# Osmosis EZ Prices

### Table Schema

`osmosis.core.ez_prices`

An to use table for finding a token's price for a given hour. The table takes the Dim\_Prices table and reduce it down to only one record per hour per token. The table also brings in the token address for easy joining to other tables that contain the address and not the token symbol.

| Field          | Type      | Description                                                                                  |
| -------------- | --------- | -------------------------------------------------------------------------------------------- |
| recorded\_hour | timestamp | The hour the price is valid for                                                              |
| symbol         | string    | The short-hand, symbolic notation for the currency. This is what shows up on price tickers.  |
| currency       | string    | An address that corresponds to the currency in the wallet.                                   |
| price          | number    | The fiat cost of the asset at this point in time in USD.                                     |
|                |           |                                                                                              |
