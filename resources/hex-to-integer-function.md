---
description: >-
  A convenience function to convert hex values to integers, useful when working
  with raw EVM event logs and transactions.
---

# Hex-to-Integer Function

**Function name**: `utils.udf_hex_to_int()`



**What is it used for**: converts hex values into integer



**When to use**:&#x20;

When working with raw event logs and data inside the fact\_transactions and fact\_event\_logs tables, you will encounter hexadecimal values, similar to what you find on Etherscan in the ‘Input data’ section or the ‘Logs’ section.

Often you will want to convert these values into integers to get the decoded values. For example, in our Example 2 below, decoding the hex value gives us the NFT token ID. Note that you can use this function is relevant for any EVM data and is not limited to Ethereum data only.&#x20;



**How to use**:

**Example 1**

```sql
Select 
utils.udf_hex_to_int (‘0000000000000000000000000000000000000000000000000000000000001ffb’)
```

This would produce ‘8187’ as the result. Note that removing the leading 0’s, to just ‘1ffb’ would also produce the same result.

**Example 2**

Consider this[ Etherscan transaction](https://etherscan.io/tx/0xfff5bcbefe615b3409f7c280445e2dc20785a0b5ac82bf465f1e031917bf88df):&#x20;

If we queried the input\_data column for this transaction in the ethereum.core.fact\_transactions table, we’d get:&#x20;

```
0x5138b08c000000000000000000000000b932a70a57673d89f4acffbe830e8ed7f75fb9e00000000000000000000000000000000000000000000000000000000000001ffb
```

We can rearrange the data above to what we see on Etherscan in the screenshot below:&#x20;

0x5138b08c\
000000000000000000000000b932a70a57673d89f4acffbe830e8ed7f75fb9e0\
0000000000000000000000000000000000000000000000000000000000001ffb

<figure><img src="../.gitbook/assets/Screenshot 2022-09-14 at 10.33.11 AM.png" alt=""><figcaption></figcaption></figure>

We can use the substr function to get the string that is associated with ‘auctionId’.

```sql
Select 
substr(input_data, 75, 64) 
from ethereum.core.fact_transactions 
    where block_number = 12994101
    and tx_hash = '0xfff5bcbefe615b3409f7c280445e2dc20785a0b5ac82bf465f1e031917bf88df'
```

And because it is an integer, we can use the hex to int function to convert it to an integer.

```sql
select 
utils.udf_hex_to_int( substr(input_data, 75, 64) ) 
from ethereum.core.fact_transactions 
    where block_number = 12994101
    and tx_hash = '0xfff5bcbefe615b3409f7c280445e2dc20785a0b5ac82bf465f1e031917bf88df'
```

This would result in 8187 which is consistent with using the decode button on Etherscan as shown in the screenshot below.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-14 at 10.33.24 AM.png" alt=""><figcaption></figcaption></figure>

There are also more utility functions available [here](../products/get-started/examples/utility-functions/).&#x20;
