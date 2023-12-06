# Validator Labels



| Column          | Type | Description                                                                                                                                                                                                                          |
| --------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| node\_id        | TEXT | The address, known on the Flow blockchain as Node ID, of the validator.                                                                                                                                                              |
| validator\_type | TEXT | The role of the node from one of the following options: collection, consensus, execution, verification, access. See the Flow [documentation](https://docs.onflow.org/node-operation/node-roles/) here for more.                      |
| project\_name   | TEXT | The overarching project name, related to the address name. For example, Kraken (vs. Kraken Deposit Wallet for address\_names). For validators, this will be the name only if provided as most validators do not provide such a name. |

{% embed url="https://flipside-flow.netlify.app/#!/model/model.flow_models.core__dim_validator_labels" %}
Full Documentation for Core Validator Labels
{% endembed %}
