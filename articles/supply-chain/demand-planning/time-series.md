---
title: Time series and planning data
description: Time series represent output from forecasts, calculations, and transformations presented in time buckets (daily, weekly, or monthly).
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/19/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Time series and planning data

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Time series represent output from forecasts, calculations, and transformations presented in time buckets (daily, weekly, or monthly).

## <a name="explore"></a>Explore time series

To see all your time series, on the navigation pane, select **Planning data \> All**. (Or select an appropriate time series category under the **Planning data** heading.)

To open a series, select its name in the **Name** column. The following illustration shows the various features of the **Output** tab of time series details page.

:::image type="content" source="media/time-series-elements.svg" alt-text="Time series elements" lightbox="media/time-series-elements.svg":::

Legend:

1. **Data view selector** – From this menu, you can save the current view (including all filters, overlaid series, and other selections) as a saved view. If you've already saved one or more views, you can also load them from here.
2. **Current filters** – If you've applied any filters to the data, they'll be listed next to the **Add filter** button as colored blocks. You can remove any listed filter by selecting its close button.
3. **Add filter** – Opens a menu where you can choose to filter the time series by any combination of date or dimension values. This affects the KPIs shown on the **Insights** FastTab, the graph shown on the **Timeline** FastTab, and the values available on the **Time series values** FastTab. Filters you add from here are added to the current filters list (2).
4. **Insights** – Shows key performance indicators (KPIs) for the current time series, including total quantity, average quantity, and standard deviation of quantity. These values reflect the filter settings.
5. **Timeline graph** – Shows a graphical representation of the selected time series. It provides the following features:
    - **Reflects time series filters** – Graph values are consistent with the filter settings made at the top of the page.
    - **Reflects row selections** – Graph values reflect the rows selected on the **Time series values** FastTab (if any).
    - **Read precise data values** – You can view precise data values at any point by hovering your mouse pointer over the graph.
    - **Set graph options** – You can adjust graph options (such as color, style, and grid options) using the **Select data** button.
    - **Overlay another time series** – You can overlay another time series (for comparison), also by using the **Select data** button. This illustration shows a second time series (in pink) overlaid over the current one (in blue).
6. **Time series values** – Shows tabular data for the selected time series. The following features and toolbar buttons are available here:
    - **Row selection** – Select a row to see only that row reflected in the timeline graph. Shift-click to select multiple rows. A blue check mark indicates which rows are selected. Select the checkmark to deselect a row. Select the checkmark at the top of the table to deselect all rows.
    - **Fit to data** – Adjusts the width of visible columns to ensure that the data isn't clipped.
    - **Downloads** – Downloads the data as a comma-separated values (CSV) file with the current filter and group options applied.
    - **Group by** – Lets you choose which of the available dimensions to use to group the data. For example, if you have dimensions for warehouses and product variants, then you could choose to group by both (to show each warehouse with each product variant listed under it), group by variant only (which shows variants but not the warehouses), or group by warehouse only (which shows the warehouses but not the variants). Totals values are aggregated to match the group selection.
    - **Filter totals** – Lets you set up a logical expression to filter the selection of rows shown in the table. For example, you might choose to only view rows with totals above 100,000 units. This setting doesn't affect the graph or KPIs.
    - **Select data** – Lets you add another time series to the graph and/or data table so that you can compare them. This opens the same dialog as the **Select data** button on the graph does, so you can also adjust graph options (such as color, style, and grid options).
    - **Edit** – Lets you edit values directly in the data table. If the edited value is aggregated due to the **Group by** settings, then the value of your edit will be divided proportionally among the aggregated data rows.

Open the **General** tab of the time series details page to view and adjust a few basic settings, many of which affect the way the time series is shown on the list page. The following settings are available on the **General** tab:

- **Name** – The name of the time series.
- **Description** – A short description of the time series.
- **Category** – The category of the time series. This value controls which navigation entry the time series will be listed in (under the **Planning data** heading in the navigation pane), in addition to the **All** entry. Select the magnifying glass button to select a category.
- **Time buckets** – Shows the time buckets used by this series (daily, monthly, or yearly).
- **Allow manual edits** – Shows whether the series allows users to manually edit data values using the data table.

## Customize time series chart and data table layouts

Demand planning provides many options that help you to analyze your time series. Among them is the ability to customize the chart layout (such as style, color, size), overlay the chart or data table with another time series to make easy comparisons, and to assign logic for highlighting certain cells in the data table to make them stand out.

