# 2024-02-05 | Data Updates

## [Solana](https://flipsidecrypto.github.io/solana-models/#!/overview)

### [fact\_bridge\_activity](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.defi\_\_fact\_bridge\_activity)

Contains information on bridge transfer on Solana for the following protocols: Debridge, Mayan Finance, and Wormhole. This includes bridging events 'from', as well as 'to' Solana.

Enable easier access to flows between Solana and other chains, allowing deeper analysis regarding cross-chain activity

### [fact\_decoded\_instructions](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_decoded\_instructions)

Added complete historical data for decoded events for various programs. The protocols with decoded events are: Flash Trade, Banx, Marginfi, and Tensor.

Full history of decoded events for popular programs which enables faster and simpler analysis.

### [dim\_nft\_metadata](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.nft\_\_dim\_nft\_metadata)

Add authority field and enhance creators field to include all creators of an NFT as well as the % of sale fee's they receive.&#x20;

Access to the authority of an NFT mint which can be used for further filtering/grouping of NFT's. The update to the creator field provides further information on who created the NFT or its collection, and the % of fee's allows analysis into how much SOL they have accumulated from sales of their NFT.

### [dim\_idl](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_dim\_idl)

A convenience table containing information for the programs contained in our decoded events tables.

An efficient way to see what programs are currently being decoded, and how far back we have historical data. This can be used to determine whether we have full historical data -- if not, a user can request we backfill the program.

## Crosschain

Added Solana bridge transfers to the comprehensive crosschain tables, which also includes blockchain and platform specific bridge activity from numerous EVM chains.

Access to native Solana bridging activity in easy to use tables for analysis across various chains.

### [fact\_bridge\_activity](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.defi\_\_fact\_bridge\_activity)

### [ez\_bridge\_activity](https://flipsidecrypto.github.io/crosschain-models/#!/model/model.crosschain\_models.defi\_\_fact\_bridge\_activity)

## [Aptos](https://flipsidecrypto.github.io/aptos-models/#!/overview)

### [fact\_bridging\_activity](https://flipsidecrypto.github.io/aptos-models/#!/model/model.aptos\_models.defi\_\_fact\_bridge\_activity)

A fact table that aggregates bridge activity in Aptos, including both bridging-in and out transactions. Activity from the following protocols are supported: CELER, MOVER, LAYER ZERO, and WORMHOLE.

Enable easier access to flows between Aptos and other chains, allowing deeper analysis regarding cross-chain activity

## [Polygon](https://flipsidecrypto.github.io/polygon-models/#!/overview)

### [ez\_nft\_sales](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.nft\_\_ez\_nft\_sales)

Added TofuNFT marketplace for Polygon NFT sales table

Query NFT sales for the TofuNFT marketplace on polygon

## [Optimism](https://flipsidecrypto.github.io/optimism-models/#!/overview)

\~97% of Lending TVL coverage added

### [ez\_lending\_borrows](https://flipsidecrypto.github.io/optimism-models/#!/model/model.optimism\_models.defi\_\_ez\_lending\_borrows)

### [ez\_lending\_deposits](https://flipsidecrypto.github.io/optimism-models/#!/model/model.optimism\_models.defi\_\_ez\_lending\_deposits)

### [ez\_lending\_flashloans](https://flipsidecrypto.github.io/optimism-models/#!/model/model.optimism\_models.defi\_\_ez\_lending\_flashloans)

### [ez\_lending\_liquidations](https://flipsidecrypto.github.io/optimism-models/#!/model/model.optimism\_models.defi\_\_ez\_lending\_liquidations)

### [ez\_lending\_repayments](https://flipsidecrypto.github.io/optimism-models/#!/model/model.optimism\_models.defi\_\_ez\_lending\_repayments)

### [ez\_lending\_withdraws](https://flipsidecrypto.github.io/optimism-models/#!/model/model.optimism\_models.defi\_\_ez\_lending\_withdraws)

## [Base](https://flipsidecrypto.github.io/base-models/#!/overview)

\~99% of Lending TVL coverage added

### [ez\_lending\_borrows](https://flipsidecrypto.github.io/base-models/#!/model/model.base\_models.defi\_\_ez\_lending\_borrows)

### [ez\_lending\_deposits](https://flipsidecrypto.github.io/base-models/#!/model/model.base\_models.defi\_\_ez\_lending\_deposits)

### [ez\_lending\_flashloans](https://flipsidecrypto.github.io/base-models/#!/model/model.base\_models.defi\_\_ez\_lending\_flashloans)

### [ez\_lending\_repayments](https://flipsidecrypto.github.io/base-models/#!/model/model.base\_models.defi\_\_ez\_lending\_repayments)

### [ez\_lending\_liquidations](https://flipsidecrypto.github.io/base-models/#!/model/model.base\_models.defi\_\_ez\_lending\_liquidations)&#x20;

### [ez\_lending\_withdraws](https://flipsidecrypto.github.io/base-models/#!/model/model.base\_models.defi\_\_ez\_lending\_withdraws)

## [Near](https://flipsidecrypto.github.io/near-models/#!/overview)

### [fact\_dex\_swaps](https://flipsidecrypto.github.io/near-models/#!/model/model.near.defi\_\_fact\_dex\_swaps)

A new model parsing dex swaps on the NEAR blockchain.

Replaces the deprecating EZ\_DEX\_SWAPS view due to inaccurate and mis-parsed data.

### [fact\_bridge\_activity](https://flipsidecrypto.github.io/near-models/#!/model/model.near.defi\_\_fact\_bridge\_activity)

A fact table that aggregates bridge activity on Near, mapping tokens flowing into and out of the NEAR Ecosystem, including across the Rainbow Bridge to and from Aurora. Tracks the four primary bridges: Rainbow, Wormhole, Allbridge, Multichain (bridge deactivated due to hack in mid 2023)\
