--- 
# required metadata 
 
title: Use the safety stock journal to update minimum coverage
description: This procedure shows how to calculate minimum coverage proposals based on historical transactions and then update the item coverage with the proposals. 
author: ChristianRytt
manager: AnnBe 
ms.date: 10/27/2016
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
# Use the safety stock journal to update minimum coverage

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to calculate minimum coverage proposals based on historical transactions and then update the item coverage with the proposals. This is done using the safety stock journal. The demo data company used to create this task is USMF. This task is intended for the production planner, to help maintain minimum coverage.


## Create a new safety stock journal name
1. Go to Safety stock journal names.
2. Click New.
3. In the Name field, type 'Material'.
4. In the Description field, type 'Material'.
5. Close the page.

## Create a safety stock journal
1. Go to Safety stock calculation.
2. Click New.
3. In the Name field, enter or select a value.
    * Select the safety stock journal name that you created, for example, Material.  
4. Click Create lines.
5. In the From date field, enter a date.
    * Set the date to '2015-01-02'.  
6. In the To date field, enter a date.
    * Set the date to '2015-12-30'.  
7. Click OK.
    * This will create lines for the dimensions that have inventory transactions.  

## Calculate proposal
1. Click Calculate proposal.
2. Select the Use average issue during lead time option.
3. Set Multiplication factor to '10'.
    * The Multiply factor is used to adjust the proposal. Because demo data only has a few transactions, you will need to set the factor to get a realistic proposal.  
4. Click OK.
    * Scroll down to find M0002 and M0003. View the Calculated minimum quantity column.   

## Update minimum quantity
1. In the New minimum quantity field, enter a number.
    * Update the New minimum quantity to match the value in the Calculated minimum quantity. If the Calculated minimum is zero,  you can enter the desired future value. For example, you can enter the Calculated minimum quantity in this field for M0002 that has warehouse 12.  
2. In the list, find and select the desired record.
    * For example, you can select M0002 that has warehouse 12.  
3. In the New minimum quantity field, enter a number.
    * Update the New minimum quantity to match the value in the Calculated minimum quantity. If the Calculated minimum is zero you can enter the desired future value.  

## Post the new minimum quantity and validate the result
1. Click Post.
2. Click OK.
3. Click to follow the link in the Item number field.
4. Click to follow the link in the Item number field.
5. On the Action Pane, click Plan.
6. Click Item coverage.
    * Notice that the Minimum quantity has been updated with the new minimum quantity from the safety stock journal.  

