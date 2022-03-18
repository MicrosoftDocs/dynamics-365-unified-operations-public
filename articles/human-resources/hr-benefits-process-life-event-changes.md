---
# required metadata

title: Process life event changes
description: This topic explains how to process life event changes in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 08/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart, BenefitLifeEventTypes, BenefitEligibilityProcessResultViewer
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

# Process life event changes


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Process life event changes in Microsoft Dynamics 365 Human Resources for two life event changes:

- Birthday changes
- Eligibility rule override expiration changes 

1. In the **Benefits management** workspace, under **Processing**, select **Life event change processing**.

2. In the **Run life event change process** dialog box, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | Enrollment period | The enrollment period to process life event changes for. |
   | Legal entity | The legal entity to process life event changes for. |

3. If you want to run the process in the background, select **Run in the background** and do the following tasks:

   1. Enter information for the process.

   2. To set up a recurring job, select **Recurrence**, enter the recurrence information, and the select **OK**.

   3. To set up a job alert, select **Alerts**, select the alerts to receive, and then select **OK**.

   4. Select **OK**. The process will run with the parameters you set.

4. Select **OK**.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
