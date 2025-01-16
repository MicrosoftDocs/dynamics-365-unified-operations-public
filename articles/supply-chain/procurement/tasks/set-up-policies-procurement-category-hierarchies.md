---
title: Set up policies for procurement category hierarchies
description: Learn how to set up rules for ordering products in a category, including processes for finding procurement policies and creating category access rules. 
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: SysPolicyListPage, SysPolicy, ProcCategoryAccessPolicyRule, ProcCategoryPolicyRule, EcoResCategorySingleLookup
ms.topic: how-to
ms.date: 11/18/2024
ms.custom: 
  - bap-template
---

# Set up policies for procurement category hierarchies

[!include [banner](../../includes/banner.md)]

Use this procedure to set up rules for ordering products in a category. The rules are defined for a specific purchasing policy. The category access rule controls which procurement categories employees have access to when they create a requisition. When a requisition is being created, the purchasing policy and category access rule that should be applied are determined by the legal entity and the operational unit that the employee belongs to. This task would typically be carried out by a purchasing manager.

## Find the procurement policy

1. Go to **Procurement and sourcing** \> **Setup** \> **Policies** \> **Purchasing policies**.
1. Open the policy that you want add a rule to. It must be an active policy.  

## Create a category access rule

1. Expand the **Policy rules** FastTab.
1. In the **Policy rule type** list, select the *Category access policy rule*. If the **Create policy rule** button is dimmed, it's because there's already an active policy rule for category access. Check the **Effective** and **Expiration** fields to determine which it is, then select it, and select **Retire policy rule**. If the **Create policy rule** button is available, you don't need to do anything.  
1. Select **Create policy rule**.
1. In the **Effective date** field, enter a date and time. The time must not overlap with another rule that's already active.  
1. Select a category that the rule will apply to. Make a note of which category this is – you'll need it later. When you select a category, its parent category or categories will also be added to the Selected categories list. If you want the rule to apply to all subcategories of the selected category, select the **Include subcategories** check box.
1. Select the right arrow to add to the **Selected categories** list.  
1. Select **OK**. If you set the **Include parent rule** option to *Yes*, the policy rule that you define for a parent category is also assigned to its child categories, if no policy rule has been defined for the child categories.

## Create a category policy rule

1. In the **Policy rule type** list, select the **Category policy rule**. If the **Create policy rule** button is dimmed, select the active policy rule, and then select **Retire policy rule**.  
2. Select **Create policy rule**.
3. In the **Effective date** field, enter a date and time.
4. Select **Add**.
5. In the **Category** field, select the same category that you used for the **Category access rule**.
6. In the **Vendor selection** field, select an option. Select a rule to control which kind of vendors can be selected for the category when requisitions are created.  
7. Select **Close**. The policy rules that you have defined have been for requisitions of type Consumption. If you wanted to define policies for requisitions of type *Replenishment*, you would create a rule for the **Policy rule type** called *Replenishment category access policy rule*.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
