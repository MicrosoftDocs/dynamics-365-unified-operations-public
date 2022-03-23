---
# required metadata

title: View plan history and planning logs
description: This topic explains how to view the history of planning jobs that are triggered by the Planning Optimization functionality.
author: t-benebo
ms.date: 10/30/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: MPSPlanRegenerationJobList, MPSPlanRegenerationJobLogs
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: AX 10.0.5

---
# View plan history and planning logs

[!include [banner](../../includes/banner.md)]

This topic explains how to view the history of planning jobs that are triggered by the Planning Optimization functionality in Microsoft Dynamics 365 Supply Chain Management.

To view the history for a plan, open the plan by going to **Master planning** \> **Setup** \> **Plans** \> **Master plans** and selecting **History**. The history lists all the jobs for the selected plan. The list includes completed and active jobs.

The history of jobs for Planning Optimization master planning runs keeps only up to 60 records per master plan. Whenever you run a new master planning calculation, that plan's earliest history record is deleted.

In addition to seeing the start time and status of jobs, you can view the log for a specific job. The log includes additional information and warnings. Not all jobs have a log. To view the log for a job, select **Log**. Log entries are only stored for 30 days after the date the job finished, after that they are automatically deleted.

If the **Batch processing** option on the **Run in the background** FastTab was enabled when master planning processing was set up, the batch job log shows more information about any warnings and errors that were generated during the master planning run. For example, auto-firming errors are captured only in the batch job log. They aren't shown in logs on the **History** page.

To view auto-firming errors and other warnings or errors that occurred during a master planning run, follow these steps.

1. Go to **System administration \> Inquiries \> Batch jobs**.
1. Find and select the record that represents the master planning run that you're interested in. (For example, the value of the **Job description** field might start with *Master planning*.)
1. Follow one of these steps, depending on whether you're using the *enhanced form* or the *legacy (unenhanced) form* for the **Batch jobs** page:

    - If you're using the enhanced form: On the Action Pane, select **Batch job history**. Then, on the **Batch job history** page, on the Action Pane, select **Log**.
    - If you're using the legacy form: On the Action Pane, on the **Batch job** tab, select **Log**.

1. Select **Message details** to open the **Message details** pane, where you can view all warnings and errors that were captured during processing.

## Related resources

- [Planning Optimization overview](planning-optimization-overview.md)
- [Get started with Planning Optimization](get-started.md)
- [Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
- [Apply filters to a plan](plan-filters.md)
- [Cancel a planning job](cancel-planning-job.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
