---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Terra Tables

## Background of Terra

**Blockchain:** [Terra](https://www.terra.money/).&#x20;

Terra is a Proof of stake chain and can also be used as a Smart contract platform. Terra protocol aims to create a stable priced currency by adopting an elastic monetary policy. Terra is supported by a basket of fiat-pegged, seigniorage share style stable coins which are algorithmically stabilized by its native crypto asset, Luna.&#x20;

## Terra Tables

The Terra table schemas build on the concepts laid out in [Flipside's event data model](broken-reference). Terra tables are available in Velocity as the `terra` schema. The tables are built based on the terra message, transactions and transition information.&#x20;

At Flipside database, for Terra, there are two types of tables, one is the Raw Tables and the other one is the Terra Base Tables, clicking the following link to see more details about the tables.&#x20;

The public Github repo with Terra model source code is [here](https://github.com/FlipsideCrypto/sql\_models/tree/main/models/terra).

### Terra Raw Tables:

{% content-ref url="terra-raw-tables/blocks.md" %}
[blocks.md](terra-raw-tables/blocks.md)
{% endcontent-ref %}

{% content-ref url="terra-raw-tables/msgs.md" %}
[msgs.md](terra-raw-tables/msgs.md)
{% endcontent-ref %}

{% content-ref url="terra-raw-tables/msg_events.md" %}
[msg\_events.md](terra-raw-tables/msg\_events.md)
{% endcontent-ref %}

{% content-ref url="terra-raw-tables/transactions.md" %}
[transactions.md](terra-raw-tables/transactions.md)
{% endcontent-ref %}

{% content-ref url="terra-raw-tables/transitions.md" %}
[transitions.md](terra-raw-tables/transitions.md)
{% endcontent-ref %}

### Terra Base Tables:

{% content-ref url="terra-base-tables/labels.md" %}
[labels.md](terra-base-tables/labels.md)
{% endcontent-ref %}

{% content-ref url="terra-base-tables/oracle-prices.md" %}
[oracle-prices.md](terra-base-tables/oracle-prices.md)
{% endcontent-ref %}

{% content-ref url="terra-base-tables/tax-rate.md" %}
[tax-rate.md](terra-base-tables/tax-rate.md)
{% endcontent-ref %}

{% content-ref url="terra-base-tables/daily-balances.md" %}
[daily-balances.md](terra-base-tables/daily-balances.md)
{% endcontent-ref %}

{% content-ref url="terra-base-tables/swap.md" %}
[swap.md](terra-base-tables/swap.md)
{% endcontent-ref %}

{% content-ref url="terra-base-tables/staking.md" %}
[staking.md](terra-base-tables/staking.md)
{% endcontent-ref %}

{% content-ref url="terra-base-tables/rewards.md" %}
[rewards.md](terra-base-tables/rewards.md)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}







## **General Table Notes**

### **Platform (how are other assets represented)**

* All assets on-chain are typically represented as an object with a denomination and an amount to differentiate between different assets

### **Precision (decimals)**

* 0.000001 (10^6)

### **Fees**

* Fees can be paid in any Terra currency (Luna, TerraSDT, TerraKRW etc)
* We can get fees in the transaction payload

### **Events**

* Events or (Msgs) in Tendermint terms can easily be captured when we query for txs in a block
* Events are emitted from a "module"



