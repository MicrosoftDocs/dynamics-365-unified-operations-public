---
# required metadata

title: Create and maintain inventory blocking
description: This procedure shows how to prevent physical on-hand inventory from being reserved by other outbound source documents by using the inventory blocking.
author: perlynne
manager: AnnBe
ms.date: 12/02/2015
ms.topic: business-process
ms.prod:  
ms.service: dynamics-ax-applications
ms.technology:  

# optional metadata

# ms.search.form:   
audience: Application User
# ms.devlang:  
ms.reviewer: yuyus
ms.search.scope: Operations
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Create and maintain inventory blocking

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to prevent physical on-hand inventory from being reserved by other outbound source documents by using the inventory blocking. You can run the procedure in demo data company USMF using the example values that are shown. You need to have an item with physical on-hand inventory available before you start this procedure.


## Create an inventory blocking
1. Go to Inventory management > Periodic tasks > Inventory blocking.
2. Click New.
3. In the Item number field, click the drop-down button to open the lookup.
4. In the list, select the item you want to choose.
    * Select an item number with physical on-hand inventory that you want to block. If you’re using USMF you can select item M9201.  
5. In the Quantity field, enter a number.
    * If you’re using item M9201, you need to select less than 200.  
6. Toggle the expansion of the Inventory dimensions section.
7. In the Warehouse field, click the drop-down button to open the lookup.
8. In the list, find and select the desired record.
    * If you’re using item M9201, you can select warehouse 51.  
9. Click Save.

## Update the conditions of the inventory blocking
1. In the Quantity field, enter a number.
    * Update the inventory quantity field to reflect the quantity to block.  
2. In the Expected date field, enter a date.
    * You might want to indicate when the blocked inventory is expected to become available for reservation by assigning an expected date. If the Expected receipts option is selected for the inventory blocking, as it is by default when you manually create a blocking, this date will appear on the expected transaction.  
3. Click Save.

## Remove the inventory blocking
1. Click Delete.
2. Click Yes.
3. Close the page.
