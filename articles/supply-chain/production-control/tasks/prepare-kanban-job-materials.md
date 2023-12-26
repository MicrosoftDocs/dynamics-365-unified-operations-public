--- 
# required metadata 
 
title: Prepare a process kanban job when materials are available for the work cell
description: This task focuses on preparing a process kanban job when all materials are available for the work cell. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: KanbanBoardWorkCell   
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
# Prepare a process kanban job when materials are available for the work cell

[!include [banner](../../includes/banner.md)]

This task focuses on preparing a process kanban job when all materials are available for the work cell. The demo data company used to create this task is USMF. This task is intended for the machine operator.

1. Go to Kanban board for process jobs.
2. In the Work cell field, click the drop-down button to open the lookup.
3. In the list, click the link in the selected row.
    * Select work cell 1250 and click OK.  
4. In the list, select row 4.
    * In the clean demo company, Kanban 000329 in row 4 is the first job that is not completed yet.  
5. Toggle the expansion of the Picking list section.
    * Verify that the supply status is available for all items in the picking list.  
    * If multiple jobs are selected, the picking list will show the sum of all items needed for the selected jobs.  
6. Click Prepare.
    * The preparation process is now completed. The selected check box for all rows in the picking list indicates that the supply status is picked.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]