--- 
# required metadata 
 
title: Define production flow models
description: Production flow models describe how the capacity of lean manufacturing work cells is calculated and maintained. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LeanProductionFlowModel   
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
# Define production flow models

[!include [banner](../../includes/banner.md)]

Production flow models describe how the capacity of lean manufacturing work cells is calculated and maintained. Therefore the definition of a production flow model is a prerequisite of the definition of work cells. The demo data company used to create this procedure is USMF.


## Define a production flow model. 
1. Go to Production control > Setup > Lean production flow > Production flow models.
2. Click New.
3. In the Production flow model field, enter an ID for the production flow model.
4. In the Model type field, select an option.
    * There are two model types: Throughput type and Hours type. For Throughput type, the capacity of work cells that use this production flow model will be expressed and calculated in product quantities. For Hours type, the capacity of work cells that uses this production flow model will be expressed and calculated in hours. Note that this property can't be changed for an existing production flow model. After a work cell has capacity reservations, the production flow model type can't be changed.  
5. Enter the number of days in the EPE Cycle.
    * The interval describes the period when every part produced by a production flow or work cell will be produced at least once. The shorter the EPE cycle, the more flexible the production process is. If EPE Cycle = 0, all demand can be produced in the same day. The EPE Cycle is used to schedule lean process jobs. When scheduling a job on a work cell with EPE Cycle = 5, the scheduling process will look for capacity on the work cell at Due date - EPE Cycle (5 days ahead of the due date) to ensure that the product can be produced in that cycle. The inventory lead time of a product is usually equal to or greater than the EPE Cycle of the related production process.  
6. In the Planning period type field, select an option.
    * After a work cell has capacity reservations, the planning period type cannot by changed. You can only select production flow models with the same period type for this given work cell.  
7. In the Planning time fence field, enter a number.
    * The planning time fence describes the number of days where capacity reservations can be made for the related work cells. In the Planning time fence, enter the number of days.   Kanban process jobs that fall outside of this period are not planned with automatic planning. The planning time fence is typically two times the average inventory lead time of the products produced in a production flow or work cell. The EPE Cycle should not be more than half the planning time fence.     
8. In the Capacity shortage reaction field, select an option.
    * The options include:   Postpone - Postponing the full demand of the scheduling event on the next available production day, with available throughput. Cancel - End the automatic planning for the scheduling event and leave the related jobs unplanned.   Add to requested day - Plan the requested jobs for the requested period. This overloads the cell for this day and requires the planner to review and to a manual interaction .   Distribute to available periods - Distribute the different jobs of the scheduling event to all available production days, beginning from the first available day. The minimum distribution quantity is the kanban job quantity. The distribution assigns the minimum planning quantity (kanban quantity) to every day with enough available throughput.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]