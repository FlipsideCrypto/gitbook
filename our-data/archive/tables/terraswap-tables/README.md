---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Terraswap Tables

From the [Terraswap docs](https://docs.terraswap.io/) : "Terraswap is a Uniswap-inspired automated market-maker (AMM) protocol implemented with smart contracts on the Terra blockchain."

The public Github repo with Terraswap model source code is [here](https://github.com/FlipsideCrypto/sql\_models/tree/main/models/terra/swap).

### Participants [#](https://docs.terraswap.io/#participants) <a href="#participants" id="participants"></a>

Terraswap users can become trader, liquidity provider or both.

A **trader** can exchange their token for another token through Terraswap using the price determined by the liquidity pool ratio.

**Liquidity provider** adds equal value of two assets to their corresponding Terraswap pair pool, which increases liquidity for the corresponding pair market while maintaining the pool price. In this process, liquidity providers are rewarded by newly minted LP tokens. LP tokens represent the liquidity provider’s share in the pool and provide the benefit of earning trading fees, which are accumulated into the pool on every swap transaction. Liquidity providers can burn their LP tokens to withdraw their share from the pool.

