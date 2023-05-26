# Sorting

In this section, we'll explore how to use server-side sorting to sort your query result set. All sorting is done over the entire query result set, server-side by the Flipside Query Engine.

Server-side result sorting is especially useful for large result sets where your client-side environment may be memory/resource constrained.

Building off the example from the previous section let's sort our results in descending order by `price_usd` descending. &#x20;

{% tabs %}
{% tab title="Python SDK" %}
```python
flipside.get_query_results(
    query_result_set.query_id,
    page_number=1,
    page_size=10000,
    sort_by=[
      {
        'column': 'price_usd',
        'direction': 'desc'
      }
    ]
)
```
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
```javascript
await flipside.query.getQueryResults({
  queryRunId: queryResultSet.queryId,
  pageNumber: 1,
  pageSize: 10000,
  sortBy: [
    {
      column: 'price_usd',
      direction: 'desc'
    }
  ]
})
```
{% endtab %}
{% endtabs %}

Valid directions include `desc` and `asc`. You may also sort by multiple columns. The order you provide the sort by objects determines which sort by object takes precedence.

The following example will first sort results in descending order by `price_usd` and then in ascending order by `project_name`.

{% tabs %}
{% tab title="Python SDK" %}
```python
flipside.get_query_results(
    query_result_set.query_id,
    page_number=1,
    page_size=10000,
    sort_by=[
      {
        'column': 'price_usd',
        'direction': 'desc'
      },
      {
        'column': 'project_name',
        'direction': 'asc'
      }
    ]
)
```
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
```javascript
await flipside.query.getQueryResults({
  queryRunId: queryResultSet.queryId,
  pageNumber: 1,
  pageSize: 10000,
  sortBy: [
    {
      column: 'price_usd',
      direction: 'desc'
    },
    {
      column: 'project_name',
      direction: 'asc'
    }
  ]
})
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
In the next section, we'll walk thru how to perform server-side filtering of your query result set.
{% endhint %}
