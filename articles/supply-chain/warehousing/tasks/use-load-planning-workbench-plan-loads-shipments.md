--- 
# required metadata 
 
title: Plan loads and shipments using the Load planning workbench
description: This article shows how to use the load planning workbench to create a load for a sales order. 
author: Mirzaab
ms.date: 07/08/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
ms.search.form: WHSHistory, WHSLoadTable, WHSLoadPlanningListPage, WHSLoadPlanningWorkbench
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Plan loads and shipments using the Load planning workbench

[!include [banner](../../includes/banner.md)]

This article shows how to use the load planning workbench to create a load for a sales order. As a prerequisite we'll create the sales order first. This procedure is part of the daily work for the transportation coordinator. The demo data company used to create this procedure is USMF.


## Create a sales order
1. Go to the **Accounts receivable > Orders > All sales orders**.
2. Select **New**.
3. In the **Customer account** field, select the drop-down button to open the lookup.
4. Select account **US-004**.
5. Select **OK**.
6. In the **Item number** field, select the drop-down button to open the lookup.
7. Select item **A0001**. **A0001** is enabled for transportation management.  
8. In the **Site** field, select the drop-down button to open the lookup, then select an item.
9. In the **Quantity** field, enter a number.
10. In the **Warehouse** field, type '24' for this example. This warehouse is enabled for transportation management and warehouse management processes (WMS).  
11. Select **Save**.
12. Close the page.

## Create a new load
1. Go to the **Transportation management > Planning > Load planning workbench**.
2. Select the **Sales lines** tab. Now you'll build the load for the sales order that you just created. Loads can be built based on supply and demand from purchase orders, transfer orders, and sales orders.  
3. On the Action Pane, select **Supply and demand**.
4. Select **To new load**.
5. In the **Load template ID** field, select the drop-down button to open the lookup. The Load template defines maximum measurements for weight and volume of the entire load. For example, the load template might represent the size of a container or truck. Select an item.
6. Select **OK**.

## Rate and route the load
1. Select **Rating and routing**.
2. Select **Rate route workbench**.
3. Select **Rate shop**.
4. In the list, find and select the desired record.
5. Select **Assign**.
6. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]