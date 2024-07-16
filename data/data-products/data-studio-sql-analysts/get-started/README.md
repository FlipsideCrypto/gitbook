# Get Started

Dive into blockchain insights in just 5 minutes! This guide will equip you with the essentials to unlock the power of Flipside Studio. We'll go over how to:

1. [Explore Flipside's Data](./#explore-the-data)
2. [Query data on Flipside](./#query-data-on-flipside)
3. [Create a chart ](./#3.-create-a-chart)
4. [Build a dashboard to share your insights](./#4.-build-a-dashboard)

{% hint style="info" %}
Before we begin, make sure you have a Flipside account ready! If not, you can [sign up for free here](https://flipsidecrypto.xyz/auth/auth0?screen\_hint=signup).&#x20;
{% endhint %}

***

### Explore the data

Steps:

1. [Launch the Studio](https://flipsidecrypto.xyz/edit)
2. Click on the database icon to access data on 26+ protocols
3. Quick introduction to how Flipside's data is organized:
   * **Hierarchy:** blockchain → schemas -> tables&#x20;
   * Read more on our [data modeling approach](../../../flipside-data/data-models.md) here.&#x20;

<figure><img src="../../../../.gitbook/assets/data explorer.png" alt=""><figcaption></figcaption></figure>

<details>

<summary>Data exploration tips:</summary>

<img src="../../../../.gitbook/assets/Screenshot 2023-12-12 at 9.33.00 AM.png" alt="" data-size="original">

* **Column details:** click on a table to see it's columns, and a data type for each.

<!---->

* **Table details:** hover over a to see the description and link to documentation.

<!---->

* **Table preview:** see sample data without writing any SQL by clicking the Preview icon.

<!---->

* **Add to query:** enter any table name into your SQL with a single mouse click.

<!---->

* **View docs:** hover over a database name and click the "book" icon to go direct to docs.

</details>

***

### Query data on Flipside&#x20;

Steps:

1. Head to [flipside.new](https://flipside.new) or [launch the Studio](https://flipsidecrypto.xyz/edit) and click "**+**" to create a new query.&#x20;
2. Write some SQL! Unsure where to start? Explore our sample query below for inspiration.
3. Hit "Run Query" (or `CMD+ENTER` on Mac / `CTRL+ENTER` on PC/Linux).

```sql
-- Top 8 NFT platforms on Ethereum by total sales in the past 30 days
select
  platform_name,
  count(*) as sales_count
from ethereum.nft.ez_nft_sales
where block_timestamp > current_date - interval '30 days'
group by platform_name
order by sales_count desc
limit 8
```

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-12-11 at 9.51.25 PM.png" alt=""><figcaption></figcaption></figure>

***

### Create a Chart

Steps:

1. Click "Add Chart" right below the query panel.&#x20;
2. Choose the chart type that best captures your data's essence. Bar, line, pie?&#x20;
3. Define the data points by setting your X and Y axes.&#x20;

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-12-11 at 9.49.47 PM.png" alt=""><figcaption></figcaption></figure>

***

### 4. Build a Dashboard to share your insights

Steps:

1. Add your chart to a new or existing dashboard.&#x20;
2. Title your dashboard&#x20;
3. Any finishing touches: adjust layout, add header, text boxes, images!
4. Publish (don't worry you can always unpublish)
5. Share by posting on Twitter/X or via URL.&#x20;
