---
description: This function will decode EVM Logs given the appropriate ABI
---

# 💡 EVM Logs Decoder

## UDF\_EVM\_DECODE\_LOG()

{% hint style="warning" %}
Please note there are limitations on this function. It is not recommend to process more than 100,000 records at a time. Anything over that will likely cause timeouts. If you need large amounts of decoded data, please use the snowflake tables.&#x20;
{% endhint %}

### Syntax

```
utils.udf_evm_decode_log(
    abi, 
    data
)
```

### Arguments

**Required:**

* `abi` (array) - The ABI (application binary interface) for the smart contract&#x20;
* `data` (object) - The event data to decode

### Sample Queries&#x20;

```sql
-- This will decode logs for Seaport 1.5
SELECT 
    block_number,
    tx_hash,
    event_index,
    OBJECT_CONSTRUCT('topics', topics, 'data', data, 'address', contract_address) AS event_data,
    abi,
    utils.udf_evm_decode_log(abi, event_data) AS decoded_data,
    decoded_data[0]:name::string AS event_name
FROM 
    ethereum.core.fact_event_logs
JOIN 
    ethereum.core.dim_contract_abis
USING 
    (contract_address)
WHERE 
    block_timestamp > current_date - 2
    AND contract_address = LOWER('0x00000000000000ADc04C56Bf30aC9d3c0aAF14dC') --seaport 1.5
    AND tx_status = 'SUCCESS'
LIMIT 
    10;


-- USDC (Proxy Contract) Example 
-- this query will decode transfer events for USDC using the latest proxy ABI
-- if you are decoding across large ranges, you may need to incorporate the start and end block

WITH contract_abi AS (
    SELECT
        abi,
        parent_contract_address AS contract_address,
        event_signature,
        start_block,
        end_block
    FROM
        crosschain.core.dim_evm_event_abis
    WHERE
        blockchain = 'ethereum'
        AND parent_contract_address = LOWER('0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48') -- USDC
        AND event_name = 'Transfer' -- Transfer event
    QUALIFY ROW_NUMBER() OVER (ORDER BY end_block DESC) = 1 -- USDC has more than one proxy, we want the latest
)

SELECT
    block_number,
    tx_hash,
    event_index,
    topics,
    data,
    OBJECT_CONSTRUCT('topics', topics, 'data', data, 'address', a.contract_address) AS event_data,
    abi,
    utils.udf_evm_decode_log(abi, event_data) AS decoded_data,
    decoded_data[0]:name::string AS event_name
FROM
    ethereum.core.fact_event_logs l
JOIN
    contract_abi a
    ON a.contract_address = l.contract_address
    AND a.event_signature = l.topics[0]::string
WHERE
    block_timestamp > current_date - 2
    AND tx_status = 'SUCCESS'
LIMIT 10;

```

### Other Notes

* The Flipside tables contain millions of ABIs (`dim_contract_abis`). We likely have the one you are looking for. If we do not, please submit ABIs [here](https://science.flipsidecrypto.xyz/abi-requestor/). Submitted ABIs will be available within 36 hours.&#x20;
* Contracts that use proxies can prove challenging. If contract A is emitting events, but it uses proxy contract B, you likely need to use the ABI from contract B to decode the emitted events from contract A.
* If we do not have the ABI, and you do, but do not want to give it to us or wait for us to ingest it, you can input ABIs manually into this function. You will likely need to wrap your ABI text in a `parse_json()` function.&#x20;
* You can input ABIs at an individual event level if you choose, however if you are looking at more than one type of emitted event, you maybe need to add additional join keys on the topics / event signature. `crosschain.core.dim_evm_event_signatures` might be helpful for you here, along with the keccak256 function.&#x20;
