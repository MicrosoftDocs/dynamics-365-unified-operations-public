--- 
# required metadata 
 
title: Correct inventory tracking information
description: This procedure walks you through the process of creating and posting an inventory transfer journal in order to correct inventory tracking information. 
author: yufeihuang
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventJournalTransfer, InventJournalCreate, InventItemIdLookupSimple, InventBatchIdLookup, InventLocationIdLookup, InventDimTracking, InventTrans   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Correct inventory tracking information

[!include [banner](../../includes/banner.md)]

This procedure walks you through the process of creating and posting an inventory transfer journal in order to correct inventory tracking information. In this example, we'll update the information of a batch controlled item by changing an incorrectly registered batch to another batch. You can walk through this procedure in demo data company USPI, or using your own data. If you use your own data, you need to have an item that's batch-enabled, and it must not be location-controlled. You also need to have an inventory journal name set up for inventory transfers. These tasks would normally be carried out by a warehouse employee.


## Create an inventory transfer journal
1. Go to Transfer.
2. Click New.
3. In the Name field, enter or select a value.
4. Click OK.

## Create journal lines
1. Click New.
2. In the Item number field, enter or select a value.
    * If you are using USPI, select item M5003.  
3. In the Quantity field, enter a number.
4. Click the Inventory dimensions tab.
5. In the Batch number field, enter or select a value.
6. In the Site field, enter or select a value.
7. In the Warehouse field, enter or select a value.
8. In the Batch number field, enter or select a value.

## Post the journal
1. Click Post.
2. Click OK.

## Check tracing information
1. Click Inventory.
2. Click Trace.
3. Click OK.
    * Using this tracing information you can back trace which batch you corrected inventory from.  You can also use the Item tracing page to see this information.  
4. Close the page.

## Check inventory transactions
1. Click Inventory.
2. Click Transactions.
    * Here you can see the transactions that were created when you posted your journal.   



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]