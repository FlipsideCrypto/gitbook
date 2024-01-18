---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# BSC Tables

Documentation for \`bsc\` tables can be found [`here`](https://flipsidecrypto.github.io/bsc-models/#!/overview).

The public Github repo with BSC model source code is [here](https://github.com/FlipsideCrypto/bsc-models).

Please note, data is in 'lite mode' - meaning, historical data has not yet been backfilled. Please see the `min(block`\_`timestamp)`.&#x20;

Quick Links to Table Docs:

* [`fact_event_logs`](https://flipsidecrypto.github.io/bsc-models/#!/model/model.bsc\_models.core\_\_fact\_event\_logs)
* [`fact_transactions`](https://flipsidecrypto.github.io/bsc-models/#!/model/model.bsc\_models.core\_\_fact\_transactions)
* [`fact_blocks`](https://flipsidecrypto.github.io/bsc-models/#!/model/model.bsc\_models.core\_\_fact\_blocks)
* [`fact_traces`](https://flipsidecrypto.github.io/bsc-models/#!/model/model.bsc\_models.core\_\_fact\_traces)
* [`fact_token_transfers`](https://flipsidecrypto.github.io/bsc-models/#!/model/model.bsc\_models.core\_\_fact\_token\_transfers)
* [`dim_labels`](https://flipsidecrypto.github.io/bsc-models/#!/model/model.bsc\_models.core\_\_dim\_labels)
* [`ez_bnb_transfers`](https://flipsidecrypto.github.io/bsc-models/#!/model/model.bsc\_models.core\_\_ez\_bnb\_transfers)

`Sushi specific tables:`

* [`dim_dex_pools`](https://flipsidecrypto.github.io/bsc-models/#!/model/model.bsc\_models.sushi\_\_dim\_dex\_pools)
* [`dim_kashi_pairs`](https://cloud.getdbt.com/accounts/1258/runs/77461492/docs/#!/model/model.bsc\_models.sushi\_\_dim\_kashi\_pairs)
* [`ez_swaps`](https://flipsidecrypto.github.io/bsc-models/#!/model/model.bsc\_models.sushi\_\_ez\_swaps)
* [`ez_borrowing`](https://cloud.getdbt.com/accounts/1258/runs/77461492/docs/#!/model/model.bsc\_models.sushi\_\_ez\_borrowing)
* [`ez_lending`](https://cloud.getdbt.com/accounts/1258/runs/77461492/docs/#!/model/model.bsc\_models.sushi\_\_ez\_lending)



Note: when working with the `fact_transactions` and `fact_event_logs` tables, you may find it useful to use the [ethereum.public.hex\_to\_int() function](../../../resources/hex-to-integer-function.md).
