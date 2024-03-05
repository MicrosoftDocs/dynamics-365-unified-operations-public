---
title: Import data into Demand planning (preview)
description: This article describes how to import data from different sources and file types, and also data that is stored in a Microsoft Azure data lake.
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

# Import data into Demand planning (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

You can import data from a range of sources and file types. For example, you can import data directly from Microsoft Dynamics 365 Supply Chain Management or by importing text files in Excel or comma-separated values (CSV) format. You can also import data that's stored in an Azure data lake. Before you import the data into Demand planning, you can use Power Query to transform it as you require.

The Demand planning app lets you build a collection of *import profiles*. Each profile imports data from a specific external source into one or more specific tables in Demand planning.

Typically, a manager or system administrator creates the initial collection of required profiles. Forecasters and other users can then run the profiles to update the data as they require.

In addition, you can use the standard user interface (UI) to import your custom data entities into custom tables or add custom fields that you've extended in the standard tables. No developer is required.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## <a name="existing-import-profiles"></a>View and run existing data import profiles

You have to import data only as often as the relevant data changes in the external systems. Some profiles must be run only occasionally, whereas others must be run almost every time that a user works with the app.

To update your data by running an existing data import profile, follow these steps.

1. On the navigation pane, select **Data management** \> **Import**.
1. Find the profile for the type of import that you want to run, and select the link for it in the **Name** column.

    The details page for the selected profile appears. It contains the following tabs:

    - **Summary** – This tab provides basic information about the profile. You can edit the name and/or description to make the profile easier to identify and work with.
    - **Jobs** – This tab shows a list of every run of the profile. It includes date information, the job status, the provider that was used, the table that was updated, and the number of records that were imported. Links to more information are provided.

1. To run the profile, select **Run** on the Action Pane. This command adds a new row to the grid on the **Jobs** tab. There, you can follow the status of the new import. The page isn't automatically refreshed. To update the status information, you must select **Refresh** on the grid toolbar.

## Create and manage data import profiles

Each time that your organization has to run a new type of data import, a manager or admin must create a new data import profile. After the profile is created, it becomes available to users, who can run it as often as they require.

Each data import profile uses a *data provider* that's optimized to import data from a specific type of external data source or file type. The following types of data providers are currently available:

- **Power Query providers** – Each of these providers imports from a specific type of file (CSV, Excel, or Azure data lake storage) through Power Query. Therefore, you can transform and map the data for the relevant table in Demand planning.
- **Microsoft finance and operations apps provider** – This provider connects directly to Supply Chain Management (or another finance and operations app) and imports data that's provided by one or more data entities into the relevant tables in Demand planning.

### Create an import profile for importing directly from Supply Chain Management

To import directly from Supply Chain Management (and other finance and operations apps), create an import profile that uses the *Microsoft finance and operations apps* data provider.

1. On the navigation pane, select **Data management** \> **Import**.
1. On the Action Pane, select **New**.
1. On the **Select data provider** page, select the **Microsoft finance and operations apps** tile.
1. A setup wizard is opened. On the **Get started** page, enter a name and description for the new profile. Then select **Next**.
1. On the **Configure data provider** page, in the **Connection URL** field, enter the URL of your Supply Chain Management environment. Then select **Next**.
1. The **Entity selection** page lists every Supply Chain Management data entity that the solution supports out of the box. It also shows which Demand planning table each data entity maps to. Turn on the **Enabled** option for each entity that you want to import from for the new profile. Then select **Next**. All Supply Chain Management data entities are supported and can be imported. Note that a table must previously be created in the Demand Planning app before you can map the fields. 
1. On the **Review and finish** page, review the summary of settings that you've configured, and then select **Review and finish** to create the new profile.
1. You're returned to the **Active Import Data Profiles** page, which now shows the new profile in the list. The profile is now available, but it hasn't yet run. To run it, follow the instructions in the [View and run existing data import profiles](#existing-import-profiles) section.

### Create an import profile for importing from exported files through Power Query

To import from a text or workbook file that was exported from an external system, create an import profile that uses one of the *Power Query* data providers. The provider that you use must match the format of the exported file, but the procedure is the same.

1. On the navigation pane, select **Data management** \> **Import**.
1. On the Action Pane, select **New**.
1. On the **Select data provider** page, under **Power Query providers**, select the tile that matches the format of the exported file that you'll use the new profile to import.
1. A setup wizard is opened. On the **Get started** page, enter a name and description for the new profile. Then select **Next**.
1. On the **Select target table** page, in the **Select table** field, select the name of the table in Demand planning that you want to use the new profile to import data into. Then select **Next**.
1. On the **Configure provider** page, select the file that you want to import and then send to Power Query, where you can transform the data and map columns from the source document to the selected Demand planning table. The connection, transformation, and mapping features are all provided by Power Query. The procedure varies slightly, depending on the Power Query provider that you're using:

    - **Excel** – For information about how to select the target file, connect to Power Query, and work with data, see [Excel](/power-query/connectors/excel) in the Power Query documentation.
    - **CSV** – For information about how to select the target file, connect to Power Query, and work with data, see [Text/CSV](/power-query/connectors/text-csv) in the Power Query documentation.
    - **Datalake** – For information about how to select the target file, connect to Power Query, and work with data, see [Datalake](/power-query/connectors/dataverse) in the Power Query documentation. A data lake must previously be set up as described in [Datalake setup](/power-query/connectors/data-lake-storage).

1. When you've finished transforming and mapping your data by using Power Query, select **Next**.
1. On the **Refresh settings** page, select or clear the **Delete all data for the chosen table before import** checkbox to specify what should happen to the data that's currently in the target table in Demand planning:

    - *Selected* – Delete all the data that's currently in the target table. You might use this option if, for example, the incoming data includes all the required records that are already in your table, and/or you haven't selected a key field for the table. This option ensures that you won't have any duplicate records, but it also deletes all the data that's currently in the target table.
    - *Cleared* – Keep all the data that's currently in the target table. You might use this option if, for example, the incoming data is an incremental export that contains only new records, and/or you've selected key fields for the table. Incoming records that have key field values that match existing records will update those records, whereas incoming records that have unique key field values will create new records. If your key fields aren't configured and mapped correctly, there's a risk that this option will create duplicate records.

1. Select **Next**.
1. On the **Review and finish** page, review the summary of settings that you've configured, and then select **Review and finish** to create the new profile.
1. You're returned to the **Active Import Data Profiles** page, which now shows the new profile in the list. The profile is now available, but it hasn't yet run. To run it, follow the instructions in the [View and run existing data import profiles](#existing-import-profiles) section.
