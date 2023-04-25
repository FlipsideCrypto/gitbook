---
description: The R programming language is a great fit for analysis of flipsidecrypto data!
---

# R

ShroomDK's R package simplifies access to the Flipside Crypto ShroomDK REST API. More details on ShroomDK available at [sdk.flipsidecrypto.xyz/shroomdk](https://sdk.flipsidecrypto.xyz/shroomdk).

### How to get your own ShroomDK API Key

ShroomDK API Keys are NFTs on the Ethereum blockchain. They are free to mint (not counting Ethereum gas) and new mints are available each day. Alternatively you can buy the NFT on any NFT Marketplace where listed (e.g., OpenSea).

### How to Install

```
# available on CRAN
install.packages("shroomDK")
library(shroomDK)

# Latest developments available on Github
library(devtools) # install if you haven't already
devtools::install_github(repo = 'FlipsideCrypto/sdk', subdir = 'r/shroomDK')
library(shroomDK)
```

## Auto Paginate Query

**auto\_paginate\_query()**\
\
The easiest way to use shroomDK is to simply auto paginate a query to return (up to) 1 Million rows in 1 function call. This function will attempt to report useful errors and warnings; but if results are not as expected, follow the traditional create\_query\_token() %>% get\_query\_from\_token() %>% clean\_query() pipeline.\
\
Documentation can be viewed within RStudio with `?auto_paginate_query` for new packages you may need to restart R to get to the documentation. It is summarized here:

| Item        | Definition                                                                                                |
| ----------- | --------------------------------------------------------------------------------------------------------- |
| Description | Grabs up to `maxrows` in a query by going through each page 100k rows at a time.                          |
| Usage       | auto\_paginate\_query(query, api\_key)                                                                    |
| query       | Flipside Crypto Snowflake SQL compatible query as a string.                                               |
| api\_key    | Flipside Crypto ShroomDK API Key                                                                          |
| maxrows     | Flipside Crypto ShroomDK maximum rows in query, default 1,000,000                                         |
| value       | <p>data frame of up to 1M rows, <br>see ?<code>clean_query</code> for more details on  column classes</p> |

For detailed examples using exclusively auto\_paginate\_query() see the [Examples](../examples.md).

```
# example
auto_paginate_query(query = "SELECT * FROM ethereum.core.fact_transactions LIMIT 1", 
                    api_key = readLines("api_key.txt")
                    )

```

### Core Functions

**create\_query\_token()**

Documentation can be viewed within RStudio with `?create_query_token` for new packages you may need to restart R to get to the documentation. It is summarized here:

| Item        | Definition                                                                                                                                                                                                         |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Description | Uses Flipside ShroomDK to create a Query Token to access Flipside Crypto data. The query token is cached up to ttl minutes allowing for pagination and multiple requests before expending more daily request uses. |
| Usage       | create\_query\_token(query, api\_key, ttl = 10, cache = TRUE)                                                                                                                                                      |
| query       | Flipside Crypto Snowflake SQL compatible query as a string.                                                                                                                                                        |
| api\_key    | Flipside Crypto ShroomDK API Key                                                                                                                                                                                   |
| ttl         | time (in minutes) to keep query in cache.                                                                                                                                                                          |
| cache       | Use cached results; set as FALSE to re-execute.                                                                                                                                                                    |
| Value       | list of `token` and `cached` use `token` in `get_query_from_token()`                                                                                                                                               |

```
# example
create_query_token(
query = "SELECT * FROM ethereum.core.fact_transactions LIMIT 1",
api_key = readLines("api_key.txt"), # gitignore your api_key! don't share!
ttl = 15,
cache = TRUE)
```





**get\_query\_from\_token()**

Documentation can be viewed within RStudio with `?get_query_from_token` for new packages you may need to restart R to get to the documentation. It is summarized here:

| Item         | Definition                                                                                                                                                                                                                                                                                                      |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Description  | Uses Flipside ShroomDK to access a Query Token. Query tokens are cached up to 'ttl' minutes for each 'query'. This function is for pagination and multiple requests while reducing your use of your daily rate limit. Note: To reduce payload it returns a list of outputs (separating column names from rows). |
| Usage        | get\_query\_from\_token(query\_token, api\_key, page\_number = 1, page\_size = 1e+05)                                                                                                                                                                                                                           |
| query\_token | token from 'create\_query\_token()'                                                                                                                                                                                                                                                                             |
| api\_key     | Flipside Crypto ShroomDK API Key                                                                                                                                                                                                                                                                                |
| page\_number | Query tokens are cached and 100k rows max. Get up to 1M rows by going through pages.                                                                                                                                                                                                                            |
| page\_size   | Default 100,000. Paginate via page\_number.                                                                                                                                                                                                                                                                     |
| Value        | returns a request of length 8: `results`, `columnLabels`, `columnTypes`, `startedAt`, `endedAt`, `pageNumber`, `pageSize`, `status`                                                                                                                                                                             |

```
# example
query = create_query_token("SELECT * FROM ETHEREUM.CORE.FACT_TRANSACTIONS LIMIT 10000", api_key) #gitignore your API key!
get_query_from_token(query$token, api_key, 1, 10000)
```



**clean\_query()**

Documentation can be viewed within RStudio with `?clean_query` for new packages you may need to restart R to get to the documentation. It is summarized here:

| Item          | Definition                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Description   | Cleans Query to be in Data Frame format                                                                                                                                                                                                                                                                                                                                                     |
| Usage         | clean\_query(request, try\_simplify = TRUE)                                                                                                                                                                                                                                                                                                                                                 |
| `request`     | The request output from `get_query_from_token()`                                                                                                                                                                                                                                                                                                                                            |
| try\_simplify | because requests can return JSON and/or may not have the same length across values, they may not be data frame compliant (all columns having the same number of rows). A key example would be TX\_JSON in EVM FACT\_TRANSACTION tables which include 50+ extra details from transaction logs. But other examples like `NULL` values in TO\_ADDRESS can have similar issues. Default `TRUE`. |
| Value         | Always returns a data frame. If 'try\_simplify' is `FALSE` OR if `try_simplify = TRUE` fails (columns having different number of rows) then the data frame is comprised of lists, where each column must be coerced to a desired class (e.g., with `as.numeric()`) to ensure each column has the same number of rows.                                                                       |

Note: The vast majority (95%+) of queries will return a simple data frame with the classes coerced intelligently (e.g., Block\_Number being numeric). But check the warnings and check your column classes, if the class is a list then try\_simplify failed (i.e., not all columns have the same number of rows when coerced).

```
#example
query = create_query_token("SELECT * FROM ETHEREUM.CORE.FACT_TRANSACTIONS LIMIT 10000", api_key)
request = get_query_from_token(query$token, api_key, 1, 10000)
clean_query(request, try_simplify = FALSE) # returns data frame of lists()
```
