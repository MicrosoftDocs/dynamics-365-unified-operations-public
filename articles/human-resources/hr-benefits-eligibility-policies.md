---
# required metadata

title: Benefit eligibility policies
description: This article provides information about benefit eligibility policies, which define who is eligible for specific benefits.
author: twheeloc
ms.date: 08/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmBenefitEligibilityDetail, SysPolicyListPage, SysPolicySourceDocumentRuleType, BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 4ad0106f-5b07-4fd5-bc1a-5834fa9b198e
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Benefit eligibility policies


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article provides information about benefit eligibility policies, which define who is eligible for specific benefits.

When you create benefits, you decide which benefits will be available to which employees. The following table shows examples of benefits that you might make available to specific employees.

| Benefit          | Who the benefit is available to |
|------------------|---------------------------------|
| Health insurance | All employees                   |
| Mobile phone     | Sales staff, executives         |
| Parking passes   | Executives                      |

The following components in are used to create eligibility policies:

-   Policy rule types
-   Benefit eligibility policies

Policy rule types define the query parameters that are used when you develop specific policy rules. After you create policy rule types, you can create benefit eligibility policies. The policies let you create a collection of rules that apply to one or more legal entities. Within each policy, you can view any of the benefit eligibility policy rule types that you created earlier. 

You define the scope of the rule within the policy. For example, if you create a benefit eligibility policy rule type that is named **Executive**, you can specify what the rule is within that policy. In this example, the rule might state that any job title that contains the word "executive" should be included in the rule. After you've defined the parameters of the rule or rules that are included in the policy, you can assign a specific rule to the benefit.






[!INCLUDE[footer-include](../includes/footer-banner.md)]
