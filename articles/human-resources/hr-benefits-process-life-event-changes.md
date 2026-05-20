---
# required metadata

title: Process life event changes
description: This article explains how to process life event changes in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 05/14/2026
ms.topic: how-to
# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart, BenefitLifeEventTypes, BenefitEligibilityProcessResultViewer
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

# Process life event changes

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Process life event changes in Microsoft Dynamics 365 Human Resources for two life event changes:

- Birthday changes
- Eligibility rule override expiration changes

1. In the **Benefits management** workspace, under **Processing**, select **Life event change processing**.
1. In the **Run life event change process** dialog box, enter values for the following fields:

   | Field | Description |
   | --- | --- |
   | Enrollment period | The enrollment period to process life event changes for. |
   | Legal entity | The legal entity to process life event changes for. |

1. If you want to run the process in the background, select **Run in the background** and complete the following tasks:

   1. Enter information for the process.
   1. To set up a recurring job, select **Recurrence**, enter the recurrence information, and then select **OK**.
   1. To set up a job alert, select **Alerts**, select the alerts to receive, and then select **OK**.
   1. Select **OK**. The process runs with the parameters you set.

1. Select **OK**.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
