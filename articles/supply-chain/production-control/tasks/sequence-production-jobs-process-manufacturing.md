--- 
# required metadata 
 
title: Sequence production jobs for process manufacturing
description: This procedure uses paint products as an example to show how to sequence planned orders according to the priority of color and package size. 
author: johanhoffmann
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: ReqTransPo, PMFSeqReqRouteChangesListPage, PMFSeqReqRoute, PMFSeqReqRouteChanges, PMFSeqReqSchedDetailsFactBox, PMFSequenceGroup, PMFSequenceItemTable, PMFSequenceTable, PmfSeqWrkCtrCapRes   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Sequence production jobs for process manufacturing

[!include [banner](../../includes/banner.md)]

This procedure uses paint products as an example to show how to sequence planned orders according to the priority of color and package size. The demo data company used to create this procedure is USPI. This procedure is intended for the production planner.


## Run master planning for USPI
1. Go to Master planning > Master planning > Run > Master planning.
2. In the Master plan field, click the drop-down button to open the lookup.
3. In the list, click the link in the selected row.
    * Select MasterPlan.  
4. Click OK.
    * This starts Master Planning, including the sequence process. This process can take a few minutes.  

## View planned orders for the paint products
1. Go to Master planning > Master planning > Planned orders.
2. Expand the Item details FactBox.
3. Expand the Schedule details FactBox.
4. In the Plan field, click the drop-down button to open the lookup.
5. In the list, find and select the desired record.
    * Select MasterPlan.  
6. In the list, click the link in the selected row.
7. Use the Quick Filter to filter on the Item number field with a value of 'P300'.
    * Unlock to scroll to the right to see the order date and delivery date. Notice that these items have an order date of Today and the delivery dates for the planned orders are not sequenced after the priority of color and package size, as shown in the product name. You can hover over an item number to see the product name and priority.  

## Sequence planned orders for paint
1. Close the page.
2. Go to Master planning > Master planning > Sequenced planned orders.
3. Expand the Item details FactBox.
4. Expand the Schedule details FactBox.
    * Note: Here you see that the Start date/time for the planned orders are sequenced according to color and package size within a bucket period of 28 days. These periods are defined by a number in the field Campaign. The sequenced planned order form acts like the typical planned order form, and the production planner can firm the planned orders here.  
5. Mark all rows.
6. Click Accept.
    * This will update the planned orders with the selected sequence action of either Postpone or Advance.  

## Verify the sequence of the planned orders
1. Close the page.
2. Go to Master planning > Master planning > Planned orders.
3. Expand the Item details FactBox.
4. Expand the Schedule details FactBox.
5. In the Plan field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
    * Select MasterPlan.  
7. In the list, click the link in the selected row.
8. Use the Quick Filter to filter on the Item number field with a value of 'P300'.
    * Notice that the orders now are sequenced according to the priority of color and size and the planned orders start at the earliest order date and delivery date. Validate the Order date column or the Start date in the Schedule details FactBbox.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]