--- 
# required metadata 
 
title: Define benefit eligibility rules and policies
description: This topics explains how to create benefit eligibility rules and policies and then assign rules to Benefits. 
author: twheeloc
ms.date: 08/23/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysPolicySourceDocumentRuleType, SysPolicyListPage, SysPolicy, HcmBenefitEligibilityPolicy, HcmBenefit, BenefitWorkspace, HcmBenefitSummaryPart  
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Version 7.0.0, Human Resources
---

# Define benefit eligibility rules and policies


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article explains how to create benefit eligibility rules and policies and then assign rules to benefits.  

## Create benefit eligibility policy rule type

1. Go to **Human resources > Benefits > Eligibility > Benefit eligibility policy rule types**.
2. Select **New**.
3. In the **Rule name** field, enter a value.
4. In the **Description** field, enter a value.
5. In the **Query name** field, select the drop-down button to open the lookup.
6. In the list, select the link in the selected row.
7. Select **Save**.
8. Close the page.

## Benefit eligibility policy

1. Go to **Human resources > Benefits > Eligibility > Benefit eligibility policies**.
2. Select an existing benefit policy.
3. In the list, select the link in the selected row.
4. Toggle the expansion of the **Policy organizations** sections. You can add or remove any organizations you want to include in the policy.
5. Expand or collapse the **Policy rules** section.
6. In the list, find the policy rule previously created.
7. Select **Create policy rule**.
8. In the **Effective date** field, enter the date in which you want the policy to become effective.
    * Setting effective end dates allows you to make future changes to policy rules so you don't need to come back to the policy when you want those changes to take effect.  
9. If needed, add a where clause to the **Add condition** field.
    * For example if you wanted the rule to only apply to Sales Managers you could create the where clause to say: Where position description equals Sales Manager. You can add multiple where statements together in the rule.  
10. Select **OK**.
11. Close the page.

## Assign rule to benefit

1. Go to **Human resources > Benefits > Benefits**.
2. In the list, find and select the desired record.
3. In the list, select the link in the selected row.
4. Expand or collapse the **Eligibility rules** section.
5. Select **Edit**.
6. In the **Eligibility** field, select the rule.
7. In the **Rule type** field, select the rule you previously created.
9. In the list, select the link in the selected row.
10. Select **Save**.
11. Close the form.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
