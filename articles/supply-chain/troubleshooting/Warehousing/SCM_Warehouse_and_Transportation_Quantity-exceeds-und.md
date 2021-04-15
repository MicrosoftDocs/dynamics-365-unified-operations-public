---
# required metadata

title: Quantity exceeds under delivery percentage throughout shipment confirmation.
description: Quantity exceeds under delivery percentage throughout shipment confirmation.
author: lbc@microsoft.com
manager: tfehr
ms.date: 4/15/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSLoadTable,WHSLoadPlanningListPage,WHSLoadPlanningWorkbench,WHSTransportLoad,WHSShipPlanningListPage,WHSShipmentDetails,WHSWorkTable,WHSWorkTableListPage
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

# Quantity exceeds under delivery percentage throughout shipment confirmation.

Error code: WAX1686



## Symptoms
The load or shipment can't be ship confirmed in current state.

The quantity of the load or shipment has only been partially picked and is not within the range of under delivery percentage.




## Resolution
Load or shipment is currently in a state where shipment confirmation fails. The quantity is currently larger than picked and not with the range of the allowed under delivery.

Two options to address this issue are:

- Set the load line quantity 
1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed
1. Open the **Load lines** tab and select the load line for the item that exceeds the under delivery
1. Open the **Line details** tab and, select **Order**
1. In the **Quantity** field set the value to the picked quantity (**Work created quantity**), allowing shipment confirmation to proceed.

- Set under delivery percentage.
1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed
1. Open the **Load lines** tab and select the load line for the item that exceeds the under delivery
1. Open the **Line details** tab and, select **General**
1. In the **Underdelivery** field set the percentage to a large value, accommodating the quantity picked against the load quantity, allowing shipment confirmation to proceed.



