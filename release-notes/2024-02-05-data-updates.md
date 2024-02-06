# 2024-02-05 | Data Updates

## [Solana](https://flipsidecrypto.github.io/solana-models/#!/overview)

### [fact\_bridge\_activity](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.defi\_\_fact\_bridge\_activity)

NEW: Our crosschain bridge transfers data now includes Solana too! The table contains bridging events to and from Debridge, Mayan Finance, and Wormhole protocols. With this table in the mix, you can create even deeper crosschain insights.

### [fact\_decoded\_instructions](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_decoded\_instructions)

Ever wanted to get more into Solana analytics? This new table is your gateway! No more lateral flattening the instructions and slowing down your queries, and no need to figure out where in the instructions specific attributes are located.

Your analytics will be faster and easier: With just a program ID, go from exploratory analysis to perusing human-readable decoded instructions to constructing your Solana event queries on complete historical data. The protocols with decoded events are: Flash Trade, Banx, Marginfi, and Tensor.

### [dim\_nft\_metadata](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.nft\_\_dim\_nft\_metadata)

This table just got better with a new `authority` field and an enhanced `creator` field. You can now analyze NFT collaborations, and query data on royalty splits for collections with several creators.

### [dim\_idl](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_dim\_idl)

For your convenience: A convenience table containing information for the programs contained in our decoded events tables.

An efficient way to see what programs are currently being decoded, and how far back we have historical data. If you want a program to be added, submit a request: https://science.flipsidecrypto.xyz/idl-requestor/

## Crosschain

Crosschain bridging tables are one of the recent additions we are most excited about! Solana bridge transfers just got added to the comprehensive crosschain tables that also include numerous EVM chains.

What you get: Access to native Solana bridging activity in easy to use tables for analysis across various chains.

### [fact\_bridge\_activity](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.defi\_\_fact\_bridge\_activity)

### [ez\_bridge\_activity](https://flipsidecrypto.github.io/crosschain-models/#!/model/model.crosschain\_models.defi\_\_fact\_bridge\_activity)

## [Aptos](https://flipsidecrypto.github.io/aptos-models/#!/overview)

### [fact\_bridging\_activity](https://flipsidecrypto.github.io/aptos-models/#!/model/model.aptos\_models.defi\_\_fact\_bridge\_activity)

Another table from our crosschain bridging data drop! A table that aggregates bridge activity in Aptos, including both bridging-in and out transactions. Protocols currently supported: Celer, Mover, Layer Zero, and Wormhole.

Enable easier access to token flows between Aptos and other chains, allowing deeper analysis of cross-chain activity.

## [Polygon](https://flipsidecrypto.github.io/polygon-models/#!/overview)

### [ez\_nft\_sales](https://flipsidecrypto.github.io/polygon-models/#!/model/model.polygon\_models.nft\_\_ez\_nft\_sales)

Added TofuNFT marketplace to the Polygon NFT sales table: Query and analyze TofuNFT sales activity!

## [Optimism](https://flipsidecrypto.github.io/optimism-models/#!/overview)

These tables are now even more comprehensive: \~97% of Lending TVL coverage added.

### [ez\_lending\_borrows](https://flipsidecrypto.github.io/optimism-models/#!/model/model.optimism\_models.defi\_\_ez\_lending\_borrows)

### [ez\_lending\_deposits](https://flipsidecrypto.github.io/optimism-models/#!/model/model.optimism\_models.defi\_\_ez\_lending\_deposits)

### [ez\_lending\_flashloans](https://flipsidecrypto.github.io/optimism-models/#!/model/model.optimism\_models.defi\_\_ez\_lending\_flashloans)

### [ez\_lending\_liquidations](https://flipsidecrypto.github.io/optimism-models/#!/model/model.optimism\_models.defi\_\_ez\_lending\_liquidations)

### [ez\_lending\_repayments](https://flipsidecrypto.github.io/optimism-models/#!/model/model.optimism\_models.defi\_\_ez\_lending\_repayments)

### [ez\_lending\_withdraws](https://flipsidecrypto.github.io/optimism-models/#!/model/model.optimism\_models.defi\_\_ez\_lending\_withdraws)

## [Base](https://flipsidecrypto.github.io/base-models/#!/overview)

These tables are now even more comprehensive: \~99% of Lending TVL coverage added.

### [ez\_lending\_borrows](https://flipsidecrypto.github.io/base-models/#!/model/model.base\_models.defi\_\_ez\_lending\_borrows)

### [ez\_lending\_deposits](https://flipsidecrypto.github.io/base-models/#!/model/model.base\_models.defi\_\_ez\_lending\_deposits)

### [ez\_lending\_flashloans](https://flipsidecrypto.github.io/base-models/#!/model/model.base\_models.defi\_\_ez\_lending\_flashloans)

### [ez\_lending\_repayments](https://flipsidecrypto.github.io/base-models/#!/model/model.base\_models.defi\_\_ez\_lending\_repayments)

### [ez\_lending\_liquidations](https://flipsidecrypto.github.io/base-models/#!/model/model.base\_models.defi\_\_ez\_lending\_liquidations)&#x20;

### [ez\_lending\_withdraws](https://flipsidecrypto.github.io/base-models/#!/model/model.base\_models.defi\_\_ez\_lending\_withdraws)

## [Near](https://flipsidecrypto.github.io/near-models/#!/overview)

### [fact\_dex\_swaps](https://flipsidecrypto.github.io/near-models/#!/model/model.near.defi\_\_fact\_dex\_swaps)

This is a brand new table to take over from the soon-to-be-deprecated `near.defi.ez_dex_swaps`. With an overhauled model, this now obtains and parses the most accurate data on Near swaps for your analytics.

### [fact\_bridge\_activity](https://flipsidecrypto.github.io/near-models/#!/model/model.near.defi\_\_fact\_bridge\_activity)

Query tokens bridged in and out of the NEAR Ecosystem, including across the Rainbow Bridge to and from Aurora. Tracks the four primary bridges: Rainbow, Wormhole, Allbridge, and historical data on Multichain (a bridge which was deactivated due to a hack in 2023).
