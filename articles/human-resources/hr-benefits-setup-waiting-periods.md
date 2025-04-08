---
# required metadata

title: Configure waiting periods
description: In Microsoft Dynamics 365 Human Resources, waiting days establish a milestone to use for benefit plans. 
author: twheeloc  
ms.date: 07/02/2024
ms.topic: article
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

# Configure waiting periods

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

In Microsoft Dynamics 365 Human Resources, waiting days establish a milestone to use for benefit plans. For example, three months from hire date, the first of each month, or six months.   

1. In the **Benefits management** workspace, under **Setup**, select **Waiting periods**.
2. Select **New**.
3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Waiting code** | A unique identifier for the waiting period. |
   | **Description** | A description of the waiting period. |
   | **Waiting method** | Select the appropriate waiting method from the drop-down list of values. Options are **Net**, **Current month**, **Current quarter**, **Current year**, and **Current week**. |
   | **Months** | Enter the number of months to add to the waiting method to calculate the waiting date. |
   | **Days** | Enter the number of days to add to the waiting method to calculate the waiting date. |
   | **Waiting day** | Select the waiting day to use to calculate the waiting date. |

4. Select **Save**.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
