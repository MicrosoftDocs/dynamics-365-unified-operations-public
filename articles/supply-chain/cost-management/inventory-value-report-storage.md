---
# required metadata

title: Inventory value storage report
description: This topic explains how to run an Inventory value storage report and make the output available digitally, either as an interactive page in Microsoft Dynamics 365 Supply Chain Management or as an exported document in any of several formats.
author: AndersGirke
manager: tfehr
ms.date: 04/17/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: aevengir
ms.search.validFrom: 2020-04-17
ms.dyn365.ops.version: Release 10.0.9
---

# Inventory value storage report

This topic explains how to run an **Inventory value storage** report and make the output available digitally, either as an interactive page in Microsoft Dynamics 365 Supply Chain Management or as an exported document in any of several formats.

When you view the report in your browser, columns and aggregate balances are dynamically adjusted, depending on the layout that you've configured. You can sort the results, filter them, drill down into the data, and more.

Report results are stored in the **Inventory value** data entity. Therefore, you can filter and export the results to a format such as comma-separated values (CSV) or Microsoft Excel format.

The **Inventory value storage** report is helpful when the output contains many lines. For example, you have 50,000 items, and 300 stores have been created as warehouses. In this case, if you request inventory ending balances by item, site, and warehouse, the output will contain many lines.

> [!NOTE]
> The report won't include subtotals that are defined in the report layout. It also won't include general ledger balances, even when they are defined in the report layout. Reconciliation to the general ledger must be done by using trial balances.

## Turn on the Inventory value storage feature

Before you can generate an **Inventory value storage** report, you must turn on the feature in your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on if it's required. In the **Feature management** workspace, the feature is listed in the following way:

- **Module** – Cost management
- **Feature name** – Inventory value storage

## Generate an Inventory value storage report

Follow these steps to generate and store an **Inventory value storage** report.

1. Go to **Cost management \> Inquiries and reports \> Inventory value report storage**.
1. Select **New**.
1. In the **Inventory value** dialog box that appears, set the following values to define which records are included in your report:

    - On the **Parameters** FastTab, enter a unique name for the report, and use the fields in the **Date interval** section to define which records are included in the report. To define the date interval, you can either select a preset range (relative to the report generation date) in the **Date interval code** field, or select specific dates in the **From date** and **To date** fields. <!-- KFM: What is the ID setting for here? What do its values mean? -->
    - On the **Records to include** FastTab, set up filters and constraints to define which data is included in the report.
    - On the **Run in the background** FastTab, specify how, when, and how often the report is generated.

    > [!NOTE]
    > This report is always run as part of a batch job.

1. Select **OK** to apply your settings and close the dialog box.

After the batch job is completed, the report will be listed on the **Inventory value report storage** page. You might have to refresh the page to see the report.

## Explore an Inventory value storage report

After you've generated a report, you can view and explore it at any time by following these steps.

1. Go to **Cost management \> Inquiries and reports \> Inventory value report storage**.
1. Select a report in the list.
1. Select **View details** to show the report content.
1. Explore the report by following any of these steps:

    - As for most standard pages in Supply Chain Management, you can select almost any column heading to sort or filter the grid by the values in that column.
    - Use the **Filter** field to filter the report by any value in any of several available columns.
    - Use the view menu (above the **Filter** field) to save and load your favorite combinations of sort and filter options.

## Export an Inventory value storage report

Every report that you generate is stored in the **Inventory value** data entity. You can use the standard data management features of Supply Chain Management to export data from this entity to any supported data format, such as CSV or Excel format.

The following example shows how to export an **Inventory value report** report.

1. Go to **System administration \> Workspaces \> Data management**.
1. In the **Import / Export** section, select the **Export** tile. 
1. On the **Export** page that appears, you will set up the export job. First enter a group name for the job.
1. In the **Selected entities** section, select **Add entity**.
1. In the dialog box that appears, set the following fields:

    - **Entity name** – Select **Inventory value**.
    - **Target data format** – Select the format to export data to.

1. Select **Add** to add the new row, and then select **Close** to close the dialog box.
1. Usually, you will export one report at a time. To export a single report, set up a filter for the row that you just added to the **Inquiry** dialog box. In this way, you can define which report from the **Inventory value** entity is included in your export. Follow these steps to set the following filter options to export a single report:

    1. On the **Range** tab, select **Add** to add a row.
    2. Set the **Table** field to **Inventory value**.
    3. Set the **Derived table** field to **Inventory value**.
    4. Set the **Field** field to the field that you want to filter by. Usually, you will use the **Execution name** field and/or the **Execution time** field.
    5. Set the **Criteria** field to the value that you want to look for in the selected field. (If you selected the **Execution name** field in the previous step, this value will be the name of the report. If you selected the **Execution time** field, it will be the time when the report was generated.)
    6. Add more rows to the **Range** tab as you require, until you've uniquely identified the report that you're looking for.

1. Select **OK** to save your settings and close the dialog box.
1. Select **Save** to save your export setup.
1. On the **Export options** tab, select **Export now** to generate the export file.
1. On the **Execution summary** page that appears, you can view the status of your export job and a list of the entities that were exported. In the **Entity processing status** section, select the **Inventory value** entity in the list, and then select **Download file** to download the data that was exported from that entity.

For more information about how to use data management to export data, see [Data import and export jobs overview](../../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md).
