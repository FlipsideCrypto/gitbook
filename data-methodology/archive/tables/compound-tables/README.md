---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Compound Tables

**Blockchain:** [Ethereum](https://ethereum.org/en/)

The Compound table schemas build on the concepts laid out in [Flipside's event data model](broken-reference). Below is a visual overview of the Compound protocol's primary functions of decentralized borrowing and lending.&#x20;

![](<../../../../.gitbook/assets/Screen Shot 2021-04-20 at 11.44.31 AM.png>)

We have tables for most major events within the Compound ecosystem, though the data is still early. The tables are intended to be as easy to work with as possible and paint as complete a picture of Compound as possible.  Here are [sample Compound queries](https://velocity-app.flipsidecrypto.com/velocity/collections/d54dd195-163c-4153-8595-50b22f629b08).

**What we have:**&#x20;

* A table for summarizing major metrics by market: `compound.market_stats.` This table aggregates by the hour, and should have all available markets/cTokens listed here [https://compound.finance/markets](https://compound.finance/markets)
* Tables for key events for suppliers: `compound.redemptions` and `compound.deposits.` In the diagram above these events correspond to both interactions between suppliers and the lending markets.
* Tables for key events for borrowers: `compound.borrows`, `compound.repayments` and `compound.liquidations`. These correspond to the three interactions between lending markets, borrowers, and liquidators in the diagram above.
* The data goes back only as far as October 2020, with more to come.

**What we don't have:**

We did choose, for now to omit tables for governance actions, such as proposals and voting. This decision was mostly due to the very different levels of activity on the two sides. There is significantly greater activity centered around the markets and what seemed to be of the greatest interest to users. However, governance actions can still be parsed from `ethereum.events`.

**Feedback and Improvements:**

All feedback and criticism remain very much appreciated! Send a ping in [our discord](https://discord.gg/uW5jK2jRTg)! (@connorH) or send us an email at _hello@flipsidecrypto.com._

**General Tips**:

* &#x20;Using marketstats as a starting point is often an excellent idea, as it tends to connect to each of the other tables and is very centrally located. This table aggregates by hour, so join on `market_stats.date_trunc('hour',block_hour) = block_timestamp AND market_stats.ctoken_address = ctoken`
* As mentioned we only have data going back to October, but we are in the process of completing a backfill of our data!&#x20;
* Governance actions may not have their own tables but they are still available. If you find the appropriate event you can locate it within the table ethereum.events\_emitted . If you think you'd be using this routinely let us know, and we'll create more views for these events.

For instance new proposals to vote on are created using ProposalCreated, so you could list all created proposals with

```
SELECT 
        block_timestamp,
        tx_id,
        event_name, 
        CASE WHEN contract_address = '0xc0da01a04c3f3e0be433606045bb7017a7323e38' THEN 'Alpha' ELSE 'Bravo' 
          END AS governor_contract,
            event_inputs:id AS proposal_id,
            REGEXP_REPLACE(event_inputs:proposer,'\"','') AS proposer,
            REGEXP_REPLACE(event_inputs:targets,'\"','') AS targets,
            REGEXP_REPLACE(event_inputs:description,'\"','') AS description
FROM ethereum.events_emitted
WHERE 
contract_address IN ('0xc0da01a04c3f3e0be433606045bb7017a7323e38', -- governance contracts
                    '0xc0da02939e1441f497fd74f78ce7decb17b66529')
AND 
block_timestamp >= CURRENT_DATE - 120
AND event_name  = 'ProposalCreated' -- the event
```

**Pro Tip for advanced users:**

* The documentation for compound combines excellently with the events\_emitted table. If you can find an event in the docs there, you can find it in the link below or [here](https://compound.finance/docs/ctokens#key-events)!&#x20;

&#x20;                                 [https://compound.finance/docs/ctokens#key-events](https://compound.finance/docs/ctokens#key-events)
