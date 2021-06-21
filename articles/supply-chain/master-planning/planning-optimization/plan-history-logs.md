---
# required metadata

title: View plan history and planning logs
description: This topic explains how to view the history of planning jobs that are triggered by the Planning Optimization functionality.
author: ChristianRytt
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
ms.author: crytt
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: AX 10.0.5

---
# View plan history and planning logs

[!include [banner](../../includes/banner.md)]

This topic explains how to view the history of planning jobs that are triggered by the Planning Optimization functionality in Microsoft Dynamics 365 Supply Chain Management.

To view the history for a plan, open the plan by going to **Master planning** \> **Setup** \> **Plans** \> **Master plans** and selecting **History**. The history lists all the jobs for the selected plan. The list includes completed and active jobs.

The history of jobs for Planning Optimization master planning runs keeps only up to 60 records per master plan. Whenever you run a new master planning calculation, that plan's earliest history record is deleted.

In addition to seeing the start time and status of jobs, you can view the log for a specific job. The log includes additional information and warnings. Not all jobs have a log. To view the log for a job, select **Log**. Log entries are only stored for 30 days after the date the job finished, after that they are automatically deleted.

You can find additional information on warnings and errors generated during the master planning run in the infolog for a batch job if the master planning was processed with **Run in the background \> Batch processing** option enabled. For example, auto-firming errors are captured in the infolog only and are not displayed in logs on the **History** page.

In order to view auto-firming errors and other warnings or errors resulted from the master planning run:

1. Go to **System administration \> Inquiries \> Batch jobs**.
1. Find and select the record representing the master planning run you need (for example, it may start with *"Master planning"*).
1. If you have *Enhanced form* switched on for **Batch jobs**, select **Batch job history** and then, on the newly opened page, select **Log** in the action pane.
1. If you have *Legacy form* switched on for **Batch jobs**, select **Batch job \> Log** in the action pane.
1. Select **Message details** to view the infolog and see all warnings and errors captured during processing.

## Related resources

- [Planning Optimization overview](planning-optimization-overview.md)
- [Get started with Planning Optimization](get-started.md)
- [Planning Optimization fit analysis](planning-optimization-fit-analysis.md)
- [Apply filters to a plan](plan-filters.md)
- [Cancel a planning job](cancel-planning-job.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]