# Contract Labels



| Column           | Type | Description                                                                                                                                                                                                                                                                                 |
| ---------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| event\_contract  | TEXT | The contract called for this event. This is equivalent to the Contract column on Flowscan and is a concatenation of the contract's account address and primary name.                                                                                                                        |
| contract\_name   | TEXT | The primary name of the contract, derived from the full contract address.                                                                                                                                                                                                                   |
| account\_address | TEXT | The account address in 0x form that instantiated the contract called in the event. Note, on the Flow blockchain the account and the contract are separate as the account may have created more than one contract, in rare instances, such as the following FLOW address 0x8624b52f9ddcd04a. |

{% embed url="https://flipside-flow.netlify.app/#!/model/model.flow_models.core__dim_contract_labels" %}
Full Documentation for Core Contract Labels
{% endembed %}
