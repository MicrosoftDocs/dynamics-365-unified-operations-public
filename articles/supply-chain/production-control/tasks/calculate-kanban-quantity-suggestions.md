--- 
# required metadata 
 
title: Calculate kanban quantity suggestions
description: This procedure focuses on optimizing the kanban size and quantities for a specific kanban rule by using the kanban quantity calculation. 
author: johanhoffmann
ms.date: 11/11/2016
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
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
# Calculate kanban quantity suggestions

[!include [banner](../../includes/banner.md)]

This procedure focuses on optimizing the kanban size and quantities for a specific kanban rule by using the kanban quantity calculation. The demo data company used to create this procedure is USMF. This procedure is intended for the value stream manager. It is a prerequisite that you have completed the procedure Add a new kanban quantity calculation policy to a kanban rule.


## Create a kanban quantity calculation
1. Go to Production control > Periodic tasks > Kanban quantity calculation > Calculate kanban quantity.
2. Click New.
3. In the Name field, type 'Speaker2016'.
4. In the Name field, click the drop-down button to open the lookup.
    * Select the policy that you have created in the procedure Add a new kanban quantity calculation policy to a kanban rule. For example, Speaker2016.  
5. In the list, click the link in the selected row.
6. In the Rule active as of date field, set the date and time to '2012-12-17T08:00:00'.
    * This date serves as the basis for determining which fixed kanban rules are included in the kanban quantity calculation.  
7. In the Fulfilled demand period start date field, set the date and time to '2012-11-17T09:00:00'.
    * The date from when past demand transactions are included to calculate the kanban quantity.  
8. In the Fulfilled demand period end date field, set the date and time to '2012-12-17T07:59:59'.
    * The date until when past demand transactions are included to calculate the kanban quantity.  
9. In the Demand period start date field, set the date and time to '2012-12-17T08:00:00'.
    * The date from when current demand transactions are included to calculate the kanban quantity.  
10. In the Demand period end date field, set the date and time to '2013-01-16T07:59:59'.
    * The date until when current demand transactions are included to calculate the kanban quantity.  

## Generate kanban quantity proposal
1. Click Save.
2. Click Generate.
    * This generates a kanban quantity proposal line for the kanban rule 000020.  

## Run kanban quantity calculation
1. Click Calculate.
    * This calculates the kanban quantity proposal.  
2. Click OK.
3. In the list, mark the selected row.
    * Notice the suggested kanban quantity is 2.  

## Change product quantity and calculate again
1. Set Product quantity to '5'.
2. Click Calculate.
3. Click OK.
    * Notice that with a kanban quantity of 5, the suggestion is changed to a kanban quantity of 4.  
    * This is caused by the fact that with a lower product quantity, we need more kanbans to fulfill the demand.  

## Update kanban rule
1. In the Rule effective date field, enter a date and time.
    * Set the 'Rule active as of date' to a date in the future. For example, today + one year.  
2. Click Update.
3. Click OK.
4. Close the page.

## Validate change on kanban rule
1. Go to Product information management > Lean manufacturing > Kanban rules.
2. In the list, click the link in the selected row.
    * Select the kanban rule that was created in the previous sub-task. This should be the first kanban rule in the list sorted by number.  
3. Toggle the expansion of the Details section.
    * Notice the effective date, which means that this rule is not activated until this date.  
4. Toggle the expansion of the Quantities section.
    * Notice this is the default quantity that you entered on the kanban quantity calculation.  
    * Notice this is the fixed kanban quantity of 4 from the kanban quantity calculation.  
5. Click the ListPanel tab.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]