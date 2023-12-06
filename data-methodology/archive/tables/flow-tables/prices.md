# Prices



| Column          | Type           | Description                                                                                                                                                                                                                                                     |
| --------------- | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| timestamp       | TIMESTAMP\_NTZ | Timestamp of when the data was recorded from the API or from on-chain data, depending on the source.                                                                                                                                                            |
| token           | TEXT           | Friendly name of the crypto token, e.g. Blocto Token.                                                                                                                                                                                                           |
| symbol          | TEXT           | Short-name symbol for the crypto token, e.g. BLT.                                                                                                                                                                                                               |
| token\_contract | TEXT           | The contract address for a token on the Flow blockchain.                                                                                                                                                                                                        |
| price\_usd      | FLOAT          | Asset price, in USD.                                                                                                                                                                                                                                            |
| source          | TEXT           | Data source for the record in question. E.g. for the prices table, this may be an API or derived from swaps. Stableswap indicates the price was calculated from a swap where one of the assets was a stablecoin, while for a flowswap the other token was Flow. |

{% embed url="https://flipside-flow.netlify.app/#!/model/model.flow_models.core__fact_prices" %}
Full Documentation for Core Prices
{% endembed %}
