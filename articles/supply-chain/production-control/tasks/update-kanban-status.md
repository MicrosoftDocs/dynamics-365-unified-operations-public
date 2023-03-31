--- 
# required metadata 
 
title: Update kanban status
description: When a kanban is emptied by mistake or a received kanban needs to be emptied, you need to update kanban status. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: Kanban, KanbanResetEmpty   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Update kanban status

[!include [banner](../../includes/banner.md)]

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



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]