# Fact Hourly Prices

### Table Schema

A fact table holding provider asset prices

`crosschain.fact_hourly_prices`

| Field          | Type      | Description                              |
| -------------- | --------- | ---------------------------------------- |
| PROVIDER       | STRING    | provider of the data                     |
| ID             | STRING    | unique identifier representing the asset |
| RECORDED\_HOUR | TIMESTAMP | opening hour of price data               |
| OPEN           | FLOAT     | open price of asset for hour             |
| HIGH           | FLOAT     | high price of asset for hour             |
| LOW            | FLOAT     | low price of asset for hour              |
| COSE           | FLOAT     | close price of asset for hour            |
