--- 
# required metadata 
 
title: Set up policies for procurement category hierarchies
description: Use this procedure to set up rules for ordering products in a category. 
author: mkirknel
manager: AnnBe 
ms.date: 08/25/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up policies for procurement category hierarchies

[!include[task guide banner](../../includes/task-guide-banner.md)]

Use this procedure to set up rules for ordering products in a category. The rules are defined for a specific purchasing policy. The category access rule controls which procurement categories employees have access to when they create a requisition. When a requisition is being created, the purchasing policy and category access rule that should be applied are determined by the legal entity and the operational unit that the employee belongs to. You can use this procedure in demo data company USMF. This task would typically be carried out by a purchasing manager.


## Find the procurement policy
1. Go to Procurement and sourcing > Setup > Policies > Purchasing policies.
2. Click the link on the Procurement Policy USMF policy.
    * This is the policy that you’ll add a rule to. It must be an Active policy.  

## Create a category access rule
1. Select the Category access policy rule.
    * If the Create policy rule button is dimmed, it’s because there’s already an active policy rule for Category access. Check the Effective and Expiration date fields to determine which it is, then select it, and click Retire policy rule. If the Create policy rule button is available, you don’t need to do anything.  
2. Click Create policy rule.
3. In the Effective date field, enter a date and time.
    * The time must not overlap with another rule that’s already active.  
    * Select a category that the rule will apply to. Make a note of which category this is – you’ll need it later. When you select a category, its parent category or categories will also be added to the Selected categories list.  
    * If you want the rule to apply to all subcategories of the selected category, select the Include subcategories check box.  
4. Click Add.
    * If you set the Include parent rule option to Yes, the policy rule that you define for a parent category is also assigned to its child categories, if no policy rule has been defined for the child categories.  
5. Click OK.

## Create a category policy rule
1. Select the Category policy rule
    * If the Create policy rule button is dimmed, select the active policy rule, and then click Retire policy rule.  
2. Click Create policy rule.
3. In the Effective date field, enter a date and time.
4. Click Add.
5. Select the same category that you used for the Category access rule.
6. In the Vendor selection field, select an option.
    * Select a rule to control which kind of vendors can be selected for the category when requisitions are created.  
7. Click Close.
    * The policy rules that you have defined have been for requisitions of type Consumption. If you wanted to define policies for requisitions of type Replenishment, you would create a rule for the Policy rule type called “Replenishment category access policy rule”.  

