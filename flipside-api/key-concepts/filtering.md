# Filtering

The Query API allows you to filter the results of your Query Result Set. This is useful if you run a large query and want to retrieve subsets of the results without re-executing the entire query. It can also be useful if you're building a front-end application and want to allow your users to filter the result set without putting pressure on client-side resources.

{% hint style="info" %}
Filters do NOT re-execute your query. They filter over the existing result set from a query. Due to some engineering ingenuity, these manipulations are able to be executed "on the fly" when requesting your query results.&#x20;
{% endhint %}

Let's build on the example from the list section and filter our results to only include the Moonbird NFT project.&#x20;

{% tabs %}
{% tab title="Python SDK" %}
```
flipside.get_query_results(
    query_result_set.query_id,
    page_number=1,
    page_size=10000,
    filters=[
      {
        'eq': 'moonbirds',
        'column': 'project_name'
      }
    ]
)
```
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
```javascript
await flipside.query.getQueryResults({
  queryRunId: result.queryId,
  pageNumber: 1,
  pageSize: 1000,
  filters: [
    {
      eq: 'moonbirds',
      column: 'project_name'
    }
  ]
})
```
{% endtab %}
{% endtabs %}

Now let's imagine we only want MoonBirds sales greater than $5k USD. We'd add an additional filter using the greater than or equals to filter ('gte').

{% hint style="info" %}
Note the order of your filters is important, they get applied in the order they are specified.
{% endhint %}

{% tabs %}
{% tab title="Python SDK" %}
```python
flipside.get_query_results(
    query_result_set.query_id,
    page_number=1,
    page_size=10000,
    filters=[
      {
        'eq': 'moonbirds',
        'column': 'project_name'
      },
      {
        'gte': 5000,
        'column': 'price_usd'
      }
    ]
)
```
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
```javascript
await flipside.query.getQueryResults({
  queryRunId: result.queryId,
  pageNumber: 1,
  pageSize: 1000,
  filters: [
    {
      eq: 'moonbirds',
      column: 'project_name'
    },
    {
      gte: 5000,
      column: 'price_usd'
    }
  ]
})
```
{% endtab %}
{% endtabs %}

Let's add one final filter to only include sales that occurred on OpenSea or Blur.

{% tabs %}
{% tab title="Python SDK" %}
```python
flipside.get_query_results(
    query_result_set.query_id,
    page_number=1,
    page_size=10000,
    filters=[
      {
        'eq': 'moonbirds',
        'column': 'project_name'
      },
      {
        'gte': 5000,
        'column': 'price_usd'
      },
      {
        'in': ['opensea', 'blur'],
        'column': 'platform_name'
      }
    ]
)
```
{% endtab %}

{% tab title="JS/TS/Node SDK" %}
```javascript
await flipside.query.getQueryResults({
  queryRunId: result.queryId,
  pageNumber: 1,
  pageSize: 1000,
  filters: [
    {
      eq: 'moonbirds',
      column: 'project_name'
    },
    {
      gte: 5000,
      column: 'price_usd'
    },
    {
      in: ['opensea', 'blur'],
      column: 'platform_name'
    }
  ]
})
```
{% endtab %}
{% endtabs %}

Here is a table of all available filters:

| Name                     | Operator (used in SDK) |
| ------------------------ | ---------------------- |
| Equals                   | `eq`                   |
| Not Equals               | `neq`                  |
| Greater Than             | `gt`                   |
| Greater Than or Equal To | `gte`                  |
| Less Than                | `lt`                   |
| Less Than or Equal To    | `lte`                  |
| Like                     | `like`                 |
| In                       | `in`                   |
| Not In                   | `notIn`                |

{% hint style="info" %}
In the next section, we'll discuss how you are debited/billed for a query's execution time using the billable metrics, Query Seconds.
{% endhint %}
