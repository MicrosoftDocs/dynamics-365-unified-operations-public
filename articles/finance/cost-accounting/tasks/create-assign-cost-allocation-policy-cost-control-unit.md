--- 
# required metadata 
 
title: Create and assign a cost allocation policy to a cost control unit
description: Use this procedure to create and assign a cost allocation policy and the corresponding rules to a cost control unit. 
author: twheeloc
ms.date: 06/28/2017
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CAMCostAccountingLedgerPolicyAssignment
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
# Create and assign a cost allocation policy to a cost control unit

[!include [banner](../../includes/banner.md)]

Use this procedure to create and assign a cost allocation policy and the corresponding rules to a cost control unit. This recording uses the USP2 demo data company.


## Create a policy
1. Go to **Cost accounting > Policies > Cost allocation policies**.
2. Click **New**.
3. In the **Policy name** field, type a value.
4. In the **Cost object dimension hierarchy** field, enter or select a value.
    * Select Organization.  
5. In the **Statistical dimension** field, enter or select a value.
6. Click **Save**.

## Create allocation rules
1. Click **New**.
2. In the list, mark the selected row.
3. In the **Cost object dimension hierarchy node** field, enter or select a value.
4. In the **Cost behavior** field, select 'Total'.
5. In the **Allocation base** field, enter or select a value.
6. Click **New**.
7. In the list, mark the selected row.
8. In the **Cost object dimension hierarchy node** field, enter or select a value.
9. In the **Cost behavior** field, select 'Total'.
10. In the **Allocation base** field, enter or select a value.
11. Click **New**.
12. In the list, mark the selected row.
13. In the **Cost object dimension hierarchy node** field, enter or select a value.
14. In the **Cost behavior** field, select 'Total'.
15. In the **Allocation base** field, enter or select a value.
    * Continue until you've created all the rules.  
16. Click **Save**.

## Assign the policy to a cost control unit
1. Click **Policy assignments for cost control unit**.
2. Click **New**.
3. In the list, mark the selected row.
4. In the **Valid from accounting date** field, enter a date.
    * The rules are date-effective. A user or the system can expire the rules if a newer version is created.  
5. In the **Cost control unit** field, enter or select a value.
6. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
