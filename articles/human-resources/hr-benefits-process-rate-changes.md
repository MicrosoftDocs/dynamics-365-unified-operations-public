---
# required metadata

title: Process rate changes
description: This topic explains how to process benefit rate changes in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 08/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart, BenefitRate, BenefitEligibilityProcessResultViewer
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

# Process rate changes


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic explains how to process benefit rate changes in Microsoft Dynamics 365 Human Resources when a new or existing benefit plan has a change in eligibility rule settings. If a new eligibility rule is created and assigned to the plan, this prompts the system to rerun worker eligibility to check if workers may now be eligible for the plan based on new eligibility options. 

1. In the **Benefits management** workspace, under **Processing**, select **Rate change update processing**.

2. In the **Run benefit rate update process** dialog box, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Enrollment period** | The enrollment period to process rate changes for. |

3. If you want to run the process in the background, select **Run in the background** and do the following tasks:

   1. Enter information for the process.

   2. To set up a recurring job, select **Recurrence**, enter the recurrence information, and the select **OK**.

   3. To set up a job alert, select **Alerts**, select the alerts to receive, and then select **OK**.

   4. Select **OK**. The process will run with the parameters you set.

4. Select **OK**.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
