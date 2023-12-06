# Osmosis Dim Prices

### Table Schema

`osmosis.core.dim_prices`

Three different sources are used to create this prices table. Coingecko, Coinmarketcap, and the swaps table. When using prices from the swaps table, please note that prices calculated during hours with low transaction volumes and / or a low number of swaps may be incorrect.&#x20;

| Field         | Type      | Description                                                                                  |
| ------------- | --------- | -------------------------------------------------------------------------------------------- |
| recorded\_at  | timestamp | The day and hour that the price was recorded.                                                |
| symbol        | string    | The short-hand, symbolic notation for the currency. This is what shows up on price tickers.  |
| price         | number    | The fiat cost of the asset at this point in time in USD.                                     |
| total\_supply | number    | The supply of the currency in circulation.                                                   |
| volume\_24h   | number    | The amount in USD of the currency that has been traded in a 24 hour period.                  |
| provider      | string    | The source the price was pulled from.                                                        |
