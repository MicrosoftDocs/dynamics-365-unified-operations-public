--- 
# required metadata 
 
title: Create and assign a cost behavior policy to a cost control unit
description: Cost behavior is the classification of costs as either fixed or variable. 
author: twheeloc
ms.date: 06/27/2017
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CAMCostBehaviorRule
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create and assign a cost behavior policy to a cost control unit

[!include [banner](../../includes/banner.md)]

Cost behavior is the classification of costs as either fixed or variable. A policy and the corresponding rules have to be assigned to a cost control unit for the policy to become effective. Use this procedure to create a policy and then assign the policy to a cost control unit.


## Create a cost behavior hierarchy
1. Go to **Cost accounting > Dimensions > Dimension hierarchies**.
2. Click **New**.
3. Click **Create**.
4. In the **Dimension hierarchy name** field, type 'Cost behavior hierarchy'.
5. In the **Dimension** field, enter or select a value.
    * Select Cost elements.  
6. Click **Save**.
7. Click **View hierarchy**.
8. Click **New**.
9. In the **Node name** field, type a value.
    * Enter Fixed cost.  
10. In the tree, select 'Cost behavior hierarchy'.
11. Click **New**.
12. In the **Node name** field, type a value.
    * Enter Variable cost.  
13. Click **Save**.
14. In the tree, select 'Cost behavior hierarchy\Fixed cost'.
15. Click **New**.
16. In the list, mark the selected row.
17. In the **From dimension member** field, enter or select a value.
    * The range of dimension members can contain gaps, but the members can't overlap.  
18. In the **To dimension member** field, enter or select a value.
    * The range of dimension members can contain gaps, but the members can't overlap.  
19. In the tree, select 'Cost behavior hierarchy\Variable cost'.
20. Click **New**.
21. In the list, mark the selected row.
22. In the **From dimension member** field, enter or select a value.
    * The range of dimension members can contain gaps, but the members can't overlap.  
23. In the **To dimension member** field, enter or select a value.
    * The range of dimension members can contain gaps, but the members can't overlap.  
24. Click **Save**.

## Create the policy and rules
1. Go to **Cost accounting > Policies > Cost behavior policies**.
2. Click **New**.
3. In the **Policy name** field, type a value.
4. In the **Cost element dimension hierarchy** field, enter or select a value.
    * Select the policy hierarchy that you just created.  
5. In the **Cost object dimension hierarchy** field, enter or select a value.
    * Select Organization.  
6. Click **Save**.
7. Click **New**.
8. In the list, mark the selected row.
9. In the **Cost element dimension hierarchy node** field, enter or select a value.
    * Expand the hierarchy to select Variable cost.  
10. In the **Cost object dimension hierarchy node** field, enter or select a value.
    * By default, the variable percentage is 100 percent.  
11. Click **Policy assignments for cost control unit**.
12. Click **New**.
13. In the list, mark the selected row.
14. In the **Valid from accounting date** field, enter a date.
    * The rules are date-effective, and a user or the system can expire a rule if a newer version is created.  
15. In the **Cost control unit** field, enter or select a value.
16. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
