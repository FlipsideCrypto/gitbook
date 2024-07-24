---
description: >-
  Flipside has licensed Highcharts for its new data visualization engine,
  allowing more viz choices (e.g. candle charts coming soon!) and advanced user
  customization for layouts and themes.
---

# Advanced Visualization

Given a chart type and key data (x axis, y axes, group variable) flipside will generate a smart default for your plot choice in our theme. Instead of creating 100s of new buttons and widgets for customization, we expose a _settings_ page that allows for direct manipulation of the [highcharts](https://api.highcharts.com/highcharts/) config.&#x20;

```json
 {
  "title": {
    "text": "CEX Flow Volume",
    "style": {
      "fontSize": "25px"
    }
  },
  "subtitle": {
    "text": "Combined In + Out Flows (USD)"
  },
  "xAxis": {
    "title": {
      "text": "Date",
      "style": {
        "color": "#FFFFF",
        "fontSize": "20px"
      }
    },
   ....
}
```

All the customization you're used too (axis titles) and a bunch of new options (font size, font colors, legend location, custom tooltips, and much more!)&#x20;

This is a _**brief**_ and incomplete guide to the 100s of options Highcharts enables across dozens of chart types (which we are working to add support for in dashboards!). The goal is to get you off the ground manipulating charts and using external tools like the highcharts docs: [https://api.highcharts.com/highcharts/](https://api.highcharts.com/highcharts/)\
\
or 3rd party references like chatGPT (for those with chatGPT Plus, we've created a [Flipside Highcharts GPT](https://chat.openai.com/g/g-83LLq5yLi-highcharts-configurator)) and soon our custom AI agent trained on all things Flipside.



<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-07-22 at 12.43.31 PM.png" alt=""><figcaption><p>Advanced Visualization of Central Exchange flows, zoomed in!</p></figcaption></figure>

#### Key Constraints&#x20;

For security purposes, we do have some limitations we'd like to note upfront. You _cannot_ manipulate the `series` object (the object that holds all your data!) and you _cannot_ use custom JavaScript (i.e. no `formatter()` functions). But there's still plenty of out of the box highcharts customization available!

#### Standard Labels

Title, subtitle, xAxis, yAxis each have their `title/text` options to name them. They also have a `style` option to change color, font, and font sizes. You edit these via nested JSON, so be careful with the brackets. Axes, here xAxis, has additional features like changing the `labels` (`26 Feb`) or even rotating them to save space. You can choose to _not_ show every date by implementing `tickInterval` in milliseconds (`432000000 = 5 days`) which allows for skipping labels to make the chart cleaner.

Some of the most powerful controls are the `LabelFormats` where you can adjust how days or months are labeled, `%b %d, %Y = Mar 01, 24`&#x20;

Common LLM tools like chatGPT are excellent at supporting these custom configurations just specify it's highcharts js.

```json
"title": {
    "text": "CEX Flow Volume",
    "style": {
      "fontSize": "25px"
    }
  },
  "subtitle": {
    "text": "Combined In + Out Flows (USD)"
  },
  "xAxis": {
    "title": {
      "text": "Date",
      "style": {
        "color": "#FFFFF",
        "fontSize": "20px"
      }
    },
    "labels": {
      "style": {
        "fontSize": "16px"
      },
      "rotation": 0
    },
    "tickInterval": 432000000,
    "dateTimeLabelFormats": {
      "day": "%b %d, %Y"
    }
  },
 
  "yAxis": {
    "title": {
      "text": "Flow Volume (USD)",
      "style": {
        "fontSize": "20px"
      }
    },
    "labels": {
      "style": {
        "fontSize": "16px"
      },
      "format": "{value:,.0f}"
    }
  }
```

#### PlotOptions

Most of the time, you won't touch plotOptions, as we fill this out using your chart selection. But for awareness options like `marker` and `line` are available to change things like making a line `dashed` or here, making all the points on the lines circles instead of different ones for each line (circle, square, triangle, etc.).

For charts that are monthly level, you may need to match your `pointIntervalUnit` with the `dateTimeLabelFormats` for the xAxis (here and above both `"day"` but could be `"month"`).

```json
 "plotOptions": {
    "line": {
      "pointStart": 1704085200000,
      "pointIntervalUnit": "day",
       "marker": {
        "enabled": true,
        "symbol": "circle"  
      }
    }
```

#### Colors, Legend, ToolTips

<figure><img src="../../../../../.gitbook/assets/Screenshot 2024-07-22 at 12.46.07 PM.png" alt=""><figcaption><p>Custom Tooltip!</p></figcaption></figure>

Colors are positionally determined based on the series data. You can manually apply an `ORDER BY` for your group (e.g. `ORDER BY date ASC, central_exchange ASC`) so that the colors are in alphabetical order; otherwise you can just play around with the ordering to identify which is which.

To more easily select colors, our data science team enjoys [iwanthue](https://medialab.github.io/iwanthue/) which has colorblind friendly, dark, light, palette, and custom color clustering, with easy to copy/paste JSON for pasting them here in the colors object.

The legend object is somewhat simple: alignment, layout, location, etc. To remove a legend you can add `"enabled": false.`

The `series` object is not available for manipulation, but it is available for referencing. This comes up for `tooltip`  `pointFormat` as you take `group` (`series.name`) and the color (`series.color`) to keep chart colors matching the hover over tooltip. The `headerFormat` works similarly as it allows custom HTML (`<b>` = bold) and style formatting (`.0f` = `whole number, 0 decimals`).

```json
"colors": [
    "#cc9e4f",
    "#523151",
    "#9061c9" 
  ],
  "legend": {
    "align": "center",
    "layout": "horizontal",
    "verticalAlign": "top"
  },
    "tooltip": {
    "shared": true,
    "pointFormat": "<span style=\"color:{series.color}\">{series.name}: {point.y:,.0f}</span><br/>",
    "headerFormat": "<b>{point.key:%b %d, %Y}</b><br/>"
  },
```

#### Exports & Other

You generally won't touch these options. But to improve the UX of charts, we enable zoom, pan, and exports (png, svg, pdf) - and our license allows for removal of the highcharts website credits.

```json
  "chart": {
    "panKey": "shift",
    "panning": {
      "type": "xy",
      "enabled": true
    },
    "zoomType": "xy"
  },
  "credits": {
    "enabled": false
  },
  "exporting": {
    "buttons": {
      "contextButton": {
        "menuItems": [
          "downloadPNG",
          "downloadJPEG",
          "downloadPDF",
          "downloadSVG"
        ]
        }
      },
    "enabled": true
   }
}
```
