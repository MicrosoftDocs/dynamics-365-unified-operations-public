--- 
# required metadata 
 
title: Mass financial period close
description: This procedure shows how to place a period on hold or permanently close a period or more than one legal entity at a time. 
author: aprilolson
manager: AnnBe 
ms.date: 10/26/2017
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
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Mass financial period close

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to place a period on hold or permanently close a period or more than one legal entity at a time. In addition, the task will show how to restrict user group posting to specific modules.

1. Go to General ledger > Period close > Ledger calendars.
    * Note that the list of legal entities displayed is dependent on the fiscal calendar selected on the page. Only legal entities using the selected fiscal calendar will display.  
2. Click Edit.
3. Select the period for which you want to modify the status.
4. Select the legal entities for which you want to update the status.
    * You can quickly select all legal entities  by selecting the check mark on the upper left side of the grid.  
5. Select Update module access to define the posting access to a selected module.
    * The module status can also be updated one-by-one by editing the records in the grid. The button is useful when you want to quickly update multiple legal entity records.  
6. In the Application module, select the module that you want to update the status. Click Select.
7. In the Access level, select All, None, or a specific user group. Click Select.
    * All indicates all users with edit access to the module can post if the period is open. None indicates that users cannot post to the module if the period is open. A specific user group indicates only users in the group are able to post to the module if the period is open.  
8. Click Update.
9. Select another period to update the status.
10. Select the legal entities for which you want to update the period status.
11. Select Update period status and set the status of On hold, Open, or Permanently closed.
    * Open indicates the period can be posted to, provided the user has access. On hold means the period cannot be posted to, but the period can be reopened. Permanently closed means the period is closed and can never be opened. Adjustments cannot be posted. We do not recommend setting a period to Permanently closed until all adjustments and audits are complete.  
12. Click Update.

