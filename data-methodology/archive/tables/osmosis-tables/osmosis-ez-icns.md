# Osmosis EZ ICNS

### Table Schema

`osmosis.core.ez_icns`

| Field         | Type      | Description                                                     |
| ------------- | --------- | --------------------------------------------------------------- |
| blockchain    | string    | Blockchain the label is applicable for.                         |
| creator       | string    | Name of the label creator.                                      |
| address       | string    | Address unique to an individual wallet, validator, or token.    |
| label         | string    | The ICNS name associated with the address.                      |
| project\_name | string    | The name of the project the name was purchased from.            |
| start\_date   | timestamp | Date the ICNS name first applies to the wallet.                 |
| end\_date     | timestamp | Date the ICNS name expires or no longer represents the wallet.  |
