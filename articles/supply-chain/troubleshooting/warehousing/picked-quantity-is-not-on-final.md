---
title: Can't confirm shipment because items haven't been picked
description: Can't confirm shipment because items haven't been picked
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

# Can't confirm a shipment because items haven't been picked

Error code: LoadNotPickedAndMovedToFinalShippingLocation

## Symptoms

When you are trying to confirm a shipment, the system displays the following error message:

> Some of the items that are needed for load %1 have not yet been picked and moved to the final shipping location.

## Cause

The load or shipment can't be confirmed in its current state because one of the following may be true:

- The related work has not yet been picked and moved to the final shipping location.
- The picked work quantity doesn't match the created work quantity on the load line.

## Resolution

Check the related sales or transfer orders for the load or shipment and make sure all of the related work is completed on final shipping location, and that the quantities match.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed.
1. On the **Load lines** FastTab, select the load line.
1. Note the **Work created quantity**.
1. On the Action Pane, open the **Loads** tab and, from the **Related information** group, select **Work**.
1. Validate that the work is completed on final shipping location and the picked **Work quantity** is matching the load line **Work created quantity**
1. Repeat this procedure for all load lines to ensure criteria is met.
