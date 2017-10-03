--- 
# required metadata 
 
title: Adjust an asset retirement obligation estimate (Japan)
description: For Japan, the initial estimate of the asset retirement obligations (ARO) can be adjusted. 
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
# Adjust an asset retirement obligation estimate (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

For Japan, the initial estimate of the asset retirement obligations (ARO) can be adjusted. 



Use this procedure to learn how to adjust the ARO amount.



To complete this procedure, the Fixed Assets configuration key must be selected.



This task was created using the demo data company JPMF.


## Adjust the ARO estimate
1. Go to Fixed assets > Asset retirement obligations > Fixed assets.
2. In the list, find and select the desired record.
3. On the Action Pane, click Fixed asset.
4. Click Asset retirement obligation.
5. Click Upward to open the drop dialog.
    * You can also click Downward for minus adjustment.  
6. In the Transaction date field, enter the date on which to post the adjustment amount.
7. In the Upward field, enter the amount of adjustment.
8. Click OK.

## Post the adjustment
1. Go to Fixed assets > Asset retirement obligations > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Save.
5. Click Lines.
6. Click Proposals.
7. Click Capitalized asset retirement obligation.
8. In the To date field, enter a date.
9. Click Filter.
10. In the Criteria field, type a value.
11. Click OK.
12. Click OK.
    * Confirm the adjustment is proposed. The amount proposed is discounted to the present value.  
13. Click Post.

