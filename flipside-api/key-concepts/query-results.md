# Query Results

After executing a query the query results can be accessed via the SDK in a query result set object.

{% tabs %}
{% tab title="Python SDK" %}


Query Results are stored in the `QueryResultSet` object. This object is returned by:

* `Flipside.run`
* `Flipside.get_query_results`

```python
class QueryResultSet(BaseModel):
    query_id: Union[str, None] = Field(None, description="The server id of the query")

    status: str = Field(
        False, description="The status of the query (`PENDING`, `FINISHED`, `ERROR`)"
    )
    columns: Union[List[str], None] = Field(
        None, description="The names of the columns in the result set"
    )
    column_types: Union[List[str], None] = Field(
        None, description="The type of the columns in the result set"
    )
    rows: Union[List[Any], None] = Field(None, description="The results of the query")
    run_stats: Union[QueryRunStats, None] = Field(
        None,
        description="Summary stats on the query run (i.e. the number of rows returned, the elapsed time, etc)",
    )
    records: Union[List[Any], None] = Field(
        None, description="The results of the query transformed as an array of objects"
    )
    page: Union[PageStats, None] = Field(
        None, description="Summary of page stats for this query result set"
    )
    error: Any
```
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
Query Results are stored in a `QueryResultSet` object. This object is returned by:

* `Flipside.query.run`
* `Flipside.query.getQueryResults`

```typescript
interface QueryResultSet {
  // The server id of the query
  queryId: string | null;

  // The status of the query (`PENDING`, `FINISHED`, `ERROR`)
  status: QueryStatus | null;

  // The names of the columns in the result set
  columns: string[] | null;

  // The type of the columns in the result set
  columnTypes: string[] | null;

  // The results of the query
  rows: any[] | null;

  // Summary stats on the query run (i.e. the number of rows returned, the elapsed time, etc)
  runStats: QueryRunStats | null;

  // The results of the query transformed as an array of objects
  records: QueryResultRecord[] | null;

  // The page of results
  page: PageStats | null;

  // If the query failed, this will contain the error
  error:
    | ApiError
    | QueryRunRateLimitError
    | QueryRunTimeoutError
    | QueryRunExecutionError
    | ServerError
    | UserError
    | UnexpectedSDKError
    | null;
}
```
{% endtab %}
{% endtabs %}

Results are accessible via `rows` and `records`. Rows is an array of arrays (CSV format), while records are an array of objects where the keys are the column names.

### Run Stats

Run stats provide a summary of the entire result set from the number of rows returned, the number of bytes returned, and a breakdown of time spent on each part of the query run's lifecycle.

{% tabs %}
{% tab title="Python SDK" %}
Python QueryRunStats object, which can be accessed on the QueryResultSet via `run_stats`

```python
class QueryRunStats(BaseModel):
    started_at: datetime = Field(None, description="The start time of the query run.")
    ended_at: datetime = Field(None, description="The end time of the query run.")
    query_exec_started_at: datetime = Field(
        None, description="The start time of query execution."
    )
    query_exec_ended_at: datetime = Field(
        None, description="The end time of query execution."
    )
    streaming_started_at: datetime = Field(
        None, description="The start time of streaming query results."
    )
    streaming_ended_at: datetime = Field(
        None, description="The end time of streaming query results."
    )
    elapsed_seconds: int = Field(
        None,
        description="The number of seconds elapsed between the start and end times.",
    )
    queued_seconds: int = Field(
        None,
        description="The number of seconds elapsed between when the query was created and when execution on the data source began.",
    )
    streaming_seconds: int = Field(
        None,
        description="The number of seconds elapsed between when the query execution completed and results were fully streamed to Flipside's servers.",
    )
    query_exec_seconds: int = Field(
        None,
        description="The number of seconds elapsed between when the query execution started and when it completed on the data source.",
    )
    record_count: int = Field(
        None, description="The number of records returned by the query."
    )
    bytes: int = Field(None, description="The number of bytes returned by the query.")
```

{% hint style="info" %}
`query_exec_seconds` represents the number of QuerySeconds used by the query that you will be billed/debited for. Note you are not billed/debited for queued, streaming, or total seconds, only execution seconds. For more information on QuerySeconds see the [QuerySeconds section here](query-seconds.md).
{% endhint %}
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
QueryRunStats which can be accessed on the QueryResultSet via `runStats`.

```typescript
type QueryRunStats = {
  startedAt: Date;
  endedAt: Date;
  elapsedSeconds: number;
  queryExecStartedAt: Date;
  queryExecEndedAt: Date;
  streamingStartedAt: Date;
  streamingEndedAt: Date;
  queuedSeconds: number;
  streamingSeconds: number;
  queryExecSeconds: number;
  bytes: number; // the number of bytes returned by the query
  recordCount: number;
};

```

{% hint style="info" %}
queryExecSeconds represents the number of QuerySeconds used by the query that you will be billed/debited for. Note you are not billed/debited for queued, streaming, or total seconds, only execution seconds. For more information on QuerySeconds see the [QuerySeconds section here](query-seconds.md).
{% endhint %}
{% endtab %}
{% endtabs %}

### Page

The `page` object returns stats about the current page of results as well as the total available pages given the specified page size you provided when requesting the results.&#x20;

For example, if there are 1 million rows returned by a query and you request results with a page size of 10,000 rows, the total number of pages will be 100.

{% tabs %}
{% tab title="Python SDK" %}
```python
class PageStats(BaseModel):
    currentPageNumber: int
    currentPageSize: int
    totalRows: int
    totalPages: int

```

Assuming we have `query_result_set` variable you can access the total number of pages simply by calling:

```
print(query_result_set.page.totalPages)
```
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
```typescript
interface PageStats {
  currentPageNumber: number;
  currentPageSize: number;
  totalRows: number;
  totalPages: number;
}

```

Assuming we have `queryResultSet` variable you can access the total number of pages simply by calling:

```
console.log(queryResultSet.page.totalPages)
```
{% endtab %}
{% endtabs %}

In the next example we'll show you how to use `PageStats` to iterate over a Query Result Set.
