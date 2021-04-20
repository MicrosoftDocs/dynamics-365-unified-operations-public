---
title: Quantity exceeds underdelivery percentage throughout shipment confirmation
description: Quantity exceeds underdelivery percentage throughout shipment confirmation
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

# Quantity exceeds underdelivery percentage throughout shipment confirmation

Error code: WAX1686

## Symptoms

The system displays the following error message:

> The shipment for load %1 could not be confirmed because the quantity for item %2 exceeds the percentage that is defined for underdelivery.

The load or shipment can't be ship confirmed in current state.

The quantity of the load or shipment has only been partially picked and is not within the range of underdelivery percentage.

## Resolution

Load or shipment is currently in a state where shipment confirmation fails. The quantity is currently larger than picked and not with the range of the allowed underdelivery.

Do one of the following to address this issue:

- Set the load line quantity
- Set the underdelivery percentage

### Set the load line quantity

To set the load line quantity:

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed
1. On the **Load lines** FastTab, select the load line for the item that exceeds the underdelivery
1. Expand the **Line details** FastTab and select **Order**
1. In the **Quantity** field set the value to the picked quantity (**Work created quantity**), allowing shipment confirmation to proceed.

### Set the underdelivery percentage

To set the underdelivery percentage:

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed
1. On the **Load lines** FastTab, select the load line for the item that exceeds the underdelivery
1. Expand the **Line details** FastTab and select **General**
1. In the **Underdelivery** field set the percentage to a large value, accommodating the quantity picked against the load quantity, allowing shipment confirmation to proceed.
