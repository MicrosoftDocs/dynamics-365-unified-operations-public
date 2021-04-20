---
title: Picked quantity is zero throughout shipment confirmation
description: Picked quantity is zero throughout shipment confirmation
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

# Picked quantity is zero throughout shipment confirmation

Error code: LoadLineWarningUpdatedToZero

## Symptoms

The system displays the following error message:

> Load line for item %1 and shipment %2 has been updated to have zero quantity due to underdelivery setup allowing not to ship any quantities for this item.

The load or shipment can't be ship confirmed in current state. <!-- KFM: "ship confirmed"-->

The calculation if picked quantity is within delivery percentage limit is based on picked quantity, load line quantity and the underdelivery percentage. <!-- KFM: I think this sentence contains typos. -->  If the result of the calculation has picked load line quantity zero then it will not be allowed to ship confirm. That can happen, for example, this error may appear if work has been cancelled and the underdelivery percentage is 100% on the load line.

## Resolution

Either the load or the shipment is currently in a state where shipment confirmation fails. Go to the related orders for the load or shipment to make sure the work is completed or cancelled.

There are several forms where we have shipments and loads, so a couple are described here: <!-- KFM: Only one is described here. Are we missing some? -->

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed.
1. Open the **Load lines** tab and select the load line for the item that exceeds the underdelivery.
1. Adjust the **Underdelivery** field percentage or **Quantity** field value to fulfill the requirement to ship confirm.

    - Alternative pick more quantities from the related work.
