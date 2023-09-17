--- 
# required metadata 
 
title: Prepare a process kanban job when materials are not available for the work cell
description: This procedure focuses on preparing a process kanban job when some materials are not available for the work cell, therefore it's necessary to pick materials from the warehouse. 
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
# Prepare a process kanban job when materials are not available for the work cell

[!include [banner](../../includes/banner.md)]

This procedure focuses on preparing a process kanban job when some materials are not available for the work cell, therefore it's necessary to pick materials from the warehouse. The procedure "Prepare a process kanban job when materials are available" is a prerequisite for creating this procedure. This procedure is intended for the machine operator. The demo data company used to create this procedure is USMF.

1. Go to Production control > Kanban > Kanban board for process jobs.
2. In the Work cell field, click the drop-down button to open the lookup.
3. In the list, click the link in the selected row.
    * Select work cell 1250.  
4. In the list, find and select the desired record.
    * Select Kanban 000356.  
5. In the list, find and select the desired record.
    * In the list, deselect row 4. or Select row 4 if you haven't completed the task "Prepare a process kanban job when materials are available."  
6. Toggle the expansion of the Picking list section.
    * The No entry icon in the supply status indicates that 48 ea of item P0002 are missing for the work cell.  

## Transfer materials to work cell
1. Toggle the expansion of the Transfer jobs section.
2. Use the Quick Filter to filter on the Item number field with a value of 'P0002'.
3. In the list, find and select the desired record.
4. Click Start.
    * Transfer is in progress.  
5. Click Complete.
    * Item P0002 is now available in the picking list for the kanban job. This means that we can prepare the kanban with all the needed materials.  
6. Click Prepare.
    * Notice that an icon in the Job status indicates that the job is now ready.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]