---
title: Export and download data
description: Learn how to export a forecast that you've created, analyzed, and edited back to Microsoft Dynamics 365 Supply Chain Management.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: how-to
ms.date: 10/19/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Export and download data

[!include [banner](../includes/banner.md)]

When you've finished creating, analyzing, and editing a forecast, you can export it back to Microsoft Dynamics 365 Supply Chain Management. Alternatively, you can download the data as a comma-separated values (CSV) file that can be viewed in Excel.

## Download time series values as a CSV file

You can download the data table from any selected time series as a CSV file that you can open in Excel, for example.

1. Open the time series that you want to export from.
1. On the **Time series values** FastTab, select **Download** on the toolbar.

The file is saved as a CSV file in your local download folder.

## <a name="existing-export-profiles"></a>View and run existing data export profiles to export to Supply Chain Management

Demand planning lets you build a collection of *export profiles*. Each profile exports data to a specific Supply Chain Management instance. Typically, a manager or system administrator creates the initial collection of required profiles. Forecasters and other users can then run the profiles to export as they require.

To run an existing data export profile, follow these steps.

1. On the navigation pane, select **Data management** \> **Export**.
1. Find the profile for the type of export that you want to run, and select the link for it in the **Name** column.

    The details page for the selected profile appears. It contains the following tabs:

    - **Get started** – This tab provides basic information about the profile. You can edit the name and/or description to make the profile easier to identify and work with.
    - **Map columns** – This tab shows how the selected profile maps columns in Demand planning to columns in the target system. You can edit the mappings from here as you require.
    - **Define data export rules** – This tab shows any export rules that have been defined for the profile. You can edit the settings from here as you require.
    - **Run schedule** – This tab lets you set up a schedule for the profile to run automatically. For details about this functionality and how to configure it, see [Rolling forecasts](rolling-forecasts.md).
    - **Jobs** – This tab shows a list of every run of the profile.

1. To run the profile, select **Run** on the Action Pane. This command adds a new row to the grid on the **Jobs** tab. There, you can follow the status of the new export. The page isn't automatically refreshed. To update the status information, you must select **Refresh** on the grid toolbar.

## Create and manage data export profiles

Each time that your organization has to run a new type of data export, a manager or admin must create a new data export profile. After the profile is created, it becomes available to users, who can run it as often as they require. Data export profiles are used to export data to Supply Chain Management.

1. On the navigation pane, select **Data management** \> **Export**.
1. On the Action Pane, select **New**.
1. On the **Select data provider** page, select the **Microsoft finance and operations apps** tile.
1. A setup wizard is opened. On the **Get started** page, enter a name and description for the new profile. Then select **Next**.
1. On the **Configure data provider** page, in the **Connection URL** field, enter the URL of your Supply Chain Management environment. Then select **Next**.
1. On the **Select output data** page, select the time series to export to Supply Chain Management. You must select exactly one time series.

    - The **Available** tab shows a list of available time series. Select the time series to export in the grid, and then select **Include data source** on the toolbar. By default, the most recent version of the selected time series is exported. However, you can select older versions on the **Included** tab.
    - The **Included** tab shows the time series that's selected for export.

        - If more than one version of the time series is available, select the version that you want to use in the **Output version** field.
        - To remove a time series, select it, and then select **Remove** on the toolbar.
        - To set up one or more filter rules to apply to the exported data, select **Filter data source** on the toolbar.

1. When you've finished selecting and setting up the time series to export, select **Next**.
1. On the **Map columns** page, use the dropdown lists to map each column in the selected time series to the appropriate column in the target Supply Chain Management data entity. When you've finished, select **Next**.
1. On the **Define data export rules** page, specify the target company (legal entity) and forecast model ID to export the data to. You can select **All** to export all the data to the same company and forecast model, or you can select **Custom** to set up rules for splitting the export between different forecast models.
1. Select **Next**.
1. On the **Set run schedule** page, you can choose to set up a schedule for the profile to run automatically. For details about this functionality and how to configure it, see [Rolling forecasts](rolling-forecasts.md).
1. Select **Next**.
1. On the **Review and finish** page, review the summary of settings that you've configured, and then select **Review and finish** to create the new profile.
1. The profile is now available, but it hasn't yet run. To run it, follow the instructions in the [View and run existing data export profiles to export to Supply Chain Management](#existing-export-profiles) section.

## Improve performance by clearing unneeded staging data

If you're experiencing performance issues, it might help to clear staging data from the *Forecast Sales Import Entity* entity in Supply Chain Management. To do this, take one of the following actions:

- Manually [clear the staging data](../../fin-ops-core/dev-itpro/data-entities/staging-tables.md) as needed.
- Set up an [automatic cleanup process](../../fin-ops-core/dev-itpro/data-entities/clean-up-data.md) to clear the staging data on a regular basis.
