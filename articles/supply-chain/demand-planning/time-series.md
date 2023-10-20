---
title: Time series models
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

# Time series

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Time series represent output from forecasts, calculations, and transformations presented in time buckets (daily, weekly, or monthly).

## Explore time series

To see all your time series, on the navigation pane, select **Output \> Time Series.**

To open a series, select its name in the **Name** column. The following illustration shows the various features of the **Output** tab of time series details page.

:::image type="content" source="media/time-series-elements.svg" alt-text="Time series elements":::

Legend:

1. **Data view selector** – From this menu, you can save the current view (including all filters, overlayed series, and other selections) as a saved view. If you've already saved one or more views, you can also load them from here.
2. **Current filters** – If you've applied any filters to the data, they will be listed next to the **Add filter** button as colored blocks. You can remove any listed filter by selecting its close button.
3. **Add filter** – Opens a menu where choose to filter the time series by any combination of date or dimension values. This will affect the KPIs shown on the **Insights** FastTab, the graph shown on the **Timeline** FastTab, and the values available on the **Time series values** FastTab. Filters you add from here are added to the current filters list (2).
4. **Insights** – Shows key performance indicators (KPIs) for the current time series, including total quantity, average quantity, and standard deviation of quantity. These values reflect the filter settings.
5. **Timeline graph** – Shows a graphical representation of the selected time series. It provides the following features:
    - **Reflects time series filters** – Graph values are consistent with the filter settings made at the top of the page.
    - **Reflects row selections** – Graph values reflect the rows selected on the **Time series values** FastTab (if any).
    - **Read precise data values** – You can view precise data values at any point by hovering your mouse pointer over the graph.
    - **Set graph options** – You can adjust graph options (such as color, style, and grid options) using the **Select data** button.
    - **Overlay another time series** – You can overlay another time series (for comparison), also by using the **Select data** button. This illustration shows a second time series (in pink) overlayed over the current one (in blue).
6. **Time series values** – Shows tabular data for the selected time series. The following features and toolbar buttons are available here:
    - **Row selection** – Select a row to see only that row reflected in the timeline graph. Shift-click to select multiple rows. A blue check mark indicates which rows are selected. Select the checkmark to deselect a row. Select the checkmark at the top of the table to deselect all rows.
    - **Fit to data** – Adjusts the width of visible columns to ensure that the data isn't clipped.
    - **Downloads** – Downloads the data as a comma-separated values (CSV) file with the current filter and group options applied.
    - **Group by** – Lets you choose which of the available dimensions to use to group the data. For example, if you have dimensions for warehouses and product variants, then you could choose to group by both (to show each warehouse with each product variant listed under it), group by variant only (which will show variants but not the warehouses), or group by warehouse only (which will show the warehouses but not the variants). Totals values are aggregated to match the group selection.
    - **Filter totals** – Lets you set up a logical expression to filter the selection of rows shown in the table. For example, you might choose to only view rows with totals above 100,000 units. This setting doesn't affect the graph or KPIs.
    - **Select data** – Lets you add another time series to the graph and/or data table so that you can compare them. This opens the same dialog as the **Select data** button on the graph does, so you can also adjust graph options (such as color, style, and grid options).
    - **Edit** – Lets you edit values directly in the data table. If the edited value is aggregated due to the **Group by** settings, then the value of your edit will be divided proportionally among the aggregated data rows.

Open the **General** tab of the time series details page to view and adjust a few basic settings, many of which affect the way the time series is shown on the list page. The following settings are available on the **General** tab:

- **Name** – The name of the time series.
- **Description** – A short description of the time series.
- **Category** – The category of the time series. This value can be useful for sorting and filtering the time series list page. Select the magnifying glass button to select a category. If you don't see the category you want, go to **Configuration &gt; Categories** to create it.
- **Time buckets** – Shows the time buckets used by this series (daily, monthly, or yearly).
- **Allow manual edits** – Shows whether the series allows users to manually edit data values using the data table.
