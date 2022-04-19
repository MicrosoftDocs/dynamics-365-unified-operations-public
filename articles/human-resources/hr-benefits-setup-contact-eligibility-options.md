---
# required metadata

title: Configure personal contact eligibility options
description: This topic explains how to configure eligibility options for personal contacts in Microsoft Dynamics 365 Human Resources. 
author: twheeloc
ms.date: 08/24/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure personal contact eligibility options


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic explains how to configure the types of personal contacts that can be used in benefits in Microsoft Dynamics 365 Human Resources. Personal contacts are the individuals who will be covered under your plans (dependents) or who will benefit from your plans (beneficiaries). Dependents are typically spouses or children. Beneficiaries can be spouses, children, trusts, or parents.

1. In the **Benefits management** workspace, under **Setup**, select **Personal contact eligibility options**.

2. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Eligibility option** | A unique eligibility option name or code to identify the eligibility option. |
   | **Description** | A brief description of the eligibility option. |
   | **Contact eligibility code** | The system code that best describes the personal eligibility option. You can choose from: <ul><li>Relationship</li><li>Student</li><li>Overage dependent</li><li>Over-aged disabled dependent</li></ul> |
   | **Status** | The status of the eligibility option. If the status for an eligibility option is set to inactive, then you can't select that personal contact eligibility option for personal contacts. |
   | **Relationship** | Specifies the relationship between the personal contact and the employee. This field is only active if the contact eligibility code is set to Relationship. |
   | **Age** | The maximum age of an eligible personal contact for the benefit plan. This field is only active if you select a relationship. This age is compared with the calculated age of the personal contact. Calculated age is: (Coverage date – personal contact birth date / 365). This number is always an integer. |

4. Select **Save**. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
