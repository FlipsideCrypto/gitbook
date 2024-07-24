---
description: 'Where the work happens: run SQL queries, get results, visualize them.'
---

# Query Editor

### Overview

The query editor has two key components:

1. [The SQL Editor](./#the-sql-editor): for data exploration and analysis
2. [The Chart Builder](./#the-chart-builder): for data visualization&#x20;

***

### The SQL Editor&#x20;

This is where you data exploration and analysis happens!

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-07-22 at 2.16.22 PM.png" alt=""><figcaption></figcaption></figure>

**Sidebar:** editor related features are consolidated and organized in a single sidebar for easy access.&#x20;

* **Parameters:**  implement variables in certain parts of your code instead of hard-coding values like contract addresses, symbols, or date ranges. These values are also adjustable from the dashboard, letting readers interact with your dashboard by entering values they care about.
  * Add a parameter by typing `{{parameter_name}}` in the editor to see a counter appear next to the parameter icon.&#x20;
  * To edit the parameter, click on the parameter icon in the sidebar to expand a drawer, where you can manager the details.&#x20;
* **Visibility:** adjust privacy settings by making selecting a visibility option: "Public", "Restricted", or "Private".
* **Refresh rate:** ensure queries refresh on a schedule by selecting a refresh rate option.
* **Export data:** download query results to access in an external tool. Or access data programmatically via a JSON/API endpoint. &#x20;

**Editor Layout**

* **Configurable panels:** click and drag the dividers between panels to resize your panels.
* **Alternate Layout option:** click on the layout button to select your preferred view. You can choose between a horizontal split or vertical split.&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-07-24 at 7.40.18 AM.png" alt="" width="375"><figcaption><p>Click to view alternate layout option</p></figcaption></figure>

**Organized and Efficient workflow**

* **Recent Items:** dedicated panel for all of your recently opened files, easily navigate between the files you're working on.&#x20;
* **Keyboard shortcuts:** run your query simply by using `cmd + enter` (mac) or `ctrl + enter` (windows/linux).
* **Auto-Complete:** start typing and the auto-complete feature will bring up Snowflake SQL keywords as well as database, schema, and table names.&#x20;
* **Select & Run:** select and highlight any part of your code to only run that snippet to see the "Selection Result" in the results panel.&#x20;

***

### The Results Panel&#x20;

This is where you'll see the data you queried. To get results, write your SQL in the query panel and hit the blue play button in the top right corner. The results panel is also where you'll see an error message if your query fails. There will be detailed feedback that will give you an idea of how to update your query. Here are a couple more things you can do through the results panel.&#x20;

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-07-22 at 2.41.14 PM.png" alt=""><figcaption></figcaption></figure>

**Rotate a table:** if your table is super wide, you may want to rotate it to get a better sense of the columns in it.&#x20;

**Note:** To include a table in your dashboard, you'll now need to first create a "Table" chart and customize it within the chart builder.

***

### The Chart Builder

Unleash the power of data visualization with our new chart builder, designed to offer unparalleled flexibility and customization.

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-07-22 at 2.00.22 PM.png" alt=""><figcaption></figcaption></figure>

Charts remain a central part of data visualization and they now reside in their own dedicated tab. Click on the big "+" button next to the query tab to launch the new chart builder! The brand new charting library empowers you to completely customize every aspect of your dashboards, transforming data into visually compelling narratives.

#### **Supported Chart types and when to use them:**

* **Table**: Present your data in a clear and concise tabular format. Useful for displaying detailed information, comparisons, or raw data sets.
* **Bar**: Ideal for comparing categories or showing changes over time.&#x20;
* **Horizontal Bar**: A bar chart rotated on its side, useful for emphasizing long category labels or showcasing comparisons across many categories.
* **Big Number**: quite simply: when you want to show just one number.
* **Bar Line**: ideal for visualizing both categories and trends within those categories.
* **Area**: when comparing quantities over time (or proportions of a whole over time).&#x20;
* **Pie**: when you need to show the share of a set of constituent parts relative to the whole, and only then (e.g., % of NFTs minted in a collection that have been held vs. sold).&#x20;
* **Scatter**: when comparing independent variables or sets of numbers, and when you think there's likely to be some relationship between them (e.g., time vs. nft sale prices vs gas prices); a great choice for exploring complex or multi-dimensional data before committing to an approach.
* **Line**: when you want to visualize a trend, or movement in some measure, over time, and especially when the dimension measures are evenly spaced (like: a value exists for every week, day or hour — price charts or rates are good examples of this, vs. transactions which are more sporadic).

Note: While adding "Table" as a chart type brings exciting customization options, it does introduce a slight change in workflow compared to the previous version. To include a table in your dashboard, you'll now need to first create a "Table" chart and customize it within the chart builder.&#x20;

#### **Unmatched Customization**

For the ultimate power users, dive into the chart's JSON object for complete control. This [advanced editing](advanced-visualization.md) mode allows granular customization of every visual aspect, from colors and fonts to intricate chart behaviors.
