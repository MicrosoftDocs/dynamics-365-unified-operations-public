---
title: You can't confirm a shipment because of incomplete or missing work
description: You can't confirm a shipment because of incomplete or missing work
author: perlynne
ms.date: 04/21/2021
ms.topic: troubleshooting
ms.search.form: WHSLoadTable_WHSShipConfirm,WHSLoadPlanningListPage_WHSShipConfirm,WHSLoadPlanningWorkbench_WHSShipConfirm,WHSTransportLoad_WHSShipConfirm,WHSShipPlanningListPage_WHSShipConfirm,WHSShipmentDetails_WHSShipConfirm,WHSWorkTable_WHSShipConfirm,WHSWorkTableListPage_WHSShipConfirm,Dialog_WHSOutboundShipConfirmController_WHSOutboundShipConfirm, WHSContainerCloseDiag_WHSShipConfirm
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: lbc
ms.search.validFrom: 2021-04-21
ms.dyn365.ops.version: 10.0.18
---

# You can't confirm a shipment because of incomplete or missing work

Error code: WAX515

## Symptoms

When you try to confirm a shipment, the system shows the following error message:

> The shipment for load %1 could not be confirmed because all work for the load must be complete.

Therefore, you can't confirm the shipment for the load.

## Cause

The load or shipment is currently in a state where shipment confirmation fails. Before you can confirm the shipment, at least some work must exist for the load, and all that work must have a status of *Closed* or *Canceled*.

## Resolution

Check the related sales orders or transfer orders for the load or shipment, and make sure that all the related work has been completed or canceled.

You can work with shipments and loads on several pages. The following subsections provide a few examples.

### All loads page

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the shipment can't be confirmed for.
1. On the Action Pane, on the **Loads** tab, in the **Related information** group, select **Work**.
1. Inspect the status of each work ID. Follow up on each work ID that doesn't have a status of *Closed* or *Canceled*.
1. When every work ID has a status of *Closed* or *Canceled*, try again to confirm the shipment.

### All shipments page

1. Go to **Warehouse management \> Shipments\> All shipments**.
1. Select the shipment that can't be confirmed.
1. On the Action Pane, on the **Shipments** tab, in the **Work** group, select **Work details**.
1. Inspect the status of each work ID. Follow up on each work ID that doesn't have a status of *Closed* or *Canceled*.
1. When every work ID has a status of *Closed* or *Canceled*, try again to confirm the shipment.

### All work page

1. Go to **Warehouse management \> Work\> All work**.
1. Select the work for the order number that the shipment can't be confirmed for.
1. On the Action Pane, on the **Shipment** tab, in the **Shipment** group, select **Confirm shipment**.
1. Inspect the status of each work ID. Follow up on each work ID that doesn't have a status of *Closed* or *Canceled*.
1. When every work ID has a status of *Closed* or *Canceled*, try again to confirm the shipment.
