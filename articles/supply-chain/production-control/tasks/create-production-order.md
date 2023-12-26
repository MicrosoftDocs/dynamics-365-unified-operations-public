--- 
# required metadata 
 
title: Create a production order
description: This procedure shows how to create a production order. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ProdTableListPage, ProdTableCreate, ProdTable, ProdBOM, ProdRoute, ProdJournalCreate
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
# Create a production order

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a production order. The demo data company used to create this procedure is USMF. This is the first procedure out of seven which explains the production order lifecycle.


## Create a production order
1. Go to Production control > Production orders > All production orders.
2. Click New production order.
3. In the Item number field, type 'D0001'.
4. In the Delivery field, enter a date.
    * The delivery date indicates when the production order should end in order to deliver on time. This date can be used in the scheduling process. For example, you can schedule the order backward from the delivery date.  
5. Set Quantity to '20'.
    * Note: The BOM number field automatically displays the number of any active BOM for the current item, but you can change the BOM for the production order by selecting an active BOM from the list of approved BOM versions.    The Route number field automatically displays the number of any active Route for the current item, but you can change the Route for the production order by selecting an active Route from the list of approved Route versions.  
6. Click Create.

## Validate the production order
1. In the list, click the link in the selected row.
    * Click the link for the production order number that you have just created. This will open the details page for the order.  
2. Click Edit.
3. In the Delivery field, enter a date.
    * For example, you can change the delivery date for the production order.  
4. Click Save.
5. Close the page.

## Update the BOM
1. On the Action Pane, click Production order.
2. Click BOM.
    * Open the BOM page to validate the BOM data that was copied from the default data when the production order was created. In this procedure, you need to update the quantity for a BOM.  
3. Click Edit.
4. In the Quantity field, enter a number.
    * Changing the quantity on the BOM line affects the cost estimate of material consumption for the production order.  
5. Click Save.
6. Close the page.

## Update the production route
1. On the Action Pane, click Production order.
2. Click Route.
    * Open the Route page to validate the data of the production route that was copied from the default data when the order was created. In this procedure, you need to update the quantity for one of the operations in the production route.  
3. In the list, find and select the desired record.
4. Click Edit.
5. In the Process qty. field, enter a number.
    * Changing the process time affects the estimated route consumption and the cost of the production order.  
6. Click Save.
7. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]