# 💡 Seaport: Real-time Orders

In this example, we'll use the LiveQuery table function `tf_latest_contract_events_decoded` to retrieve real-time orders from the Seaport contract.

{% hint style="warning" %}
If you'd like to follow along in your own Flipside Studio Account please make sure you've added the QuickNode integration to your account. QuickNode [instructions here](../../add-ons/quicknode-setup-guide.md).&#x20;
{% endhint %}

Here we will query the Seaport Version 1.5 Contract on the Ethereum Mainnet, address: [`0x00000000000000ADc04C56Bf30aC9d3c0aAF14dC`](https://etherscan.io/address/0x00000000000000ADc04C56Bf30aC9d3c0aAF14dC#events)

```sql
SELECT
*
FROM TABLE(
    ethereum_mainnet.tf_latest_contract_events_decoded(lower('0x00000000000000ADc04C56Bf30aC9d3c0aAF14dC'))
);
```

{% hint style="warning" %}
Note you must wrap the call to the function in `TABLE()` since this function returns a table structure.&#x20;
{% endhint %}

The above example will return a table with the following columns:

| Column            | Type    |
| ----------------- | ------- |
| status            | varchar |
| blockchain        | varchar |
| network           | varchar |
| tx\_hash          | varchar |
| block\_number     | number  |
| event\_index      | number  |
| event\_name       | varchar |
| contract\_address | varchar |
| event\_topics     | array   |
| event\_data       | varchar |
| decoded\_data     | object  |

Now that we've covered the basics let's extract the offers from the decoded events:

```sql
WITH realtime_events AS (
  SELECT
   block_number,
   tx_hash,
   event_index,
   event_name,
   decoded_data
  FROM TABLE(
    ethereum_mainnet.tf_latest_contract_events_decoded('0x00000000000000ADc04C56Bf30aC9d3c0aAF14dC')
  )
)
SELECT
  block_number,
  tx_hash,
  event_index,
  event_name,
  decoded_data:offerer::varchar as offerer_address,
  decoded_data:orderHash::varchar as order_hash,
  value as offer
FROM realtime_events, LATERAL FLATTEN (input => decoded_data:offer)
ORDER BY block_number DESC, event_index DESC
```

The above SQL uses a CTE to retrieve the latest events from the Seaport Contract and then uses the `LATERAL FLATTEN` function to explode out each `offer` in the `decoded_data` object into its own row. We also retrieve the `offerer`, and `orderHash` from the `decoded_data` object.

