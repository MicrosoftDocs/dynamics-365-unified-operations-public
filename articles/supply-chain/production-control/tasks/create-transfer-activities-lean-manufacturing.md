--- 
# required metadata 
 
title: Create transfer activities for lean manufacturing
description: Create a transfer activity for lean manufacturing. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LeanProductionFlow, PlanActivity, PlanActivityWizard, LeanWorkCellLookup, InventLocationIdLookup   
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
# Create transfer activities for lean manufacturing

[!include [banner](../../includes/banner.md)]

Create a transfer activity for lean manufacturing. 

Prerequisites: 

1. A production flow and version that is not active must be created.

2. The from and to warehouse and locations must be created. Optionally, the replenishing or the replenished work cell should be created.


## Find the production flow version
1. Go to Production control > Setup > Lean production flow > Production flows.
2. In the list, find and select the desired record.
    * Note that the production flow must have a version in draft status.  
3. In the list, click the link in the selected row.

## Create a new activity
1. Click Activities.
    * Ensure that the selected production flow has a version in draft and select that version.  
2. Click Create new plan activity.
3. Click Next.
4. In the Name field, type a value.
5. In the Activity type field, select 'Transfer'.
6. In the Process quantity field, enter a number.
7. Click Next.

## Select the Work cells
1. In the Replenishing field, click the drop-down button to open the lookup.
    * To use the work cell output location as the from location in the transfer activity, select a work cell. The same can be done with the replenished work cell, which sets the target location of the transfer activity.  
2. In the list, click the link in the selected row.

## Define the inventory updates
1. In the Product type field, select an option.
    * Note that a transfer does not change the type of product. You can transfer finished products or semi-finished products (transfer between two activities of a production flow and possibly a kanban flow).     When transferring finished products, you can select if picking or receiving results in an inventory transaction.  

## Define the transfer locations
1. Click Next.
2. In the Warehouse field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. In the Location field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
7. In the Freighted by field, select 'Shipper'.
    * Options include: Shipper - the organization operating the shipping warehouse, Recipient -  the organization operating the receiving warehouse, Carrier - a third party vendor. If the operating organization is a vendor, the transfer activity requires a subcontracting agreement.  
8. Click Next.

## Define the activity times
1. In the list, find and select the desired record.
    * The definition of a Runtime is required. The Runtime is used to calculate cost and the throughput times of the kanban jobs. Runtimes are not used to calculate capacity load and consumption, which is calculated by cycle time, derived from the production flow version task.  
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