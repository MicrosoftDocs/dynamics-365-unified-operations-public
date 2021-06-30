---
title: Released quantity cannot be negative.
description: Released quantity of the sales line in the inventory unit  is negative after an associated load line is updated or deleted. 
author: GalynaFedorova
ms.date: 6/30/2021
ms.topic: troubleshooting
ms.search.form: WHSLoadPlanningListPage_WHSLoadLineUnShipQty,WHSLoadTable_WHSLoadLineUnShipQty,WHSLoadPlanningWorkbench_WHSLoadLineUnShipQty,WHSShipmentDetails_WHSLoadLineUnShipQty,WHSLoadPlanningListPage_DeleteButtonLoadLine,WHSLoadTable_DeleteButtonLoadLine,WHSLoadPlanningWorkbench_DeleteButtonLoadLine,WHSShipmentDetails_DeleteButtonShipment
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-gfedorova
ms.search.validFrom: 2021-06-30
ms.dyn365.ops.version: 10.0.21
---

# Released quantity cannot be negative.

Error code: @WAX:ReleasedQtyCannotBeNegative

## Symptoms

As part of the load line update/delete, the data supplied to it would have a negative released quantity.

When you try to update/delete the load line, the system shows the following error message:

> Released quantity cannot be negative for item %1, lot %2.

Therefore, you can't update/delete the load line.

## Cause

The system updates the released quantity of the sales line in the inventory unit  (*whsSalesLine.ReleaseQty*) after an associated load line is updated or deleted. The system evaluates the released quantity and if the system finds that released quantity of the line after update would be a negative, you can't update/delete the load line. 
This validation happens whenever you try to update either the load line quantity or unit of measure upon different actions like load line deletion, shipment deletion, load line quantity change, reducing picked quantity, short picking and so on. 

The most common root cause of this issue is that the unit conversion being used in the open load lines was changed.
For example, unit conversion upon sales order release was 50 Ea = 1 PL. Later on, unit conversion was changed to 100 Ea = 1 PL without finalization of the load shipment that existed before the unit conversion change.

## Resolution

The intention is to revert the unit conversion changes, update/delete the load line and put back the conversion.
It's' necessary to hold other loads with the item that cause an issue from being processed until the issue is fixed because the new conversions might be used for other loads that are already open.

To fix this issue, complete the following tasks:
- Check the unit conversion that was used for the load line.
- Check the unit conversion that is set on the item to make adjustments that load line can be updated/deleted.
- Update/delete the load line and revert the unit conversion adjustments.

### Check the unit conversion that was used for the load line.

Use the following procedure to review your load lines and make a note of the unit conversion that was used for the load line.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the load line can't be deleted/updated for.
1. On the Action Pane, on the *Loads* tab, in the **Related information** group, select **Work**.
1. Determine the conversion between **Inventory quantity** and **Quantity**. Make a note of the conversion.
1. Repeat this procedure for all work IDs to make sure that the same conversion was used.

### Check the unit conversion that is set on the item to make adjustments that load line can be updated/deleted.

Use the following procedure to review your products unit conversion and make adjustments to ensure that the unit conversion is aligned with the load line.

1. Go to **Product information management \> Products \> Released products**.
1. Open a product to go to its Product details page.
1. On the Action Pane, on the *Product* tab, in the **Related information** group, select **Unit conversions**.
1. Select the conversion between the units and make adjustments using conversion determined in the previous step.

### Update/delete the load line and revert the unit conversion adjustments.

Use the following procedure to process the load line as required and revert the unit conversions.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the load line can't be deleted/updated for.
1. On the **Load lines** FastTab, select the load line.
1. Continue with the required actions as needed like deleting the load line, changing the load line quantity etc.
1. Go to **Product information management \> Products \> Released products**.
1. Open a product to go to its Product details page.
1. On the Action Pane, on the *Product* tab, in the **Related information** group, select **Unit conversions**.
1. Select the conversion between the units and revert the adjustments from the previous step.