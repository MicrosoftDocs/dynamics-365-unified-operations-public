---
# required metadata

title: Open or no work exists throughout shipment confirmation.
description: Open or no work exists throughout shipment confirmation.
author: lbc@microsoft.com
manager: tfehr
ms.date: 4/15/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSLoadTable_WHSShipConfirm,WHSLoadPlanningListPage_WHSShipConfirm,WHSLoadPlanningWorkbench_WHSShipConfirm,WHSTransportLoad_WHSShipConfirm,WHSShipPlanningListPage_WHSShipConfirm,WHSShipmentDetails_WHSShipConfirm,WHSWorkTable_WHSShipConfirm,WHSWorkTableListPage_WHSShipConfirm,Dialog_WHSOutboundShipConfirmController_WHSOutboundShipConfirm
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: lbc@microsoft.com
ms.assetid: 
ms.search.region: Global
ms.author: lbc@microsoft.com

---

# Open or no work exists throughout shipment confirmation.

Error code: WAX515

The system displays the following error message:

> The shipment for load %1 could not be confirmed because all work for the load must be complete.

## Symptoms
The load or shipment can't be ship confirmed in current state.

**Open** or **In process ** work for related orders needs to be closed or no work exists for the load.




## Resolution
Load or shipment is currently in a state where shipment confirmation fails. Navigate to related orders for the load / shipment ensuring the work is completed or cancelled.

There are several forms where we have shipments and loads, so a couple are described here:

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed
1. On the Action Pane, open the **Loads** tab and, from the **Related information** group, select **Work** 

or

1. Go to **Warehouse management \> Shipments\> All shipments**.
1. Select the shipment that cannot be ship confirmed
1. On the Action Pane, open the **Shipments** tab and, from the **Work** group, select **Work details** 

Or

1. Go to **Warehouse management \> Work\> All work**.
1. Select the work for the order number that cannot be ship confirmed
1. On the Action Pane, open the **Shipment** tab and, from the **Shipment** group, select **Confirm shipment** 

- Ensure all the work is completed or cancelled for the related orders



