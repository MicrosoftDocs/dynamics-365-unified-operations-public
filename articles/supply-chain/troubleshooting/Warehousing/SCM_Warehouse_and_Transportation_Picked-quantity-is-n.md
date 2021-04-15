---
# required metadata

title: Picked quantity is not on final shipping location throughout shipment confirmation.
description: Picked quantity is not on final shipping location throughout shipment confirmation.
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

# Picked quantity is not on final shipping location throughout shipment confirmation.

Error code: LoadNotPickedAndMovedToFinalShippingLocation



## Symptoms
The load or shipment can't be ship confirmed in current state.

The related work have not yet been picked and moved to the final shipping location. Picked work quantity do no match the created work quantity on the load line.




## Resolution
Load or shipment is currently in a state where shipment confirmation fails. Navigate to related orders for the load / shipment ensuring the work is completed on final shipping location and quantities matches.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that cannot be ship confirmed
1. Open the **Load lines** tab and select the load line 
1. Note the **Work created quantity**
1. On the Action Pane, open the **Loads** tab and, from the **Related information** group, select **Work** 
 
- Validate that the work is completed on final shipping location and the picked **Work quantity** is matching the load line **Work created quantity**
- Go through above steps for all load lines to ensure criteria is meet.



