--- 
# required metadata 
 
title: Use assemble list for fixed assets (Japan)
description: In Japan, you can transfer an inventory item to a fixed asset. 
author: ShylaThompson
manager: AnnBe 
ms.date: 11/10/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Use assemble list for fixed assets (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

In Japan, you can transfer an inventory item to a fixed asset. 



This task walks you through using the assembly list to consume inventory items and create the fixed asset at the same time.



This task was created using the demo data company JPMF.


## Assign component in an assembly list
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. In the list, mark the selected row.
    * Select the fixed asset that you want to assign the assembly list to.  
3. On the Action Pane, click Fixed asset.
4. Click Components.
5. Click Add.
6. In the Item number field, type a value.
    * For example: enter 'D0001'  
7. Click Save.

## Use the assembly list to post a fixed asset write-up transaction
1. Go to Fixed assets > .. > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Lines.
5. In the Date field, enter a date.
6. In the Transaction type field, select 'Write up adjustment'.
7. In the Account field, specify the desired values.
    * Select the fixed asset number that you have assigned to the assembly list.  
8. In the Debit field, enter a number.
    * Enter the cost of the inventory item.  
9. Click Post.

