--- 
# required metadata 
 
title: Split a fixed asset
description: This task guide will split a percentage of one asset book to a new asset book. 
author: saraschi2
manager: AnnBe 
ms.date: 10/19/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Split a fixed asset

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide will split a percentage of one asset book to a new asset book.  It uses the Accountant role and USMF demo data.


## Create a new fixed asset
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. Click New.
3. In the Fixed asset group field, enter or select a value.
4. Note the fixed asset number to use in the split process later.
5. In the Name field, type a value.
6. Close the form.

## Split a fixed asset
1. In the list, find and select the fixed asset to split.
2. In the list, click the link in the selected row.
3. Click Books.
    * Select the book to split to the new asset.  
4. Click Functions.
5. Click Split fixed asset.
6. In the To fixed asset field, enter or select a value.
7. In the To book field, click the drop-down button to open the lookup.
8. In the Transaction date field, enter a date.
9. In the Percent field, enter a number.
10. In the Journal name field, enter or select a value.
11. Click OK.

## Post the journal transaction
1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. In the list, select the journal created with the split process.
3. Click Lines.
    * Verify the journal lines created.  An Acquisition adjustment transaction is created for the original asset to decrease the value by the percentage specified during the split process.  An Acquisition transaction is created for the new asset for the same amount.  
4. Click Post.

