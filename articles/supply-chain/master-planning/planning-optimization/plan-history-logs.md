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

In addition to seeing the start time and status of jobs, you can view the log for a specific job. The log includes additional information and warnings. Not all jobs have a log. To view the log for a job, select **Log**. The log storage is limited to 30 days since the date the job finished. Any log older than that is deleted automatically.

## Related resources

[Planning Optimization overview](planning-optimization-overview.md)

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)

[Apply filters to a plan](plan-filters.md)

[Cancel a planning job](cancel-planning-job.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]