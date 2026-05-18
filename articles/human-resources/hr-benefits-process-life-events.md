---
# required metadata

title: Process life events
description: During the employee lifecycle in Microsoft Dynamics 365 Human Resources, each employee may encounter various life event changes.
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

# Process life events

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

During the employee lifecycle in Microsoft Dynamics 365 Human Resources, each employee might encounter various life event changes. For example, marriage, change in employment, or dependent or beneficiary change. To use life events, you must enable life events on the **Benefits parameters** page, set up life event types, and set up life event options for plan types.

Before you can process life events, you must run open enrollment at least once during a hiring time frame. In the United States, open enrollment typically occurs once per year. Outside the United States, open enrollment might occur at the time of hire. A worker doesn't need to select a benefit plan for life events to be processed, but they need to be included in open enrollment processing.

Use life event processing when you have workers who have life events that take place on a future date. This event processes all life events that aren't processed, like future life events, or life events that you add that aren't specific to any one worker. One example is a new benefit. Real-time life events are hidden.

For example, if today is February 1, and on February 14 worker Joe Smith is scheduled to change legal entities, if you run life event processing for February 15, the system processes all events up until February 15.

1. In the **Benefits management** workspace, under **Processing**, select **Life event processing**.
1. In the **Run life event process** dialog box, specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Enrollment period** | The enrollment period to process life events for. |
   | **Legal entity** | The legal entity to process life events for. |
   | **Life event date** | The system processes all events during the enrollment period that occur up until this date. |
   | **Worker** | The worker to process life events for. If you leave this field blank, the system processes life events for all workers. |

1. If you want to run the process in the background, select **Run in the background** and complete the following tasks:

   1. Enter information for the process.
   1. To set up a recurring job, select **Recurrence**, enter the recurrence information, and then select **OK**.
   1. To set up a job alert, select **Alerts**, select the alerts to receive, and then select **OK**.
   1. Select **OK**. The process runs with the parameters you set.

1. Select **OK**.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
