---
# required metadata

title: When to reset a data mart
description: Resetting a data mart can be time consuming. Depending on the circumstances, it might or might not be the solution that's needed. This topic lists the circumstances that might be improved by resetting a data mart, as well as circumstances in which resetting your data mart is unlikely to help.
author: jinniew
manager: AnnBe
ms.date: 12/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jiwo
ms.search.validFrom: 2020-12-15
ms.dyn365.ops.version: 10.0.15

---

# When to reset a data mart

Resetting a data mart can be time consuming. Depending on the circumstances, it might or might not be the solution that's needed. This topic lists the circumstances that might be improved by resetting a data mart, as well as circumstances in which resetting your data mart is unlikely to help.  

## When do you need to do a data mart reset?
Consider the following questions before resetting a data mart. Answering yes to one or more questions might indicate that your organization can benefit by resetting the data mart.

- The application database was restored, but the data mart database was not restored.
- You see incorrect data for an accounting period, that isn't the result of an issue with the report design.
- You see incorrect data for an accounting period, and records are listed under Integration attempts on the **Integration status** page in Report Designer (start the Report Designer and select **Tools > Integration status**.
- You've opened a support incident and a support engineer has instructed you to reset the data mart as part of a troubleshooting step.
 
## When is not appropriate to reset a data mart reset?
There are some circumstances when we don't recommend resetting a data mart. These include the following. 

- Anytime the reason isn’t listed in this topic.
- You're experiencing performance issues that are associated with a data sync. In this circumstance, resetting the data mart probably won't help.
- If you have a recurring reset pattern due to any of the following reasons: 
  - **Missing data** - First eliminate report design issues and data sync timing issues, for example, you observe that the fact map hasn’t run since missing data was posted.
  - **Stuck** integration state - If the integration is slow or seems stuck, resetting the data mart is unlikely to resolve the issue.
  - If a number of attempts to complete a reset have been made, and have been unsuccessful because of missing data, we recommend opening a support incident and working with a support engineer to analyze your situation before attempting to reset to reset the data mart again.
  - Stale records by themselves don't necessarily justify resetting the data mart.  If you have a large data set, the reset process will take some time to run, but is unlikely to result in improvement.
 
## What happens during a reset?  
- A reset will only start when existing tasks are complete to ensure old data isn’t inserted.  At this point you may see a message like this: “The data mart reset was unable to be processed because of an active task. Please try again later.”
- The reset will disable the integration tasks and delete all the data mart data. The integration is re-enabled.

> [!Note]
> The following points specify two things that resetting a data mart will *not* do. <br>
> - Resets do not clear report designs. <br>
> - Resets do not clear company or user data unless selected.
