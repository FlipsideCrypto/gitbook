# Crosschain Address Tags

### Table Schema

`crosschain.core.address_tags`

Also learn more about tags [here](broken-reference).

| Field       | Type      | Description                                                            |
| ----------- | --------- | ---------------------------------------------------------------------- |
| blockchain  | string    | The name of the blockchain.                                            |
| creator     | string    | The name of the creator of the tag.                                    |
| address     | string    | The address that the tag belongs to. Use this to join to other tables. |
| tag\_name   | string    | The name of the tag or the tag itself.                                 |
| tag\_type   | string    | The type of the tag.                                                   |
| start\_date | timestamp | The starting date that the tag is valid for.                           |
| end\_date   | timestamp | The ending date of the tag's validity.                                 |
