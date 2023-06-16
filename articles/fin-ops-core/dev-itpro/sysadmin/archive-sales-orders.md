---
title: Archive sales orders
description: This article describes how to archive sales orders. In this way, you help improve database performance but also keep the records available for historical reporting, auditing, machine learning, legal claims, and other purposes.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: ArchiveWorkspace, ProcessScheduleSeriesWizard, SalesOrderArchiveProcessAutomationCriteriaForm, SalesOrderArchiveForm
ms.topic: how-to
ms.date: 06/13/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Archive sales orders

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.34 GA -->

Over time, your company will probably generate and store a large volume of sales orders and sales order lines. Although these records aren't required for day-to-day operations, they might still be required for historical reporting, auditing, machine learning, and other purposes. However, a large volume of historical sales orders and sales order lines in your day-to-day working environment not only increases storage costs but also affects system performance and usability.

To address these issues, you can use the archive solution for finance and operations apps to implement rule-based archiving of historical sales orders and sales order lines. During archiving, the system first moves records from the sales order headers database table (`SalesTable`) and the related sales order lines table (`SalesLine`) to the `SalesTableHistory` and `SalesLineHistory` tables, respectively. Administrators and other users can then view and validate the archived sales order records.

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.34 or later.
- The data archive micro-service must be installed on your system from Microsoft Dynamics Lifecycle Services. For more information, see [Install the Archive add-in from Lifecycle Services](archive-setup.md#install-addin).
- The following features must be turned on in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). For more information, see [Enable the features that you need](archive-setup.md#enable-features).

    - *(Preview) Archive*
    - *(Preview) Archive sales orders to history tables*
    - *(Preview) Archive sales orders to history tables using archive service*

## <a name="archival-requirements"></a>Which sales orders can be archived and when

Sales orders can be archived if all the following conditions are met:

- The sales orders that you want to archive are fully invoiced.
- Sales invoices that are related to the sales orders are at least one year old.
- The ledger period that includes a related sales invoice is either *closed* or *on hold*.
- Inventory has been closed for the period that includes a related sales invoice.

## Schedule archiving of sales orders

To schedule archiving of sales orders, follow these steps.

1. Go to **System administration \> Workspaces \> Archive**.
1. In the **Archive** workspace, on the Action Pane, select **Archive**.
1. In the drop-down dialog box that appears, set the following fields:

    - **Name** – Select *SalesOrderArchiveAutomation*.
    - **Company** – Select the legal entity (company) that you want to archive sales orders for.

1. Select **Archive** to apply your settings and close the drop-down dialog box.
1. On the **Create new process automation** page, on the **General** tab, you must set the **Name** field to define the name of the archive and the **Schedule time** field to define when the archive job should start to run. You can also specify how often the archive job should run. If you decide to set up multiple occurrences, you can set the **End time** field to limit the amount of time that an archive job runs during a day. Any archive job doesn't finish running within that time limit is paused and picked up during the next occurrence. You can also set up alerts as required.
1. Select **Next** to continue.
1. On the **Sales order archive automation** tab, set the following fields:

    - **Archive from date** – Enter the date of the oldest sales orders that you want to move to the history tables.
    - **Archive to date** – Enter the date of the newest sales orders that you want to move to the history tables.

    > [!NOTE]
    > Only dates that meet the [archival requirements](#archival-requirements) are available for selection.

1. Select **Finish**.

## Review sales orders in the history tables

The **Archive** workspace shows your full archiving history. Each row in the grid shows information such as the date when the archive was created, the user who created it, and its status. Follow these steps to view details about a selected archive.

1. Go to **System administration \> Workspaces \> Archive**.
1. In the **Archive** workspace, on the **Sales order archive** tab, the grid lists your sales order archives. To view details about the sales orders that are included in an archive, select the archive, and then select **Archived sales order details** on the toolbar.
1. The **Archived sales orders** page that appears lists every sales order that's included in the archive. To view an order, including its header and all its order lines, select it in the grid, and then, on the Action Pane, select **Archived sales order details**. From the order details, you can view more related information about the order. On the Action Pane, select **Inquiry**, and then, on the menu, select the type of records that you want to inspect (**Sent sales quotations**, **Sales order confirmations**, **Picking list**, **Packing slip** or **Invoice journal**).
