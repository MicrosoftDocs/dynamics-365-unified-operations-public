---
title: Time series, worksheets, and planning data
description: Learn about time series, worksheets, and planning data, which represent the output from forecasts, calculations, and transformations in daily, weekly, or monthly time buckets.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: how-to
ms.date: 11/29/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Time series, worksheets, and planning data

[!include [banner](../includes/banner.md)]

Time series, worksheets, and planning data represent the output from forecasts, calculations, and transformations in daily, weekly, or monthly time buckets.

- *Time series* is a term that describes the type of data consumed and created by forecasts, calculations, and transformations. Each time series is a collection of data values plotted against a series regular time intervals. Planning data and worksheets both contain time series data.
- *Planning data* is the processed and categorized output created by forecasts and calculations. Demand planning presents planning data using both a graph and a grid of values, and provides tools for organization, editing, combining, and presenting this data. Based on how it was created, each planning data record is categorized as containing *Forecast*, *Demand*, *Financials*, or *Miscellaneous* data.
- *Worksheets* let you view, modify, and combine various types, versions, and views of planning data. You can create and switch between any number of worksheets for each planning data record.

<!--KFM: The above details are my best guess. Requires review. -->

## <a name="explore"></a>Explore planning data and worksheets

To view all your planning data, on the navigation pane, select **Planning data** \> **All**. (Alternatively, select an appropriate planning data category under **Planning data**.) To view shared worksheets, on the navigation pane, select **Home** \> **Worksheets**.

To open a worksheet or planning data record, select its name in the **Name** column. The following illustration highlights the features on the **Output** tab of the time series details page.

:::image type="content" source="media/time-series-elements.svg" alt-text="Screenshot of time series elements on the Output tab of the time series details page." lightbox="media/time-series-elements.svg":::

Legend:

1. **Worksheet selector** – On this menu, you can save the current view (including all filters, overlaid series, and other selections) as a worksheet. If you've already saved one or more worksheets, you can load them from here. To list a worksheet under **Home** \> **Worksheets**, create or set it as a **Shared worksheet** using the controls provided here.
1. **Current filters** – If you've applied any filters to the data, they're listed next to the **Add filter** button as colored blocks. You can remove any listed filter by selecting its **Close** button (**X**).
1. **Add filter** – Open a menu where you can choose to filter the time series by any combination of date or dimension values. This filtering affects the key performance indicators (KPIs) that are shown on the **Insights** FastTab, the chart that's shown on the **Timeline** FastTab, and the values that are available on the **Time series values** FastTab. Filters that you add from here are added to the current filters list (2).
1. **Insights** – This FastTab shows KPIs for the current time series, including total quantity, average quantity, and standard deviation of quantity. These values reflect the filter settings.
1. **Timeline chart** – This chart is a graphical representation of the selected time series. It provides the following capabilities:

    - **The chart reflects time series filters.** Chart values are consistent with the filter settings that are configured at the top of the page.
    - **The chart reflects row selections.** Chart values reflect any rows that are selected on the **Time series values** FastTab.
    - **View precise data values.** You can view precise data values at any point by hovering your mouse pointer over the chart.
    - **Set chart options.** You can adjust chart options (such as color, style, and grid options) by using the **Select data** button.
    - **Overlay another time series.** You can overlay another time series for comparison by using the **Select data** button. In this illustration, a second time series (pink) is overlaid on the current time series (blue).

1. **Time series values** – This FastTab shows tabular data for the selected time series. The following features and toolbar buttons are available:

    - **Row selection** – Select a row to see only that row reflected in the timeline chart. To select multiple rows, select the **Shift** key while you tap or click. A blue check mark indicates each row that's selected. Select the check mark to clear the selection of a row. Select the check mark at the top of the table to clear the selection of all rows.
    - **Fit to data** – Adjust the width of visible columns to ensure that the data isn't clipped.
    - **Downloads** – Download the data as a comma-separated values (CSV) file where the current filter and group options are applied.
    - **Group by** – Select which of the available dimensions to use to group the data. For example, if you have dimensions for warehouses and product variants, you can group by both warehouse and variant (to show each warehouse, with each product variant listed under it), group by variant only (to show the variants but not the warehouses), or group by warehouse only (to show the warehouses but not the variants). Totals values are aggregated to match the group selection.
    - **Filter totals** – Set up a logical expression to filter the selection of rows that are shown in the table. For example, you can view only rows that have totals above 100,000 units. This setting doesn't affect the chart or KPIs.
    - **Select data** – Add another time series to the chart and/or data table, so that you can compare them. This button opens the same dialog box that the **Select data** button above the chart opens. Therefore, you can also adjust chart options (such as color, style, and grid options).
    - **Edit** – Edit values directly in the data table. If an edited value is aggregated because of the **Group by** settings, the value of your edit will be divided proportionally among the aggregated data rows. If a cell shows a lock symbol, it's currently locked by a time fence and therefore can't be edited. Learn more about time fences in [Limit time series edits with time fences](time-fences.md).

Select the **General** tab of the time series details page to view and adjust the following basic settings. Many of these settings affect the way that the time series is shown on the list page.

