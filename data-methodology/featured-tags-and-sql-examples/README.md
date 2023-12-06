---
description: >-
  Want to see what interesting addresses are up to? Have a list of addresses you
  want to analyze without pasting them into your where clause? Tags are for you.
---

# Tags

Tags can be specific and provable, e.g. "OpenSea user", or simply a tool to group addresses and clean up your code. Your tags. Your rules.&#x20;

Check back often as our list of tags is constantly being updated!&#x20;

[`crosschain.core.address_tags` table docs](../archive/tables/crosschain-tables/crosschain-address-tags.md)\
&#x20;\
Don't see the perfect tag? [Add your own! ](how-to-add-your-own-tags.md#how-to-add-tags)



## Table of Contents

| Tag Type                                           |
| -------------------------------------------------- |
| [token standard](./#token-standard)                |
| [contract](./#contract)                            |
| [cex (centralized exchange)](./#cex)               |
| [dex (decentralized exchange)](./#dex)             |
| [nft](./#nft)                                      |
| [activity (general behavior)](./#activity)         |
| [wallet (token contents of an address)](./#wallet) |

### Token Standard

Tag\_type 'token standard' is a set of tags that define the token standard of an address!

| tag\_name      | description                           | blockchains |
| -------------- | ------------------------------------- | ----------- |
| erc-20         | An erc-20 address                     | ethereum    |
| erc-721        | An erc-721 address                    | ethereum    |
| erc-1155       | An erc-1151 address                   | ethereum    |
| erc-4626       | An erc-4626 address                   | ethereum    |
| erc-6551       | An erc-6551 address                   | ethereum    |
| erc-6551 owner | A token address that owns an erc-6551 | ethereum    |

Want to know the difference in behaviors of erc-721's vs. erc-1155's? Leveraging the 'token standard' tag\_name will make this segmentation and subsequent analysis trivial!

The code below will find all erc-721s that are on Ethereum!&#x20;

```sql
select 
  distinct address
from crosschain.core.address_tags 
where 
    tag_type = 'token standard' 
    and tag_name = 'erc-721'
    and creator = 'flipside'
```

### Contract

Tag\_type 'contract' is a group of tags that call out contract addresses! \
Contracts are discovered by looking through the blockchain's logs and tagged for you!\


| tag\_name           | description                               | blockchains |
| ------------------- | ----------------------------------------- | ----------- |
| contract address    | An address that is a contract             | Ethereum    |
| gnosis safe address | An address that is a gnosis safe contract | Ethereum    |

Leveraging the tag type 'contract' is a useful way to exclude contracts from your analysis, and only focus on externally owned addresses (EOAs). \
Add the below code to a where statement within your analysis to ensure you are not pulling in any contracts!

<pre class="language-sql"><code class="lang-sql"><strong>select 
</strong>  distinct address
from crosschain.core.address_tags 
where 
    tag_type = 'contract' 
    and tag_name = 'contract address'
    and creator = 'flipside'
</code></pre>

[back to top](./#table-of-contents)

### CEX

Tag\_type 'cex' is a group of tags pertaining to 'centralized exchanges' or 'cex' for short.&#x20;

| tag\_name        | description                                                                                     | blockchains |
| ---------------- | ----------------------------------------------------------------------------------------------- | ----------- |
| \[cex name] user | Identifies an address that either sent or received funds from a particular centralized exchange | Ethereum    |

CEX tags can be used to group addresses based on which centralized exchange they use. \
Want to know which centralized exchange has the most addresses interacting with it? See below for code to get an ordered list!

```sql
select 
  tag_name, 
  count(distinct address) as num_addresses
from crosschain.core.address_tags 
where 
    tag_type = 'cex' 
    and tag_name like '% user'
    and creator = 'flipside'
group by tag_name
order by num_addresses desc
```

[back to top](./#table-of-contents)

### DEX

Tag\_type 'dex' is a group of tags for 'decentralized exchanges' or 'dex' for short.&#x20;

| tag\_name                     | description                                                    | blockchains                                                                         |
| ----------------------------- | -------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| thorchain dex user            | Identifies an address that has done a swap with thorchain      | bitcoin, bitcoin cash, bsc, cosmos, dogechain, Ethereum, litecoin, terra, thorchain |
| thorchain liquidity provider  | Identifies an address that has provided liquidity to thorchain | bitcoin, bitcoin cash, bsc, cosmos, dogechain, Ethereum, litecoin, terra, thorchain |

Ever wondered what Ethereum addresses are providing liquidity to Thorchain? It has never been easier with the help of tags!:

```sql
select 
  distinct address
from crosschain.core.address_tags 
where 
    tag_type = 'dex' 
    and tag_name = 'thorchain liquidity provider'
    and creator = 'flipside'
    and blockchain = 'ethereum'
```

[back to top](./#table-of-contents)

### NFT

Tag\_type 'nft' is a group of tags pertaining to nft usage!

| tag\_name               | description                                                        | blockchains |
| ----------------------- | ------------------------------------------------------------------ | ----------- |
| \[nft marketplace] user | Identifies addresses that use a particular nft marketplace         | Ethereum    |
| nft transactor top 1%   | addresses that are in the top 1% of transactions involving an nft  | Ethereum    |
| nft transactor top 5%   | addresses that are in the top 5% of transactions involving an nft  | Ethereum    |
| nft transactor top 10%  | addresses that are in the top 10% of transactions involving an nft | Ethereum    |

Want to know which marketplace has the most addresses interacting with it? Tags can help you with a simple query:

```sql
select 
  tag_name, 
  count(distinct address) as num_addresses
from crosschain.core.address_tags 
where 
    tag_type = 'nft' 
    and tag_name like '% user'
    and creator = 'flipside'
group by tag_name
order by num_addresses desc
```

[back to top](./#table-of-contents)

### Activity

Tag\_type 'activity' is for tags that describe an address's activity. General tags that are not protocol specific!

| tag\_name                      | description                                                                                     | blockchains                                           |
| ------------------------------ | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| active on \[blockchain] last 7 | identifies an address that has sent at least 1 transaction on a blockchain in the last 7 days.  | Arbitrum, Avalanche, Bsc, Ethereum, Optimism, Polygon |

There are many use cases for an active tag! A simple one is to see what other EVM's an address is active on.\
Here is a query to see addresses that are active on both Ethereum and Arbitrum:

<pre class="language-sql"><code class="lang-sql">with eth_addresses as (
select 
    distinct address 
from crosschain.core.address_tags 
where tag_name = 'active on ethereum last 7'
<strong>    and creator = 'flipside'
</strong>)
select 
  distinct address
from crosschain.core.address_tags 
where 
    tag_name = 'active on arbitrum last 7'
    and address in (select distinct address from eth_addresses)
    and creator = 'flipside'
</code></pre>

[back to top](./#table-of-contents)

### Wallet

Tag\_type 'wallet' is for tags pertaining to the token contents of an address.&#x20;

| tag\_name                        | description                                                                                                                 | blockchains |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ----------- |
| airdrop master                   | address is in the top 10% of airdrop recipients based on token value. Value of token is calculated at time of airdrop claim | Ethereum    |
| eth billionaire                  | address has an ETH balance of at least $1,000,000,000                                                                       | Ethereum    |
| eth millionaire                  | address has an ETH balance of at least $1,000,000                                                                           | Ethereum    |
| eth top 1%                       | address has an ETH balance in the top 1% of all ETH holders                                                                 | Ethereum    |
| optimism airdrop 1 recipient     | addresses that received the first optimism airdrop                                                                          | Optimism    |
| optimism airdrop 2 recipient     | addresses that received the second optimism airdrop                                                                         | Optimism    |
| token billionaire                | address has a non-eth token  balance of at least $1,000,000,000                                                             | Ethereum    |
| token millionaire                | address has a non-eth token balance of at least $1,000,000                                                                  | Ethereum    |
| token top 1%                     | address has a non-eth token balance in the top 1% of all non-eth token holders                                              | Ethereum    |
| wallet billionaire               | address has a total wallet (ETH and token) balance of at least $1,000,000,000                                               | Ethereum    |
| wallet millionaire               | address has a total wallet (ETH and token) balance of at least $1,000,000                                                   | Ethereum    |
| wallet top 1%                    | address has a total wallet (ETH and token) balance in the top 1% of all addresses                                           | Ethereum    |
| vested or locked token recipient | address has received vested/unlocked tokens from a protocol                                                                 | Ethereum    |

Using wallet type in combination with some other tags can yield more interesting results. For example, let look at what nft platforms wallet millionaires use:

```sql
with wallet_millionaire as (
select 
    distinct address 
from crosschain.core.address_tags 
where tag_name = 'wallet millionaire'
    and creator = 'flipside'
)
select 
  tag_name, 
  count(distinct address) as num_addresses
from crosschain.core.address_tags 
where 
    tag_type = 'nft'
    and address in (select distinct address from wallet_millionaire)
    and creator = 'flipside'
group by tag_name
order by num_addresses desc
```

[back to top](./#table-of-contents)

###
