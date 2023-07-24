---
description: High Level Functions for Querying EVM-compatible network
---

# 🧙♂ EVM Functions

EVM functions are custom-built to query EVM-compatible networks and exist as an abstraction over Flipside's API functions. These functions are deployed on specific chain/network schemas under the `livequery` database, for example: `ethereum_mainnet` , `ethereum_goerli`, `polygon_mainnet`, etc. Flipside automatically defaults all queries to the `livequery` database so you do not need to specify the `livequery` db when writing your queries.&#x20;

View the full documentation within Data Studio on available functions and blockchains/networks.

{% hint style="danger" %}
EVM functions require you to associate a node provider with your Flipside Account. See the [Add-Ons section](../../add-ons/) of the documentation for details on adding a node provider to your Flipside Account.
{% endhint %}

{% hint style="warning" %}
Two types of EVM Functions Exist:

1. Table Functions, prefixed with `tf_`&#x20;
   1. These functions must be wrapped in a `table()` function&#x20;
2. User Defined functions, prefixed with `udf_`
   1. These functions are used in a select statement
{% endhint %}

## Table Functions

### **Contract Event Examples**

The following examples show off how to fetch the latest events/logs for a contract/set of contracts. Available event functions include:&#x20;

* `<chain>_<network>.tf_latest_contract_events`
* `<chain>_<network>.tf_latest_contract_events_decoded`
* `<chain>_<network>.tf_all_contract_events`
* `<chain>_<network>.tf_all_contract_events_decoded`

{% content-ref url="seaport-real-time-orders.md" %}
[seaport-real-time-orders.md](seaport-real-time-orders.md)
{% endcontent-ref %}

### Balance Examples

The following examples show off how to fetch balances. Available balance functions include:&#x20;

* `<chain>_<network>.tf_latest_token_balance`
* `<chain>_<network>.tf_latest_native_balance`
* `<chain>_<network>.tf_historical_token_balance`
* `<chain>_<network>.tf_historical_native_balance`

{% content-ref url="weth-pool-balances.md" %}
[weth-pool-balances.md](weth-pool-balances.md)
{% endcontent-ref %}

## UDF Primitives

These functions are a set of UDFs (user defined functions) designed to make interacting with EVM nodes as easy as possible in Snowflake SQL. They are more dynamic than the EVM table functions because they allow you to call any JSON RPC methods supported by our partners. However, this flexibility comes with a tradeoff - the data returned from these calls will be in a much more raw format. In most cases, you will likely need apply some sort of decoding. The functions in our `utils` schema are designed to help with these types of decoding and transformations. &#x20;

Due to the need to apply decoding and transformations, these functions are mainly recommend for more advanced users that are comfortable working with data from EVM nodes. Available functions include:

* `<chain>_<network>.udf_rpc`
* `<chain>_<network>.udf_rpc_eth_call`
* `<chain>_<network>.udf_rpc_eth_get_logs`
* `<chain>_<network>.udf_rpc_eth_get_balance`
* `<chain>_<network>.udf_get_token_balance`

### Generic RPC Call Examples

{% content-ref url="general-evm-node-queries.md" %}
[general-evm-node-queries.md](general-evm-node-queries.md)
{% endcontent-ref %}
