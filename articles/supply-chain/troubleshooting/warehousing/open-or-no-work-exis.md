---
title: Open or no work exists throughout shipment confirmation
description: Open or no work exists throughout shipment confirmation
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
# Open or no work exists throughout shipment confirmation

Error code: WAX515

## Symptoms

The system displays the following error message:

> The shipment for load %1 could not be confirmed because all work for the load must be complete.

The load or shipment can't be ship confirmed in current state.<!-- KFM: What is "ship confirmed"? Confirmed as shipped? Confirmed for shipment? -->

*Open* or *In process* work for related orders needs to be closed or no work exists for the load.  <!-- KFM: Is this a symptom or a cause? This also needs to be clear, maybe in two sentences. -->

## Resolution

Load or shipment is currently in a state where shipment confirmation fails. Navigate to related orders for the load / shipment ensuring the work is completed or cancelled.

There are several pages where you can work shipments and loads. The following sub-sections provide a few examples.

### On the All loads page

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed.
1. On the Action Pane, open the **Loads** tab and, from the **Related information** group, select **Work**.

### On the All shipments page

1. Go to **Warehouse management \> Shipments\> All shipments**.
1. Select the shipment that cannot be ship confirmed.
1. On the Action Pane, open the **Shipments** tab and, from the **Work** group, select **Work details**.

### On the All work page

1. Go to **Warehouse management \> Work\> All work**.
1. Select the work for the order number that cannot be ship confirmed.
1. On the Action Pane, open the **Shipment** tab and, from the **Shipment** group, select **Confirm shipment**.
    - Ensure all the work is completed or cancelled for the related orders
