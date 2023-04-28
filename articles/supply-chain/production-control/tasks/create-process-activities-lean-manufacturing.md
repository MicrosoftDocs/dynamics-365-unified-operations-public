--- 
# required metadata 
 
title: Create process activities for lean manufacturing
description: Create a process activity for lean manufacturing. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LeanProductionFlow, PlanActivity, PlanActivityWizard, LeanWorkCellLookup, InventLocationIdLookup, PlanActivityDetails, KanbanJobPickingListPart
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
# Create process activities for lean manufacturing

[!include [banner](../../includes/banner.md)]

Create a process activity for lean manufacturing. 

Prerequisites: 

1. A production flow and version that is not active must be created.

2. A work cell must be created.


## Find the production flow version
1. Go to Production control > Setup > Lean production flow > Production flows.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.

## Create a new activity
1. Click Activities.
    * Ensure that the selected production flow has a version in draft and select that version.  
2. Click Create new plan activity.
3. Click Next.
4. In the Name field, type a value.
5. In the Name field, type a value.
    * Note that the name must be unique for a given production flow for all versions.  
6. In the Process quantity field, enter a number.
    * Note that no matter what job quantity will be processed, this is the minimum quantity per job to calculate the labor cost. If job quantities deviate from this quantity, labor cost variance will be created.  
7. Click Next.

## Select the work cell
1. In the Work cell field, click the drop-down button to open the lookup.
2. In the list, click the link in the selected row.

## Define the inventory updates
1. Select or clear the Update on hand receipt check box.
    * If Update On hand = No, you can define the activity to receive a semi-finished product (the activity does not reach the next BOM level).    You can also select to consume semi-finished products.  

## Define the picking activities
1. Click Next.
2. In the list, mark the selected row.
    * A default picking activity is created for the input location of the selected work cell.  
3. Click Add.
    * You can create additional picking activities for specific products, that are not staged at the work cell input activity.  
4. In the list, find and select the desired record.
5. In the Item number field, type a value.
6. In the Warehouse field, click the drop-down button to open the lookup.
    * With this definition, all materials consumed in the activity are picked from the default input warehouse and location except the item that is defined in the second picking activity. This item will be picked from a different warehouse and location.  
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.
9. Select or clear the Register scrap check box.
10. Click Next.

## Define the activity times
1. In the list, find and select the desired record.
    * The definition of a Runtime is required. The Runtime is used to calculate costs and the throughput times of the kanban jobs. Runtimes are not used to calculate capacity load and consumption, this is calculated by cycle time, derived from the production flow version task.  
2. In the Time field, enter a number.
3. In the Unit field, type a value.
4. Select the Time unit.
5. In the Per quantity field, enter a number.
6. In the list, find and select the desired record.
    * Queue times are optional.  
7. In the Time field, enter a number.
8. In the Unit field, type a value.
9. Select the Time unit.
10. In the Per quantity field, enter a number.
11. Click Next.
12. Click Finish.
13. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]