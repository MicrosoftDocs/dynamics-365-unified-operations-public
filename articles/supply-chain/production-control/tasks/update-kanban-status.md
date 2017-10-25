--- 
# required metadata 
 
title: Update kanban status
description: When a kanban is emptied by mistake or a received kanban needs to be emptied, you need to update kanban status. 
author: ChristianRytt
manager: AnnBe 
ms.date: 06/20/2016
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
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Update kanban status

[!include[task guide banner](../../includes/task-guide-banner.md)]

When a kanban is emptied by mistake or a received kanban needs to be emptied, you need to update kanban status. The demo data company used to create this procedure is USMF. This procedure is intended for the shop supervisor.


## Find the kanban.
1. Go to Production control > Kanban > Kanbans.
2. Open Handling unit status column filter.
3. Click Clear.
    * This resets the filters.  
4. Use the Quick Filter to find records. For example, filter on the Card number field with a value of '000149'.

## Change emptied status to received status
1. Click Reverse empty handling unit.
2. Click OK.
    * Notice that the Handling unit status is Received.  

## Change received status to emptied status
1. Click Empty kanban.
2. In the list, mark the selected row.
    * Notice that the Handling unit status is Emptied.  

