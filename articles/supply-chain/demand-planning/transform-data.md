---
title: Transform data
description: Learn how to transform the imported data in a selected table into time series. You can then use the time series to create a forecast or do calculations.
author: aevengir
ms.author: aevengir
ms.topic: how-to
ms.date: 10/19/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Transform data

[!include [banner](../includes/banner.md)]

Transformations let you transform the imported data in a selected table into time series. You can then use the time series to create a forecast, do a comparison to a forecast, or do calculations. For example, you might want to shift the historical demand time from last year by 12 months, so that it can be used as the basis for next year's forecast. Alternatively, you might want to combine daily historical demand data into monthly buckets, because you run planning on a monthly basis.

Demand planning lets you build a collection of *transformation profiles*. Each profile transforms data from a specific data table that's already set up in the app into a time series that you can analyze by using the app.

Each transformation profile takes a selected [main table](tables.md) as its input. That main table can have other tables that are related to it.

- The main table typically represents historical demand, such as sales orders.
- The main table must include a *timestamp* column. This column will become the x-axis of the output time series and typically represents the order date or delivery date.
- The main table must also include a *measure* column. This column will become the y-axis of the output time series and typically represents units that are sold.
- Either the main table or one of its related tables must include at least one dimension column. Often, you'll select more than one dimension, so that you can analyze the data in multiple ways. For example, if you're looking at T-shirts, you might include columns for the color, size, style, and warehouse dimensions. You can then view the output time series to see, for example, the historical demand for red, extra-large T-shirts that are sold from the Chicago warehouse. You can also compare that demand with the overall sales of all T-shirts from all warehouses.

Typically, a manager or system administrator creates the initial collection of required profiles. Forecasters and other users can then run the profiles to update the time series as they require.

## View and run existing transformation profiles

You have to run a transformation profile only as often as you import new data into the relevant tables. Some profiles must be run only occasionally, whereas others must be run almost every time that a user works with the app.

To update your time series by running an existing transformation profile, follow these steps.

1. On the navigation pane, select **Operations** \> **Transformations**.
1. Find the profile for the type of transformation that you want to run, and select the link for it in the **Name** column.

    The details page for the selected profile appears. It contains the following tabs:

    - **Summary** – This tab provides basic information about the profile. You can edit the name and/or description to make the profile easier to identify and work with. Although you can also change the owner and adjust the time bucket, you typically shouldn't change these details for existing profiles. For information about how to work with the settings on this tab, see the [Create and manage transformation profiles](#create-transformation-profiles) section.
    - **Transformations** – This tab shows details about the transformation that the profile will process. For information about how to work with the settings on this tab, see the [Create and manage transformation profiles](#create-transformation-profiles) section.
    - **Run schedule** – This tab lets you set up a schedule for the profile to run automatically. For details about this functionality and how to configure it, see [Rolling forecasts](rolling-forecasts.md).
    - **Jobs** – This tab shows a list of every run of the profile. It includes date information, the job status, and the time series that was updated. Select a link in the **Time Series** column to open the time series.

1. To run the profile, select **Run** on the Action Pane. This command adds a new row to the grid on the **Jobs** tab. There, you can follow the status of the new transformation. The page isn't automatically refreshed. To update the status information, you must select **Refresh** on the grid toolbar.

## <a name="create-transformation-profiles"></a>Create and manage transformation profiles

Each time that your organization requires a new type of data transformation, a manager or admin must create a new transformation profile. After the profile is created, it becomes available to users, who can run it as often as they require.

To create or edit a transformation profile, follow these steps.

1. On the navigation pane, select **Operations** \> **Transformations**.
1. On the Action Pane, select **New**.
1. A setup wizard is opened. On the **Get started** page, set the following fields:

    - **Name** – Enter a name for the new profile.
    - **Description** – Enter a short description of the profile.
    - **Owner** – Select the user account that owns the profile.
    - **Time Bucket** – Specify the time span to sum data by in the time series that this profile generates as output: *Daily*, *Weekly*, or *Monthly*. The shorter the time bucket, the more data points there will be on the x-axis. Select the time bucket that will give the required level of granularity.

1. Select **Next**.
1. On the **Configure transformation** page, select a table, and then map the columns of that table and its related tables to transform the data into a timeline.

    - The grid has a row for each column that the transformation generates as output.
    - You can use the buttons on the toolbar to add columns to the grid, remove selected columns from the grid, or completely reset the grid.
    - You can select only one main table at a time. To change the main table, you must reset the grid.

1. To select the main table, and/or add or remove columns for the main table and related tables, select **Add column** on the toolbar.
1. In the **Add columns to your transformation** dialog box, if no main table has been selected yet, select one in the **Tables** field. (If you have to change the main table, you must first reset the whole transformation by selecting **Reset**.)
1. To add a data column to the transformation, select a table in the left column of the dialog box. Then, in the middle column, select the name of the data column in that table that you want to add. For information about how the different types of columns are used, see the beginning of this article.

    - Under **Timestamp**, you must select exactly one column. This column will become the x-axis of the output time series and typically comes from the main table.
    - Under **Measure**, you select exactly one column. This column will become the y-axis of the output time series and typically comes from the main table.
    - Under **Dimension**, you must select at least one dimension column. Dimensions provide interactive parameters that let you choose which values to view in the output time series. These columns can come from the main table and/or any related tables.

    > [!NOTE]
    > The order that you add the dimension columns in defines how the output time series aggregates the data.

    Each time that you add a data column, it's added to the list in the right column of the dialog box. Therefore, you can view your previous selections while you explore the different tables. Under **Dimension**, the order reflects the order that you selected the dimensions in.

1. When you've finished selecting data columns, select **OK**.
1. Select **Next**.
1. On the **Set run schedule** page, you can choose to set up a schedule for the profile to run automatically. For details about this functionality and how to configure it, see [Rolling forecasts](rolling-forecasts.md).
1. Select **Next**.
1. On the **Review and finish** page, review the summary of settings that you've configured, and then select **Review and finish** to create the new profile.
1. The profile is now saved, but it hasn't yet run. If you're ready to create a time series now, select **Run** on the Action Pane.
