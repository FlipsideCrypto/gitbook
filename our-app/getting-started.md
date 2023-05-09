---
description: How to get started querying data with the Flipside data app.
---

# Getting Started

### Step 1: Create an account.

To get started, create an account on our app — you can sign up using an email address, ETH address, or your discord account.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2023-02-15 at 8.12.06 PM.png" alt=""><figcaption><p>The account sign-up link is in the bottom left-hand corner of the page.</p></figcaption></figure>

###

### Step 2: **Create a new query.**

You can create a new query by clicking the big blue "+ Create New" button in the main navigation panel, then selecting "Query."

<figure><img src="../.gitbook/assets/Screenshot 2023-02-15 at 8.09.14 PM.png" alt=""><figcaption><p>Easiest way to create a new query is to click the big blue button.</p></figcaption></figure>

You can also create new queries in a few other ways:

* from My Work, with the + button.
* if you have the Editor open, from the query tab bar with the + button there.
* by entering [flipside.new](https://flipside.new) into your browser's URL bar.

Doing this will drop you into the Editor part of the app, with your new query open:

<figure><img src="../.gitbook/assets/Screenshot 2023-02-15 at 3.50.59 PM.png" alt=""><figcaption><p>Brand new query, ready for SQL.</p></figcaption></figure>

A few things to note here:

* By default, your query is named the date and time it was created. You can rename it by clicking on its name in the query task bar (above the code editor and below the tabs).
* The "My Work" menu will be expanded in the left sidebar, and a new line representing your query will be added to it. Here you can organize your queries, search them by title, and navigate between them. More on that later.
* When you create a fresh query, your cursor will be focused in the code editor. Here you can enter SQL to query the various blockchain databases on offer. How do you know which databases to query, though? Well...



### Step 3: **Explore Flipside's data.**&#x20;

From the side menu, navigate to the Data Explorer to see all the databases, schemas and tables available to you — there is typically one database dedicated to each blockchain we cover. For now, let's take a look at one of our Ethereum core tables: so click Ethereum, then Core, then "ez\_token\_transfers" to expand that table's details.

Pro tips for data exploration:

* **Column details:** click on the table name to see a list of it's columns, and a data type for each.
* **Table preview**: see sample data without writing any SQL by clicking the Preview icon.
* **Add to query**: enter any table name into your SQL with a single mouse click.&#x20;
* **View docs:** hover over a database name and click the "book" icon to go direct to docs.

<figure><img src="../.gitbook/assets/Explore data.png" alt=""><figcaption><p>The data explorer is the easiest way to find tables, check out their contents, and add them to your query.</p></figcaption></figure>



### Step 4: **Write your query → Run it → See results**  &#x20;

Now let's run a query from ethereum.core.ez\_nft\_sales. Here's one you can use, that gets the top 8 NFT platforms on Ethereum by total sales in the past 30 days:

```sql
select
  platform_name,
  count(*) as sales_count
from ethereum.core.ez_nft_sales
where block_timestamp > current_date - interval '30 days'
group by platform_name
order by sales_count desc
limit 8
```

Paste that into the code editor (and modify it if you like: maybe change the "limit" and get top 10 instead of 8, or change the "interval" to get total sales from the past week instead of month?) and you're ready to go.

To run your query, you can hit the big blue "play" button in the top right-hand corner, or use a keyboard shortcut:

* Mac: CMD + ENTER
* PC or Linux: CTRL + ENTER

After a few moments, you should see your results appear in the Results Panel — you've got data!

<figure><img src="../.gitbook/assets/Screenshot 2023-05-05 at 10.46.18 AM.png" alt=""><figcaption><p>Your screen should look something like this at this point.</p></figcaption></figure>

###

### Step 5: **Visualize the data!**

Let's take a look at what the table above is telling us! Click **"Add Chart"** on the bottom of the screen to fire up the chart builder. For this example, we'll choose **Bar** chart from the chart type menu, then set a few options to get started:

* for X Axis, select "PLATFORM\_NAME"
* for Y Axis (Bar), select "SALES\_COUNT"
* for Group By Value, select "PLATFORM\_NAME"

Your screen should look something like this:

<figure><img src="../.gitbook/assets/Screenshot 2023-05-05 at 10.56.44 AM.png" alt=""><figcaption><p>You've got a chart!</p></figcaption></figure>

###

### Step 6: **Create a dashboard and publish.**

Now that you have your results and a basic chart, you can tie everything together by creating a dashboard. Click the "add to dashboard" icon in the chart panel, then click "+ New Dashboard" to get started:

<figure><img src="../.gitbook/assets/Screenshot 2023-05-05 at 10.58.57 AM.png" alt=""><figcaption><p>"Add to dashboard" is the quickest way to get a new chart into a dashboard.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2023-02-15 at 8.16.45 PM.png" alt=""><figcaption><p>This interface lets you find an existing dashboard to add your chart to, or instantly create a new one.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2023-05-05 at 11.06.13 AM.png" alt=""><figcaption><p>Your new dashboard is ready to edit! It should look something like this.</p></figcaption></figure>

###

### Step 7: **Publish and Share!**

There are many ways to customize a dashboard — you can add text boxes, charts, tables, and images to your dashboard to showcase what you've discovered, resize and arrange them as you see fit, and even organize them in tabs.&#x20;

For now, we'll stick to the basics — let's give this dashboard a name! Click the default assigned name (the date and time the dashboard was created) and name it something appropriate like "NFT Platform Sales Walkthrough".

<figure><img src="../.gitbook/assets/Screenshot 2023-05-05 at 11.07.51 AM (1).png" alt=""><figcaption><p>Click the big timestamp and name it something appropriate.</p></figcaption></figure>

Make any other changes you see fit:

* **Action Bar**: you can add text, images, or charts from the action bar at the bottom of the page.
* **My Work**: you can also drag charts and results tables onto the dashboard from My Work.
* **Tabs**: finally you can create additional pages or "tabs" in your dashboard to help organize your work by clicking the "Activate Tab Mode" box, and then adding tabs with the + button, and editing or removing them with the gear icon.

Once you're happy with your dashboard, hit the publish button on the top right corner — after a short delay, you should see a confirmation like this:

<figure><img src="../.gitbook/assets/Screenshot 2023-02-15 at 8.35.24 PM.png" alt=""><figcaption><p>Your dashboard publish confirmation shows you a preview of how your dashboard will appear when shared on the web.</p></figcaption></figure>

###

### Step 8: **Find it in Discover.**&#x20;

Now that your dashboard is published, you can find it in Discover:

<figure><img src="../.gitbook/assets/Screenshot 2023-02-15 at 8.38.16 PM.png" alt=""><figcaption><p>Click that Discover link!</p></figcaption></figure>

There are a few ways to find your dashboard in discover, here's the easiest one:

1. Click "Analysts" to find your account in the Analyst Leaderboard.
2. Click "Search" and enter your username to find your profile.
3. Click your profile card to go to your profile page.
4. Your dashboard should show up near the top!

<figure><img src="../.gitbook/assets/Screenshot 2023-02-15 at 8.43.16 PM.png" alt=""><figcaption><p>Get to the analysts section and search for your profile to find your dashboard.</p></figcaption></figure>

Congrats — you've published!

### Next Steps:

* **Edit your profile** — add contact information, customize your avatar and background image.
* **Get inspired** — go back to Discover and scope out the trending work: filter by a project you're interested in, and see what the best analysts in crypto are making on Flipside. Oh, and if you see something you like, be sure to hit that ❤️ button — "likes" impact the rankings and you'll help more people see good work by voting for things you enjoy.
* **Check out bounties** — there are a few [Flipside bounties](http://localhost:5000/s/q3ZsciVeKRUUcuezp6ax/rpc/data-types/sqlstatement) left, but the new stuff is mostly at [MetricsDAO](https://metricsdao.xyz/) — check it out, accept a challenge, submit your work, and get paid!

