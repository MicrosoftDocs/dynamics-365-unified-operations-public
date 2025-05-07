---
title: Export posted trade agreement lines
description: Learn step-by-step instructions on how to export posted trade agreement lines.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: VendTable, CustTable, PriceDiscAdm, DMFExecutionHistoryList, DMFQuickImportExportEnhanced, DataManagementWorkspace
ms.topic: how-to
ms.date: 05/06/2025
ms.custom: 
  - bap-template
---
# Export posted trade agreement lines

This article provides step-by-step instructions on how to export posted trade agreement lines. Standard data entities don't support the direct export of posted trade agreement lines. This article describes how to convert posted trade agreement lines to unposted lines, which makes them exportable.

## Convert posted trade agreement lines

To convert posted trade agreement lines into unposted lines, follow these steps.

1. Open the list of active trade agreement lines for your vendor or customer.

   - For *purchase trade agreements*, go to **Accounts payable** \> **Vendors** \> **All vendors**. Select the vendor you want to work with. On the Action Pane, open the **Procurement** tab and, from the **Agreements** group, select **Trade agreements**.

   - For *sales trade agreements*, go to **Accounts receivable** \> **Customers** \> **All customers**. Select the customers you want to work with. On the Action Pane, open the **Sell** tab and, from the **Trade agreements** group, select **Agreements**.

1. Select the lines you want to convert for eventual export.
1. On the Action Pane, select **Edit selected lines**.
1. In the dialog, set the **Name** field to the name of the journal that you want to assign to your selected lines.
1. Select **OK**. This action converts the active price trade agreement lines into open trade agreement lines, which are now exportable.

## Export the open trade agreement lines

After you've converted the relevant lines to open trade agreements, you'll be able to export them using the standard data management features of Supply Chain Management. You can export data from this entity to any supported data format (such as comma-separated values (CSV) or Microsoft Excel).

1. Go to **System administration** \> **Workspaces** \> **Data management**.
1. In the **Import / Export** section, select the **Export** tile.
1. On the **Export** page, enter a **Group name** for the job.
1. On the **Selected entities** FastTab toolbar, select **Add entity**.
1. In the **Add entity** drop-down dialog, set the following fields:
    - **Entity name** – Select *Open purchase price journal lines V2* or *Open sales price journal lines V2*.
    - **Target data format** – Select the format to export data to.

1. Select **Add** to add the new row, and then select **Close** to close the dialog box.
1. On the Action Pane, select **Save**.
1. On the Action Pane, open the **Export options** tab and select **Export now**.
1. The **Execution summary** page opens. Here you can view the status of your export job and a list of the entities that were exported. In the **Entity processing status** section, select the *Open purchase price journal lines V2* or *Open sales price journal lines V2* entity in the list, and then select **Download file** to download the data that was exported from that entity.

For more information about how to use data management to export data, see [Data import and export jobs overview](../../fin-ops-core/fin-ops/data-entities/data-import-export-job.md).

## Clean up resources

After exporting the data, ensure that any temporary journal entries used for the conversion process are deleted or archived to maintain data integrity and avoid clutter in your system.
