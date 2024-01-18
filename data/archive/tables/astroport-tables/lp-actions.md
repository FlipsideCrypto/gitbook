---
description: astroport.pool_reserves
---

# Astroport Pool Reserves

This table provides block by block pool reserve information including total pool shares, pool currencies, and token amounts in Astroport pools.&#x20;

<table data-header-hidden><thead><tr><th width="227.33333333333331">Field</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>Field</td><td>Type</td><td>Description</td></tr><tr><td><code>blockchain</code></td><td>text</td><td>The blockchain this pool was created on.</td></tr><tr><td><code>chain_id</code></td><td>text</td><td>ID of blockchain to connect to, it can be <em>columbus-3, columbus-4, columbus-5, etc.</em></td></tr><tr><td><code>block_id</code></td><td>number</td><td>The block number that this pool reserve was recorded</td></tr><tr><td><code>block_timestamp</code></td><td>timestamp</td><td>The block timestamp that this pool reserve was recorded</td></tr><tr><td><code>contract_address</code></td><td>address</td><td>The address of the liquidity pool</td></tr><tr><td><code>total_share</code></td><td>number</td><td>The total amount of shares  in a pool</td></tr><tr><td><code>token_0_currency</code></td><td>text</td><td>Token 0 currency</td></tr><tr><td><code>token_0_amount</code></td><td>number</td><td>Token 0 amount in pool</td></tr><tr><td><code>token_1_currency</code></td><td>text</td><td>Token 1 currency</td></tr><tr><td><code>token_1_amount</code></td><td>number</td><td>Token 1 amount in pool</td></tr></tbody></table>
