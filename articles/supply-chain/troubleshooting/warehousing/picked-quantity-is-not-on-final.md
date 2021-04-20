---
title: Picked quantity is not on final shipping location throughout shipment confirmation.
description: Picked quantity is not on final shipping location throughout shipment confirmation.
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
<!-- KFM: Does this describe the issue the customer wants to solve? -->
# Picked quantity is not on final shipping location throughout shipment confirmation

Error code: LoadNotPickedAndMovedToFinalShippingLocation

## Symptoms

The system displays the following error message:

> Some of the items that are needed for load %1 have not yet been picked and moved to the final shipping location.

The load or shipment can't be ship confirmed in current state. <!-- KFM: What is "ship confirmed"? Confirmed as shipped? Confirmed for shipment? -->

The related work have not yet been picked and moved to the final shipping location. Picked work quantity do no match the created work quantity on the load line.  <!-- KFM: Is this a symptom or a cause? -->

## Resolution

Load or shipment is currently in a state where shipment confirmation fails. Navigate to related orders for the load / shipment ensuring the work is completed on final shipping location and quantities matches.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed.
1. On the **Load lines** FastTab, select the load line.
1. Note the **Work created quantity**.
1. On the Action Pane, open the **Loads** tab and, from the **Related information** group, select **Work**.

    - Validate that the work is completed on final shipping location and the picked **Work quantity** is matching the load line **Work created quantity**
    - Go through above steps for all load lines to ensure criteria is meet.