---
# required metadata

title: Create coverage options
description: Coverage options in Microsoft Dynamics 365 Human Resources are levels of coverage for a participant's election in a benefit plan or program.
author: andreabichsel
manager: AnnBe
ms.date: 04/01/2020
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

# Create coverage options

[!include [banner](includes/preview-feature.md)]

Coverage options in Microsoft Dynamics 365 Human Resources are levels of coverage for a participant's election in a benefit plan or program. For example, coverage options could include **Employee Only** for a medical plan, or **2x Salary** for a life insurance plan. Once defined, you can reuse benefit coverage options. You can associate an option with one or more plans.

After you define coverage options, attach the coverage options to a benefit plan type. The plan type is then associated with a benefit plan or program. Coverage options that are associated with a plan type are available to all plans that are created with that plan type. 

1. In the **Benefits management** workspace, under **Setup**, select **Coverage options**.

2. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Coverage option** | A unique coverage option name. |
   | **Description** | A description of the coverage option. |
   | **Coverage code** | Coverage codes assign minimum and maximum amounts for each eligible covered person type. A coverage code indicates who is covered or the amount of coverage allowed for a plan type. You can express the amount of coverage as a dollar amount or a percentage. For example:</br></br>- **Emp+1** – to be qualified, the employee must have one dependent selected (if more than one is selected, they no longer qualify).</br></br>- **Emp+family** – to be qualified, the employee must have at least two dependents selected. |
   | **Maximum number** | The maximum number of dependents. |
   | **Status** | The status of the coverage option. If the Coverage option status is set to Inactive, the Coverage option can’t be selected on plan types. |
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
