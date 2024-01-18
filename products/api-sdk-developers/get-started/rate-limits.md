# Rate Limits

**Max Concurrent Queries**

Every account has a limit of 15 concurrent query runs. This means you cannot run more than 15 queries at the same time across all your API keys. This rate limit is in place to protect query spamming (_whether accidental or intentional_) for the benefit of all API/SDK users.&#x20;

**Query Execution Result Limits**

Query results are not limited by row size but by data size. All query results have a hard upper limit of 1GB. If you execute a query that returns more than 1GB of data you will receive an error message.

**Query Page Result Limits**

When requesting a page of a query result set the size of the result set cannot exceed 30mb. If you exceed 30mb an error will be thrown with a recommendation on the proper page size to use.

{% hint style="info" %}
**Require higher limits?** Contact us about our Enterprise solutions by sending an email to data-shares@flipsidecrypto.com with the subject line "_Enterprise API Inquiry_"
{% endhint %}
