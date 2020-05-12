--- 
# required metadata 
 
title: Define benefit eligibility rules and policies
description: This article shows you how you can create benefit eligibility rules and policies and then assign rules to Benefits. 
author: andreabichsel
manager: AnnBe 
ms.date: 02/03/2020
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysPolicySourceDocumentRuleType, SysPolicyListPage, SysPolicy, HcmBenefitEligibilityPolicy, HcmBenefit   
audience: Application User 
# ms.devlang:  
ms.reviewer: anbichse
ms.search.scope: Core, Operations, Human Resources
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Version 7.0.0, Human Resources
---

# Define benefit eligibility rules and policies

This article shows you how you can create benefit eligibility rules and policies and then assign rules to Benefits.  

The demo data company used to create this recording is USMF.


## Create benefit eligibility policy rule type
1. Go to Human resources > Benefits > Eligibility > Benefit eligibility policy rule types.
2. Click New.
3. In the Rule name field, type a value.
4. In the Description field, type a value.
5. In the Query name field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
7. Click Save.
8. Close the page.

## Benefit eligibility policy
1. Go to Human resources > Benefits > Eligibility > Benefit eligibility policies.
2. Select an existing benefit policy.
3. In the list, click the link in the selected row.
4. Toggle the expansion of the Policy organizations sections.  Here you can add or remove any organizations you want to include in the policy.
5. Expand or collapse the Policy rules section.
6. In the list find the policy rule previously created.
7. Click Create policy rule.
8. In the Effective date field, enter the date in which you want the policy to become effective.
    * Setting effective and end dates allows you to make future changes to policy rules and removing the need to come back to the policy when you want those changes to take effect.  
9. 
    * For example if you wanted the rule to only apply to Sales Managers you could create the Where clause to say: Where position description equals Sales Manager.  You can And or Or multiple Where statements together in the rule.  
10. Click OK.
11. Close the page.
12. Close the page.

## Assign rule to benefit
1. Go to Human resources > Benefits > Benefits.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Expand or collapse the Eligibility rules section.
5. Click Edit.
6. In the Eligibility field, select Rule based from the list.
7. In the Rule type field, click the drop down button to open the lookup.
8. In the list find and select the rule you previously created.
9. In the list, click the link in the selected row.
10. Click Save.
11. Close the form.

