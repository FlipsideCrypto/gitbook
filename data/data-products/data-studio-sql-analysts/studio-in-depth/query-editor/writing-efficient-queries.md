---
description: How to write queries that return results quickly.
---

# Writing Efficient Queries

A few basic techniques:

* **Date Filtering:** when querying fact tables, or any table with a large number of rows, it's best to filter your query to a small date range by adding a "where" clause, something like this: \
  `WHERE block_timestamp >= CURRENT_DATE - interval '1 day'` — this is especially helpful if you're just getting started exploring a particular table, are looking for quick sample data, etc.
* **Select Only Columns You Need**: instead of using `SELECT *` every time, try selecting only the particular columns required to get the results you need — this optimization can often be applied after you're done making charts, dashboards etc., when you know definitively which columns you're really using, and will yield faster results for viewers of your work.

