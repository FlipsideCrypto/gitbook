---
description: Query external APIs, combine with Flipside data, directly in SQL
---

# LiveQuery

**LiveQuery enables you to query any API directly within a Flipside SQL Query, from nodes to your favorite crypto data providers.**&#x20;

{% embed url="https://www.loom.com/share/da2957d686804f8ca4e1dac4c5688411?sid=57459c86-f36d-41a2-9d3b-60c37ef1b9d4" %}

This gives you the power to remix data and generate unique insights beyond Flipside's curated data sets as well as leverage real-time updates directly from blockchain nodes.

```sql
SELECT * FROM table(ethereum_mainnet.tf_latest_contract_events_decoded(<address>))
```

If you're already writing SQL at Flipside you already have access to the power of LiveQuery.

## Examples

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Seaport: Real-time Orders</strong></td><td>Retrieve the latest Seaport Orders directly from an Ethereum Node.</td><td></td><td><a href="examples/evm-functions/seaport-real-time-orders.md">seaport-real-time-orders.md</a></td></tr><tr><td><strong>WETH Pool Balances</strong></td><td>Retrieve the real-time WETH balance for the top WETH pools by volume over the past 1 week. </td><td></td><td><a href="examples/evm-functions/weth-pool-balances.md">weth-pool-balances.md</a></td></tr><tr><td><strong>Query TheGraph</strong></td><td>Retrieve the TVL for the top 500 UniswapV3 Pools on Polygon using LiveQuery and TheGraph</td><td></td><td><a href="examples/evm-functions/general-evm-node-queries.md">general-evm-node-queries.md</a></td></tr></tbody></table>

Check out more examples here:

{% content-ref url="examples/" %}
[examples](examples/)
{% endcontent-ref %}

## Add-On Setup Guides

{% hint style="info" %}
Add-Ons provide a secure means of incorporating your API keys for third-party data sources like blockchain nodes or cryptocurrency data APIs. This functionality enables you to run and share your queries while ensuring your API secrets remain undisclosed to other users.
{% endhint %}

{% content-ref url="add-ons/quicknode-setup-guide.md" %}
[quicknode-setup-guide.md](add-ons/quicknode-setup-guide.md)
{% endcontent-ref %}

We're excited to announce that additional third-party cryptocurrency data add-ons are on the horizon! Until then, explore our detailed, [step-by-step examples](examples/) **or** [link your QuickNode account](add-ons/quicknode-setup-guide.md) to use LiveQuery for querying blockchain nodes.

{% hint style="danger" %}
Note if you publish a dashboard that contains LiveQuery-powered queries users that refresh your dashboard will trigger queries against the Add-ons you have integrated.
{% endhint %}
