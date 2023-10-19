# Customize time series chart and data table layouts

Demand planning provides many options that help you to analyze your time series. Among them is the ability to customize the chart layout (such as style, color, size), overlay the chart or data table with another time series to make easy comparisons, and to assign logic for highlighting certain cells in the data table to make them stand out.

To make these settings, open a time series and then select **Select data** from either the Timeline FastTab or the Time series values FastTab (it doesn't matter which). The **Select data** dialog opens.

![A screenshot of a computer Description automatically generated](media/image11.png)

To add a new time series to the graph and/or data table, select the **Add** button. You'll be asked to select an existing time series. After you select a time series, it will be added as a new row in the **Select data** dialog. To remove a time series from the graph and data table, select its close box on the right side of the row. The top row of the **Select data** dialog lists the current time series, which you can customize, but can't remove.

Each row in the **Select data** dialog provides the following information and options for each listed time series:

- **Name** – Shows the name of the time series.

- **Version** – For time series that have more than one version, select the version to use from this drop-down list.

- **Description** – Shows a short description of the time series.

- **Show in chart** – Enable this option for each time series that you want to include in the graph.

- **Chart styling** – Select the **Customize** link in this column to open a dialog where you can customize the way the selected row appears in the graph. You can choose to present the series as a line or series of bars, and you can choose the color. You can also choose to add a **Secondary axis**, which is useful if your selected series use very different values from either other (such as when comparing sales in the millions of units against prices in the hundreds of dollars). When you choose to add a secondary axis, a new set of values will be shown on the right side of the chart to indicate the scale of the second time series.

- **Show in grid** – Enable this option for each time series that you want to include in the data table.

- **Grid formatting** – Select the **Customize** link in this column to open a dialog where you can specify logic for highlighting cells in the data table. You can highlight cells for the selected series according to their own values, or according to values from another time series for the same time bucket. (Set **Use values from another time series** to *Yes* and then specify a series and version if you want to compare to another series.) You can add as many rules as you need. For each rule, specify the logic (for example, find values less than 4,000,000) and the style (color and icon) to apply to cells that match that rule.

After you've spent time customizing and formatting your time series, you'll probably want to save your settings as a new data view so you can return to it later. To do so, open the drop-down menu at the top-left of the page and select **Save as new dataview** (see also [Explore time series](explore-time-series.md)). You can save as many data views as you need for each time series.

