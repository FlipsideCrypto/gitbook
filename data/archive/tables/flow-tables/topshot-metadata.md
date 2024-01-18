# TopShot Metadata



| Column                          | Type           | Description                                                                                                                                       |
| ------------------------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| nft\_id                         | TEXT           | The id of the NFT, usually a number.                                                                                                              |
| nft\_collection                 | TEXT           | The contract address or ID for the NFT Collection.                                                                                                |
| nbatopshot\_id                  | TEXT           | The ID used by NBA TopShot. This can be pasted into the URL https://nbatopshot.com/moment/{nbatopshot\_id} to view the moment on the marketplace. |
| serial\_number                  | NUMBER         | The serial number for the Moment, such as 25, within the collection.                                                                              |
| total\_circulation              | NUMBER         | The total number of moments minted for the particular play.                                                                                       |
| moment\_description             | TEXT           | Long-form description of the play, from NBA TopShot.                                                                                              |
| player                          | TEXT           | The player who is the focus of the moment.                                                                                                        |
| team                            | TEXT           | The team that the player from the moment is on, at the time of the moment.                                                                        |
| season                          | TEXT           | The season during which the moment occurred.                                                                                                      |
| play\_category                  | TEXT           | The broad category of play that is shown in the moment.                                                                                           |
| play\_type                      | TEXT           | The more granular (than play\_category) type of play that is shown in the moment.                                                                 |
| moment\_date                    | TIMESTAMP\_NTZ | When the moment occurred.                                                                                                                         |
| set\_name                       | TEXT           | Name of the set in which the moment was dropped.                                                                                                  |
| set\_series\_number             | NUMBER         | The series number for this particular set of drops, within the set\_name.                                                                         |
| video\_urls                     | ARRAY          | An array containing links to the moments.                                                                                                         |
| moment\_stats\_full             | OBJECT         | A dictionary of the full moment stats.                                                                                                            |
| player\_stats\_game             | OBJECT         | The statline for the player in the Moment, from the game highlighted.                                                                             |
| player\_stats\_season\_to\_date | OBJECT         | The season stats for the player as of the game featured in the moment.                                                                            |

{% embed url="https://flipside-flow.netlify.app/#!/model/model.flow_models.silver__nft_topshot_metadata" %}
Full Documentation for TopShot Metadata
{% endembed %}
