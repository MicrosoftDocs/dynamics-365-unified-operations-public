---
# required metadata

title: Create coverage options
description: 
author: andreabichsel
manager: AnnBe
ms.date: 02/01/2020
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
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: Human Resources April 2020 update

---

# Create coverage options

Coverage options in Microsoft Dynamics 365 Human Resources are levels of coverage for a participant's election in a benefit plan or program, such as Employee Only for a medical plan, or 2x Salary for a life insurance plan. Once defined, benefit coverage options are re-usable and you can associate an option with one or more plans.

Once the coverage options are defined, attach the coverage options to a benefit plan type. The plan type is then associated with a benefit plan or program. Coverage options that are associated with a plan type will be available to all plans that are created with that plan type. 

1. In the **Benefits management** workspace, under **Setup**, select **Coverage options**.

2. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Coverage option** | A unique coverage option name. |
   | **Description** | A description of the coverage option. |
   | **Coverage code** | Microsoft Dynamics 365 for Finance and Operations provides some coverage option codes for which a predefined minimum and maximum amount are assigned for each eligible covered person type. Benefit coverage codes are used to validate enrollments against a total number of eligible covered persons (employee, dependent, or beneficiary). For example, a coverage code that allows enrollment of the employee plus one dependent. |
   | **Maximum number** | The maximum number of dependents. |
   | Status | The status of the coverage option. If the Coverage option status is set to Inactive, the Coverage option can’t be selected on plan types. |
   | **Percent** | The percent amount. This field is only active if % x Salary was selected in the Coverage code field. |
   | **Divisor** | The divisor to use in the calculation when you select the coverage code % x salary. |
   | **Percent minimum** | The minimum percentage when you select the Percentage coverage code. |
   | **Percent maximum** | The maximum percentage when you select the Percentage coverage code. |

4. Under **Personal contact eligibility options**, attach the appropriate personal contacts eligibility option to each coverage option.

5. Under **Self service**, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Allow employee contribution amount** | Specifies whether to allow employees to modify the contribution amount on benefits self-service when they select benefits. If you select this check box, the system will calculate benefit plan parameters based on the contribution amount the employee enters on benefits self-service. |
   | **Allow employee coverage amount** | Specifies whether to allow employees to modify the coverage amount on benefits self-service when they select benefits. If you select this check box, the system will calculate benefit plan parameters based on the coverage amount the employee enters in Employee self service. |

6. Select **Save**. 

## See also