---
title: Archive sales orders
description: This article describes how to archive sales orders to help improve database performance while keeping the records available for historical reporting, auditing, machine learning, legal claims, and other purposes.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 05/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Archive sales orders

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.34 GA -->
<!--KFM: Add form codes to metadata -->

Over time, your company will probably generate and store a large volume of sales orders and sales order lines. Although these records aren't required for day-to-day operations, they may still be needed for purposes such as historical reporting, auditing, machine learning, and so on. Keeping a large volume of historical sales orders and lines in your day-to-day working environment not only results in increased storage costs, but also impacts system performance and usability.

To solve these issues, you can use the archival framework for finance and operations apps to implement rules-based archiving of historical sales orders and order lines. During archiving, the system starts by moving records from the sales orders headers database table (`SalesTable`) and the related sales order lines table (`SalesLine`) to the `SalesTableHistory` and `SalesLineHistory` tables, respectively. Administrators and other users can then view and validate the archived sales order records.

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.34 or later.
- The data archive micro-service must be installed on your system from Lifecycle Services (LCS). See also [Set up record archiving](archive-setup.md).
- The following features must be turned on in [feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). See also [Set up record archiving](archive-setup.md).
    - *(Preview) Archive*
    - *(Preview) Archive sales orders to history tables*
    - *(Preview) Archive sales orders to history tables using archive service*

## <a name="archival-requirements"></a>Which sales orders can be archived and when

Sales orders can be archived when the following conditions are met:

- The sales orders to be archived must be fully invoiced.
- Sales invoices related to the sales orders to be archived must be at least one year old.
- The ledger period that includes the related sales invoice must be closed or on hold.
- Inventory must be closed for the period that includes the related sales invoice.

## Schedule archiving of sales orders

To schedule sales order archiving, follow these steps:

1. Open the **Archive** workspace.
1. On the Action Pane, select **Archive** to open a drop-down dialog box, and then make the following settings:
    - **Name** – Select *Sales order archive automation*.
    - **Company** – Select the legal entity (company) for which you want to archive sales orders.
1. Select **Archive** to apply your settings and close the drop-down dialog box.
1. The **Create new process automation** page opens, open to the **General** tab. Use the settings on this page to establish when the archive job should start running, how often it should run, and when it should stop running (if you set up multiple occurrences). You can also set up alerts as needed. <!-- KFM: Is a name required? Is there a duration setting that we should mention? -->
1. Select **Next** to continue to the **Sales order archive automation** tab. Make the following settings:
    - **Archive from date** – Enter the date of the oldest sales orders that you want to archive.
    - **Archive to date** – Enter the date of the newest sales orders that you want to archive.

    > [!NOTE]
    > Only dates that meet the [archival requirements](#archival-requirements) will be available for selection.

1. Select **Finish**.

## Review archived sales orders

The **Archive** workspace shows your full archiving history. Each row in the grid shows information such as the date when the archive was created, the user who created it, and its status. Follow these steps to view details about a selected archive:

1. Open the **Archive** workspace.
1. Open the **Sales order archive** tab.
1. Your sales order archives are listed in the grid. To view details about the sales orders included in any archive, select an archive and then select **Archived sales order details** on the toolbar.
1. The **Archived sales orders** page opens, showing a list of each sales order included in the archive.
1. To view an order, including its header and all of its order lines, select it in the grid and select **Archived sales order details** on the Action Pane. From the order details, you can view more related information about an order by opening the **Inquiry** menu on the Action Pane and then choose the entry for the type of records you'd like to inspect (**Sent sales quotations**, **Sales order confirmations**, **Picking list**, **Packing slip** or **Invoice journal**).

## Reverse an archive

When you reverse an archive, the system moves records from the selected archive from the history tables back to the live tables. This operation is useful if you need to edit an archived sales order because you cannot edit records in the history tables. To reverse an archive, follow these steps:<!-- KFM: Confirm this procedure -->

1. Open the **Archive** workspace.
1. Open the **Sales order archive** tab.
1. Your existing archives are listed in the grid. Select the archive you want to reverse and then select **Reverse** on the toolbar.
1. The **Reverse** dialog opens. Schedule the reverse job by entering a **Reversal start time** and select **OK**.
1. A message appears asking you to confirm the operation. Select **OK** to confirm. <!-- KFM: Confirm this label -->

<!-- KFM: Check whether more toolbar or Action Pane buttons need documentation (maybe history or log buttons) -->
