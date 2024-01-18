---
description: Getting familiar with our SQL dialect.
---

# Using Snowflake SQL

If you're familiar with common SQL dialects like Postgres or MySQL, you'll find that while there are a few specific differences, the basics will be very familiar, as the Snowflake SQL dialect is ANSI SQL compliant. ([More on SQL standards and interoperability](https://en.wikipedia.org/wiki/SQL#Interoperability\_and\_standardization).)&#x20;

Here's a roundup of [some of the key differences](https://towardsdatascience.com/from-postgres-to-snowflake-f4b403548066) people run into when switching from Postgres to Snowflake that we found helpful. In particular:

* Filtering in Snowflake must be done with CASE statements.
* No support for DISTINCT ON, so people use window functions, generally.

To help navigate this all of this, Snowflake also maintains a comprehensive [SQL reference](https://docs.snowflake.com/en/sql-reference-commands.html), and many Snowflake-specific functions are available. (Crypto analysts often find their [JSON parsing functions](https://docs.snowflake.com/en/sql-reference/functions-semistructured.html) can be particularly helpful.)

