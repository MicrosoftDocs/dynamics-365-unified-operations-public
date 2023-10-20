---
title: Transform data
description: Transformations allow you to select a table that holds imported data and transform that data into time series, which you can use to create a forecast, compare to a forecast, or make calculations.
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

# Transform data

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Transformations allow you to select a table that holds imported data and transform that data into time series, which you can use to create a forecast, compare to a forecast, or make calculations.

For example, you might want to time shift the historical demand time from last year by 12 months so it can be used as the base for the forecast for next year. Or you might want to combine historical demand data that is daily into monthly buckets because you run planning on a monthly basis.

Demand planning lets you build a collection of *transformation profiles*, each of which transforms data from a specific data table already set up in the app into a time series that you can analyze using the app.

Each transformation profile takes a selected [main table](tables.md) as its input, and that main table could have other tables related to it.

- The main table typically represents historical demand, such as sales orders.
- The main table must include a *timestamp* column, which will become the X-axis of the output time series. This will typically be the order date or delivery date.
- The main table must include a *measure* column, which will become the Y-axis of the output time series. This will typically represent units sold.
- Either the main table or one of its related tables must include at least one dimension column. Often you'll select more than one dimension because that will let you analyze the data in several ways. For example, if you're looking at T-shirts, you might include dimensions for color dimension, size, style, and warehouse. These dimensions would allow you to view the output time series to see, for example, the historical demand for red, extra-large T-shirts sold from the Chicago warehouse and compare that with the overall sales of all T-shirts from all warehouses.

Typically, a manager or system administrator will create the initial collection required profiles and, after that, forecasters and other users will be able to run the profiles to update the time series as needed.

## View and run existing transformation profiles

You only need to run a transformation profile as often as you import new data into the relevant tables. Some profiles will only need to be run occasionally, while others might be run nearly every time a user works with the app.

To refresh your time series by running an existing transformation profile, follow these steps:

1. On the navigation pane, select **Operations \> Transformations**.

1. Find the profile for the type of transformation you want to run and select the link in its **Name** column.

1. The detail page opens for your selected profile. It provides the following tabs:
    - **Summary** – Provides basic information about the profile. If you like, you can edit the **Name** and/or **Description** to make the profile easier to identify and work with. You can also change the **Owner** and adjust the **Time Bucket** but usually you shouldn't change these for existing profiles. For more information about these settings, see [Create and manage transformation profiles](#create-transformation-profiles).
    - **Transformations** – Shows details about the transformation that the profile will process. See [Create and manage transformation profiles](#create-transformation-profiles) for more information about these settings.
    - **Jobs** – Shows a list of each time the profile was run, include date information, job status, and the times series that was updated. Select the link in the **Time Series** column to open the time series.

1. To run the profile, select **Run** on the Action Pane. This command adds a new row to the grid on the **Jobs** tab, where you can follow the status of the new transformation. The page doesn't refresh automatically, so you must select **Refresh** in the grid toolbar to refresh the status information.

## <a name="create-transformation-profiles"></a>Create and manage transformation profiles

Each time your organization requires a new type of data transformation, a manager or admin must create a new transformation profile. Once the profile is created, it will be available to users, who can run it as often as needed.

To create or edit a transformation profile, follow these steps:

1. On the navigation pane, select **Operations \> Transformations**.

1. On the Action Pane, select **New**.

1. A setup wizard launches, open to the **Get started** page. Make the following settings:
    - **Name** – Enter a name for the new profile.
    - **Description** – Enter a short description of the profile.
    - **Owner** – Select the user account that owns the profile.
    - **Time Bucket** – Specify the time span by which data should summed in the time series output by this profile (*Daily*, *Weekly*, or*Monthly*). A shorter time bucket results in more data points along the X-axis. Choose the level of granularity that meets your needs.

1. Select **Next**.

1. The **Configure transformation** page opens. Select a table and then map the columns of that table, and its related tables, to transform the data into a timeline.
    - The grid shows a row for each column output by the transformation.
    - Buttons on the toolbar let you add new columns, remove a column selected in the grid, or reset the grid entirely.
    - You can only select a single main table at a time. If you need to change the main table, then you must reset the grid.

1. To select the main table and/or add or remove columns for the main table and related tables Select **Add column** from the toolbar. The **Add columns to your transformation dialog** opens.

1. If no main table has been selected yet, then select one from the **Tables** drop-down list. (If you need to change the main table, you must first reset the entire transform by selecting **Reset**.)

1. To add a data column to the transformation, select a table in the left column of the dialog, then in the middle column, select the name of the data column from that table that you want to add. For more information about how these various types of columns are used, see the introduction to this article.
    - You must have exactly one column selected under the **Timestamp** heading. This will become the X-axis of the output time series and will typically come from the main table.
    - You must have exactly one column selected under the **Measure** heading. This will become the Y-axis of the output time series and will typically come from the main table.
    - You must have at least one dimension column selected under the **Dimension** heading. Dimensions provide interactive parameters that let you choose which values to view in the output time series. These columns might come from the main table and/or any of the related tables.

    > [!NOTE]
    > The order in which you add the dimension columns defines how the output time series aggregates the data.

    Each time you add a data column, it's added to the list in the right column of the dialog, which lets you see your previous selections even while you explore the various tables. The order in which you selected the dimensions is reflected under the **Dimension** heading here.

    Select **OK** when you're done selecting data columns.

1. The **Review and finish page** opens. It summarizes the settings you've made. Review your settings and then select **Review and finish** to create the new profile.

1. Your profile is now saved, but it hasn't run yet. If you're ready to create a time series now, then select **Run** on the Action Pane.
