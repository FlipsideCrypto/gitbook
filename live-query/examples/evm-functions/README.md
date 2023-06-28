---
description: High Level Functions for Querying EVM-compatible network
---

# 🧙♂ EVM Functions

EVM functions are custom-built to query EVM-compatible networks and exist as an abstraction over Flipside's API functions. These functions are deployed on specific chain/network schemas under the `livequery` database, for example: `ethereum_mainnet` , `ethereum_goerli`, `polygon_mainnet`, etc. Flipside automatically defaults all queries to the `livequery` database so you do not need to specify the `livequery` db when writing your queries.&#x20;

View the full documentation within Data Studio on available functions and blockchains/networks.

{% hint style="danger" %}
EVM functions require you to associate a node provider with your Flipside Account. See the [Add-Ons section](../../add-ons/) of the documentation for details on adding a node provider to your Flipside Account.
{% endhint %}

### **Latest Contract Event Examples**

The following examples show off how to fetch the latest events/logs for a contract/set of contracts.

`<chain>_<network>.latest_contract_events`

`<chain>_<network>.latest_contract_events_decoded`

{% content-ref url="seaport-real-time-orders.md" %}
[seaport-real-time-orders.md](seaport-real-time-orders.md)
{% endcontent-ref %}

### Balance Examples

The following examples show off how to fetch balances.&#x20;

`<chain>_<network>.latest_token_balance`

`<chain>_<network>.latest_native_balance`

`<chain>_<network>.historical_token_balance`

`<chain>_<network>.historical_native_balance`

{% content-ref url="weth-pool-balances.md" %}
[weth-pool-balances.md](weth-pool-balances.md)
{% endcontent-ref %}
