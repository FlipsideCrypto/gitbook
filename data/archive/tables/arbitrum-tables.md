---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Arbitrum Tables

Documentation for \`arbitrum\` tables can be found [here](https://flipsidecrypto.github.io/arbitrum-models/#!/overview).

The public Github repo with Arbitrum model source code is [here](https://github.com/FlipsideCrypto/arbitrum-models).

Please note, data is in 'lite mode' - meaning, historical data has not yet been backfilled. Please see the `min(block`\_`timestamp)`.&#x20;

Quick Links to Table Docs:

* [`fact_event_logs`](https://flipsidecrypto.github.io/arbitrum-models/#!/model/model.arbitrum\_models.core\_\_fact\_event\_logs)
* [`fact_transactions`](https://flipsidecrypto.github.io/arbitrum-models/#!/model/model.arbitrum\_models.core\_\_fact\_transactions)
* [`fact_blocks`](https://flipsidecrypto.github.io/arbitrum-models/#!/model/model.arbitrum\_models.core\_\_fact\_blocks)
* [`fact_traces`](https://flipsidecrypto.github.io/arbitrum-models/#!/model/model.arbitrum\_models.core\_\_fact\_traces)
* [`fact_token_transfers`](https://flipsidecrypto.github.io/arbitrum-models/#!/model/model.arbitrum\_models.core\_\_fact\_token\_transfers)
* [`dim_labels`](https://flipsidecrypto.github.io/arbitrum-models/#!/model/model.arbitrum\_models.core\_\_dim\_labels)
* [`ez_eth_transfers`](https://flipsidecrypto.github.io/arbitrum-models/#!/model/model.arbitrum\_models.core\_\_ez\_eth\_transfers)
* [`dim_contracts`](https://flipsidecrypto.github.io/arbitrum-models/#!/model/model.arbitrum\_models.core\_\_dim\_contracts)

Arbitrum sushi tables

* [sushi\_\__dim\_dex\__pools](https://cloud.getdbt.com/accounts/1258/runs/68372630/docs/#!/model/model.arbitrum\_models.sushi\_\_dim\_dex\_pools)
* [sush\_\__dim\_kashi\_pairs_ ](https://cloud.getdbt.com/accounts/1258/runs/68372630/docs/#!/model/model.arbitrum\_models.sushi\_\_dim\_kashi\_pairs)
* [_sushi\_\_ez\_swaps_](https://cloud.getdbt.com/accounts/1258/runs/68372630/docs/#!/model/model.arbitrum\_models.sushi\_\_ez\_swaps)
* [_sushi\_\_ez\_borrowing_](https://flipsidecrypto.github.io/arbitrum-models/#!/model/model.arbitrum\_models.sushi\_\_ez\_borrowing)
* [_sushi\_\_ez\_lending_](https://flipsidecrypto.github.io/arbitrum-models/#!/model/model.arbitrum\_models.sushi\_\_ez\_lending)



Note: when working with the `fact_transactions` and `fact_event_logs` tables, you may find it useful to use the [ethereum.public.hex\_to\_int() function](../../../resources/hex-to-integer-function.md).
