# App

The app table is contains a current list of all the apps with their app\_id and current status.

## Table Schema

| Field             | Type    | Description                                 |
| ----------------- | ------- | ------------------------------------------- |
| `APP_ID`          | number  | App ID                                      |
| `CREATOR_ADDRESS` | text    | wallet creator account address              |
| `APP_CLOSED`      | boolean | whether or not the app is currently deleted |
| `CLOSED_AT`       | number  | block that the app was deleted              |
| `CREATED_AT`      | number  | block that the app was created              |
| `PARAMS`          | array   |                                             |

