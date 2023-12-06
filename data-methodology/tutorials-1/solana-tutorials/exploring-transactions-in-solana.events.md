# Exploring Transactions in solana.events

Learn how transactions are structured on Solana, and how to analyze Solana projects using the solana.events table.\
\
We’ll first look at transactions for a specific project, [Marinade Finance](https://marinade.finance/), and then we’ll see how to find transactions for _any_ project on Solana. We’ll also show you how to begin analyzing these transactions in Flipside’s solana.events table.

We recommend you create a query in [Flipside’s app](https://app.flipsidecrypto.com/) and follow along!

_Note: this article is written for readers who are new to crypto data analysis **or** readers who have some experience but want to learn more about data on Solana._

_Technical Note: As of this writing Feb 18 2022, Marinade Finance uses two different transaction structures for staking deposits, depending on the amount of mSOL available in their liquidity pools. This article is written using only one of these formats, but the same general analysis strategy applies. The first transaction format is shown_ [_here_](https://solscan.io/tx/ngF3HJPi3g7WwkEXU7L4d8gRuggtLTq9cJ31tLXvhxqyet73oX23iaZiqL3cMv9o573xa4gjKqotrksB7N6unf1)_, the second_ [_here_](https://solscan.io/tx/3LtFYvLTnNiFuwQoDswuA6fqdSwgDiUAdVkq8FcPy5FGm1q8XLzWtQLkaWrhqoGxJTv9LXPhc4GVtn9Kwkqw2YA)_. The difference is in the Inner Instructions of the Deposit instruction.)_

## **Case Study: Marinade Finance**

To motivate our learning let’s start with a practical case study: let’s pretend you’ve been asked to visualize staking deposit transactions on [Marinade Finance](https://marinade.finance/) over time.

How will you find Marinade transaction data in Flipside’s Solana tables? And specifically staking deposit transactions?

## Finding Transactions: **Participate & Analyze!**

Let’s learn a strategy you can use to find transactions related to any project on Solana with data from the solana.events table.

The first step is to _participate_ in the project to generate a transaction. You’ll then _analyze_ that transaction using Flipside’s data and a blockchain explorer like Solscan.

_Participate_

In the context of our case study we visited [Marinade’s app](https://marinade.finance/app/staking), we connected our Phantom wallet, and we staked SOL to receive mSOL — this generated a staking transaction.

_Analyze_

To analyze our transaction we looked up our wallet address on [Solscan](https://solscan.io/) and found our transaction’s signature, and then we used that signature to look up our transaction in Flipside’s data!

If you participated in Flipside’s first Solana Scavenger hunt you probably found your Marinade staking transaction in Flipside’s data using a query like this:

```sql
SELECT *
FROM solana.transactions
where date_trunc('day', block_timestamp) = '2022-01-21 00:00:00.000'
			-- on Solana we *always* add a small date range for query efficiency!
and tx_id = 'ngF3HJPi3g7WwkEXU7L4d8gRuggtLTq9cJ31tLXvhxqyet73oX23iaZiqL3cMv9o573xa4gjKqotrksB7N6unf1'
```

The query above finds a specific transaction in the solana.transactions table, but in this article we’re going to show you how to find Marinade staking transactions using the solana.events table which contains more detail.

Let’s find our transaction in the solana.events table:

```sql
select *
from solana.events
where date_trunc('day', block_timestamp) = '2022-01-21 00:00:00.000'
			-- on Solana we *always* add a small date range for query efficiency!
and tx_id = 'ngF3HJPi3g7WwkEXU7L4d8gRuggtLTq9cJ31tLXvhxqyet73oX23iaZiqL3cMv9o573xa4gjKqotrksB7N6unf1'
```

Take a look at the results — you’ll see much of the same information as in solana.transactions (BLOCK\_ID, BLOCK\_TIMESTAMP, etc.).

Notice that solana.transactions had columns like TX\_FROM\_ADDRESS and TX\_TO\_ADDRESS, but we don’t see these columns in the solana.events table... instead the solana.events table has this information stored in columns called INSTRUCTION and INNER\_INSTRUCTION, and the information is stored inside JSON data structures like these:

_An example value in the INSTRUCTION column of solana.events:_

```json
{
  "accounts": [
    "8szGkuLTAux9XMgZ2vtY39jVSowEcpBfFfD8hXSEqdGC",
    "mSoLzYCxHdYgdzU16g5QSh3i5K3z3KZK7ytfqcJm7So",
    "UefNb6z6yvArqe4cJHTXCqStRsKmWhGxnZzuHbikP5Q",
    "7GgPYjS5Dza89wV6FpZ23kUJRG5vbQ1GM25ezspYFSoE",
    "EyaSjUtSgo9aRD1f8LWXwdvkpDTmXAW54yoSHZRF14WL",
    "Du3Ysj1wKbxPKkuPPnvzQLQh8oMSVifs3jGZjJWXFmHN",
    "2GfVuJm5Hbtf5rr6FeUuNXqpPYzJAq8P9HQg6XsrurxV",
    "9dNe8PGfFU8s8eDQE2uXWG33pxASV2ESHPVnqwcCnYes",
    "3JLPCS1qM2zRw3Dp6V4hZnYHd4toMNPkNesXdX9tg6KM",
    "11111111111111111111111111111111",
    "TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA"
  ],
  "data": "WuE7HjnsyebMnwtCrYDY9d",
  "programId": "MarBmsSgKXdrN1egZf5sqe1TMai9K1rChYNDJgjq7aD"
}
```

_An example value in the INNER\_INSTRUCTION column of solana.events:_

```json
{
  "index": 0,
  "instructions": [
    {
      "parsed": {
        "info": {
          "amount": "116672",
          "authority": "EyaSjUtSgo9aRD1f8LWXwdvkpDTmXAW54yoSHZRF14WL",
          "destination": "9dNe8PGfFU8s8eDQE2uXWG33pxASV2ESHPVnqwcCnYes",
          "source": "7GgPYjS5Dza89wV6FpZ23kUJRG5vbQ1GM25ezspYFSoE"
        },
        "type": "transfer"
      },
      "program": "spl-token",
      "programId": "TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA"
    },
    {
      "parsed": {
        "info": {
          "destination": "UefNb6z6yvArqe4cJHTXCqStRsKmWhGxnZzuHbikP5Q",
          "lamports": 120000,
          "source": "2GfVuJm5Hbtf5rr6FeUuNXqpPYzJAq8P9HQg6XsrurxV"
        },
        "type": "transfer"
      },
      "program": "system",
      "programId": "11111111111111111111111111111111"
    }
  ]
}
```

To begin to understand this JSON data we need to learn more about how transactions are organized on Solana.

**Solana Transactions Are Organized into Programs & Instructions**

Transactions on Solana are organized into programs (similar to smart contracts on Ethereum). These programs execute sets of ‘instructions’. You can think of each program’s instructions as telling Solana to “do this, then do this, then do this, etc...”

Here’s a conceptual outline of how a hypothetical transaction could invoke multiple programs, each with its own set of instructions:

_**Conceptual Outline of a Solana Transaction**_

transaction

* program 1
  * instruction 1
    * inner instruction 1 _\[note: instructions can contain ‘inner instructions’]_
    * inner instruction 2
    * inner instruction 3
* program 2
  * instruction 1 _\[note: often instructions do **not** have ‘inner instructions’]_
* program 3
  * instruction 1
    * inner instruction 1
    * inner instruction 2
  * instruction 2

This hypothetical Solana transaction invoked three programs: the first program had one instruction with three inner instructions; the second program had only one instruction with zero inner instructions, etc.

To make things clearer, let’s create an outline for our Marinade Staking transaction!

_**Outline of our Marinade Staking Transaction**_

transaction

* program 1
  * instruction 1
    * inner instruction 1
    * inner instruction 2

We created this outline by looking at [our transaction on Solscan](https://solscan.io/tx/ngF3HJPi3g7WwkEXU7L4d8gRuggtLTq9cJ31tLXvhxqyet73oX23iaZiqL3cMv9o573xa4gjKqotrksB7N6unf1), and we can use Solscan to add even more detail.

_**More Detail: Outline of our Marinade Staking Transaction**_

transaction: <mark style="background-color:red;">ngF3HJPi3g7WwkEXU7L4d8gRuggtLTq9cJ31tLXvhxqyet73oX23iaZiqL3cMv9o573xa4gjKqotrksB7N6unf1</mark>

* program 1: <mark style="background-color:red;">Marinade Finance - MarBmsSgKXdrN1egZf5sqe1TMai9K1rChYNDJgjq7aD</mark>
  * instruction 1: <mark style="background-color:red;">Deposit</mark>
    * inner instruction 1: <mark style="background-color:red;">Token Transfer</mark>
    * inner instruction 2: <mark style="background-color:red;">SOL Transfer</mark>

Again we got all this info from [Solscan](https://solscan.io/tx/ngF3HJPi3g7WwkEXU7L4d8gRuggtLTq9cJ31tLXvhxqyet73oX23iaZiqL3cMv9o573xa4gjKqotrksB7N6unf1) (see screenshots below). Shortly we’ll show you how to access this info in Flipside’s data to power our analysis, but for now we’ll reference Solscan screenshots while we improve our conceptual understanding:

_**More Detail with Screenshots: Outline of our Marinade Staking Transaction**_

* program: <mark style="background-color:red;">Marinade Finance - MarBmsSgKXdrN1egZf5sqe1TMai9K1rChYNDJgjq7aD</mark>

![](<../../../.gitbook/assets/Untitled (1) (1)>)

*   instruction 1: <mark style="background-color:red;">Deposit</mark>

    * inner instruction 1: <mark style="background-color:red;">Token Transfer</mark>
    * inner instruction 2: <mark style="background-color:red;">SOL Transfer</mark>



![](<../../../.gitbook/assets/image (5).png>)

So now that we understand that Solana transactions are organized into programs, instructions, and inner instructions, it’s clearer to see how our transaction’s data show up in the solana.events table. For example you’ll see a lot of the information from Solscan in this JSON from the INNER\_INSTRUCTIONS column:

```javascript
{
  "index": 0,
  "instructions": [
    {
      "parsed": {
        "info": {
          "amount": "116672",
          "authority": "EyaSjUtSgo9aRD1f8LWXwdvkpDTmXAW54yoSHZRF14WL",
          "destination": "9dNe8PGfFU8s8eDQE2uXWG33pxASV2ESHPVnqwcCnYes",
          "source": "7GgPYjS5Dza89wV6FpZ23kUJRG5vbQ1GM25ezspYFSoE"
        },
        "type": "transfer"
      },
      "program": "spl-token",
      "programId": "TokenkegQfeZyiNwAJbNbGKPFXCWuBvf9Ss623VQ5DA"
    },
    {
      "parsed": {
        "info": {
          "destination": "UefNb6z6yvArqe4cJHTXCqStRsKmWhGxnZzuHbikP5Q",
          "lamports": 120000,
          "source": "2GfVuJm5Hbtf5rr6FeUuNXqpPYzJAq8P9HQg6XsrurxV"
        },
        "type": "transfer"
      },
      "program": "system",
      "programId": "11111111111111111111111111111111"
    }
  ]
}
```

### **Checkpoint Review**

Let’s review what we’ve learned so far:

1. Our goal was to find _all_ Marinade staking transactions in Flipside’s data.
2. We started by participating in Marinade staking and generating a transaction.
3. We found our transaction on [Solscan](https://solscan.io/tx/ngF3HJPi3g7WwkEXU7L4d8gRuggtLTq9cJ31tLXvhxqyet73oX23iaZiqL3cMv9o573xa4gjKqotrksB7N6unf1) and in Flipside’s solana.events table
4. We learned that transactions on Solana are organized into programs, instructions, and inner instructions, and this helped us better recognize these data in the JSON of the solana.events table.

Now we need to find _all_ Marinade staking transactions, not just our transaction.

Let’s quickly think through how to analyze our single transaction’s data to find _all_ Marinade staking transactions. Along the way we’ll learn how to access JSON data using SQL.

## Extracting data from **solana.events**

**Extracting the program**

Let’s extract only the PROGRAMID field, which we think will be important because the program is identified on Solscan as Marinade Finance.

From our staking transaction we’ll use the PROGRAMID value to find all similar transactions on that day:

```sql
select
	instruction:programId,
	*
from solana.events
where date_trunc('day', block_timestamp) = '2022-01-21 00:00:00.000'
-- on Solana we *always* add a small date range for query efficiency!
and instruction:programId = 'MarBmsSgKXdrN1egZf5sqe1TMai9K1rChYNDJgjq7aD'
order by block_timestamp;
```

We accessed the PROGRAMID value by using a colon to ‘traverse’ the JSON structure and pull out the value:

```sql
instruction:programId
--use colons ':' to select nested fields in JSON structure
```

If you're following along with a query in [Flipside’s app](https://app.flipsidecrypto.com/), you'll see we get 1,043 rows, and from quickly looking at [the first transaction on Solscan](https://solscan.io/tx/36Q1wDeSGvtXqW32GT4EoTiuU2vkHWNrph1ieUBrXx23oxqA7GpA5Y8wiHZxRUyxRPpXj1tfa6ZBCZiCeTfm44jZ) we see that its program’s INSTRUCTION is referenced as ‘MergeStakes’ — _not_ ‘Deposit’ like our staking transaction.

This means that filtering on the PROGRAMID alone is not selective enough to find staking transactions, because our query includes other kinds of transactions.

**Extracting the source**

Can we find something more specific about our transaction that identifies it as a staking transaction?

After further data exploration, we notice that the amount of mSOL we received came from a SOURCE address starting with ‘7GgPYj...’, an address that is included in our staking transaction’s INNER INSTRUCTIONS field. Also, [Solscan](https://solscan.io/tx/ngF3HJPi3g7WwkEXU7L4d8gRuggtLTq9cJ31tLXvhxqyet73oX23iaZiqL3cMv9o573xa4gjKqotrksB7N6unf1) listed this address ‘7GpPYj...’ as “Liq Pool Msol Leg” (see its list of input accounts for the Deposit instruction) — this might be read as e.g. “Liquidity Pool Msol Ledger” so we reason that all Marinade staking deposits must come from this address.

Let’s add this SOURCE field with address ‘7GpPYj...’ to our query:

```sql
select
	instruction:programId,
	inner_instruction:instructions[0]:parsed:info:source,
	*
from solana.events
where date_trunc('day', block_timestamp) = '2022-01-21 00:00:00.000'
-- on Solana we *always* add a small date range for query efficiency!
and instruction:programId = 'MarBmsSgKXdrN1egZf5sqe1TMai9K1rChYNDJgjq7aD'
and inner_instruction:instructions[0]:parsed:info:source = '7GgPYjS5Dza89wV6FpZ23kUJRG5vbQ1GM25ezspYFSoE'
order by block_timestamp;
```

We accessed the SOURCE value by using colons _and brackets_:

```sql
inner_instruction:instructions[0]:parsed:info:source
--use colons ':' to select nested fields in JSON structure
--the 'instructions' field contains an array enclosed in brakets [...]
--so we use [0] to access the 1st element in that array
```

You can read more about [traversing unstructured JSON data here in Snowflake’s documentation](https://docs.snowflake.com/en/user-guide/querying-semistructured.html#querying-semi-structured-data).

**Mission Accomplished! Or is it?...**

Again if you run our query in [Flipside’s app](https://app.flipsidecrypto.com/), you'll see we get 766 rows, and from inspecting the transactions we see yes they are all deposits just like our staking transaction.

We used the SOURCE field to find all Marinade staking transactions! In other words, we decided that all transactions coming from this source must be deposit staking transactions.

But what if a transaction were organized like this?

transaction

* program 1
  * instruction 1
    * inner instruction 1
    * inner instruction 2 ...source: ‘7GgPYj...’
    * inner instruction 3

(In fact, here’s [a transaction just like this on Solscan](https://solscan.io/tx/49vjSXygKZFazHKVdQ9roEib1628qYxg1xajp8Pgw83RtLQoe4rghkDh9RGUkcNDUgzvzwz5S57KWsEyR48BShWv).)

Is this a staking deposit transaction? Our query would have missed it because we used \[0] to access _the first_ inner instruction, not the second! (Arrays in JSON are ‘zero-indexed’.)

```sql
inner_instruction:instructions**[0]**:parsed:info:source
--use colons ':' to select nested fields in JSON structure
--the 'instructions' field contains an array enclosed in brakets [...]
--so we use [0] to access the 1st element in that array
```

Even though this transaction had a token transfer coming from ‘7GpPYj...’ Solscan labels the instruction as ‘removeLiquidity’ _not_ ‘Deposit’.

So we decide we’re okay, we aren’t missing those transactions, but let’s use a query to make sure:

```sql
select
	instruction:programId,
	inner_instruction:instructions[0]:parsed:info:source,
	*
from solana.events
where date_trunc('day', block_timestamp) = '2022-01-21 00:00:00.000'
-- on Solana we *always* add a small date range for query efficiency!
and inner_instruction:instructions[1]:parsed:info:source = '7GgPYjS5Dza89wV6FpZ23kUJRG5vbQ1GM25ezspYFSoE'
order by block_timestamp;
```

This time we get 88 rows and we check a few more transactions on Solscan like [this one](https://solscan.io/tx/3dxLsDGPWqo1ihwc1CAsTBW9mGUMNdwchC7ZWUFDSWMtZyRKjX43oNQrxWMS48h2rpY64kYerFooGpF72hj8q6af) and now we have more decisions to make and questions to answer:

This transaction had a token transfer coming from ‘7GpPYj...’ but we don’t see Marinade Finance listed anywhere in the programs... ! What are these other programs? Are they also creating staking transactions?

After more digging and thinking we decided see the first program above doesn’t transfer any mSOL, so it can’t be a deposit, but the second program ‘mRefx8...’ _does_ contain a deposit. It turns out that if we [search Github for that program](https://github.com/search?q=mRefx8ypXNxE59NhoBqwqb3vTvjgf8MYECp4kgJWiDY\&type=code) we find evidence it’s connected to [Marinade’s Referral Program](https://docs.marinade.finance/partnerships/referral-program) — aha! We conclude users are in fact making staking deposits into Marinade here, but through the referral program, and we probably should include these in a thorough analysis of Marinade staking deposits.

## Conclusion & Takeaways

We successfully found a way to identify all Marinade staking transaction data on Solana!

Again let’s review what we learned:

1. Our goal was to find all Marinade staking transactions in Flipside’s data.
2. We started by participating in Marinade staking and generating a transaction.
3. We found our transaction on [Solscan](https://solscan.io/tx/ngF3HJPi3g7WwkEXU7L4d8gRuggtLTq9cJ31tLXvhxqyet73oX23iaZiqL3cMv9o573xa4gjKqotrksB7N6unf1) and in Flipside’s solana.events table.
4. We learned that transactions on Solana are organized into programs, instructions, and inner instructions, and this helped us better recognize these data in the JSON of the solana.events table.
5. We used SQL to analyze JSON data, to explore related transactions, and to make decisions about how to identify _all_ Marinade staking transactions.

Let’s acknowledge some important takeaways we can draw from this process:

* We used the process of participate & analyze to find Marinade Finance staking transactions, but you can use this process to find transactions for _any_ project of your choice on Solana.
* For analyses in general we may want to analyze some set of transaction behaviors (like Marinade staking transactions), but because Solana transactions are organized into different hierarchies and program/instruction orderings, it takes some detective work and critical thinking to make decisions for your analyses and come up with qualifying criteria (these are great data analyses skills to practice).
* Throughout this article we limited our explorations to a single day of Solana data for simplicity and query performance. This is because the Solana network’s high throughput generates a LOT of data — you always want to set small date ranges while doing exploratory analyses.

As a final note, we chose the solana.events table because it contains a lot of transaction detail that can power a wide range of analyses. Flipside is excited to offer Solana data to the Solana community and our community analysts, and this means building fast — we’re constantly making improvements and we’re working on more curated tables and labeled data to make your analyses easier. Working with tables like solana.events will help you build a deep understanding of transactions so you can leverage the growing power of Flipside’s Solana data!
