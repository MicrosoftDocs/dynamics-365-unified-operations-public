---
title: You can't confirm a shipment because the quantity exceeds the overdelivery percentage
description: You can't confirm a shipment because the quantity exceeds the overdelivery percentage
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

# You can't confirm a shipment because the quantity exceeds the overdelivery percentage

Error code: WAX1687

## Symptoms

When you try to confirm a shipment, the system shows the following error message:

> The shipment for load %1 could not be confirmed because the quantity for item %2 exceeds the percentage that is defined for overdelivery.

Therefore, you can't confirm the shipment for the load.

## Cause

The quantity of the load or shipment has been only partially picked. The quantity currently exceeds the picked quantity by a percentage that is outside the allowed overdelivery percentage.

## Resolution

To fix this issue, complete one of the following tasks:

- Set the load line quantity.
- Set the overdelivery percentage.

### Set the load line quantity

To set the load line quantity, follow these steps.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the shipment can't be confirmed for.
1. On the **Load lines** FastTab, select the load line for the item that exceeds the overdelivery percentage.
1. On the **Line details** FastTab, select **Order**.
1. In the **Quantity** field, set the value to the picked quantity (that is, to the **Work created quantity** value), so that shipment confirmation can occur.

### Set the overdelivery percentage

To set the underdelivery percentage, follow these steps.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the shipment can't be confirmed for.
1. On the **Load lines** FastTab, select the load line for the item that exceeds the overdelivery percentage.
1. On the **Line details** FastTab, select **General**.
1. In the **Overdelivery** field, set the value to a larger percentage that accommodates the quantity that has been picked against the load quantity, so that shipment confirmation can occur.
