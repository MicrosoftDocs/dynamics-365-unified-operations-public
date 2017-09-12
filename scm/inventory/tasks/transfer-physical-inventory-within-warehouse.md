---
# required metadata

title: Transfer physical inventory within the warehouse
description: This procedure walks you through the process of creating and posting an inventory transfer journal in order to register movement of an item from one location in a warehouse to another.
author: MarkusFogelberg
manager: AnnBe
ms.date: 03/02/2016
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
# Transfer physical inventory within the warehouse

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure walks you through the process of creating and posting an inventory transfer journal in order to register movement of an item from one location in a warehouse to another. You need to have an inventory journal name set up for inventory transfers before you start this. You can walk through this procedure in demo data company USMF using the example values that are shown, or using you can use your own data if you have products and locations set up. These tasks would normally be carried out by a warehouse employee.


## Create an inventory transfer journal
1. Go to Transfer.
2. Click New.
3. In the Name field, enter or select a value.
4. Click OK.
    * There is the option to specify 'From' and 'To' dimensions for each journal line. These are essential for this journal type. You can transfer items to locations using different rules. In this example we’ll transfer an item within the same warehouse, from a license plate controlled location to a location that is not license plate controlled.   

## Create journal lines
1. Click New.
2. In the Item number field, enter or select a value.
    * If you are using USMF, you can select 'A0001'.  
3. In the From site field, enter or select a value.
    * If you are using USMF, you can select '2'.  
4. In the To site field, enter or select a value.
    * If you are using USMF, you can select '2'.  
5. In the From warehouse field, enter or select a value.
    * If you are using USMF, you can select '24'.  
6. In the To warehouse field, enter or select a value.
    * If you are using USMF, you can select '24'.  
7. In the From location field, enter or select a value.
    * If you are using USMF, you can select 'FL-001'.  
8. In the To location field, enter or select a value.
    * If you are using USMF, you can select 'BULK-001'.  
9. In the Quantity field, enter a number.
10. Click the Inventory dimensions tab.
11. In the License plate field, enter or select a value.
    * If you are using USMF, you can select '24'.  
12. Click Save.

## Post the inventory transfer journal
1. Click Post.
2. Click OK.

## View inventory transactions
1. Click Inventory.
2. Click Transactions.
    * Here you can see the transactions that were created when you posted your journal.  