- **Name** – The name of the time series.
- **Description** – A short description of the time series.
- **Category** – The category of the time series. This setting controls which navigation entry, in addition to **All**, the time series is listed in under **Planning data** on the navigation pane. Select the **Search** button (magnifying glass symbol) to select a category.
- **Time buckets** – The time buckets that are used by the time series (daily, monthly, or yearly).
- **Allow manual edits** – A value that indicates whether the series allows users to manually edit data values by using the data table.

## Customize time series chart and data table layouts

Demand planning provides many options that help you analyze your time series. For example, you can customize the chart layout (such as style, color, and size), overlay the chart or data table with another time series so that you can easily make comparisons, and assign logic to highlight specific cells in the data table so that they stand out.

To configure these options, open a time series, and then select **Select data** on either the **Timeline** FastTab or the **Time series values** FastTab. The **Select data** dialog box appears.

To add a new time series to the chart and/or data table, select **Add**. You're prompted to select an existing time series. The time series that you select is then added as a new row in the **Select data** dialog box. To remove a time series from the chart and data table, select its **Close** box on the right side of the row. The top row of the **Select data** dialog box lists the current time series. You can customize this time series, but you can't remove it.

The row for each time series that's listed in the **Select data** dialog box provides the following information and options:

- **Name** – The name of the time series.
- **Version** – For time series that have more than one version, select the version to use.
- **Description** – A short description of the time series.
- **Show in chart** – Enable this option for each time series that you want to include in the chart.
- **Chart styling** – Select the **Customize** link in this column to open a dialog box where you can customize the way that the selected row appears in the chart. You can select whether the series is presented as a line or a series of bars, and you can select the color. You can also add a secondary axis. A secondary axis is useful if the selected series use very different values (for example, when you compare sales in the millions of units against prices in the hundreds of dollars). If you add a secondary axis, a new set of values is shown on the right side of the chart to indicate the scale of the second time series.
- **Show in grid** – Enable this option for each time series that you want to include in the data table.
- **Grid formatting** – Select the **Customize** link in this column to open a dialog box where you can specify logic to highlight cells in the data table. You can highlight cells for the selected series according to either their own values or values from another time series for the same time bucket. (If you want to compare the selected series to another series, set the **Use values from another time series** option to *Yes*, and then specify a series and version.) You can add as many rules as you need. For each rule, specify the logic (for example, find values that are less than 4,000,000) and the style (color and symbol) that are applied to cells that match that rule.

After you've spent time customizing and formatting your time series, you'll probably want to save your settings as a new data view that you can return to later. To save the current settings as a data view, select **Save as new dataview** on the dropdown menu in the upper left of the page. (Learn more in the [Explore time series](#explore) section.) You can save as many data views as you need for each time series.

## Time series versions, version control, and change log

Demand planning lets you edit cell values directly. Therefore, you can modify the underlying data for any time series. Each time that you edit cell values, the change is noted in the change log, where all users can see when the change was made and who made it. At any time, you can save the edits that you've made so far (since the last version) as a new version and provide a name for it. You can view any version by selecting it in the version history, and you can restore any previous version to the current version.

Sometimes, when you're selecting a time series, you can select which version to use. For example, when you use **Select data** to overlay one time series on the current time series, you can choose which version to use. You can even overlay a previous version of the same time series to quickly see what changed between versions.

To view the change log and version history for a time series, open the time series, and then select **Version history** on the Action Pane. The **Version history** pane that appears shows a log entry for each relevant edit event. Log entries are grouped under the version that they apply to.

The following illustration highlights the features of the **Version history** pane.

:::image type="content" source="media/version-history-elements.svg" alt-text="Screenshot that shows the elements of the Version history pane." lightbox="media/version-history-elements.svg":::

Legend:

1. **Save changes as current version** – Save a new version that includes all the changes that have been made since the last saved version. When you select this button, you're prompted to provide a name for the version.
1. **Time series version** – Each saved version shows its version name next to a blue dot on the timeline. Select a version to view it in the chart and data table. You can collapse or expand each version to hide or view the log of edits that were made to create that version. The top version is always the current version. This version might include edits that have been made since the last saved version.
1. **Change log entry** – Change log entries are nested below the version where they were made. Each entry shows the date and time when the change was made, and the user who made it.
1. **Initial version** – The initial version and its change log entry represent the time series creation event. It's always saved as a version. Therefore, you can easily view or restore it as you require.
1. **Version edit button** – Open a menu where you can select any of the following actions:

    - **Rename** – Enter a new name for the version.
    - **Restore** – Make the selected version the current version.
    - **Deactivate** – Deactivate the selected version. The values of newer versions aren't affected. Deactivated versions aren't shown in version selectors.
    - **Activate** – Reactivate an inactive version.

## Commenting and collaboration

You can add comments to a time series to communicate with other users. For example, you can explain why you chose to edit specific time series values or how to understand a saved data view. Users can also reply to each other's comments, edit or delete comments, and mark comment threads as resolved.

To view and work with comments, open a time series, and select the **Commenting Pane** button :::image type="icon" source="media/button-commenting-pane.png" border="false"::: in the upper-right corner of the page. The commenting pane that appears shows all the comments that have been made so far for the current series. From here, you can perform the following actions:

- Select **New** to add a new comment.
- For exiting comments, select the **More thread actions** button :::image type="icon" source="media/button-more-actions.png" border="false"::: to open a menu where you can choose to edit or delete the selected comment or mark the selected thread as resolved.
- Reply to an existing comment by entering text in its **Reply** field.
