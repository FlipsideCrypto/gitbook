# Prices Swap

This table can be used to price assets within the Algorand blockchain using on-chain swaps. Price is calculated by using all swaps within two standard deviations from the hour average price, calculating the average price at the dex level, then weighting the dex price by the previous day's volume to create a weighted average across all dexes.



<table><thead><tr><th>Field</th><th width="150">Type</th><th>Description</th></tr></thead><tbody><tr><td>BLOCK_HOUR</td><td>timestamp</td><td>The hour for which the price is valid</td></tr><tr><td>ASSET_ID</td><td>numeric</td><td>ID associated with the asset</td></tr><tr><td>ASSET_NAME</td><td>string</td><td>Name of the asset</td></tr><tr><td>PRICE_USD</td><td>numeric</td><td>This table can be used to price assets within the Algorand blockchain using on-chain swaps. Price is calculated by using all swaps within two standard deviations from the hour average price, calculating the average price at the dex level, then weighting the dex price by the previous day's volume to create a weighted average across all dexes.</td></tr><tr><td>MIN_PRICE_USD_HOUR</td><td>numeric</td><td>The lowest price found in a swap in the hour in USD</td></tr><tr><td>MAX_PRICE_USD_HOUR</td><td>numeric</td><td>The highest price found in a swap in the hour in USD</td></tr><tr><td>VOLATILITY_MEASURE</td><td>numeric</td><td>The difference between the min and max price for the hour</td></tr><tr><td>SWAPS_IN_HOUR</td><td>integer</td><td>The number of swap transactions in the hour that involved this asset</td></tr><tr><td>VOLUME_USD_IN_HOUR</td><td>numeric</td><td>The volume of swap transactions (in USD) in the hour for this asset</td></tr></tbody></table>