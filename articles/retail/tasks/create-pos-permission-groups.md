--- 
# required metadata 
 
title: Create POS permission groups
description: This procedure will show how to create a POS permission group. 
author: scott-tucker
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
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: scotttuc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create POS permission groups

[!include[task guide banner](../includes/task-guide-banner.md)]

This procedure will show how to create a POS permission group. The demo data company used to create this task is USRT. This task is intended for the Retail operations manager role.

1. Go to Permission groups.
2. Click New.
3. In the POS permission group ID field, type a value.
4. In the Description field, type a value.
5. Select Yes in the View time clock entries field.
    * You can now enable or disable various permissions for your POS Permission group. For some permission you can set a value that will be used to evaluate if the POS user can perform the action.  This task guide enables a few permission that might be given to a cashier.  
6. Select Yes in the Allow create order field.
7. Select Yes in the Allow edit order field.
8. Select Yes in the Allow retrieve order field.
9. Select Yes in the Allow password change field.
10. Select Yes in the Allow blind close field.
11. Click Save.
    * After your changes are saved you need to run the Staff distribution schedule to push the changes to retail channels.  
12. Close the page.
13. Go to Jobs.
    * Next we will assign the POS permission group to a Job.  
14. In the list, find and select the desired record.
15. In the list, click the link in the selected row.
16. Click Edit.
17. Expand the Job classification section.
18. In the POS permission group field, enter or select a value.
    * All Workers in Positions for this Job will use this POS permission group’s settings unless the workers POS permissions have been overridden at their Position level.  
19. Click Save.
    * After your changes are saved you need to run the Staff distribution schedule to push the changes to retail channels.  

