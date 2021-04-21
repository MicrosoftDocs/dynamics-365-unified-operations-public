---
title: Can't confirm shipment because of incomplete or missing work
description: Can't confirm shipment because of incomplete or missing work
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

# Can't confirm a shipment because of incomplete or missing work

Error code: WAX515

## Symptoms

When you are trying to confirm a shipment, the system displays the following error message:

> The shipment for load %1 could not be confirmed because all work for the load must be complete.

Therefore, you can't confirm the shipment for this load.

## Cause

The load or shipment is currently in a state where shipment confirmation fails. Before you can confirm the shipment, at least some of work for the load must exist, and all of this work must be have a status of *Closed* or *Cancelled*.

## Resolution

Check the related sales or transfer orders for the load or shipment and make sure all of the related work is completed or cancelled.

There are several pages where you can work with shipments and loads. The following sub-sections provide a few examples.

### On the All loads page

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that can't be ship confirmed.
1. On the Action Pane, open the **Loads** tab and, from the **Related information** group, select **Work**.
1. Inspect the status of each work ID. Follow up on each work ID that is not *Closed* or *Cancelled*.
1. When all work is *Closed* or *Cancelled*, try again to confirm the shipment.

### On the All shipments page

1. Go to **Warehouse management \> Shipments\> All shipments**.
1. Select the shipment that can't be ship confirmed.
1. On the Action Pane, open the **Shipments** tab and, from the **Work** group, select **Work details**.
1. Inspect the status of each work ID. Follow up on each work ID that is not *Closed* or *Cancelled*.
1. When all work is *Closed* or *Cancelled*, try again to confirm the shipment.

### On the All work page

1. Go to **Warehouse management \> Work\> All work**.
1. Select the work for the order number that can't be ship confirmed.
1. On the Action Pane, open the **Shipment** tab and, from the **Shipment** group, select **Confirm shipment**.
1. Inspect the status of each work ID. Follow up on each work ID that is not *Closed* or *Cancelled*.
1. When all work is *Closed* or *Cancelled*, try again to confirm the shipment.
