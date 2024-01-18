# Dim Asset Metadata

### Table Schema

A dimension table holding provider specific asset metadata

`crosschain.dim_asset_metadata`

| Field          | Type   | Description                                                    |
| -------------- | ------ | -------------------------------------------------------------- |
| PROVIDER       | STRING | provider of the data                                           |
| ID             | STRING | unique identifier representing the asset                       |
| NAME           | STRING | name of asset                                                  |
| SYMBOL         | STRING | symbol of asset                                                |
| TOKEN\_ADDRESS | STRING | specific address representing the asset in a specific platform |
| PLATFORM       | STRING | platform where this asset has a token address                  |
