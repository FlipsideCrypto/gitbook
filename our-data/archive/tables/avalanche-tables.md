---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Avalanche Tables

Documentation for \`avalanche\` tables can be found [here](https://flipsidecrypto.github.io/avalanche-models/#!/overview).

The public Github repo with Avalanche model source code is [here](https://github.com/FlipsideCrypto/avalanche-models).

Please note, data is in 'lite mode' - meaning, historical data has not yet been backfilled. Please see the `min(block`\_`timestamp)`.&#x20;

Quick Links to Table Docs:

* ``[`fact_event_logs`](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.core\_\_fact\_event\_logs)``
* ``[`fact_transactions`](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.core\_\_fact\_transactions)``
* ``[`fact_blocks`](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.core\_\_fact\_blocks)``
* ``[`fact_traces`](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.core\_\_fact\_traces)``
* &#x20;[`fact_token_transfers`](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.core\_\_fact\_token\_transfers)
* ``[`dim_labels`](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.core\_\_dim\_labels)``
* ``[`ez_avax_transfers`](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.core\_\_ez\_avax\_transfers)``
* ``[`dim_contracts`](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.core\_\_dim\_contracts)``

`Sushi specific tables:`

* [sushi\_\_dim\_dex\_pools](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.sushi\_\_dim\_dex\_pools)
* [sushi\_\_dim\_kashi\_pairs](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.sushi\_\_dim\_kashi\_pairs)
* [sushi\_\_ez\_swaps](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.sushi\_\_ez\_swaps)&#x20;
* [sushi\_\_ez\_borrowing](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.sushi\_\_ez\_borrowing)
* [sushi\_\_ez\_lending](https://flipsidecrypto.github.io/avalanche-models/#!/model/model.avalanche\_models.sushi\_\_ez\_lending)



Note: when working with the `fact_transactions` and `fact_event_logs` tables, you may find it useful to use the [ethereum.public.hex\_to\_int() function](../../hex-to-integer-function.md).
