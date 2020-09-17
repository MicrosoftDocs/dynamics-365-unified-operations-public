---
# required metadata

title: Troubleshoot Sales orders
description: This topic describes how to fix issues that you might encounter while working with discrete manufacturing.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Discrete Manufacturing

This topic describes how to fix common issues that you might encounter while working with Discrete Manufacturing.

##  Warehouse management processes are currently being used. If work lines are not yet registered, you can cancel the created work and any load or shipment lines, and then continue with the picking or shipping process.
The cause of this is because the inventory transaction is in status Picked which means that the material is picked. Therefore it is not possible to reserve or release work for that line.
		
**Resolution/Fix**
You can:

1. Reverse production order status to Estimated or Released
2. Or click "Stop and unpick" button on the Warehouse tab of the production order (this will unpick all picked transactions). Then, click "Remove stop" to proceed with processing the production order.

Here is an explanation of the Unpick and Stop function:

**Unpick**
This action will reverse the status of inventory transactions for BOM/Formula lines in status "Picked" to "On order". The lines gets to status "Picked" when work for raw material picking is completed. This state blocks the production order from being reset to status: Created. The Unpick function can then be used to revert the transactions from status Picked, and then the production order can be reset to status Created.

**Stop**
This actions sets a stop flag on the production order which prevents any status update on the production order (You can find the Stop flag field under the Warehouse fasttab on the production order details page).

>Note:
>- The fields are only visible when the production order is created for items enabled for the warehouse processes.
>- The field group is only visible under the Warehouse tab in the production order details page. The fields are not visible under the Warehouse tab in the production order list page

