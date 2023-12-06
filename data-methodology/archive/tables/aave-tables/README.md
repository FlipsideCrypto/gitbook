---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# AAVE Tables

AAVE is a lending platform, somewhat similar in scope and design to Compound. As a result we have a similar design schema for this project. Feedback remains very welcome as much of this data remains very beta!

### New Tables (Compared to Compound)

Unlike for Compound there are three further tables:

* _Aave votes and proposals:_ Governance actions do exist on Compound and in fact can even be found within the events data, however with AAVE we've begun to opt to give these their own tables. These come as a pair -- proposals tracks all ongoing proposals and their current status, votes tracks votes for and against their proposals. The two can be joined on proposal ID.
* _Flashloans:_ AAVE has explicit support for flashloans -- loans taken and repaid within the same transaction. Once again on Compound this is technically possible but AAVE has flashloans built in as their own set of functions.

### Variable and Stable Debts

Additionally a key feature of AAVE's lending markets is that each market (i.e. USDC) supports two types of loans, one at a stable borrow rate and another at a variable rate. Both V1 and V2 (and AMM), support these but V2 and up has an additional feature aimed direct at these types of loans -- debt tokens.

Debt tokens tokenize debt in the same way aTokens (or Compounds' cTokens) tokenize amounts supplied to the market. aTokens are given to suppliers proportionally based on how much they supply to that market. Stable Debt Tokens are given to borrowers based on how much debt at a stable borrow rate they have from that market. Identically Variable Debt Tokens are given to borrowers based on how much variable debt they hold

### What about the Version columns (and blockchain)?

![](<../../../../.gitbook/assets/Screen Shot 2021-08-16 at 3.22.45 PM.png>)

Aave a few different subsets of markets, shown above.&#x20;

AAVE V1: Debt tokens do not exist and more technically, (though less significantly for our data) all interactions are done through the Lending Pool. aTokens do exist and stable/variable borrow rates are still available

AAVE V2: Debt tokens exist to more easily track outstanding debt. Direct interactions are split among a Lending Pool and a Data Provider contract (though not necessary for anyone not planning to interact with the protocol directly on chain, i.e. app developers)

AAVE AMM: Identical in design to AAVE V2 though it uses its own set of contracts. Designed for pool tokens.

AAVE Polygon: Also shares a design with V2, with the key difference is that it is on the Polygon chain (whereas all others are Ethereum only)

### General

{% content-ref url="market-stats.md" %}
[market-stats.md](market-stats.md)
{% endcontent-ref %}

### Governance

{% content-ref url="votes.md" %}
[votes.md](votes.md)
{% endcontent-ref %}

{% content-ref url="proposals.md" %}
[proposals.md](proposals.md)
{% endcontent-ref %}

### Supplying

{% content-ref url="withdraws.md" %}
[withdraws.md](withdraws.md)
{% endcontent-ref %}

{% content-ref url="deposits.md" %}
[deposits.md](deposits.md)
{% endcontent-ref %}

### Liquidations

{% content-ref url="liquidations.md" %}
[liquidations.md](liquidations.md)
{% endcontent-ref %}

### Borrowing

{% content-ref url="borrows.md" %}
[borrows.md](borrows.md)
{% endcontent-ref %}

{% content-ref url="repayments.md" %}
[repayments.md](repayments.md)
{% endcontent-ref %}

{% content-ref url="flashloans.md" %}
[flashloans.md](flashloans.md)
{% endcontent-ref %}

