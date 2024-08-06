---
title: Manually handle sales and transfer line picking exceptions
description: Learn how administrators can manually pick (or unpick) inventory transactions to fix issues that are caused by corrupted sales and transfer order data.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 08/19/2022
ms.reviewer: kamaybac
ms.search.form: WHSManualSalesLinePicking, WHSManualInventTransferLinePicking, InventTransPick, WHSLoadLineManualCorrection, WHSTroubleshootingSelfService
---

# Manually handle sales and transfer line picking exceptions

[!include [banner](../includes/banner.md)]

Manual handling of sales and transfer line picking exceptions enables administrators to fix issues that are caused by corrupted sales and transfer order data. It lets trusted users manually pick (or unpick) inventory transactions that are related to sales and transfer order lines while warehouse processes are already in progress.

The functionality that is described here should be used only in cases where the system can't finish processing the warehouse processes stack in the usual way. By default, only users who have a system admin role are allowed to use it. However, you can grant access to it by assigning the *Pick sales lines manually* privilege to other roles as you require.

## Turn on this feature for your system

Before you can use the features described in this article, they must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the features and turn them on. In the **Feature management** workspace, the features are listed by using the following names:

- *Manual sales line picking service for admin or similar trusted users*<br>(As of Supply Chain Management version 10.0.25, this feature is mandatory and can't be turned off.)
- *Manual transfer line picking service for admin or similar trusted users*

## Correct transactions related to sales or transfer order lines

Use the following procedure to correct transactions that are related to sales or transfer order lines.

1. Follow one of these steps, depending on the type of order that you must correct:

    - To correct a transaction that is related to a sales order, go to **Warehouse management \> Periodic tasks \> Clean up \> Pick sales line manually**.
    - To correct a transaction that is related to a transfer order, go to **Warehouse management \> Periodic tasks \> Clean up \> Pick transfer lines manually**.

1. On the **Pick sales lines manually** or **Pick transfer lines manually** page, use the filters at the top of the grid to find the line that you're looking for, and then select the target order line in the upper grid.
1. Use the **Inventory transactions**, **Load lines**, **Work lines** and **Container lines** tabs in the lower section to view more information about the selected line. The information on these tabs gives a basic overview of the related warehouse processes and their statuses.
1. On the Action Pane, select **Pick** to open the selected order line on the **Pick** page for inventory transactions. You can complete this step even for order lines that have already been released to the warehouse. (Usually, order lines that have been released to the warehouse can't be opened on the **Pick** page.)

    > [!NOTE]
    > You might receive various warnings when you open the **Pick** page. Take any action that these warnings recommend. For example, you might receive a warning about order lines that are linked to warehouse work. In this case, it makes sense to try to cancel the work by using the standard [cancel work](cancel-warehouse-work.md) functionality before you do manually correction.

1. Select the line in the **Transactions** grid, and then select **Add picking line** on the **Transactions** toolbar.
1. The selected line is moved to the **Picking lines** grid. Set appropriate values for any columns that are missing required information. (For example, specify the location and license plate that the item should be picked/un-picked from.)
1. Select **Confirm pick all** on the **Picking lines** toolbar.

## Correct load line quantities

Use the following procedure to correct a load line quantity.

1. Follow one of these steps, depending on the type of order that you must correct:

    - To correct a transaction that is related to a sales order, go to **Warehouse management \> Periodic tasks \> Clean up \> Pick sales line manually**.
    - To correct a transaction that is related to a transfer order, go to **Warehouse management \> Periodic tasks \> Clean up \> Pick transfer lines manually**.

1. On the **Pick sales lines manually** or **Pick transfer lines manually** page, use the filters at the top of the grid to find the line that you're looking for, and then select the target order line in the upper grid.
1. On the **Load lines** tab in the lower section, select **Correct load lines manually** on the toolbar.
1. On the **Correct load lines manually** page, in the **Inventory transactions** grid, review the inventory transactions that are related to the selected load line.
1. In the upper grid, correct the load line quantities in the following columns as required:

    - **Work created quantity**
    - **Picked quantity**
    - **Planned cross docking quantity**

    The system will validate any changes that you make to these columns.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
