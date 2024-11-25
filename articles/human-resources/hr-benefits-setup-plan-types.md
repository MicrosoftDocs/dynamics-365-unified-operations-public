---
# required metadata

title: Plan type overview
description: A plan type in Microsoft Dynamics 365 Human Resources is a high-level grouping of specific types of benefits. 
author: twheeloc
ms.date: 07/02/2024
ms.topic: overview
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

# Plan type overview

[!include [banner](../includes/preview-banner.md)]

A plan type is a high-level grouping of specific types of benefits. Each plan type has a plan type code that determines rules for the plan type. For example, the **Basic life** plan type will have the **Life** plan type code, because it's a type of life insurance plan and must conform to rules that have been established for the **Life** plan type code. Another plan type might be **Supplemental life**. This plan type will also have the **Life** plan type code.

Each plan type indicates whether an employee can enroll in one plan of its type or multiple. For example, an employee would likely be able to enroll in both the **Basic life** and the **Supplemental life** policies of plan type Life. An employee would likely be allowed to enroll in only one policy of type Medical.

If a plan type involves contacts, the plan type indicates whether contacts are beneficiaries or dependents. For example, a **Basic life** plan type would have beneficiaries, while a Basic medical plan type would have dependents. In some cases, a plan may not have any personal contacts. For example, a Flexible Spending Account or Parking allowance.


A plan type may define coverage options. The coverage options are defined on the **Coverage options** page. A coverage option can specify the amount of the benefit or the contacts who are eligible for the plan type. For example, if the contact type is **Beneficiary**, the coverage option should define the terms of what the beneficiary is eligible to receive when the benefit is utilized. If the contact type is **Dependent**, the coverage option should define the relationship between the dependent and employee. 

> [!IMPORTANT]
> The **Plan types** page includes key data that affects the options that are available when a new benefit plan is created:
>
> - **Plan type code** – This field affects what is shown on the **Configuration** tab when the actual benefit is set up.  
> - **Concurrent enrollment** – This field determines whether multiple enrollments are allowed. (For a medical plan, this field is typically set to **One enrollment**.)
> - **Contact type** – This field enables dependents or beneficiaries to be added to a plan. If it's set to **None**, employees who enroll in benefits won't have the option to select either a beneficiary or a dependent.
> - **Coverage options** – Use this field to link the coverage options with the plan types. It defines either the individuals who will be covered by this plan type or the coverage amounts that are available for this plan type. For example, you can specify that coverage for a medical plan type will be available to the employee only, the employee and one other person, or the employee and their family.

## Create plan types

1. In the **Benefits management** workspace, under **Setup**, select **Plan types**.
2. Select **New**.
3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Plan type** | A unique name that identifies the plan type. |
   | **Description** | A description of the plan type. |
   | **Plan type code** | Select a plan type code from the drop-down list of values. The plan type code list displays all the plan types that are supported in the current version. |
   | **Concurrent enrollment** | Specifies whether an employee can enroll in multiple benefit plans of the same plan type or only one benefit plan per plan type. |
   | **Contact type** | Specifies the role of the personal contact. The values are blank, Dependent, and Beneficiary. You can leave **Contact type** blank if their plan type does not require a dependent or beneficiary based on the coverage option. |

4. To configure life event options, select **Actions**, and then select **Life event options**. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Plan type** | The plan type to configure life event options for. |
   | **Life event type ID** | The ID of the life event type. |
   | **Change coverage option** | Specifies whether an employee can change coverage options during the life event. |
   | **Change to a new plan** | Specifies whether an employee can change plans during the life event. |
   | **Auto reopen eligibility check** | Specifies whether to automatically reopen the benefits enrollment eligibility check during the life event. |
   | **Life event enrollment period** | Specifies the reporting window, in days, of the life event. **Note**: If you don't enter an amount, the system assumes the reporting window to be zero and won't process the life event. |
   | **Editable by administrators only** | Specifies whether administrators can cancel or edit a plan during a life event. No changes can be made by the employee in the **Employee self-service** workspace. |
   | **Auto cancel plan** | Specifies whether the plan should automatically be canceled during a life event. After the life event changes are processed, the **Auto cancel plan** option will retain the plan selection. Only the **Confirmed** or **Checked out** status will be removed. The plan remains selected. Therefore, employees who don't make plan selections during the life event enrollment period won't lose the plan selection. 

5. Select **Save**. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
