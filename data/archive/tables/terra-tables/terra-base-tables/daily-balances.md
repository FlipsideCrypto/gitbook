# Daily Balances

Daily Balance shows the balance amount for each address. The label information can be found at [(see Labels section for details)](../../../../flipside-data/labels/).&#x20;

## Table Schema

**table name:** `terra.daily_balances`

| Field                   | Type    | Description                                                                                        |
| ----------------------- | ------- | -------------------------------------------------------------------------------------------------- |
| `DATE`                  | date    | The date time for this balance record                                                              |
| `ADDRESS`               | address | The balance address                                                                                |
| `ADDRESS_LABEL_TYPE`    | text    | [(see Labels section for details)](../../../../flipside-data/labels/)                              |
| `ADDRESS_LABEL_SUBTYPE` | text    | [(see Labels section for details)](../../../../flipside-data/labels/)                              |
| `ADDRESS_LABEL`         | text    | [(see Labels section for details)](../../../../flipside-data/labels/)                              |
| `ADDRESS_NAME`          | text    | [(see Labels section for details)](../../../../flipside-data/labels/)                              |
| `BALANCE`               | number  | The amount of the balance                                                                          |
| `BALANCE_USD`           | number  | The amount of the balance in USD, it is calculated by the hourly price multiple the balance amount |
| `BALANCE_TYPE`          | text    | The balance type                                                                                   |
| `CURRENCY`              | text    | The balance currency                                                                               |
