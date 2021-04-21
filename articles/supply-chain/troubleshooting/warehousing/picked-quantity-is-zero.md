---
title: Can't confirm a shipment because there is zero quantity
description: Can't confirm a shipment because there is zero quantity
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

# Can't confirm a shipment because there is zero quantity

Error code: LoadLineWarningUpdatedToZero

## Symptoms

When you are trying to confirm a shipment, the system displays the following error message:

> Load line for item %1 and shipment %2 has been updated to have zero quantity due to underdelivery setup allowing not to ship any quantities for this item.

## Cause

The load or shipment can't be confirmed in current state.

The system evaluates whether the picked quantity is within delivery percentage limit based on the picked quantity, load line quantity, and underdelivery percentage. It the system finds that the picked load line quantity is zero, then you will not be allowed to confirm the shipment. For example, this error may appear if work has been cancelled and the underdelivery percentage is 100% on the load line.

## Resolution

Check your load lines to make sure the underdelivery percentage and quantities are in alignment with the picked work.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed.
1. On the **Load lines** FastTab, select the load line for the item that exceeds the underdelivery.
1. Adjust the **Underdelivery** field percentage or **Quantity** field value as required.

> [!TIP]
> If the issue remains unresolved, you may need to complete more picking work for the related sales or transfer orders until the available quantity is alignment with the load or shipment.
