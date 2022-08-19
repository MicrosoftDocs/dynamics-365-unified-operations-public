---
title: Manual sales/transfer line picking service for admin or similar trusted users
description: This article describes how to use the "Manual sales line picking service for admin or similar trusted users" and "Manual transfer line picking service for admin or similar trusted users" features
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

# Manual sales and transfer line picking exception handling for admin or similar trusted users

[!include [banner](../includes/banner.md)]

## Feature introduction

This capability allows administrators to fix issues arising from the corruption of sales and transfer order data, by allowing manual picking (or unpick) of inventory transactions related to sales and transfer order 
lines while warehouse processes are already in progress.

The functionality should only be used in cases where the system couldn't finish processing the warehouse processes stack as usual. By default, only users with a system admin role are allowed to use it (but you can 
grant access to it by assigning the Pick sales lines manually privilege to other roles, as needed).

## Turn on the capability

Before you can use the functionality that is described in this article, you must complete the following procedure to turn on the required features.

1. Go to **System administration \> Workspaces \> Feature management**. (For more information about how to use the **Feature management** workspace, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).)
1. Turn on the feature that is listed in the following way:
    - **Module:** *Warehouse management*
    - **Feature name:** *Manual sales line picking service for admin or similar trusted users*

 1. Turn on the feature that is listed in the following way:
    - **Module:** *Warehouse management*
    - **Feature name:** *Manual transfer line picking service for admin or similar trusted users*

## How to use the capability

### Correction of transactions related to sales order lines
1. Go to **Warehouse management > Periodic tasks > Clean up > Pick sales line manually**
1. The **Pick sales lines manually** page opens. Use the filters provided at the top of the grid to find the line you are looking for. The following filters are provided:
   - Sales order
   - Load ID
   - Shipment ID

1. Select the target order line and use the tabs below the lines grid to see more information about the selected line. Here, you can inspect all of the *Inventory transactions*, *Load lines*, *Work lines* and *Container lines* for the selected order line, which gives a basic overview of its related warehouse processes (and their statuses).
1. Select the **Pick** button on the Action Pane to open the selected order line on the inventory transactions **Pick** page. You will even be able to do this for order lines that have already been release to warehouse (which normally isn't possible).
1. The **Pick** page opens, showing your selected order line. Select the line in the *Transactions* grid and then select **Add picking line** from the *Transactions* toolbar.
1. The line moves to the *Picking lines* grid. Fill in appropriate values for any columns that are missing required information (such as from which location and license plate the item should be picked/un-picked).
1. Select **Confirm pick all** from the Picking lines toolbar

### Correction of transactions related to transfer order lines
1. Go to **Warehouse management > Periodic tasks > Clean up > Pick transfer lines manually**
1. The **Pick transfer lines manually** page opens. Use the filters provided at the top of the grid to find the line you are looking for. The following filters are provided:
   - Transfer number
   - Load ID
   - Shipment ID

1. Select the target order line and use the tabs below the lines grid to see more information about the selected line. Here, you can inspect all of the *Inventory transactions*, *Load lines*, *Work lines* and *Container lines* for the selected order line, which gives a basic overview of its related warehouse processes (and their statuses).
1. Select the **Pick** button on the Action Pane to open the selected order line on the inventory transactions **Pick** page. You will even be able to do this for order lines that have already been release to warehouse (which normally isn't possible).
1. The **Pick** page opens, showing your selected order line. Select the line in the *Transactions* grid and then select **Add picking line** from the *Transactions* toolbar.
1. The line moves to the *Picking lines* grid. Fill in appropriate values for any columns that are missing required information (such as from which location and license plate the item should be picked/un-picked).
1. Select **Confirm pick all** from the Picking lines toolbar

> [!NOTE]
> Different warnings will appear when opening the *Pick* page. Please take the action to follow the recommendation. A typical example being order lines linked to warehouse work. Here it makes sense to try canceling the work by using the [**Cancel work**](cancel-warehouse-work.md) before manually correcting.

### Correction of load line quantities
You can from either the **Pick sales lines manually** or **Pick transfer lines manually** pages select a load line in the bottom grid **Load lines** section and select tne **Correct load lines manually** button.

This will open the **Correct load lines manually** page from where it is possible to correct the following load line quantities:
   - Work created quantity
   - Picked quantity
   - Planned cross docking quantity

You will be able to view the related inventory transactions in the bottom grid and validation will get run when updating the quantities.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
