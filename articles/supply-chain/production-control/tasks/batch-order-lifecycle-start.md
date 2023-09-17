--- 
# required metadata 
 
title: Batch order lifecycle from create to start
description: This procedure takes you through the first part of the life cycle of a batch order. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ProdTableListPage, ProdTableCreate, ProdBOM, PmfProdCoBy, ProdParmCostEstimation, ProdCalcTrans, ProdParmRelease, ProdSchedule, ProdRouteJob, ProdParmStartUp, ProdJournalTransBOM, ProdJournalTransRoute   
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
# Batch order lifecycle from create to start

[!include [banner](../../includes/banner.md)]

This procedure takes you through the first part of the life cycle of a batch order.

From creation, cost estimation, and over production job scheduling to the actual start of a batch order.



The demo data company used to create this procedure is USMF. 



The prerequisites for running the procedure with another dataset are a released product with an active formula and route version.


## Create a batch order
1. Go to All production orders.
2. Click New batch order.
3. In the Item number field, enter or select a value.
4. Click Create.
5. Use the Quick Filter to filter on the Production field with a value of 'b'.

## View production formula and expected co-products
1. On the Action Pane, click Production order.
2. Click Formula.
3. Close the page.
4. Click Co-products.
5. Close the page.

## Estimate the batch order
1. Click Estimate.
2. Click OK.
3. On the Action Pane, click Manage costs.
4. Click View calculation details.
5. Close the page.

## Release the batch order
1. On the Action Pane, click Production order.
2. Click Release.
3. Click OK.

## Schedule production jobs
1. On the Action Pane, click Schedule.
2. Click Schedule jobs.
3. Select No in the Finite capacity field.
4. Select No in the Finite material field.
5. Click OK.
6. On the Action Pane, click Production order.
7. Click All jobs.
8. Close the page.

## Start the batch order
1. Click Start.
2. Click the General tab.
3. Select No in the Post picking list now field.
4. Click OK.
5. On the Action Pane, click View.
6. Click Picking list.
7. In the list, click the link in the selected row.
8. Close the page.
9. Close the page.
10. Click Route card.
11. In the list, click the link in the selected row.
12. Close the page.
13. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]