---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Polygon 2.0 Tables

Documentation for \`polygon\` tables can be found [here](https://flipsidecrypto.github.io/polygon-models/#!/overview).

The public Github repo with Polygon 2.0 model source code is [here](https://github.com/FlipsideCrypto/polygon-models).

Please note, data is in 'lite mode' - meaning, historical data has not yet been backfilled. Please see the `min(block`\_`timestamp)`.&#x20;

Quick Links to Table Docs:

* ``[`fact_event_logs`](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.core\_\_fact\_event\_logs)``
* ``[`fact_transactions`](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.core\_\_fact\_transactions)``
* ``[`fact_blocks`](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.core\_\_fact\_blocks)``
* ``[`fact_traces`](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.core\_\_fact\_traces)``
* ``[`fact_token_transfers`](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.core\_\_fact\_token\_transfers)``
* ``[`dim_labels`](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.core\_\_dim\_labels)``
* ``[`ez_matic_transfers`](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.core\_\_ez\_matic\_transfers)``
* ``[`dim_contracts`](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.core\_\_dim\_contracts)``



Polygon sushi tables

* [sushi\_\__dim\_dex\__pools](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.sushi\_\_dim\_dex\_pools)
* [sush\_\__dim\_kashi\_pairs_ ](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.sushi\_\_dim\_kashi\_pairs)__
* __[_sushi\_\_ez\_lending_](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.sushi\_\_ez\_lending)__
* __[_sushi\_\_ez\_borrowing_](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.sushi\_\_ez\_borrowing)__
* __[_sushi\_\_ez\_swaps_](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.sushi\_\_ez\_swaps)__



Note: when working with the `fact_transactions` and `fact_event_logs` tables, you may find it useful to use the [ethereum.public.hex\_to\_int() function](../../hex-to-integer-function.md).\
__
