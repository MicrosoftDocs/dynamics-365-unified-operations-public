---
title: Export and download data
description: When you're done creating, analyzing, and editing a forecast, you can export back to Supply Chain management or download the data as a CSV file for viewing in Excel.
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

# Export and download data

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

When you're done creating, analyzing, and editing a forecast, you can export back to Supply Chain management or download the data as a CSV file for viewing in Excel.

## Download time series values as a CSV file

You can download the data table from any selected time series as a CSV file that you can open, for example, in Microsoft Excel. Follow these steps:

1. Open the time series you want to export from.
1. On the **Time series values** FastTab toolbar, select **Download**.
1. The file is saved as a CSV file in your local download folder.

## <a name="existing-export-profiles"></a>View and run existing data export profiles to export to Supply Chain Management

The Demand planning app lets you build a collection of *export profiles*, each of which exports data to a specific Supply Chain Management instance. Typically, a manager or system administrator will create the initial collection required profiles and, after that, forecasters and other users will be able to run the profiles to export as needed.

To run an existing data export profile, follow these steps:

1. On the navigation pane, select **Data management \> Export**.

1. Find the profile for the type of export you want to run and select the link in its **Name** column.

1. The detail page opens for your selected profile. It provides the following tabs:

    - **Get started** – Provides basic information about the profile. If you like, you can edit the **Name** and/or **Description** to make the profile easier to identify and work with.
    - **Map columns** – Shows how the selected profile maps columns in Demand planning to columns in the target system. You can edit these mappings from here if needed.
    - **Define data export rules** – Shows any export rules that have been defined for the profile. You can edit these settings from here if needed.
    - **Jobs** – Shows a list of each time the profile was run.

1. To run the profile, select **Run** on the Action Pane. This command adds a new row to the grid on the **Jobs** tab, where you can follow the status of the new export. The page doesn't refresh automatically, so you must select **Refresh** in the grid toolbar to refresh the status information.

## Create and manage data export profiles

Each time your organization needs to run a new type of data export, a manager or admin must create a new data export profile. Once the profile is created, it will be available to users, who can run it as often as needed. Data export profiles are used to export data to Supply Chain Management.

Follow these steps:

1. On the navigation pane, select **Data management \> Export**.
1. On the Action Pane, select **New**.
1. On the **Select data provider** page, select the **Microsoft finance and operations apps** tile.
1. A setup wizard launches, open to the **Get started** page. Enter a **Name** and **Description** for your new profile. Then select **Next**.
1. The **Configure data provider** page opens. In the **Connection URL** field, enter the URL of your Supply Chain Management environment. Then select **Next**.
1. The **Select output data** page opens. Use this page to choose which time series to export to Supply Chain Management.
    - The **Available** tab shows a list of available time series. Select the time series you want to support in the grid and then select **Include data source** from the toolbar. You must select exactly one time series to export. By default, the most recent version of the selected time series will be exported, but you can select older versions by going to the **Included** tab.
    - The **Included** tab shows the time series selected for this export.
        - If the time series has more than one version available, select the version you want to use from the **Output version** drop-down list.
        - To remove a time series, select it and then select **Remove** from the toolbar.
        - If you'd like to set up one or more filter rules to apply to the exported data, select **Filter data source** from the toolbar. (Each export profile can export to just one legal entity. If the time series has legal entity as a dimension, then you must set up a legal entity filter to choose which legal entity to export to. If you need to export to multiple legal entities, then create an export profile for each of them.)

    Select **Next** when you're done selecting and setting up the time series to export.

1. The **Map columns** page opens. Use the drop-down lists here to map each column in the selected time series to the appropriate column in the target Supply Chain Management data entity. Select **Next** when you're done.
1. The **Define data export rules** page opens. Use this page to specify the target **Company** (legal entity) and **Forecast model ID** to which you want to export the data. You can choose to export **All** of the data to the same company and forecast model, or select **Custom** to set up rules for splitting the export between different forecasts models. Select **Next** when you're done.
1. The **Review and finish page** opens. It summarizes the settings you've made. Review your settings and then select **Review and finish** to create the new profile.
1. The profile is now available but hasn't run yet. To run it, follow the instructions in [View and run existing data export profiles to export to Supply Chain Management](#existing-export-profiles).
