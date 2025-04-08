---
title: Cancel a planning job
description: Learn how to cancel an active planning job that uses the Planning optimization functionality with a step-by-step process.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 02/18/2020
ms.custom: 
ms.reviewer: kamaybac 
ms.search.form: ReqCreatePlanWorkspace
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


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]