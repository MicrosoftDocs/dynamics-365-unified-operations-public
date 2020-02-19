---
# required metadata

title: Cancel a planning job
description: This topic explains how to cancel an active planning job that uses the Planning Optimization functionality.
author: ChristianRytt
manager: AnnBe
ms.date: 10/26/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: AX 10.0.5

---
# Cancel a planning job

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/preview-banner.md)]

In Microsoft Dynamics 365 Supply Chain Management, you can cancel an active planning job that uses the Planning Optimization functionality.

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

## Related resources

[Planning Optimization overview](planning-optimization-overview.md)

[Get started with Planning Optimization](get-started.md)

[Planning Optimization fit analysis](planning-optimization-fit-analysis.md)

[View plan history and planning logs](plan-history-logs.md)

[Apply filters to a plan](plan-filters.md)
