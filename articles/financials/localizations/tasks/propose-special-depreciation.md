--- 
# required metadata 
 
title: Propose special depreciation (Japan)
description: In Japan, a special depreciation is permitted under certain conditions. 
author: ShylaThompson
manager: AnnBe 
ms.date: 02/26/2016
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
# Propose special depreciation (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

In Japan, a special depreciation is permitted under certain conditions. For Reserve method, this is a two step task: post reserve, and then post reserve allocation. For Direct-off method, only one step is needed, which is the same procedure as post reserve. 



Use this procedure to learn how to propose special depreciation under Reserve method.

Make sure that the fixed asset has been acquired before following this procedure. Also, be sure that the Fixed Assets configuration key is selected.



This procedure uses the JPMF demo company data.


## Post Reserve
1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Save.
5. Click Lines.
6. Click Proposals.
7. Click Extraordinary depreciation proposal.
8. In the To date field, enter a date.
9. Click Filter.
10. In the Criteria field, type a value.
11. Click OK.
12. Click OK.
13. Click Post.

## Post Reserve allocation
1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Save.
5. Click Lines.
6. Click Proposals.
7. Click Extraordinary depreciation proposal.
8. In the To date field, enter a date.
    * Depending on the Allocation start convention, the Reserve allocation start date is different.  
9. Click Filter.
10. In the Criteria field, type a value.
11. Click OK.
12. Click OK.
13. Click Post.

