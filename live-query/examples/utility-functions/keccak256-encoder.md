---
description: This function returns the keccak256 hash of the input string.
---

# 💡 Keccak256 Encoder

## UDF\_KECCAK256()

### Syntax

```
utils.udf_keccak256(
  text_signature
)
```

### Arguments

**Required:**

* `text_signature` (string): The text to hash

### Sample Query&#x20;

```sql
Select utils.udf_keccak256('Transfer(address,address,uint256)') as hex_signature
```