To make these settings, open a time series and then select **Select data** from either the **Timeline** FastTab or the **Time series values** FastTab (it doesn't matter which). The **Select data** dialog opens.

To add a new time series to the graph and/or data table, select the **Add** button. You'll be asked to select an existing time series. After you select a time series, it will be added as a new row in the **Select data** dialog. To remove a time series from the graph and data table, select its close box on the right side of the row. The top row of the **Select data** dialog lists the current time series, which you can customize, but can't remove.

Each row in the **Select data** dialog provides the following information and options for each listed time series:

- **Name** – Shows the name of the time series.
- **Version** – For time series that have more than one version, select the version to use from this drop-down list.
- **Description** – Shows a short description of the time series.
- **Show in chart** – Enable this option for each time series that you want to include in the graph.
- **Chart styling** – Select the **Customize** link in this column to open a dialog where you can customize the way the selected row appears in the graph. You can choose to present the series as a line or series of bars, and you can choose the color. You can also choose to add a **Secondary axis**, which is useful if your selected series use very different values from either other (such as when comparing sales in the millions of units against prices in the hundreds of dollars). When you choose to add a secondary axis, a new set of values will be shown on the right side of the chart to indicate the scale of the second time series.
- **Show in grid** – Enable this option for each time series that you want to include in the data table.
- **Grid formatting** – Select the **Customize** link in this column to open a dialog where you can specify logic for highlighting cells in the data table. You can highlight cells for the selected series according to their own values, or according to values from another time series for the same time bucket. (Set **Use values from another time series** to *Yes* and then specify a series and version if you want to compare to another series.) You can add as many rules as you need. For each rule, specify the logic (for example, find values less than 4,000,000) and the style (color and icon) to apply to cells that match that rule.

After you've spent time customizing and formatting your time series, you'll probably want to save your settings as a new data view so you can return to it later. To do so, open the drop-down menu at the top-left of the page and select **Save as new dataview** (see also [Explore time series](#explore)). You can save as many data views as you need for each time series.

## Time series versions, version control, and change log

Demand planning lets you edit cell values directly, which means that you can modify the underlying data for any time series. Each time you do this, the change is noted in the change log, where all users can see when the change was made and who made it. At any time, you can save your edits so far (since the last version) as a new version, which you can give a name. You can view any version by selecting it in the version history, and you can restore any previous version to the current version.

Sometimes, when you're selecting a time series, you'll be able to choose which version to use. For example, when you use **Select data** to overlay one time series over the current one, you can choose which version to use. You can even overlay a previous version of the same time series to quickly see what changed between versions.

To view the change log and version history for a time series, open the time series and then select **Version history** from the Action Pane. The **Version history** panel opens, which shows a log entry for each relevant edit event, with log entries grouped under the version where they apply.

The following illustration highlights the features of the **Version history** panel.

:::image type="content" source="media/version-history-elements.svg" alt-text="Elements of the version history panel" lightbox="media/version-history-elements.svg":::

Legend:

1. **Save changes as current version** – Select this button to save a new version that includes all of the changes made since the last saved version. You'll be asked to provide a version name.
1. **Time series version** – Each saved version shows its version name next to a blue dot on the timeline. Select a version to view it in the graph and data table. You can collapse or expand each version to hide or view the log of edits made to create that version. The top version is always the current version, which might include edits made since the last saved version.
1. **Change log entry** – Change log entries are nested below the version where they were made. Each entry shows the date and time the change was made and the user who made it.
1. **Initial version** – The initial version and its change log entry represent the time series creation event. It's always saved as a version so you can easily view or restore it as needed.
1. **Version edit button** – Select this button to open a menu where you can select any of the following actions:
    - **Rename** – Lets you enter a new name for the version.
    - **Restore** – Makes the selected version the current version.
    - **Deactivate** – Deactivates the selected version but doesn't affect the values of newer versions. Deactivated versions aren't shown in version selectors.
    - **Activate** – Reactivates an inactive version.

## Commenting and collaboration

You can add comments to a time series to communicate with other users. For example, you might add an explanation about why you chose to edit certain time series values or how to understand a saved data view. Users can also reply to one another's comments, edit or delete comments, and mark comment threads as resolved.

To view and work with comments, open a time series and select the **Commenting Pane** button :::image type="icon" source="media/button-commenting-pane.png" border="false"::: at the top-right corner of the page. This opens the commenting pane, which shows all comments made so far for the current series. From here, you can do the following actions:

- Select **New** to add a new comment.
- For exiting comments, select the **More thread actions** button :::image type="icon" source="media/button-more-actions.png" border="false"::: to open a menu where you can choose to edit or delete the selected comment or mark the selected thread as resolved.
- Reply to an existing comment by entering text in its **Reply** field.
