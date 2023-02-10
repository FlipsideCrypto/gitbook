---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Osmosis Tables

### Background of Osmosis

**Blockchain:** [Osmosis](https://app.osmosis.zone/)

Osmosis is a proof-of-stake IBC blockchain with a decentralized exchange application enabling users to provide liquidity, swap, and stake tokens from across the Cosmos ecosystem. The Osmosis Frontier application, which is a full permissionless listing and curation of bridged ETH and CW20 assets, exists alongside the main Osmosis application.&#x20;

The native token of Osmosis, Osmo, is used for governance and paying transaction fees for actions performed on the DEX. There are a few points that make Osmosis a unique DEX:

* **Self-Governing Liquidity Pools:** In Osmosis, the LP shares are used to calculate the fractional ownership of a LP, as well as the right to participate in the strategic decision making of the LP via governance. To incentivize long-term liquidity commitment, shares must be locked up for an extended period. Longer-term commitments are awarded by additional voting power and additional liquidity mining revenue.
* **Superfluid Staking:** A method of staking the OSMO tokens that underlie your LP positions to earn additional rewards. Superfluid staking is at time of writing only available on certain OSMO pools on Osmosis.
* **MEV Resistance:** Osmosis was conceived with the goal of Maximal Extractable Value (MEV) resistance at its core and includes several unique solutions to help limit MEV.

### Current Osmosis Tables

The Osmosis tables are built on Osmosis transaction and messages information.&#x20;

[Fact Blocks](osmosis-fact-blocks-table.md)

[Fact Daily Balances](osmosis-daily-balances.md)

[Fact Governance Proposal Deposits](osmosis-fact-governance-proposal-deposits.md)

[Fact Governance Submit Proposal](osmosis-fact-governance-submit-proposal.md)&#x20;

[Fact Governance Votes](osmosis-fact-governance-votes.md)

[Dim Labels ](osmosis-dim-labels.md)

[Dim Liquidity Pools](osmosis-dim-liquidity-pools.md)

[Fact Liquidity Provider Actions](osmosis-fact-liquidity-provider-actions.md)&#x20;

[Fact Msg Attributes](osmosis-fact-msg-attributes-table.md)

[Fact Msgs](osmosis-fact-msgs-table.md)

[Dim Prices](osmosis-dim-prices.md)

[Fact Staking Rewards](osmosis-fact-staking-rewards.md)

[Fact Staking](osmosis-fact-staking.md)

[Fact Superfluid Staking](osmosis-fact-superfluid-staking.md)

[Fact Swaps](osmosis-fact-swaps.md)

[Dim Tokens](osmosis-dim-tokens.md)

[Fact Transactions](osmosis-fact-transactions-table.md)

[Fact Transfers](osmosis-fact-transfers.md)

[Fact Validators](osmosis-fact-validators.md)

[Dim Vote Options](osmosis-dim-vote-options.md)

[EZ Prices](osmosis-ez-prices.md)

[EZ ICNS](osmosis-ez-icns.md)

#### What we have:

* All on-chain Osmosis events dating back to the genesis block in June 2021.&#x20;
* Labels for all available tokens and liquidity pools on the Osmosis app and Osmosis validators.

#### What we don't have:&#x20;

* Data related to pool APY, as this is not available on chain.&#x20;
* Some labels & decimals for LP tokens and low market cap tokens.&#x20;
