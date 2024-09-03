---
title: Inventory aging report storage
description: Learn about the functionality that lets you run an Inventory aging report and make the output available as a form and a chart.
author: JennySong-SH
ms.author: yanansong
ms.topic: how-to
ms.date: 09/03/2024
ms.custom:
  - bap-template
ms.reviewer: kamaybac
ms.search.form: InventAgingStorage, InventAgingStorageChart, InventAgingStorageDetails
---

# Inventory aging report storage

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 Supply Chain Management, you can run an *inventory aging report storage* report and make the output available as a form and a chart. In the form, columns and aggregate balances are dynamically adjusted, depending on the layout that is configured. The chart provides a visual overview that supports filtering and lets you drill down into details. Additionally, a data entity that is named *Inventory aging report* lets you export the results of an *inventory aging report storage* report run to a format such as a Microsoft Excel file or a PDF file.

This method of running an inventory aging report is helpful in cases where the output contains many lines. For example, the output will contain many lines if you have 50,000 items and 300 stores that are created as warehouses, and you request inventory aging by item, site, and warehouse.

## Set up and generate reports

To set up and generate *inventory aging report storage* reports, follow these steps.

1. Go to **Cost management \> Inquiries and reports \> Inventory aging report storage**.
1. Select **New**. The **Inventory aging** dialog opens.
1. On the **Parameters** FastTab, make the following settings:
    - **Name** – Enter a unique name for the report.
    - **As of date** – Select the date to base the values of the report on. Leave blank to use the date on which the report runs, which is useful if you choose to set up a repeating schedule.
    - **View** – Choose which fields to include in your report. Tooltips are provided for each of them, so you can hover your mouse pointer for more information. Select one of the following values for each field:
        - *No* – Don't include the field in the report.
        - *View* – Include the field in the report.
        - *Total* – Display the field as a subtotal (subtotals aren't shown in the online reports).
    - **Unit of aging period** – Choose how you want to define your aging periods. Select one of the following values:
        - *Days* – Specify each period as a number of days previous to the **As of date**.
        - *Dates* – Select a specific calendar date for each period.
        - *Date intervals* – Select from a list of predefined date intervals related to the **As of date**.
    - **Aging periods** – You can specify up to four aging periods using the unit you selected for **Unit of aging period**

1. If you want to limit the records included in your report expand the **Records to include** FastTab and add the filters you require, just as you might do for other batch jobs in Supply Chain Management.
1. On the **Run in the background** FastTab, set up batch, scheduling, and recurrence options as you require, just as you might do for other batch jobs in Supply Chain Management. The report is always run in a batch job.
1. Select **OK** to run and/or schedule the report.
1. After the batch job is completed, the output is shown on the **Inventory aging report storage** page. If you set up a recurring report, then a new report is added to the list each time the report runs.

## View a report

To view an inventory aging report storage, follow these steps.

1. Go to **Cost management \> Inquiries and reports \> Inventory aging report storage**.
1. On the list pane, select the report that you want to view.
1. On the Action Pane, select one of the following actions:
    - **View details** – View the report as a form that has a traditional grid layout.
    - **View chart** – View the report as an aggregated chart.

> [!NOTE]
> The views don't include the subtotals that are defined in the report layout.

## Export a report

Every report that you generate is stored in the *Inventory value report storage* data entity. You can use the standard data management features of Supply Chain Management to export data from this entity to any supported data format, such as CSV or Excel format.

The following example shows how to export an inventory aging report storage report.

1. Go to **System administration \> Workspaces \> Data management**.
1. In the **Import / Export** section, select the **Export** tile.
1. On the **Export** page, enter a **Group name** for the job.
1. On the **Selected entities** FastTab, select **Add entity**.
1. In the **Add entity** drop-down dialog, set the following fields:

    - **Entity name** – Select *Inventory aging report storage*.
    - **Target data format** – Select the format to export data to.

1. Select **Add** to add the new row, and then select **Close** to close the dialog box.
1. Usually, you'll export one report at a time. To export a single report, select the button in the **Filter** column for the row that you just added to **Selected entities** FastTab. Then use the query designer to set up the following filter:
    - **Table** – Select *Inventory aging report storage*.
    - **Field** – Select *Execution name*.
    - **Criteria** – Enter the name of the report that you want to export.

1. On the Action Pane, select **Save**.
1. On the Action Pane, open the **Export options** tab and select **Export now**.
1. The **Execution summary** page opens. Here you can view the status of your export job and a list of the entities that were exported. In the **Entity processing status** section, select the **Inventory value** entity in the list, and then select **Download file** to download the data that was exported from that entity.

For more information about how to use data management to export data, see [Data import and export jobs overview](../../fin-ops-core/fin-ops/data-entities/data-import-export-job.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
