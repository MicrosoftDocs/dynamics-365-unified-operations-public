--- 
# required metadata 
 
title: Set up compensation grids
description: Compensation grids are used to define and maintain the pay structures for fixed compensation plans. 
author: twheeloc
ms.date: 01/03/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: HRCCompGrid, HRCCompGridView, HcmCompensationWorkspace
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 

---

# Set up compensation grids


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Compensation grids are used to define and maintain the pay structures for fixed compensation plans. Compensation grids can be shared between multiple plans or copied when creating a new compensation plan.  Before creating a compensation grid, Levels and Reference points must be set up. This example will create a new Grade type of compensation grid using demo data for the Levels and Reference points. The demo data company used to create this procedure is USMF.


## Set up information about the compensation grid
1. Go to **Human resources** > **Compensation** > **Fixed compensation** > **Compensation grids**.
2. Click **New**.
3. In the **Grid** field, type a value.
4. In the **Description** field, type a value.
5. In the **Type** field, select an option.
6. In the **Reference** setup field, enter or select a value.
7. In the **Currency** field, enter or select a value.
8. In the **Effective date** field, enter a date.

## Add levels to the compensation structure
1. Click **Compensation structure**.
2. In the list, mark the selected row.
3. In the **Level** field, enter or select a value.
4. Click **New**.
5. In the list, mark the selected row.
6. In the **Level** field, enter or select a value.
7. Click **New**.
8. In the list, mark the selected row.
9. In the **Level** field, enter or select a value.
10. Click **New**.
11. In the list, mark the selected row.
12. In the **Level** field, enter or select a value.
13. Click **New**.
14. In the list, mark the selected row.
15. In the **Level** field, enter or select a value.

## Fill in the compensation structure with values
1. In the list, mark the selected row.
    * At this point, compensation values can manually be entered into each field in the table, or the Mass change functionality can be used to easily fill in multiple fields and perform basic calculations.  
2. Click **Mass change**.
    * For this grid, we'll first apply the value for the midpoint of the first level's to all the fields in the table. This will be the basis for the compensation matrix.  
3. In the **Adjustment type** field, select an option.
4. In the **Adjustment amount** field, enter a number.
5. In the list, mark or unmark all rows.
6. Click **Apply to grid**.
    * Now we'll use the mass change function to increment the amounts in each subsequent level by a certain percentage or amount. In this example, each grade will have a 12.5% spread between their midpoints.  
7. In the **Adjustment type** field, select an option.
8. In the **Adjustment amount** field, enter a number.
9. In the list, find and select the desired record.
10. Click **Apply to grid**.
    * Now we'll use the mass change function to adjust the Minimum and Maximum reference points for each level. This example will use a 50% spread so the Minimum reference point will be adjusted -20% and the Maximum will be adjusted +20%.  
11. In the **Adjustment amount** field, enter a number.
12. In the **Reference point** field, enter or select a value.
13. In the list, mark or unmark all rows.
14. Click **Apply to grid**.
15. In the **Adjustment amount** field, enter a number.
16. In the **Reference point** field, enter or select a value.
17. In the list, mark or unmark all rows.
18. Click **Apply to grid**.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
