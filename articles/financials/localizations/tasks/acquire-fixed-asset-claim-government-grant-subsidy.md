--- 
# required metadata 
 
title: Acquire a fixed asset and claim for the government grant subsidy (Japan)
description: Use this task to walk through acquiring a fixed asset and then claiming it for a government grant. 
author: ShylaThompson
manager: AnnBe 
ms.date: 09/22/2016
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
# Acquire a fixed asset and claim for the government grant subsidy (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

Use this task to walk through acquiring a fixed asset and then claiming it for a government grant.



In order to complete this task, the Fixed Asset configuration key must be selected.



This task uses the JPMF demo data.


## Acquire the fixed asset
1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Lines.
5. In the Date field, enter a date.
6. In the Account field, specify the desired values.
    * Select the fixed asset to acquire.  
7. In the Book field, type a value.
8. In the Debit field, enter a number.
9. Click Save.
10. Click Post.

## Claim the fixed asset for a government grant
1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Save.
5. Click Lines.
6. Click Proposals.
7. Click Reduction entry proposal.
8. Click Filter.
    * You can filter to help find the fixed asset faster.  
9. In the Criteria field, type a value.
10. Click OK.
11. Click OK.
12. In the Date field, enter a date.
    * Enter the accounting date on which to journalize the subsidy.  
13. In the Credit field, enter a number.
    * Enter the amount of the government grant.  
14. Click Post.

