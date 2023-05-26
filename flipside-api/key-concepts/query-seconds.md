# Query Seconds

Query Seconds represent computational time against Flipside's data warehouse, canonically referred to as a DataSource. Every QueryRun has the following life cycle.&#x20;

<figure><img src="../../.gitbook/assets/Untitled (4).png" alt=""><figcaption></figcaption></figure>

A query run that is in the state `QUERY_STATE_READY` has been queued for execution. Once it begins execution it transitions to `QUERY_STATE_RUNNING`. From here it can transition to a number of states. If the query executes against the data source successfully it will transition to `QUERY_STATE_STREAMING_RESULTS` and begin downloading the query results for you to export.&#x20;

If the query failed for any reason (_syntax error, warehouse issue, etc._) the query will transition to a state of `QUERY_STATE_FAILED`. If the user decides to explicitly cancel the query the query run will be terminated and its state will transition to `QUERY_STATE_CANCELED`. Finally, if the QueryRun finishes downloading its results from the data source it will transition to `QUERY_STATE_SUCCESS` .

Given the above life-cycle for a QueryRun, let's walk thru a real example to determine how you might be billed for a query. Here is a query we're going to execute to find the address associated with an ENS domain.

```sql
SELECT
  origin_from_address
FROM ethereum.core.fact_event_logs
WHERE
  contract_address = lower('0x283af0b28c62c092c9727f1ee09c02ca627eb7f5')
  AND event_inputs:name = lower('{ens_domain}')
  AND event_name = 'NameRegistered'
  AND block_timestamp >= GETDATE() - interval'4 year'
```

This query will produce four different time stamps:

1. **TotalElapsedSeconds** - the time difference between a terminal state (`QUERY_STATE_SUCCESS` , `QUERY_STATE_FAILED`  or `QUERY_STATE_CANCELED` ), and `QUERY_STATE_READY` .
2. **StreamingSeconds** - the time difference between `QUERY_STATE_SUCCESS` and `QUERY_STATE_STREAMING_RESULTS`
3. **ExecutionSeconds** - the time difference between `QUERY_STATE_STREAMING_RESULTS` and `QUERY_STATE_RUNNING`
4. **QueuedSeconds** - the time difference between `QUERY_STATE_READY` and `QUERY_STATE_RUNNING`

{% hint style="info" %}
You are only debited/billed for ExecutionSeconds (#3) for a successfully run query. If your query fails or was canceled you are not billed for the ExecutionSeconds.
{% endhint %}

Let's assume this Query has never been executed, meaning no results exist, and as a result, a billable QueryRun is created.

This QueryRun executes successfully for a total of 18 seconds, here is the breakdown:

| Breakdown        | Seconds |
| ---------------- | ------- |
| StreamingSeconds | 4       |
| ExecutionSeconds | 12      |
| QueuedSeconds    | 1       |

Since you are only billed for ExecutionSeconds you would be debited for 12 seconds. At a rate of $0.02 per query second, you would be billed $0.24 (12 Execution Query Seconds \* $0.02/query second).

{% hint style="info" %}
In the next section will discuss controlling query execution (and costs) by using the parameter `maxAgeMinutes`.
{% endhint %}
