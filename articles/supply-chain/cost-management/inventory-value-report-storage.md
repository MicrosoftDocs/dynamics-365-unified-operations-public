---
# required metadata

title: Inventory value storage report
description: This feature provides you the ability to execute the Inventory value storage report and make the output available digitally, either as an interactive page in Dynamics 365 Supply Chain Management, or as an exported document in any of several formats.
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

This topic explains how to run a **Inventory value storage** report and make the output available digitally, either as an interactive page in Dynamics 365 Supply Chain Management, or as an exported document in any of several formats.

When you view the report in your browser, columns and aggregate balances are dynamically adjusted, depending on your configured layout. You can sort the results, filter them, drill down into the data, and more.

Report results are stored in the **Inventory value** data entity, which lets you filter and export the results to a format such as CSV or Microsoft Excel.

The **Inventory value storage** report is helpful in cases where the output contains many lines. For example, the output will contain many lines if you request inventory ending balance by item, site and warehouse when you have 50,000 items and 300 stores created as warehouses.

> [!NOTE]
> The report won't include subtotals defined in the report layout. General ledger balances won't be included in the output even when defined in the report layout. Reconciliation to general ledger must be done using trial balance.

## Enable Inventory value storage report

Before you can use this feature, you must enable it on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - Cost management
- **Feature name** - Inventory value storage

## Generate an Inventory value storage report

Follow these steps to generate and store an **Inventory value storage** report:

1. Go to **Cost management > Inquiries and reports > Inventory value report storage**.

1. Select **New** to open the **Inventory value** pane. Set the following options to define which records to include in your report:

    - On the **Parameters** FastTab, give the report a unique **Name** and use the fields in the **Date interval** section to define which records to include. You can define the date either by selecting a preset range (relative to the report-generation date) from the **Date interval** code drop-down list or by selecting specific dates in the **From date** and **To date** fields. <!-- KFM: What is the ID setting for here? What do its values mean? -->
    - On the **Records to include** FastTab, set up filters and constraints to define which data to include in the report.
    - On the **Run in the background** FastTab, set up how, when, and the frequency at which you want to generate the report.
    > [!NOTE]
    > This report is always executed as part of a batch job.

1. Select **OK** to apply your settings and close the pane.

1. After the batch job is completed, it will be listed on the **Inventory value report storage** page. You may need to refresh the page to see the report.

## Explore an Inventory value storage report

After you've generated a report, you can view and explore it at any time as follows:

1. Go to **Cost management > Inquiries and reports  > Inventory value report storage**.

1. Select a report from the list.

1. Select **View details** to see the report content.

1. Explore the report by doing the following:

    - Select almost any column heading to sort or filter the table by values in that column, just as with most standard forms in Supply Chain Management.
    - Use the **Filter** field to filter the report by any value in any of several available columns.
    - Use the view menu (above the **Filter** field) to save and load your favorite combinations of sort and filter options.

## Export an Inventory value storage report

Each report that you generate is stored in the **Inventory value** data entity. You can use the standard data management features of Supply Chain Management to export data from this entity to any supported data format, including CSV or Microsoft Excel.

The following is an example of how to export a **Inventory value report** report:

1. Go to **System administration > Workspaces > Data management**.

1. Select the **Export** button in the **Data management** section.

1. The **Export** page opens, which you'll use to set up your export job. Start by giving your job a **Group name**.

1. In the **Selected entities** section, select **Add entity** to open a dialog box where you can set the following options:

    - **Entity name** - Select **Inventory value**.
    - **Target data format** - Choose the format that you want to export to.

1. Select **Add** to add the new row and then select **Close** to close the dialog box.

1. Usually you'll export one report at a time. To do this, set up a **Filter** for the row you just added to the **Inquiry** pane. This will let you define which reports from the **Inventory value** entity that you want to include in your export. Set the following filter options to export a single report:

    - On the **Range** tab, select **Add** to add a new row.
    - Set **Table** to **Inventory value**.
    - Set **Derived table** to **Inventory value**.
    - Set **Field** to the field that you want to filter by. Usually you'll use **Execution name** and/or **Execution time**.
    - Set **Criteria** to the value from your selected field that you want to look for (either the name of the report or the time the report was generated).
    - If necessary, add more rows to the **Range** table until you have uniquely identified the report that you're looking for.

1. Select **OK** to save your settings and close.

1. Select **Save** to save your export setup.

1. Open the **Export options** tab and select **Export now** to generate the export file.

1. The **Execution summary** page opens, where you can see the status of your export job and a list of entities that were exported. Select the **Inventory value** entity listed in the **Entity processing status** area and then select **Download file** to download the data exported from that entity.

For more information about how to use data management to export data, see [Data import and export jobs overview](../../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md).