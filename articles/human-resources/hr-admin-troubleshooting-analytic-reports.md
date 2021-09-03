---
# required metadata

title: Troubleshoot analytic reports
description: This topic explains how to troubleshoot and diagnose issues if a customer's data changes don't appear in any of the customer's workspaces.
author: twheeloc
ms.date: 08/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: HcmPersonnelManagementWorkspace, LeaveAbsenceWorkspace, HcmTalentBenefitWorkspace, HcmCompensationWorkspace, HcmEmployeeDevelopmentWorkspace, HcmLearningWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Troubleshoot analytic reports

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

**Issue**

A customer's data changes don't appear on the **Analytics** tabs of any of the customer's workspaces.

**Cause**

By default, Microsoft Power BI reports are refreshed every four hours, according to the schedule of the Deploy measurement batch job.

**Resolution**

This issue might just be a matter of timing. Follow these steps to start the batch job and update the analytics workspaces.

1. Open the **Batch jobs** page at **System administration \> Links \> Batch jobs \> Batch jobs**. Alternatively, use Search, and enter **Batch Jobs**.
1. Find the **Deploy measurement** job in the list.
1. Select **Edit** at the top of the page, and set the scheduled start date/time to a value that will refresh the analytics closer to the current time.

![Batch jobs.](media/batch-jobs.png)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
