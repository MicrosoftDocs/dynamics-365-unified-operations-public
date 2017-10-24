---
# required metadata

title: Count inventory in a warehouse
description: This procedure walks you through the process of creating and posting an inventory counting journal in order to count a specific item at a location in the warehouse.
author: MarkusFogelberg
manager: AnnBe
ms.date: 11/14/2016
ms.topic: business-process
ms.prod:  
ms.service: dynamics-ax-applications
ms.technology:  

# optional metadata

# ms.search.form:   
audience: Application User
# ms.devlang:  
ms.reviewer: YuyuScheller
ms.search.scope: Operations
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mafoge
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Count inventory in a warehouse

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure walks you through the process of creating and posting an inventory counting journal in order to count a specific item at a location in the warehouse. The procedure applies to “basic warehousing” functionality, available in the Inventory management module, not to the warehousing functionality that’s available in the Warehouse management module. You can walk through this procedure in demo data company USMF, or using your own data. If you’re using your own data, make sure that you have products and locations set up, and that you’ve created an inventory journal name for counting journals. Inventory counting is normally carried out by a warehouse employee.


## Create an inventory counting journal
1. Go to Inventory management > Journal entries > Item counting > Counting.
2. Click New.
3. In the Name field, click the drop-down button to open the lookup.
4. In the list, click on the inventory counting journal name you want to use
    * Some other fields will be populated based on the setup of the inventory counting journal name that you select.  
5. In the Worker field, click the drop-down button to open the lookup.
6. In the list, select the worker you want to use.
7. Click Select.
8. Click OK.

## Create journal lines
1. Click New.
2. In the Item number field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
    * If you are using demo data company USMF, select 'A0001'.  
4. In the Site field, click the drop-down button to open the lookup.
5. In the list, find and select the desired record.
    * If you are using demo data company USMF, select site '2'.  
6. In the Warehouse field, click the drop-down button to open the lookup.
7. In the list, find and select the desired record.
    * If you are using demo data company USMF, select warehouse '24'.  
8. In the Location field, click the drop-down button to open the lookup.
9. In the list, find and select the desired record.
    * If you are using demo data company USMF, select location 'BULK-001'  
10. In the Counted field, enter a number.
    * If you enter a counted number that’s different to the number shown in the On-hand field, the Quantity field is updated to show the discrepancy.  
11. Click Save.

## Post the inventory counting journal
1. Click Post.
    * When you post an inventory counting journal, if the counted amount differs from amount that’s reported in the On-hand field an inventory receipt or issue is posted, the inventory level and value are changed, and ledger transactions are generated.  
2. Click OK.

## View inventory transactions
1. Click Inventory.
2. Click Transactions.
    * Here you can see any related transactions that will be created when you post your inventory counting journal.   
