---
description: These functions convert from hexadecimal to string and integer formats
---

# 💡 Hex Converters

## UDF\_HEX\_TO\_INT()

Converts from hexadecimal to integer. The number is returned as a string to avoid any big number limitations.

### Syntax

```sql
utils.udf_hex_to_int(
    [encoding,]
    hex
)
```

### Arguments

**Required:**

* `hex` (string): The hex string to convert

**Optional:**

* `encoding` (string): The encoding to use. Valid values are `s2c` and `hex`. This parameter is optimal.&#x20;
  * Default: `hex`

### Sample Queries

```sql
-- These are all the same.
select
  utils.udf_hex_to_int ('1E240')::int as int1,
  utils.udf_hex_to_int ('0x1E240')::int as int2,
  utils.udf_hex_to_int ('hex','0x1E240')::int as int3;

-- Hex to Signed 2's Complement Integer. These are the same.
select
  livequery.utils.udf_hex_to_int ('s2c','FFFE1DC0')::int as int1,
  livequery.utils.udf_hex_to_int ('s2c','0xFFFE1DC0')::int as int2
```

## UDF\_INT\_TO\_HEX()

### Synatx

```
utils.udf_int_to_hex(
    int
)
```

### Arguments

**Required:**&#x20;

* `int` (integer): The integer to conver&#x20;

### Sample Query

```sql
select
  utils.udf_int_to_hex(123)::string as hex
```

## UDF\_HEX\_TO\_STRING()

Converts from hexadecimal to string. It will handle obscure characters like emojis and special characters.&#x20;

### Syntax

```
utils.udf_hex_to_string(
  hex
)
```

### Arguments

**Required:**

* `hex` (string): The hex string to convert&#x20;

### Sample Query

```
select utils.udf_hex_to_string('4469616D6F6E642048616E6473') as text1;
```

## UDF\_BASE58\_TO\_HEX()

Converts from base58 to hexadecimal. Typically used for encoding Solana public keys and instructions.

### Syntax

```
utils.udf_base58_to_hex(
  base58
)
```

### Arguments

**Required:**

* `base58` (string): The base58 string to convert. This cannot be NULL. Output will contain the `0x` prefix. If 32 byte outputs are required, append leading zeroes on encoded outputs <= 64 characters (excluding `0x`).

### Sample Query

```
select utils.udf_base58_to_hex('3EdUJnbcGFLs') as text1;
```

## UDF\_HEX\_TO\_BASE58()

Converts from hexadecimal to base58. Typically used for decoding within EVM to non-EVM environments, such as Solana.

### Syntax

```
utils.udf_hex_to_base58(
  hex
)
```

### Arguments

**Required:**

* `hex` (string): The hex string to convert. This cannot be NULL and must contain the '0x' prefix.

### Sample Query

```
select utils.udf_hex_to_base58(
    '0x0ed19fefacde5ce40f9a33e6d366f4198f8a00e5b9ae75c306fbb553de9e7e1b') as text1;
```

## UDF\_HEX\_TO\_BECH32()

Converts from hexadecimal to bech32. Typically used for decoding within EVM to non-EVM environments, such as IBC. Requires both a hex string input and HRP (human-readable part), which is chain specific. Please refer to the respective blockchain's documentation for proper HRP input.

### Syntax

```
utils.udf_hex_to_bech32(
  hex,
  hrp
)
```

### Arguments

**Required:**

* `hex` (string): The hex string to convert. This cannot be NULL and must contain the '0x' prefix.
* `hrp` (string): The human-readable part to be included within the decoding algorithm. This is empty by default, but is required for proper decoding.&#x20;

### Sample Query

```
--OSMOSIS
select utils.udf_hex_to_bech32(
    '0x52391ba8acdffc2776ba0ccce8d4c45dd2cbb10f','osmo') as text1;

--SEI
select utils.udf_hex_to_bech32(
    '0x617c7dbac8e4a908f1ac66fdc294b977df527f0f','sei') as text2;

--TERRA
select utils.udf_hex_to_bech32(
    '0x108545dfbddb074d278a7e9488ab6174aea62aa3','terra') as text3;
```
