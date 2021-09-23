---
title: You can't confirm a shipment because there is zero quantity
description: You can't confirm a shipment because there is zero quantity
author: perlynne
ms.date: 04/21/2021
ms.topic: troubleshooting
ms.search.form: WHSLoadTable_WHSShipConfirm,WHSLoadPlanningListPage_WHSShipConfirm,WHSLoadPlanningWorkbench_WHSShipConfirm,WHSTransportLoad_WHSShipConfirm,WHSShipPlanningListPage_WHSShipConfirm,WHSShipmentDetails_WHSShipConfirm,WHSWorkTable_WHSShipConfirm,WHSWorkTableListPage_WHSShipConfirm,Dialog_WHSOutboundShipConfirmController_WHSOutboundShipConfirm
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: lbc
ms.search.validFrom: 2021-04-21
ms.dyn365.ops.version: 10.0.18
---

# You can't confirm a shipment because there is zero quantity

Error code: LoadLineWarningUpdatedToZero

## Symptoms

When you try to confirm a shipment, the system shows the following error message:

> Load line for item %1 and shipment %2 has been updated to have zero quantity due to underdelivery setup allowing not to ship any quantities for this item.

Therefore, you can't confirm the shipment for the load.

## Cause

The system evaluates whether the picked quantity is within the expected limits, based on the picked quantity, load line quantity, and underdelivery percentage. If the system finds that the picked quantity on the load line is 0 (zero), you can't confirm the shipment. For example, this issue might occur if work has been canceled, and the underdelivery percentage on the load line is 100 percent.

## Resolution

Check your load lines to make sure that the underdelivery percentage and quantities are aligned with the picked work.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the shipment can't be confirmed for.
1. On the **Load lines** FastTab, select the load line for the item that exceeds the underdelivery percentage.
1. Adjust the value of the **Underdelivery** field or the **Quantity** field as required.

> [!TIP]
> If the issue still isn't fixed, you might have to complete more picking work for the related sales orders or transfer orders until the available quantity is aligned with the load or shipment.
