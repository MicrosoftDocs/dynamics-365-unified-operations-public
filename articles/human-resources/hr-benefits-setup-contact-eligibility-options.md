---
# required metadata

title: Configure personal contact eligibility options
description: This article explains how to configure eligibility options for personal contacts in Microsoft Dynamics 365 Human Resources. 
author: twheeloc
ms.date: 05/26/2026
ms.topic: how-to
# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure personal contact eligibility options

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article explains how to configure the types of personal contacts that you can use in benefits in Microsoft Dynamics 365 Human Resources. Personal contacts are the individuals who are covered under your plans (dependents) or who benefit from your plans (beneficiaries). Dependents are typically spouses or children. Beneficiaries can be spouses, children, trusts, or parents.

1. In the **Benefits management** workspace, under **Setup**, select **Personal contact eligibility options**.
1. Select **New**.
1. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Eligibility option** | A unique eligibility option name or code to identify the eligibility option. |
   | **Description** | A brief description of the eligibility option. |
   | **Contact eligibility code** | The system code that best describes the personal eligibility option. Choose from: <ul><li>Relationship</li><li>Student</li><li>Overage dependent</li><li>Over-aged disabled dependent</li></ul> |
   | **Status** | The status of the eligibility option. If you set the status for an eligibility option to inactive, you can't select that personal contact eligibility option for personal contacts. |
   | **Relationship** | Specifies the relationship between the personal contact and the employee. This field is only active if you set the contact eligibility code to Relationship. |
   | **Age** |Specifies the maximum age of an eligible personal contact for the benefit plan. This field is only active if you select a relationship. This age is compared with the calculated age of the personal contact. Calculated age is: (Coverage date – personal contact birth date / 365). This number is always an integer. For **Overage dependent personal** contact eligibility option, the age in this field is the minimum age. For example, if you set age to 18 on the **Overage dependent** option, the dependents who are marked as overage dependent and are 18 or older are covered by the eligibility option.  |

1. Select **Save**.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
