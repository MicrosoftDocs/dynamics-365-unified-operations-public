---
title: Can't update a load line because the released quantity would be negative
description: This issue occurs when updating or deleting a load line would result in a negative released quantity. 
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

# Can't update a load line because the released quantity would be negative

Error code: @WAX:ReleasedQtyCannotBeNegative

## Symptoms

This issue occurs when updating or deleting a load line would result in a negative released quantity. In this case, when you try to update or delete the load line, the system shows the following error message:

> Released quantity cannot be negative for item %1, lot %2.

Therefore, you can't update or delete the load line.

## Cause

After you update or delete a load line, the system updates the released quantity of the related sales line (*whsSalesLine.ReleaseQty*). The system evaluates the released quantity and, if it finds that released quantity of the line after the update would be a negative, it won't let you update or delete the line. This validation occurs whenever you try to update either the load line quantity or the unit of measure through various actions such as deleting a load line deletion, deleting a shipment, changing the quantity of a load line, reducing picked quantity, short picking, and so on.

The most common root cause of this issue is a change in the unit conversion being used for open load lines. For example, the unit conversion when a sales order was released was *50 Ea = 1 PL*, but the unit conversion was then changed to *100 Ea = 1 PL* before the related load shipment was finalized.

## Resolution

The solution is to revert the unit conversion changes, update or delete the load line, and then re-implement the conversion. You must prevent other loads with the item that caused the issue from being processed until the issue is fixed because the new conversions might be used for other loads that are already open.

To fix this issue, complete the following tasks:

- Check the unit conversion that was used for the load line.
- Check the current unit conversion for the item and make adjustments that will enable the load line to be updated or deleted.
- Update or delete the load line and revert the unit conversion adjustments.

### Check the unit conversion that was used for the load line

Use the following procedure to review your load lines and make a note of the unit conversion that was used for the load line.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that includes the load line that can't be deleted or updated.
1. On the Action Pane, on the **Loads** tab, in the **Related information** group, select **Work**.
1. Calculate the conversion rate between **Inventory quantity** and **Quantity**. Make a note of the rate. <!-- KFM: Where are these fields? -->
1. Repeat this procedure for all relevant work IDs to make sure that the same conversion was used.

### Check the current unit conversion for the item and make adjustments

Use the following procedure to review your product's unit conversion and make adjustments to ensure that the unit conversion is aligned with the load line.

1. Go to **Product information management \> Products \> Released products**.
1. Open the relevant product to go to its **Released product details** page.
1. On the Action Pane, on the **Product** tab, in the **Related information** group, select **Unit conversions**. <!-- KFM: I don't see this group or button here. -->
1. Select the conversion between the units and make adjustments using conversion you found in the previous step.

### Update or delete the load line and revert the unit conversion adjustments

Use the following procedure to process the load line as required and revert the unit conversions.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Open the load that includes the load line that can't be deleted or updated.
1. On the **Load lines** FastTab, select the load line.
1. Continue with the required actions as needed (such as deleting the load line or changing its quantity).
1. Go to **Product information management \> Products \> Released products**.
1. Open the relevant product to go to its **Released product details** page.
1. On the Action Pane, on the **Product** tab, in the **Related information** group, select **Unit conversions**. <!-- KFM: I don't see this group or button here. -->
1. Select the conversion between the units and revert the adjustments you made in the previous section.