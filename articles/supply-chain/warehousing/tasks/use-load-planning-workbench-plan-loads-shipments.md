--- 
# required metadata 
 
title: Plan loads and shipments using the Load planning workbench
description: This procedure shows how to use the load planning workbench to create a load for a sales order. 
author: BibiSp
manager: AnnBe 
ms.date: 11/11/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: bis
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Plan loads and shipments using the Load planning workbench

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to use the load planning workbench to create a load for a sales order. As a prerequisite we'll create the sales order first. This procedure is part of the daily work for the transportation coordinator. The demo data company used to create this procedure is USMF.


## Create a sales order
1. Go to Accounts receivable > Orders > All sales orders.
2. Click New.
3. In the Customer account field, click the drop-down button to open the lookup.
4. Select account US-004.
5. Click OK.
6. In the Item number field, click the drop-down button to open the lookup.
7. Select item A0001.
    * A0001 is enabled for transportation management.  
8. In the list, click the link in the selected row.
9. In the Quantity field, enter a number.
10. In the Warehouse field, type '24'.
    * In this example select warehouse 24. This warehouse is enabled for transportation management and advanced warehouse management.  
11. Click Save.
12. Close the page.

## Create a new load
1. Go to Transportation management > Planning > Load planning workbench.
2. Click the Sales lines tab.
    * Now you'll build the load for the sales order that you just created. Loads can be built based on supply and demand from purchase orders, transfer orders, and sales orders.  
3. On the Action Pane, click Supply and demand.
4. Click To new load.
5. In the Load template ID field, click the drop-down button to open the lookup.
    * The Load template defines maximum measurements for weight and volume of the entire load. For example, the load template might represent the size of a container or truck.  
6. In the list, click the link in the selected row.
7. Click OK.

## Rate and route the load
1. Click Rating and routing.
2. Click Rate route workbench.
3. Click Rate shop.
4. In the list, find and select the desired record.
5. Click Assign.
6. Close the page.
7. Close the page.

