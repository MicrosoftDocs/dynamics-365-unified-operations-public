---
title: Can't update a load line because the released quantity would be negative
description: This issue occurs when updating or deleting a load line would cause a negative released quantity.
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

This issue occurs when updating or deleting a load line would cause a negative released quantity. In this case, when you try to update or delete the load line, the system shows the following error message:

> Released quantity cannot be negative for item %1, lot %2.

Therefore, you can't update or delete the load line.

## Cause

After you update or delete a load line, the system updates the released quantity of the related sales line (*whsSalesLine.ReleaseQty*). The system evaluates the released quantity, and if it finds that the released quantity of the line would be a negative after the update, it won't let you update or delete the line. This validation occurs whenever you try to update either the load line quantity or the unit of measure through various actions, such as deleting a load line, deleting a shipment, changing the quantity of a load line, reducing the picked quantity, and short picking.

The most common root cause of this issue is a change in the unit conversion that is used for open load lines. For example, the unit conversion when a sales order was released was *50 Ea = 1 PL*. However, before the related load shipment was finalized, the unit conversion was changed to *100 Ea = 1 PL*.

## Resolution

The solution is to revert the unit conversion changes, update or delete the load line, and then re-implement the conversion. You must prevent other loads that include the item that caused the issue from being processed until the issue is fixed. Otherwise, the new conversions might be used for other loads that are already open.

To fix this issue, complete the following tasks:

1. Review the unit conversion that was used for the load line.
2. Review the current unit conversion for the item, and make adjustments that will enable the load line to be updated or deleted.
3. Update or delete the load line, and revert the unit conversion adjustments.

### Review the unit conversion that was used for the load line

Use the following procedure to review your load lines and make a note of the unit conversion that was used for the load line.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that includes the load line that can't be deleted or updated.
1. On the Action Pane, on the **Loads** tab, in the **Related information** group, select **Work**.
1. In the upper grid, select the relevant work ID.
1. On the **General** tab at the bottom of the page, calculate the conversion rate between the **Inventory work quantity** value and the **Work quantity** value. Make a note of the rate.
1. Repeat this procedure for all relevant work IDs to make sure that the same conversion was used.

### Review the current unit conversion for the item and make adjustments

Use the following procedure to review your product's unit conversion and make adjustments to ensure that the unit conversion is aligned with the load line.

1. Go to **Product information management \> Products \> Released products**.
1. Open the relevant product to go to its **Released product details** page.
1. On the Action Pane, on the **Product** tab, in the **Set up** group, select **Unit conversions**.
1. Select the conversion between the units, and make adjustments by using the conversion that you found in the previous section.

### Update or delete the load line, and revert the unit conversion adjustments

Use the following procedure to process the load line as required and revert the unit conversions.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Open the load that includes the load line that can't be deleted or updated.
1. On the **Load lines** FastTab, select the load line.
1. Continue with the required actions as needed. (For example, delete the load line, or change its quantity.)
1. Go to **Product information management \> Products \> Released products**.
1. Open the relevant product to go to its **Released product details** page.
1. On the Action Pane, on the **Product** tab, in the **Set up** group, select **Unit conversions**.
1. Select the conversion between the units, and revert the adjustments that you made in the previous section.
