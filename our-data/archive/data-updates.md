---
description: '[Legacy Documentation, Not Maintained, For Reference Only]'
---

# Data Updates

**Join our** [**Discord**](https://discord.gg/ZmU3jQuu6W) **for recent data updates.**&#x20;

This page is used for major occasional changes that may impact existing queries (e.g. moving refactoring schemas).

### **September 2022: Ethereum & EVM changes**

flipside\_prod\_db.aave -->ethereum.aave\
flipside\_prod\_db.compound -->ethereum.compound\
fipside\_prod\_db.ethereum --> ethereum.core\
flipside\_prod\_db.polygon --> polygon.core\
flipside\_prod\_db.uniswapv3-->  ethereum.uniswapv3

All queries above should be moved to the new corresponding databases. Dashboards will still populate, but there will be no new data coming into those tables. The legacy flipside\_prod\_db tables will not be seen in the Flipside query editor after September 13, 2022.&#x20;

### **June 2022: Solana Schema**

Solana will be have its own database starting early June 2022! We will move it from

flipside\_prod\_db --> solana

Your queries and dashboards will continue to work for a period of time. To future proof your dashboards, you should move over **all work** to the three part naming convention in the new solana database.&#x20;

### **May 2022: Three Part Naming**

For more information on new databases and three part naming, please see [this document](https://docs.google.com/document/d/1swYTBHYNoY27Mz5FB2Ru0KNTLRhwX6imWQtlyW5F-7Q/edit).

### **May 2022: Ethereum Schema**

Ethereum will have its own database starting May 25, 2022! flipside\_prod\_db.ethereum\_core will still be supported until June. We are actively making infrastructure upgrades and it will replace both flipside\_prod\_db.ethereum and ethereum\_core.&#x20;

New Ethereum tables will be released in April 2022!

The new Ethereum schema will be **ethereum\_core**. Ethereum was one of the first blockchains that was developed within Flipside and there have been upgrades to infrastructure, warehousing, model building, etc. The Flipside developers have been working on what is being called the Ethereum facelift where many of the tables have been re-built from the ground up taking into account user feedback, usage, and lessons learned.&#x20;

Timeline:\
\- April 18, 2022 - Eth Week! New Schema exposed for all users. All bounties will have to use ethereum\_core schema.\
\
__

