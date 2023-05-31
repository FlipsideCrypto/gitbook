# ShroomDK Migration Guide

## Migration Guide: ShroomDK to API v2

As we continue to innovate, we're transitioning from our legacy API/SDK, ShroomDK, to our new and improved API v2. This upgraded API enables users to execute complex SQL queries on Flipside's Blockchain Data Sets and provides enhanced scalability and performance.

For additional details and guidance, visit our [API Documentation](https://docs.flipsidecrypto.com/flipside-api/getting-started).&#x20;

If you need to generate new API keys or want to monitor your usage, visit your [account page](https://flipsidecrypto.xyz/account/api-keys).

### **Migrating to API v2: Key Steps**

Here are the key steps for migrating to API v2:

1. [Updating SDKs ](shroomdk-migration-guide.md#1.-updating-sdks)
2. [Modifying API Endpoint URLs ](shroomdk-migration-guide.md#2.-modifying-api-endpoint-urls)
3. [Handling Changes in JSON Responses](shroomdk-migration-guide.md#3.-handling-changes-in-json-responses)

#### 1. Updating SDKs

For Python or JavaScript SDK users, please update to the latest versions:

{% tabs %}
{% tab title="Python" %}
```
pip install flipside
```

Then, create a new Flipside instance with your API key and the new API endpoint:

```python
flipside = Flipside("<YOUR_API_KEY>", "https://api-v2.flipsidecrypto.xyz")
```
{% endtab %}

{% tab title="JavaScript" %}
```
npm install @flipsidecrypto/sdk
```

Subsequently, instantiate a new Flipside object using your API key and the new API endpoint:

```javascript
const flipside = new Flipside("<YOUR_API_KEY>", "https://api-v2.flipsidecrypto.xyz");
```
{% endtab %}
{% endtabs %}

The updated SDKs will automatically target the new API v2 endpoints.

#### 2. Modifying API Endpoint URLs

If you're directly accessing the API, replace all ShroomDK API URLs in your codebase with the new v2 API URL: `https://api-v2.flipsidecrypto.xyz`.

#### 3. Handling Changes in JSON Responses

API v2 introduces changes to JSON responses. Adjust your response handling code to match these new specifications. Detailed information on the new JSON responses is available on our [API documentation page](https://api-docs.flipsidecrypto.xyz/).

After making these changes, be sure to thoroughly test your applications to confirm smooth functionality with API v2. For any issues encountered during the migration, please reach out to our support team.\
\
