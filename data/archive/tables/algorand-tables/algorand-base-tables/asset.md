# Asset

The asset table is contains a current list of all the assets with their asset\_id, current status and other info.

## Table Schema

| Field             | Type    | Description                                   |
| ----------------- | ------- | --------------------------------------------- |
| `ASSET_ID`        | number  | Asset ID                                      |
| `CREATOR_ADDRESS` | text    | Address of the asset creator                  |
| `TOTAL_SUPPLY`    | number  | Total supply of the asset                     |
| `ASSET_NAME`      | text    | Name of the asset                             |
| `ASSET_URL`       | text    | The url to the asset website                  |
| `DECIMALS`        | number  | Number of decimals this asset has             |
| `ASSET_DELETED`   | boolean | whether or not the asset is currently deleted |
| `CLOSED_AT`       | number  | block that the asset was closed               |
| `CREATED_AT`      | number  | block that the asset was created              |
