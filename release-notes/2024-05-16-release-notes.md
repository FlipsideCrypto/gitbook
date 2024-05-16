---
description: >-
  New Defi table on Solana, a new curated NFT Sales table on NEAR, and a new
  table to our External database.
---

# 2024-05-16 | Release Notes

### Highlights

This week we’re launching a new Defi table on Solana, a new curated NFT Sales table on NEAR, and a new table to our External database (Data Studio Only) to analyze tokens listed on [https://tokenlists.org](https://tokenlists.org).&#x20;

{% hint style="warning" %}
**Reminder:** Last update we announced our new [pricing data](broken-reference). This may require you to take action in order to prevent any issues with your queries. Learn more about the updates and any actions you need to take [here](broken-reference).
{% endhint %}

Check out these updates and the rest of the release notes below.

### External (Data Studio Only)

**New Table:**

A Uniswap project, Token Lists, is a community-led initiative to improve discoverability, reputation and trust in ERC20 token lists in a manner that is inclusive, transparent, and decentralized. This table contains dimensional information about the tokens listed on [https://tokenlists.org/](https://tokenlists.org/). This EZ view joins in Defillama's dim\_chains for additional chain metadata.

* _external.tokenlists.ez\_verified\_tokens_

### [NEAR](https://flipsidecrypto.github.io/near-models/#!/overview)

**New Table:**

This table records all the NFT sales actions on the main Near marketplaces.

* _core.ez\_nft\_sales_

### [Solana](https://flipsidecrypto.github.io/solana-models/#!/overview)

**New Table:**

This table enables easier analysis of Meteora, one of the largest platforms for providing liquidity. The newly added data includes any actions involving the deposit and withdrawal of tokens, as well as related mints and burns of LP tokens.

* _defi.fact\_liquidity\_pool\_actions_

### Useful Resources&#x20;

Request a smart contract ABI to be decoded: [https://science.flipsidecrypto.xyz/abi-requestor/](https://science.flipsidecrypto.xyz/abi-requestor/)&#x20;

Request a Solana IDL to be decoded: [https://science.flipsidecrypto.xyz/idl-requestor](https://science.flipsidecrypto.xyz/idl-requestor)&#x20;

Add labels: [https://science.flipsidecrypto.xyz/add-a-label](https://science.flipsidecrypto.xyz/add-a-label)&#x20;
