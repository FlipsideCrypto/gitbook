---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Uniswap V3 Tables

**Blockchain:** [Ethereum](https://ethereum.org/en/)

UniswapV3 tables are available in Velocity as the `uniswapv3` schema. These tables are built leveraging Ethereum logs, traces, and contract readings from Flipside's fully archival Ethereum cluster. Each table covers a core V3 concept.&#x20;

The public Github repo with Uniswap V3 model source code is [here](https://github.com/FlipsideCrypto/sql\_models/tree/main/models/uniswapv3/eth\_mainnet).

### Tables

![](<../../../../.gitbook/assets/Uniswap V3 - Copy of uniswapv3 silver\_tables.png>)

{% content-ref url="pools.md" %}
[pools.md](pools.md)
{% endcontent-ref %}

{% content-ref url="pool-stats.md" %}
[pool-stats.md](pool-stats.md)
{% endcontent-ref %}

{% content-ref url="positions.md" %}
[positions.md](positions.md)
{% endcontent-ref %}

{% content-ref url="lp-actions.md" %}
[lp-actions.md](lp-actions.md)
{% endcontent-ref %}

{% content-ref url="../polygon-tables/position-collected-fees.md" %}
[position-collected-fees.md](../polygon-tables/position-collected-fees.md)
{% endcontent-ref %}

{% content-ref url="../polygon-tables/swaps.md" %}
[swaps.md](../polygon-tables/swaps.md)
{% endcontent-ref %}



### **General Table Notes:**

* The suffix `_adjusted` on a column name indicates it was decimal adjusted by its underlying token pair.
* `price_1_0`is equivalent to `price` and indicates the price of token1 in terms of token0
* `price_0_1`is equivalent to `1/price` and indicates the price of token0 in terms of token1

