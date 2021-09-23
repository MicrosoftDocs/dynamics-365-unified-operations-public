---
title: You can't confirm a shipment because load lines have zero quantity
description: You can't confirm a shipment because load lines have zero quantity.
author: GalynaFedorova
ms.date: 07/30/2021
ms.topic: troubleshooting
ms.search.form: WHSLoadTable_WHSShipConfirm,WHSLoadPlanningListPage_WHSShipConfirm,WHSLoadPlanningWorkbench_WHSShipConfirm,WHSTransportLoad_WHSShipConfirm,WHSShipPlanningListPage_WHSShipConfirm,WHSShipmentDetails_WHSShipConfirm,WHSWorkTable_WHSShipConfirm,WHSWorkTableListPage_WHSShipConfirm,Dialog_WHSOutboundShipConfirmController_WHSOutboundShipConfirm
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-gfedorova
ms.search.validFrom: 2021-07-30
ms.dyn365.ops.version: 10.0.21
---

# You can't confirm a shipment because load lines have zero quantity

Error code: WAX:LoadTableWarningAllLinesZero, WAX2543

## Symptoms

When you try to confirm a shipment, the system shows the following error message:

> All the lines in load %1 have quantity zero.  
> The shipment for load %1 could not be confirmed.

Therefore, you can't confirm the shipment for the load.

## Cause

The system evaluates whether the load line can be ship confirmed, based on the work IDs that are created, the load line quantity, and the underdelivery percentage. If the system finds that there are no work IDs, and if underdelivery percentage is set to 100 percent, you can't confirm the shipment.

For example, this issue might occur if the work has been canceled, and the underdelivery percentage on the load line is 100 percent.

## Resolution

The load or shipment is currently in a state where shipment confirmation fails. To fix this issue, complete one of the following tasks:

- Review your load lines to make sure that all the related work has been completed at the final shipping location, and that the quantities match.
- Review your load lines to make sure that the underdelivery percentage and quantities are aligned with the picked work.

### Review your load lines to make sure that all the related work has been completed at the final shipping location, and that the quantities match

Use the following procedure to review your load lines to make sure that all the related work has been completed at the final shipping location, and that the quantities match.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Open the load that the shipment can't be confirmed for.
1. On the **Load lines** FastTab, select the load line.
1. Make a note of the value of the **Work created quantity** field.
1. On the Action Pane, on the **Loads** tab, in the **Related information** group, select **Work**.
1. Verify that the work has been completed at the final shipping location, and that the picked work quantity matches the created work quantity on the load line.
1. If you find a mismatch, cancel the relevant work, reconfigure the location directive, and re-release the load. For instructions, see [You can't confirm a shipment because items haven't been picked](picked-quantity-is-not-on-final.md).
1. Repeat this procedure for all load lines to make sure that all criteria are met.

### Review your load lines to make sure that the underdelivery percentage and quantities are aligned with the picked work

Use the following procedure to review your load lines to make sure that the underdelivery percentage and quantities are aligned with the picked work.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Open the load that the shipment can't be confirmed for.
1. On the **Load lines** FastTab, select the load line for the item that exceeds the underdelivery percentage.
1. Adjust the value of the **Underdelivery** field or the **Quantity** field as required.

> [!TIP]
> If the issue still isn't fixed, you might have to complete more picking work for the related sales orders or transfer orders until the available quantity is aligned with the load or shipment.
