# Python SDK

[![Python Continuous Testing](https://github.com/FlipsideCrypto/sdk/actions/workflows/ci\_python.yml/badge.svg)](https://github.com/FlipsideCrypto/sdk/actions/workflows/ci\_python.yml)

_**To skip the walkthrough and go straight to dedicated API Documentation,**_ [_**click here**_](https://api-docs.flipsidecrypto.xyz/)_**.**_

### 💾 Install the SDK

**Python 3.7 and above, is required to use `flipside`**

_If you don't already have an API Key get one for free_ [_here in Flipside's Data Studio_](https://flipsidecrypto.xyz/account/api-keys)_._

```
pip install flipside
```

### 🦾 Getting Started

{% hint style="warning" %}
_**For legacy ShroomDK users:** you can still import ShroomDK from flipside: i.e. `from flipside import ShroomDK`_
{% endhint %}

```python
from flipside import Flipside

# Initialize `Flipside` with your API Key
sdk = Flipside("<YOUR_API_KEY>")

# Parameters can be passed into SQL statements 
# via native string interpolation
my_address = "0x...."
sql = f"""
    SELECT 
        nft_address, 
        mint_price_eth, 
        mint_price_usd 
    FROM ethereum.core.ez_nft_mints 
    WHERE nft_to_address = LOWER('{my_address}')
"""

# Run the query against Flipside's query engine 
# and await the results
query_result_set = sdk.query(sql)

# Iterate over the results
for record in query_result_set.records:
    nft_address = record['nft_address']
    mint_price_eth = record['mint_price_eth']
    mint_price_usd = record['mint_price_usd']
    print(f"${nft_address} minted for {mint_price_eth}ETH (${mint_price_usd})")
```



### The Details

**Executing a Query**

When executing a query the following parameters can be passed into the `query` method on the `ShroomDK` object:

| Argument                 | Description                                                                                                                                                                                                                                                                                        | Default Value   |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- |
| sql                      | The sql string to execute                                                                                                                                                                                                                                                                          | None (required) |
| max\_age\_minutes        | The the max age of results you are willing to accept before a query is re-executed. For example: if set to 15, you are willing to accept cached results that were generated within the last 15 minutes, if not a query execution is triggered. A value of 0 will always trigger a query execution. | 0               |
| timeout\_minutes         | The number of minutes until your query run times out                                                                                                                                                                                                                                               | 20              |
| retry\_interval\_seconds | The number of seconds to wait between polls to the server                                                                                                                                                                                                                                          | 1               |
| page\_size               | The number of rows/records to return                                                                                                                                                                                                                                                               | 100,000         |
| page\_number             | The page number to return (starts at 1)                                                                                                                                                                                                                                                            | 1               |

Let's create a query to retrieve all NFTs minted by an address:

```python
my_address = "0x...."
sql = f"""
    SELECT 
        nft_address, 
        mint_price_eth, 
        mint_price_usd 
    FROM ethereum.core.ez_nft_mints 
    WHERE nft_to_address = LOWER('{my_address}')
    LIMIT 100
"""
```

Now let's execute the query and retrieve the first 5 rows of the result set. Note we will set `page_size` to 5 and `page_number` to 1 to retrieve just the first 5 rows.

```python
query_result_set = sdk.query(
    sql,
    max_age_minutes=0,
    timeout_minutes=20,
    retry_interval_seconds=1,
    page_size=5,
    page_number=1
)
```

**Understanding MaxAgeMinutes, aka Caching**

The results of this query will be saved for 60 minutes, given the `ttl_minutes` the parameter is set to 60.

However, note the `max_age_minutes` parameter. This parameter controls whether the query itself is re-executed on subsequent calls to `sdk.query`. The `max_age_minutes` parameter instructs the API how many minutes you are willing to accept cached results up to before a new query execution is triggered.&#x20;

If `max_age_minutes` is set to 0, every call to `sdk.query` will re-execute the query and will count against your query\_seconds. If `max_age_minutes` is set to 15, subsequent calls to `sdk.query` will not re-execute for up to 15 minutes, because there are results available less than 15 minutes old.



**📄 Pagination**

If we wanted to retrieve the next 5 rows of the query result set simply increment the `page_number` to 2 and use the `get_query_results` function:

```python
page2_results = sdk.get_query_results(
    query_result_set.query_id,
    page_number=2,
    page_size=100
)
```

All query runs can return a maximum of 1 GB and a maximum of 100k records can be returned in a single page.

Now let's examine the query result object that's returned.



**The `QueryResultSet` Object**

After executing a query the results are stored in a `QueryResultSet` object:

```python
class QueryResultSet(BaseModel):
    query_id: Union[str, None] = Field(None, description="The server id of the query")
    status: str = Field(False, description="The status of the query (`PENDING`, `FINISHED`, `ERROR`)")
    columns: Union[List[str], None] = Field(None, description="The names of the columns in the result set")
    column_types: Union[List[str], None] = Field(None, description="The type of the columns in the result set")
    rows: Union[List[Any], None] = Field(None, description="The results of the query")
    run_stats: Union[QueryRunStats, None] = Field(
        None,
        description="Summary stats on the query run (i.e. the number of rows returned, the elapsed time, etc)",
    )
    records: Union[List[Any], None] = Field(None, description="The results of the query transformed as an array of objects")
    error: Any
```

Let's iterate over the results from our query above.\
\
Our query selected `nft_address`, `mint_price_eth`, and `mint_price_usd`. We can access the returned data via the `records` parameter. The column names in our query are assigned as keys in each record object.

```python
for record in query_result_set.records:
    nft_address = record['nft_address']
    mint_price_eth = record['mint_price_eth']
    mint_price_usd = record['mint_price_usd']
    print(f"${nft_address} minted for {mint_price_eth}E ({mint_price_usd})USD")
```

Other useful information can be accessed on the query result set object such as run stats, i.e. how long the query took to execute:

```python
started_at = query_result_set.run_stats.started_at
ended_at = query_result_set.run_stats.ended_at
elapsed_seconds = query_result_set.run_stats.elapsed_seconds
record_count = query_result_set.run_stats.record_count

print(f"This query took ${elapsed_seconds} seconds to run and returned {record_count} records from the database.")
```

### 🙈 Error Handling

The SDK implements the following errors that can be handled when calling the `query` method:



**Query Run Time Errors**

**`QueryRunRateLimitError`**

Occurs when you have exceeded the rate limit for creating/running new queries. Example:

```python
from flipside.errors import QueryRunRateLimitError

try:
    sdk.query(sql)
except QueryRunRateLimitError as e:
    print(f"you have been rate limited: {e.message}")
```

**`QueryRunTimeoutError`**

Occurs when your query has exceeded the `timeout_minutes` parameter passed into the `query` method. Example:

```python
from flipside.errors import QueryRunTimeoutError

try:
    sdk.query(sql, timeout_minutes=10)
except QueryRunTimeoutError as e:
    print(f"your query has taken longer than 10 minutes to run: {e.message}")
```

**`QueryRunExecutionError`**

Occurs when your query fails to compile/run due to malformed SQL statements. Example:

```python
from flipside.errors import QueryRunExecutionError

try:
    sdk.query(sql)
except QueryRunExecutionError as e:
    print(f"your sql is malformed: {e.message}")
```



**Server Error**

`ServerError` - occurs when there is a server-side error that cannot be resolved. This typically indicates an issue with Flipside Crypto's query engine API. If the issue persists please contact support in the Flipside Crypto discord server.

```python
from flipside.errors import ServerError

try:
    sdk.query(sql)
except ServerError as e:
    print(f"a server-side error has occurred: {e.message}")
```



**API Error**

`ApiError` - this typically occurs when you, the user, submit a bad request to the API. This often occurs when an invalid API Key is used, or invalid object IDs are requested.

```python
from flipside.errors import ApiError

try:
    sdk.query(sql)
except ApiError as e:
    print(f"an api error has occurred: {e.message}")
```

**SDK Error**

`SDKError` - this error is raised when a generic client-side error occurs that cannot be accounted for by the other errors. SDK level errors should be reported [here](https://github.com/FlipsideCrypto/sdk/issues) as a Github Issue with a full stack-trace and detailed steps to reproduce.

```
from flipside.errors import SDKError

try:
    sdk.query(sql)
except SDKError as e:
    print(f"a client-side SDK error has occurred: {e.message}")
```
