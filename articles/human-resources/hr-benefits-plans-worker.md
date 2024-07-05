---
# required metadata

title: Create worker benefit plans
description: This article describes how to create, select, and confirm worker benefit plans in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 07/02/2024
ms.topic: article
# optional metadata

ms.search.form: BenefitPlanEmployee, BenefitWorkspace, HcmBenefitSummaryPart
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

# Create worker benefit plans

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

You can create worker benefit plans in Microsoft Dynamics 365 Human Resources to select benefit plans for employees and to confirm benefit plan selections. Typically, employees select benefit plans themselves by using Employee self service, and then a benefits administrator confirms the selections. 

1. In the **Benefits management** workspace, under **Plans**, select **Worker benefit plans**.
2. Select **New**.
3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | Period | Specifies a benefits period to use to filter the plans in the **Plans** FastTab. Filter the plans to help you select a subset of all the plan records so that you can confirm the subset. For example, select a period you created called 2015 to confirm all the benefit enrollment selections for 2015. |
   | Worker | Specifies a worker to use to filter the plans in the **Plans** FastTab. Filter the plans to help you select a subset of all the plan records so that you can confirm the subset. |
   | Legal entity | Specifies a legal entity to use to filter the plans in the **Plans** FastTab. Filter the plans to help you select a subset of all the plan records so that you can confirm the subset. |
   | Coverage option | Specifies a coverage option to use to filter the plans in the **Plans** FastTab. Filter the plans to help you select a subset of all the plan records so that you can confirm the subset. |
   | Default | Filters the benefit plans based on whether they are a default plan. Filter the plans to help you select a subset of all the plan records so that you can confirm the subset. |
   | Status | Filters benefit plans based on their status. Filter the plans to help you select a subset of all the plan records so that you can confirm the subset. |
   | Confirmation | Specifies the confirmation status to use to filter the plans in the **Plans** FastTab. Filter the plans to help you select a subset of all the plan records so that you can confirm the subset. |
   | Cancellation | Specifies the cancellation status to use to filter the plans in the **Plans** FastTab. Filter the plans to help you select a subset of all the plan records so that you can confirm the subset. |
   | Effective date filter | Filters the plans based on whether they’re expired, active, or will be active in the future. Select the checkboxes that correspond to the plans you want to see in the **Plans** fast tab. |
   | Plans | The **Plans** FastTab contains the plans that meet the filter criteria you specified. The relevant configuration options that were set by HR staff and the enrollment selections that were chosen by employees are included on each line. The **Qualified** field specifies whether there is a validation conflict with the plan selection. |

4. Select **Save**.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
