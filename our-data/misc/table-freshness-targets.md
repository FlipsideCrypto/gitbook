---
description: The following can be tuned/adjusted.
---

# Table Freshness Targets

Flipside's tables target the following latency schedule from Chain Head. The following can be tuned based on use cases/needs. Please reach out if you have a specific use case that requires a latency closer to the chain head and our team would be happy to discuss solutions with you.

Flipside refreshes data across three dimensions fact tables, dim tables, and ez tables.

| Blockchain | Category (Fact, Dim, Ez) | Target Latency from Chain Head |
| ---------- | ------------------------ | ------------------------------ |
| Arbitrum   | Fact + Dim + EZ          | 30 minutes                     |
| Avalanche  | Fact + Dim + EZ          | 30 minutes                     |
| Avalanche  | decoded\_event\_logs     | 30 minutes                     |
| Axelar     | Fact + Dim               | 30 minutes                     |
| Axelar     | EZ                       | 30 minutes                     |
| Bitcoin    | Fact + Dim + EZ          | 30 minutes                     |
| BSC        | Fact + Dim + EZ          | 30 minutes                     |
| Cosmos     | Fact + Dim + Ez          | 30 minutes                     |
| Ethereum   | Fact + Dim               | 20 minutes                     |
| Ethereum   | Ez                       | 30 minutes                     |
| Ethereum   | Balances                 | 4 hours                        |
| Flow       | Fact + Dim + Ez          | 45 Minutes                     |
| Gnosis     | Fact + Dim + Ez          | 30 minutes                     |
| NEAR       | Fact + Dim               | 2 hours                        |
| NEAR       | Ez                       | 3 hours                        |
| Optimism   | Fact + Dim + Ez          | 30 minutes                     |
| Osmosis    | Fact + Dim + Ez          | 30 minutes                     |
| Osmosis    | ez\_pools                | 24 hours                       |
| Polygon    | Fact + Dim + Ez          | 30 minutes                     |
| Polygon    | decoded\_event\_logs     | 30 hours                       |
| Solana     | Fact + Dim               | 30 Minutes                     |
| Solana     | Ez                       | 30 minutes                     |
| Terra      | Fact + Dim + Ez          | 30 minutes                     |
| Thorchain  | Fact + Dim + Ez          | 2 hours                        |
