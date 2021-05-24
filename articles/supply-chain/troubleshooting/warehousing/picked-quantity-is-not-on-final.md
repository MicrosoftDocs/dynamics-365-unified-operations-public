---
title: You can't confirm a shipment because items haven't been picked
description: You can't confirm a shipment because items haven't been picked
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

# You can't confirm a shipment because items haven't been picked

Error code: LoadNotPickedAndMovedToFinalShippingLocation

## Symptoms

When you try to confirm a shipment, the system shows the following error message:

> Some of the items that are needed for load %1 have not yet been picked and moved to the final shipping location.

Therefore, you can't confirm the shipment for the load.

## Cause

The load or shipment can't be confirmed in its current state because one of the following conditions might exist:

- The related work hasn't yet been picked and moved to the final shipping location.
- The picked work quantity doesn't match the created work quantity on the load line.

## Resolution

Check the related sales orders or transfer orders for the load or shipment. Make sure that all the related work has been completed at the final shipping location, and that the quantities match.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the shipment can't be confirmed for.
1. On the **Load lines** FastTab, select the load line.
1. Make a note of the value of the **Work created quantity** field.
1. On the Action Pane, on the **Loads** tab, in the **Related information** group, select **Work**.
1. Verify that the work has been completed at the final shipping location, and that the picked work quantity matches the created work quantity on the load line.
1. Repeat this procedure for all load lines to make sure that all criteria are met.
