# Pro Tips for Querying

### Using Snowflake SQL&#x20;

If you're familiar with common SQL dialects like Postgres or MySQL, you'll find that while there are a few specific differences, the basics will be very familiar, as the Snowflake SQL dialect is ANSI SQL compliant. ([More on SQL standards and interoperability](https://en.wikipedia.org/wiki/SQL#Interoperability\_and\_standardization).)&#x20;

Here's a roundup of [some of the key differences](https://towardsdatascience.com/from-postgres-to-snowflake-f4b403548066) people run into when switching from Postgres to Snowflake that we found helpful. In particular:

* Filtering in Snowflake must be done with CASE statements.
* No support for DISTINCT ON, so people use window functions, generally.

To help navigate this all of this, Snowflake also maintains a comprehensive [SQL reference](https://docs.snowflake.com/en/sql-reference-commands.html), and many Snowflake-specific functions are available. (Crypto analysts often find their [JSON parsing functions](https://docs.snowflake.com/en/sql-reference/functions-semistructured.html) can be particularly helpful.)

***

### Writing Efficient Queries&#x20;

A few basic techniques:

* **Date Filtering:** when querying fact tables, or any table with a large number of rows, it's best to filter your query to a small date range by adding a "where" clause, something like this: \
  `WHERE block_timestamp >= CURRENT_DATE - interval '1 day'` — this is especially helpful if you're just getting started exploring a particular table, are looking for quick sample data, etc.
* **Select Only Columns You Need**: instead of using `SELECT *` every time, try selecting only the particular columns required to get the results you need — this optimization can often be applied after you're done making charts, dashboards etc., when you know definitively which columns you're really using, and will yield faster results for viewers of your work.
