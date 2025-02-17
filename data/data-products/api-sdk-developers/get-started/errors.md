# Errors

The SDK implements the following errors that can be handled when calling the `query` method:

### **Query RunTime Errors**

**`QueryRunRateLimitError`**

Occurs when you have exceeded the rate limit for creating/running new queries.&#x20;

{% tabs %}
{% tab title="Python SDK" %}
```python
from flipside.errors import QueryRunRateLimitError

try:
    sdk.query(sql)
except QueryRunRateLimitError as e:
    print(f"you have been rate limited: {e.message}")
```
{% endtab %}
{% endtabs %}

**`QueryRunTimeoutError`**

Occurs when your query has exceeded the `timeout_minutes` parameter passed into the `query` method.&#x20;

{% tabs %}
{% tab title="Python SDK" %}
```python
from flipside.errors import QueryRunTimeoutError

try:
    sdk.query(sql, timeout_minutes=10)
except QueryRunTimeoutError as e:
    print(f"your query has taken longer than 10 minutes to run: {e.message}")
```
{% endtab %}
{% endtabs %}

**`QueryRunExecutionError`**

Occurs when your query fails to compile/run due to malformed SQL statements.

{% tabs %}
{% tab title="Python SDK" %}
```python
from flipside.errors import QueryRunExecutionError

try:
    sdk.query(sql)
except QueryRunExecutionError as e:
    print(f"your sql is malformed: {e.message}")
```
{% endtab %}
{% endtabs %}

### **Server Error**

`ServerError` - occurs when there is a server-side error that cannot be resolved. This typically indicates an issue with Flipside Crypto's query engine API. If the issue persists please contact support in the Flipside Crypto discord server.

{% tabs %}
{% tab title="Python SDK" %}
```python
from flipside.errors import ServerError

try:
    sdk.query(sql)
except ServerError as e:
    print(f"a server-side error has occurred: {e.message}")
```
{% endtab %}
{% endtabs %}

### **API Error**

`ApiError` - this typically occurs when you, the user, submit a bad request to the API. This often occurs when an invalid API Key is used, or invalid object IDs are requested.

{% tabs %}
{% tab title="Python SDK" %}
```python
from flipside.errors import ApiError

try:
    sdk.query(sql)
except ApiError as e:
    print(f"an api error has occurred: {e.message}")
```
{% endtab %}
{% endtabs %}

### **SDK Error**

`SDKError` - this error is raised when a generic client-side error occurs that cannot be accounted for by the other errors. SDK level errors should be reported [here](https://github.com/FlipsideCrypto/sdk/issues) as a Github Issue with a full stack-trace and detailed steps to reproduce.

{% tabs %}
{% tab title="Python SDK" %}
```python
from flipside.errors import SDKError

try:
    sdk.query(sql)
except SDKError as e:
    print(f"a client-side SDK error has occurred: {e.message}")
```
{% endtab %}
{% endtabs %}
