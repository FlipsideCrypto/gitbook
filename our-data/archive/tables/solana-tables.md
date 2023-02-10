---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Solana Tables

### Background of Solana

**Blockchain:** [Solana](https://solana.com/)

Solana is a public base-layer blockchain protocol that optimizes for scalability. The goal of the Solana blockchain is to provide a platform that enables developers to create decentralized applications (dApps) without needed to design around performance bottlenecks. Solana features a new timestamp system called Proof of History (PoH) that enables automatically ordered transactions. It also uses Proof of Stake (PoS) consensus algorithm to help secure the network.&#x20;

The public Github repo with Solana model source code is [here](https://github.com/FlipsideCrypto/solana-models).

### Current Solana Tables

The current Solana table schemas build concepts laid out in [Flipside's event data model](broken-reference). Solana tables are available in Velocity as the `solana` schema. The tables are built based on the Solana events and transactions information. The following Solana tables are available:

[Solana Dim Labels](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_dim\_labels)

[Solan Dim Tokens](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_dim\_tokens)

[Solana EZ Signers](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_ez\_signers)

[Solan EZ Token Prices Hourly](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_ez\_token\_prices\_hourly)

[Solana Fact Blocks](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_blocks)

[Solana Fact Events](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_events)&#x20;

[Solana Fact Gauges Votes](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_gauges\_votes)

[Solana Fact Gov Actions](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_gov\_actions)

[Solana Dim NFT Metadata](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_dim\_nft\_metadata)

[Solana Fact NFT Mints](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_nft\_mints)

[Solana Fact NFT Sales](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_nft\_sales)

[Solana Fact Proposal Creation](broken-reference)

[Solana EZ Staking/LP Actions](broken-reference)

[Solana Fact Staking/LP Actions](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_staking\_lp\_actions)

[Solana Fact Stake Pool Actions](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_stake\_pool\_actions)

[Solana Fact Swaps](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_swaps)

[Solana Fact Token Prices Hourly](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_token\_prices\_hourly)

[Solana Fact Transactions](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_transactions)

[Solana Fact Transfers](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_transfers)

[Solana Fact Votes Agg Blocks](https://flipsidecrypto.github.io/solana-models/#!/model/model.solana\_models.core\_\_fact\_votes\_agg\_block) &#x20;



#### What we have:

* All native on-chain Solana events dating back to November 28, 2021.&#x20;
* Labels for certain common Solana wallet addresses and programs.&#x20;
* NFT metadata for top Solana NFT projects.&#x20;

#### What we don't have:&#x20;

* Off-chain events such as DEX order book transactions and bids on secondary NFT marketplaces.&#x20;
* Data before Nov. 28th, 2021. We are in the process of backfilling the Solana tables, earlier data will be made available shortly.&#x20;
* Votes anywhere besides the `solana.votes_block_agg` table and Pyth Oracle transactions.

### Solana Labels&#x20;

Solana labels are available and located in the table `solana.labels`. To include Solana labels in your analysis, perform a join on address or program ID. Please note that all address labels stored in the `solana.labels` table are in lower case and that Solana addresses are case sensitive. To join the tables, use the SQL function `COLLATE` to create a case insensitive `JOIN` statement.&#x20;

### Solana NFT Tables And Metadata

We have three Solana NFT tables: `solana.nfts` (mints, sales, etc), `solana.nft_metadata` (token names, images, attributes, etc), and `solana.airdrops` (NFT and token airdrops).

The goal of these tables is to create a unified table of on-chain Solana NFT data that makes it easy to compare across and within NFTs. To do this, we have curated metadata from top Solana NFT projects. The metadata is nowhere near comprehensive, we add projects one or two at a time. That being said, we want these tables to be interesting to our community and would love feedback and recommendations for projects to add.&#x20;

### How to Contribute to Our Data

Are there labels or NFT metadata that you would like to see added to our data? Let us know the following information in Discord or via email (hello@flipsidecrypto.com):&#x20;

**Good:** Send us the name of the token/label and the contract address.&#x20;

**Better:** Send us the name of the token/label, the contract address, and the project website.

**Best:** Send us the name, contract address, project website, and example transactions (links to solscan.io). For an NFT, we would appreciate examples of the following transaction types:&#x20;

* minting
* list
* unlist
* bid
* sale
* any other special thing you can "do" with this NFT (ex: staking)
