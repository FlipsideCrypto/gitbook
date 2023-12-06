# Account Asset

The account asset table is contains a current list of all the address that hold the existing assets on the algorand network.

## Table Schema

| field                | Type    | Description                                            |
| -------------------- | ------- | ------------------------------------------------------ |
| `ADDRESS`            | text    | Wallet Address that is holding the asset               |
| `ASSET_ID`           | number  | Asset ID, same as index identifier in asset table      |
| `ASSET_NAME`         | text    | Name of the asset                                      |
| `AMOUNT`             | number  | Amount of asset the wallet currently holds             |
| `ASSET_ADDED_AT`     | number  | Block that the asset was added to an account           |
| `ASSET_LAST_REMOVED` | number  | block that the asset was last removed from the account |
| `ASSET_CLOSED`       | boolean | whether or not the asset is currently deleted          |
| `FROZEN`             | boolean | whether or not the holding is frozen.                  |
