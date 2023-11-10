---
description: >-
  Where the work happens: run SQL queries, get results, visualize them, and
  publish them on a dashboard, all from one place in the app
---

# Query Editor

This section will cover:

* [How to customize the editor?](query-editor.md#the-editor)
* [How to get started with the query panel?](query-editor.md#the-query-panel)
* [How to get started with the results panel? ](query-editor.md#the-results-panel)
* [How to get started with the charts panel?](query-editor.md#the-charts-panel)

### Overview of the Editor

The editor is composed of three main panels - query, results, and charts. To the left of these panels, you have access to My Work or the Data Explorer. To the top, you can see all the queries and dashboards you've opened in tabs.&#x20;

<figure><img src="../../../.gitbook/assets/Group 27.png" alt=""><figcaption><p>Work interface. </p></figcaption></figure>

**Configure your Interface.**

Focus on different panels as you go through your workflow by expanding/collapsing panels. Here are three ways you can do that:

* **Click & Drag:** click and drag the dividers between panels.&#x20;
* **Double-click to maximize:** double click on the header of each panel to maximize that panel. &#x20;
* **Expand/Collapse button:** click on the expand/collapse button on the top-right corner of each panel to expand or minimize it.&#x20;



### The Query Panel&#x20;

This is where you input your SQL + Run it. Here are some features of the query panel.&#x20;

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-12 at 7.54.53 PM.png" alt=""><figcaption></figcaption></figure>

* **Auto-Complete:** start typing and the auto-complete feature will bring up Snowflake SQL keywords as well as database, schema, and table names.&#x20;
* **Select & Run:** select and highlight any part of your code to only run that snippet to see the "Selection Result" in the results panel.&#x20;
*   **Parameterized Queries:** implement variables in certain parts of your code instead of hard-coding values like contract addresses, symbols, or date ranges. These values are also adjustable from the dashboard, letting readers interact with your dashboard by entering values they care about.&#x20;

    * To insert a parameter, you can click the "+ Parameter" button or simply type `{{parameter_name}}` and manage your parameters at the bottom of the query panel.&#x20;
    * To add a select list of values for your end user to choose from, include a comma-separated list in the default values. This will show up as a dropdown list on your dashboard. See an example below:

    <figure><img src="../../../.gitbook/assets/Screenshot 2023-05-09 at 10.28.39 AM.png" alt=""><figcaption><p>Comma-separated list as a dropdown in your dashboard.</p></figcaption></figure>
* **Auto-Format:** make your query more readable by using the auto-format button!



### The Results Panel&#x20;

This is where you'll see the data you queried. To get results, write your SQL in the query panel and hit the blue play button in the top right corner. Or, you can run a query using your keyboard shortcut: `cmd + enter (mac)` or `ctrl + enter (windows/linux)`.&#x20;

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-12 at 7.56.38 PM.png" alt=""><figcaption></figcaption></figure>

The results panel is also where you'll see an error message if your query fails. There will be detailed feedback that will give you an idea of how to update your query. Here are a couple more things you can do through the results panel.&#x20;

* **Rotate a table:** if your table is super wide, you may want to rotate it to get a better sense of the columns in it.&#x20;
* **Download results as CSV:** download queried results and analyze them in your preferred tool.&#x20;
* **Add to Dashboard:** add the results table to your dashboard.&#x20;



### The Charts Panel&#x20;

This is where you visualize your data. Using the Flipside App, you can create a **Bar**, **Area**, **Line**, **Scatter**, **Big Number**, or **Donut chart**.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-03-12 at 8.00.44 PM.png" alt=""><figcaption><p>The chart editor will give you some initial guidance on how to get started.</p></figcaption></figure>

Here's a quick reference on when to choose which chart:

* **Bar** — when comparing quantities across categories, and / or over time.
* **Area** — when comparing quantities over time (or proportions of a whole over time, if you choose stack + normalize).
* **Line** — when you want to visualize a trend, or movement in some measure, over time, and especially when the dimension measures are evenly spaced (like: a value exists for every week, day or hour — price charts or rates are good examples of this, vs. transactions which are more sporadic).
* **Scatter** — when comparing independent variables or sets of numbers, and when you think there's likely to be some relationship between them (e.g., time vs. nft sale prices vs gas prices); a great choice for exploring complex or multi-dimensional data before committing to an approach.
* **Big Number** — quite simply: when you want to show just one number.
* **Donut** — when you need to show the share of a set of constituent parts relative to the whole, and only then (e.g., % of NFTs minted in a collection that have been held vs. sold).&#x20;
