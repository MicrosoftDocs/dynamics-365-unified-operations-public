---
# required metadata

title: Set up flex credit programs
description: You can use flex credit programs in Microsoft Dynamics 365 Human Resources to enroll employees in benefits according to a predetermined number of flex credits.
author: twheeloc
ms.date: 07/02/2024
ms.topic: article
# optional metadata

ms.search.form: BenefitCreditPrograms, BenefitWorkspace, HcmBenefitSummaryPart
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

# Set up flex credit programs

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

You can use flex credit programs in Microsoft Dynamics 365 Human Resources to enroll employees in benefits according to a predetermined number of flex credits. Employees can choose how to allocate their flex credits. For example, if an employee is covered under their spouse’s health insurance plan, they may want to use the credits they would have otherwise used on health coverage toward other benefits. 

1. In the **Benefits management** workspace, under **Plans**, select **Flex credit programs**.

2. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Benefit credit ID** | The unique identifier of the flex credit program. |
   | **Description** | A description of the flex credit program. | 
   | **From date** | The date the flex credit program becomes active. |
   | **To date** | The end date of the flex credit program. You can leave the default value (12/31/2154) to indicate that the flex credit program doesn’t have a scheduled expiration. |
   | **Total credit value** | The number of credits each employee will have to use for their benefits. |
   | **Prorate rule** | The rule to use for prorating flex credits when an employee is hired in the middle of the flex credit period. </br></br><ul><li>**None** – The employee receives no flex credits if they are hired after the flex credit program period begins.</li><li>**Full credit** – The employee receives the full amount of flex credits, regardless of when they are hired.</li><li>**Prorate** – The employee receives a prorated amount of flex credits based on their start date.</li></ul> |
   | **Flex credit prorate formula** | The rule to use for prorating flex credits for employees who are hired in the middle of a benefit period for the flex credit program. The proration is based on the employment start date. This field is only used if you select **Prorate** in the **Prorate rule** field. </br></br><ul><li>**Daily** – Prorates the number of flex credits an employee receives to the day level. The total number of flex credits is divided by the number of days in the period. For example, if your benefit period is 400 days, the system will divide the total number of flex credits by 400 to calculate the number of flex credits employees receive per day.</li><li>**Current month** – Prorates the number of flex credits an employee receives to the month level, rounded to the current month. The total number of flex credits is divided by the number of months in the period. For example, if your benefit period is 15 months, the system will divide the total number of flex credits by 15 to calculate the number of flex credits employees receive per month.</li><li>**Following month** – Prorates the number of flex credits an employee receives to the month level, rounded to the next month. The total number of flex credits is divided by the number of months in the period. For example, if your benefit period is 15 months, the system divides the total number of flex credits by 15 to calculate the number of flex credits employees receive per month.</li></ul> |
   


[!INCLUDE[footer-include](../includes/footer-banner.md)]
