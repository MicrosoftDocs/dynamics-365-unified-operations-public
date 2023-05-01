--- 
# required metadata 
 
title: Define lean schedule groups
description: Lean schedule groups are defined to group and distinguish products in kanban scheduling. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LeanScheduleGroup, GanttColorTableLookup   
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
# Define lean schedule groups

[!include [banner](../../includes/banner.md)]

Lean schedule groups are defined to group and distinguish products in kanban scheduling. The grouping can be done as generic association per company or specific to a work cell. Each group has a color code assigned for visual indication in the kanban scheduling listpage. The demo data company used to create this procedure is USMF.


## Define lean scheduling group
1. Go to Product information management > Lean manufacturing > Lean schedule groups.
2. Click New.
3. In the Schedule group field, type a value.
    * A schedule group can be defined as global group or specific to a work cell. In this simple example, we define a global group, and the work cell is kept empty. The settings of this group apply to all work cells that do not have specific schedule groups.  
4. Select a color from the color selection.
    * The colors are used to highlight the jobs on the kanban schedule list page or the kanban process board.  
5. In the list, mark the selected row.
6. In the list, click the link in the selected row.

## Associate product
1. Associate a specific product
    * There are two ways to associate products to lean schedule groups, either as a specific product (Item relation type = Item) or as part of an item allocation key (item relation type = group).    
2. In the Item relation type field, select Item
3. In the Item number field, type a value.
4. In the Throughput ratio field, enter a number.
    * The default Throughput ratio is 1, which means that the related products consume exactly the capacity specified in the process activites of the production flows. Throughput ratio > 1 defines a higher resource consumption, Throughput ratio < 1 defines a lower resource consumption. The ratio is used in the cost calculation and in the calculation of the kanban job consumption.  

## Associate item allocation key
1. Associate an item allocation key
    * Add an association to an item allocation key by using the Item relation type Group.   Note that for this process, you need a forecast item alllocation key defined in your data.  
2. In the Item relation type field, select Group
3. In the Item allocation key field, click the drop-down button to open the lookup.
4. In the list, click the link in the selected row.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]