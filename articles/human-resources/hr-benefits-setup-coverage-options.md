---
# required metadata

title: Create coverage options
description: This topic describes the coverage options in Microsoft Dynamics 365 Human Resources for a participant's election in a benefit plan or program.
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

# Create coverage options


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Coverage options determine who should be covered, or how much coverage is available in an insurance plan. For example, for a medical plan, you might have an **Employee only** option, an **Employee + 1** option, and a **Family** option. For life insurance, you might offer coverage for **1 x salary** or **2 x salary**.

After benefit coverage options are defined, you can reuse them. You can associate an option with one or more plans.

> [!IMPORTANT]
> After you define coverage options, attach them to a benefit plan type. The plan type is then associated with a benefit plan or program. Coverage options that are associated with a plan type are available to all plans of that type that are created.

## Create coverage options
1. In the **Benefits management** workspace, under **Setup**, select **Coverage options**.

2. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Coverage option** | A unique coverage option name. |
   | **Description** | A description of the coverage option. |
   | **Coverage code** | Coverage codes assign minimum and maximum amounts for each eligible covered person type. A coverage code indicates who is covered or the amount of coverage allowed for a plan type. You can express the amount of coverage as a dollar amount or a percentage. For example:<ul><li>**Emp+1** – to be qualified, the employee must have one dependent selected (if more than one is selected, they no longer qualify).</li><li>**Emp+family** – to be qualified, the employee must have at least two dependents selected.</li></ul> |
   | **Maximum number** | The maximum number of dependents. |
   | **Status** | The status of the coverage option. If the Coverage option status is set to **Inactive**, the Coverage option can't be selected on plan types. |
   | **Percent** | The percent amount. This field is only active if % x Salary was selected in the Coverage code field. |
   | **Divisor** | The divisor to use in the calculation when you select the coverage code % x salary. |
   | **Percent minimum** | The minimum percentage when you select the Percentage coverage code. |
   | **Percent maximum** | The maximum percentage when you select the Percentage coverage code. |

4. Under **Personal contact eligibility options**, attach the appropriate personal contacts eligibility option to each coverage option.

5. Under **Self service**, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Allow employee contribution amount** | Specifies whether to allow employees to modify the contribution amount in Benefits self service when they select benefits. If you select this check box, the system will calculate benefit plan parameters based on the contribution amount the employee enters in Benefits self service. |
   | **Allow employee coverage amount** | Specifies whether to allow employees to modify the coverage amount in Benefits self service when they select benefits. If you select this check box, the system will calculate benefit plan parameters based on the coverage amount the employee enters in Employee self service. |

6. Select **Save**. 


[!INCLUDE[footer-include](../includes/footer-banner.md)]
