--- 
# required metadata 
 
title: Record the receipt of goods on the purchase order
description: This procedure shows you how to record receipt of goods directly on a purchase order. 
author: FrankDahl
manager: AnnBe 
ms.date: 08/23/2016
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
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Record the receipt of goods on the purchase order

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to record receipt of goods directly on a purchase order. It’s also possible to register product receipt in the warehouse, and then later record it on the purchase order. This task is typically done by a purchasing agent or an accounts payable coordinator. The example shown in this guide can be used in the USMF demo data company. The example includes steps to create a simple purchase order so that you can play the procedure as a task guide. If you were using the procedure on your own data, you would start at the Record receipt of goods subtask.


## Prepare a new purchase order for receipt of goods
1. Go to Procurement and sourcing > Purchase orders > All purchase orders.
2. Click New.
3. In the Vendor account field, enter US-101.
4. Click OK.
5. In the Item number field, enter M0001.
6. In the Quantity field, enter 5.
7. On the Action Pane, click Purchase.
8. Click Confirm.

## Record receipt of goods
1. On the Action Pane, click Receive.
2. Click Product receipt.
    * The Quantity field allows you to select different options for the quantity that you want to receive. For example, if a quantity has previously been registered in the warehouse, you can select Registered quantity.  For this example, use the value Ordered quantity.   
3. In the Product receipt field, type any value.
    * This field is used to enter a reference that will be used as voucher for the product receipt journal.  
4. Expand the Lines section.
5. Set Quantity to '4'.
    * Here you are able to manually specify the quantity that is being received for each line on the order.  
6. Collapse the Lines section.
7. Click OK.
    * The goods have now been recorded as received on the purchase order, and a product receipt journal has been created as document to reflect this. You can use the Product receipt action to review the journals created with the purchase order, and see what was received, and when.  

