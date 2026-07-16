--- 
# required metadata 
 
title: Define benefit eligibility rules and policies
description: This article explains how to create benefit eligibility rules and policies and then assign rules to Benefits. 
author: twheeloc
ms.date: 06/12/2026
ms.topic: how-to 
 
# optional metadata 
 
ms.search.form: SysPolicySourceDocumentRuleType, SysPolicyListPage, SysPolicy, HcmBenefitEligibilityPolicy, HcmBenefit, BenefitWorkspace, HcmBenefitSummaryPart  
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Version 7.0.0, Human Resources
---

# Define benefit eligibility rules and policies

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article explains how to create benefit eligibility rules and policies, and then assign rules to benefits.  

## Create benefit eligibility policy rule type

1. Go to **Human resources > Benefits > Eligibility > Benefit eligibility policy rule types**.
1. Select **New**.
1. In the **Rule name** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Query name** field, select the dropdown button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Save**.
1. Close the page.

## Benefit eligibility policy

1. Go to **Human resources > Benefits > Eligibility > Benefit eligibility policies**.
1. Select an existing benefit policy.
1. In the list, select the link in the selected row.
1. Toggle the expansion of the **Policy organizations** sections. Add or remove any organizations you want to include in the policy.
1. Expand or collapse the **Policy rules** section.
1. In the list, find the policy rule you previously created.
1. Select **Create policy rule**.
1. In the **Effective date** field, enter the date when you want the policy to become effective.
    * By setting effective end dates, you can make future changes to policy rules without needing to return to the policy when you want those changes to take effect.  
1. If needed, add a where clause to the **Add condition** field.
    * For example, if you want the rule to only apply to Sales Managers, create the where clause to say: Where position description equals Sales Manager. You can add multiple where statements together in the rule.  
1. Select **OK**.
1. Close the page.

## Assign rule to benefit

1. Go to **Human resources > Benefits > Benefits**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Expand or collapse the **Eligibility rules** section.
1. Select **Edit**.
1. In the **Eligibility** field, select the rule.
1. In the **Rule type** field, select the rule you previously created.
1. In the list, select the link in the selected row.
1. Select **Save**.
1. Close the page.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
