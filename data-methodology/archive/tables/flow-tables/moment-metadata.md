# Moment Metadata

{% embed url="https://flipside-flow.netlify.app/#!/model/model.flow_models.core__dim_moment_metadata" %}
Full documentation for the Moment Metadata table
{% endembed %}



| Column          | Description                                                                                                                                                                                               |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| nft\_collection | The contract address or ID for the NFT Collection.                                                                                                                                                        |
| nft\_id         | The id of the NFT, usually a number.                                                                                                                                                                      |
| serial\_number  | The serial number for the Moment, such as 25, within the collection.                                                                                                                                      |
| max\_mint\_size | The gross NFTs minted for the batch.                                                                                                                                                                      |
| play\_id        | The numeric ID of the play for the moment. For example, with topshot moment ABC may be a version of Play 123. The play id is 123 and moment metadata is associated with the play, rather than the moment. |
| series\_id      | The numeric ID for the series of moments or plays. This corresponds with the series column found in some metadata tables.                                                                                 |
| series\_name    | The series for this particular set of drops.                                                                                                                                                              |
| set\_id         | The numeric ID for the set. This corresponds with the set name found in some metadata columns.                                                                                                            |
| set\_name       | Name of the set in which the moment was dropped.                                                                                                                                                          |
| edition\_id     | The numeric ID for the edition of moments. This is likely a bundle of moment NFTs within the same type of play, differentiated by some trait like rarity.                                                 |
| tier            | The tiered rarity of the edition.                                                                                                                                                                         |
| metadata        | A JSON object containing moment or play metadata.                                                                                                                                                         |
