---
title: Manually handle sales and transfer line picking exceptions
description: This article describes how administrators can manually pick (or unpick) inventory transactions to fix issues arising from the corruption of sales and transfer order data.
author: perlynne
ms.date: 08/19/2022
ms.topic: article
ms.search.form: WHSManualSalesLinePicking, WHSManualInventTransferLinePicking, InventTransPick, WHSLoadLineManualCorrection, WHSTroubleshootingSelfService
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29
---

# Manually handle sales and transfer line picking exceptions

[!include [banner](../includes/banner.md)]

Manual sales and transfer line picking exception handling enables administrators to fix issues arising from the corruption of sales and transfer order data. It allows trusted users to manually pick (or unpick) inventory transactions related to sales and transfer order lines while warehouse processes are already in progress.

The functionality described here should only be used in cases where the system couldn't finish processing the warehouse processes stack as usual. By default, only users with a system admin role are allowed to use it (but you can grant access to it by assigning the *Pick sales lines manually* privilege to other roles, as needed).

## Turn on this feature for your system

Before you can use the features described in this article, they must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the features and turn them on. In the **Feature management** workspace, the features listed using the following names:

- *Manual sales line picking service for admin or similar trusted users*<br>(As of Supply Chain Management version 10.0.25, this feature is mandatory and can't be turned off.)
- *Manual transfer line picking service for admin or similar trusted users*

## Correct transactions related to sales or transfer order lines

Use the following procedure to correct transactions related to sales or transfer order lines:

1. Depending on which type of order you need to correct, do one of the following steps:
    - To correct a transaction related to a sales order, go to **Warehouse management > Periodic tasks > Clean up > Pick sales line manually**.
    - To correct a transaction related to a transfer order, go to **Warehouse management > Periodic tasks > Clean up > Pick transfer lines manually**.

1. The **Pick sales lines manually** or **Pick transfer lines manually** page opens. Use the filters provided at the top of the grid to find the line you're looking for and then select the target order line in the top grid.
1. Use the **Inventory transactions**, **Load lines**, **Work lines** and **Container lines** tabs in the bottom section to see more information about the selected line. The information on these tabs gives a basic overview of the related warehouse processes and their statuses.
1. Select **Pick** on the Action Pane to open the selected order line on the inventory transactions **Pick** page. You'll even be able to do this action for order lines that have already been release to warehouse (which normally isn't possible).
    > [!NOTE]
    > Various warnings may appear when opening the **Pick** page. Please take any recommended actions. For example, you may typically see a notice regarding order lines being linked to warehouse work. Here it makes sense to try canceling the work by using the standard [cancel work](cancel-warehouse-work.md) functionality before manually correcting.

1. Select the line in the **Transactions** grid and then select **Add picking line** from the **Transactions** toolbar.
1. The line moves to the **Picking lines** grid. Fill in appropriate values for any columns that are missing required information (such as the location and license plate the item should be picked/un-picked from).
1. Select **Confirm pick all** from the **Picking lines** toolbar.

## Correct load line quantities

Use the following procedure to correct a load line quantity:

1. Depending on which type of order you need to correct, do one of the following steps:
    - To correct a transaction related to a sales order, go to **Warehouse management > Periodic tasks > Clean up > Pick sales line manually**.
    - To correct a transaction related to a transfer order, go to **Warehouse management > Periodic tasks > Clean up > Pick transfer lines manually**.

1. The **Pick sales lines manually** or **Pick transfer lines manually** page opens. Use the filters provided at the top of the grid to find the line you're looking for and then select the target order line in the top grid.
1. Open the **Load lines** tab in the bottom section.
1. Select **Correct load lines manually** from the **Load lines** tab toolbar.
1. The **Correct load lines manually** page opens. Check the **Inventory transactions** grid to see the inventory transactions related to your selected load line.
1. Correct the following load line quantities in the top grid as needed:
    - **Work created quantity**
    - **Picked quantity**
    - **Planned cross docking quantity**

    The system will validate any changes you make to these columns.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
