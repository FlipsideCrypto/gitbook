# Account App

The account app table  contains all apps within the Algorand Ecosystem and an app ID and other information about the app, such as whether it's currently active.

## Table Schema

| Field        | Type    | Description                                                                                  |
| ------------ | ------- | -------------------------------------------------------------------------------------------- |
| `ADDRESS`    | text    | Wallet address tied to app                                                                   |
| `APP_ID`     | number  | App ID, tied to index in the app table                                                       |
| `APP_CLOSED` | boolean | Has this app been deleted?                                                                   |
| `CLOSED_AT`  | number  | block that the account\_app was last removed from the account                                |
| `CREATED_AT` | number  | block that the app was added to an account                                                   |
| `APP_INFO`   | array   | Is the app currently deleted from the account? if not it will have json about current status |
