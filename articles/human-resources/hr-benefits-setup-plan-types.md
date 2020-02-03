---
# required metadata

title: Create plan types
description: 
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Create plan types

[!include [banner](includes/preview-feature.md)]

A plan type in Microsoft Dynamics 365 Human Resources is a high-level grouping of specific types of benefits. Each plan type has a plan type code that determines rules for the plan type. For example, the plan type Basic life would have the plan type code Life because it’s a kind of life insurance plan and must conform to rules established for the Life plan type code. Another plan type might be Supplemental life, also with plan type code Life.

Each plan type indicates whether an employee can enroll in one plan of its type or multiple. For example, an employee would likely be able to enroll in both the Basic life and the Supplemental life policies of plan type Life. An employee would likely be allowed to enroll in only one policy of type Medical.

If a plan type involves contacts, the plan type indicates whether contacts are beneficiaries or dependents. For example, a Basic life plan type would have beneficiaries, while a Basic medical plan type would have dependents. In some cases, a plan may not have any personal contacts. For example, a Flexible Spending Account or Parking allowance.

A plan type may define coverage options. The coverage options are defined in the Coverage option form. A coverage option can specify the amount of the benefit or the contacts who are eligible for the plan type. For example, if the contact type is Beneficiary, the coverage option should define the terms of what the beneficiary is eligible to receive when the benefit is utilized. If the contact type is Dependent, the coverage option should define the relationship between the dependent and employee. 

1. In the **Benefits management** workspace, under **Setup**, select **Plan types**.

2. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | Plan type | A unique name that identifies the plan type. |
   | Description | A description of the plan type. |
   | Plant type code | Select a plan type code from the drop down list of values. The plan type code list displays all the plan types that are supported in the current version. |
   | Concurrent enrollment | Specifies whether an employee can enroll in multiple benefit plans of the same plan type or only one benefit plan per plan type. |
   | Contact type | Specifies the role of the personal contact. The values are blank, Dependent, and Beneficiary. You can leave Contact type blank if their plan type does not require a dependent or beneficiary based on the coverage option. |

4. To configure life event options, select **Actions**, and then select **Life event options**. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | Plan type | The plan type to configure life event options for. |
   | Life event type id | The ID of the life event type. |
   | Allow cancellation | Specifies whether an employee can cancel a benefits plan during the life event. |
   |Change coverage option | Specifies whether an employee can change coverage options during the life event. |
   | Change to a new plan | Specifies whether an employee can change plans during the life event. |
   | Auto cancel plan |Specifies whether to automatically cancel the plan during the life event. |
   | Auto reopen eligibility check | Specifies whether to automatically reopen the benefits enrollment eligibility check during the life event. |
   | Reporting window | Specifies the reporting window, in days, of the life event. **Note**: If you don't enter an amount, the system assumes the reporting window to be zero and won't process the life event. |

5. Select **Save**. 
