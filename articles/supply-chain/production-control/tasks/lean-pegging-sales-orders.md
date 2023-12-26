--- 
# required metadata 
 
title: Lean pegging from sales orders
description: This procedure focuses on validating the pegging tree from a sales line where the item is produced with kanbans. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, LeanPeggingTree   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Lean pegging from sales orders

[!include [banner](../../includes/banner.md)]

This procedure focuses on validating the pegging tree from a sales line where the item is produced with kanbans. After validating the pegging tree, all the kanban jobs are planned. This is useful for order scenarios where the order taker needs to ensure that production can start right away. The demo data company used to create this procedure is USMF. This procedure is intended for the advanced order taker working in a lean company.


## Create a sales order for a kanban controlled item
1. Go to All sales orders.
2. Click New.
3. In the Customer account field, enter or select a value.
    * Use US-001.  
4. Click OK.
5. In the Item number field, type 'L0001'.
6. Set Quantity to '30'.
    * It is important that the quantity is higher than 24 in order to trigger the event kanban rule.  

## Open a pegging tree 
1. Click Product and supply.
2. Click View pegging tree.
    * Notice that the pegging tree shows all levels of the pegging needed for the sales order line. In this case, there are two levels of kanbans and all the required components.  

## Plan the pegging tree
1. In the tree, select 'Sales line 000832\Kanban 000558'.
2. Expand the Kanban jobs section.
    * Notice that the job status for the kanban job is Not planned.  
3. Click Plan entire pegging tree.
    * This will plan all kanban jobs in the pegging tree, changing the Job status from Not planned to Planned.  
4. Refresh the page.
    * Notice that the kanban Job status changed from Not planned to Planned.  
5. In the tree, select 'Sales line 000832\Kanban 000558\Issue for L0001\Kanban 000559'.
    * The job for the second kanban is also planned, because the entire pegging tree is planned. Notice that the kanban job status is changed from Not planned to Planned.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]