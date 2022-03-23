---
# required metadata

title: Cancel a planning job
description: This topic explains how to cancel an active planning job that uses the Planning optimization functionality.
author: t-benebo
ms.date: 02/18/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
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
# Cancel a planning job

[!include [banner](../../includes/banner.md)]

In Microsoft Dynamics 365 Supply Chain Management, you can cancel an active planning job that uses the Planning optimization functionality. When you select **Cancel** in the dialog box when a Planning optimization job is triggered directly from the user interface (not in the background), this will not cancel the Planning optimization job. Even if you receive a warning such as “Operation canceled”, you will still need to use the following steps to cancel a planning job with Planning optimization.


To cancel an active planning job, follow these steps. 

> [!NOTE]
> Only active jobs can be canceled.

1. Go to **Master planning \> Setup \> Plans**.
2. Select an appropriate plan for the planning run.
3. Select **History**.
4. Select the planning job to cancel.
5. Select **Cancel**.

The job status will be **Canceling** until the Planning Optimization service confirms that the job has been canceled. The status will then be changed to **Canceled**.

> [!NOTE]
> To see status changes, you must refresh the page by selecting the **Refresh** button.

## Additional resources

[Planning Optimization overview](planning-optimization-overview.md)

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)

[View plan history and planning logs](plan-history-logs.md)

[Apply filters to a plan](plan-filters.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]