---
title: Export and download data
description: Learn how to export a forecast that you've created, analyzed, and edited back to Microsoft Dynamics 365 Supply Chain Management.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: how-to
ms.date: 11/29/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Export and download data

[!include [banner](../includes/banner.md)]

When you've finished creating, analyzing, and editing a forecast, you can export it back to Microsoft Dynamics 365 Supply Chain Management. Alternatively, you can download the data as a comma-separated values (CSV) file that can be viewed in Excel.

## Export to to Supply Chain Management

### <a name="existing-export-profiles"></a>View and run existing data export profiles to export to Supply Chain Management

Demand planning lets you build a collection of *export profiles*. Each Supply Chain Management export profile exports data to a specific Supply Chain Management instance. Typically, a manager or system administrator creates the initial collection of required profiles. Forecasters and other users can then run the profiles to export as they require.

To run an existing data export profile, follow these steps.

1. On the navigation pane, select **Data management** \> **Export**.
1. Find the profile for the type of export that you want to run, and select the link for it in the **Name** column.

    The details page for the selected profile appears. Supply Chain Management export profiles contain the following tabs:

    - **Get started** – This tab provides basic information about the profile. You can edit the name and/or description to make the profile easier to identify and work with.
    - **Map columns** – This tab shows how the selected profile maps columns in Demand planning to columns in the target system. You can edit the mappings from here as you require.
    - **Define data export rules** – This tab shows any export rules that have been defined for the profile. You can edit the settings from here as you require.
    - **Run schedule** – This tab lets you set up a schedule for the profile to run automatically. For details about this functionality and how to configure it, see [Rolling forecasts](rolling-forecasts.md).
    - **Jobs** – This tab shows a list of every run of the profile.

1. To run the profile, select **Run** on the Action Pane. This command adds a new row to the grid on the **Jobs** tab. There, you can follow the status of the new export. The page isn't automatically refreshed. To update the status information, you must select **Refresh** on the grid toolbar.

### Create and manage profiles for exporting to Supply Chain Management

Each time that your organization has to run a new type of data export, a manager or admin must create a new data export profile. After the profile is created, it becomes available to users, who can run it as often as they require. Each profile exports either to Supply Chain Management or an CSV file, depending on how to set them up. This section describes how to create a profile that exports to your selected Supply Chain Management instance.

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

## Export to a CSV file

### Download a time series values grid as a CSV file

You can download the time series values grid from any selected time series as a CSV file. This type of export creates a CSV file that presents the data the same way as it's shown in **Time series values** grid for the time series, which means that it contains one row for each combination of dimensions and a column for each dimension, the grand total value, and the value for each available date. If you require a file that instead has a row for each date, you should instead create a CSV export profile and run it as described later in this topic (this type of CSV file might be more useful for importing data into other systems).

To export the time series values grid from any selected time series to a CSV file, follow these steps.

1. Open the time series that you want to export from.
1. On the **Time series values** FastTab, select **Download** on the toolbar.

The file is saved as a CSV file in your local download folder.

### <a name="existing-csv-profiles"></a>View and run existing data export profiles to export to CSV

Demand planning lets you build a collection of *export profiles*. Each CSV export profile exports data from a selected time series to a CSV file saved on your local computer. The CSV file includes a row for each date with columns for the date, value, and each dimension.

Typically, a manager or system administrator creates the initial collection of required profiles. Forecasters and other users can then run the profiles to export as they require.

To run an existing data export profile, follow these steps.

1. On the navigation pane, select **Data management** \> **Export**.
1. Find the profile for the type of export that you want to run, and select the link for it in the **Name** column.

    The details page for the selected profile appears. CSV export profiles contain the following tabs:

    - **Get started** – This tab provides basic information about the profile. You can edit the name and/or description to make the profile easier to identify and work with.
    - **Run schedule** – This tab lets you set up a schedule for the profile to run automatically. For details about this functionality and how to configure it, see [Rolling forecasts](rolling-forecasts.md).
    - **Jobs** – This tab shows a list of every run of the profile.

1. To run the profile, select **Run** on the Action Pane. This command adds a new row to the grid on the **Jobs** tab. There, you can follow the status of the new export. The page isn't automatically refreshed. To update the status information, you must select **Refresh** on the grid toolbar.
1. When the job is finished, select **Download** on the Action Pane to download the data as a CSV file and save it in your local download folder.

### Create and manage profiles for exporting to CSV

Each time that your organization has to run a new type of data export, a manager or admin must create a new data export profile. After the profile is created, it becomes available to users, who can run it as often as they require. Each profile exports either to Supply Chain Management or an CSV file, depending on how to set them up. This section describes how to create a profile that exports to CSV.

1. On the navigation pane, select **Data management** \> **Export**.
1. On the Action Pane, select **New**.
1. On the **Select data provider** page, select the **CSV** tile.
1. A setup wizard is opened. On the **Get started** page, enter a name and description for the new profile. Then select **Next**.
1. On the **Configure data provider** page, in the **Connection URL** field, enter the URL of your Supply Chain Management environment. Then select **Next**.
1. On the **Select output data** page, select the time series to export to CSV. You must select exactly one time series.

    - The **Available** tab shows a list of available time series. Select the time series to export in the grid, and then select **Include data source** on the toolbar. By default, the most recent version of the selected time series is exported. However, you can select older versions on the **Included** tab.
    - The **Included** tab shows the time series that's selected for export.

        - If more than one version of the time series is available, select the version that you want to use in the **Output version** field.
        - To remove a time series, select it, and then select **Remove** on the toolbar.
        - To set up one or more filter rules to apply to the exported data, select **Filter data source** on the toolbar.

1. When you've finished selecting and setting up the time series to export, select **Next**.
1. On the **Set run schedule** page, you can choose to set up a schedule for the profile to run automatically. For details about this functionality and how to configure it, see [Rolling forecasts](rolling-forecasts.md).
1. Select **Next**.
1. On the **Review and finish** page, review the summary of settings that you've configured, and then select **Review and finish** to create the new profile.
1. The profile is now available, but it hasn't yet run. To run it, follow the instructions in the [View and run existing data export profiles to export to CSV](#existing-csv-profiles) section.

## Improve performance by clearing unneeded staging data

If you're experiencing performance issues, it might help to clear staging data from the *Forecast Sales Import Entity* entity in Supply Chain Management. To do this, take one of the following actions:

- Manually [clear the staging data](../../fin-ops-core/dev-itpro/data-entities/staging-tables.md) as needed.
- Set up an [automatic cleanup process](../../fin-ops-core/dev-itpro/data-entities/clean-up-data.md) to clear the staging data on a regular basis.
