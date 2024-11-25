---
title: Cancel a job that was created using the deprecated master planning engine
description: Learn how to cancel an active planning job that uses the deprecated master planning engine with an outline on preferred cancel options.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 05/14/2020
ms.custom: 
ms.reviewer: kamaybac
ms.search.form: ReqCreatePlanWorkspace, ReqProcessList
---

# Cancel a job that was created using the deprecated master planning engine

[!include [banner](../includes/banner.md)]

There are multiple options for canceling a job that was created using the deprecated master planning engine. For example, you may want to cancel a master planning job if it was started by mistake or is running longer than expected and you want to end it.

The best way to cancel a planning job is from  the **Unfinished planning processes** page. Alternative options from the **Batch jobs** and **Batch jobs enhanced** pages should only be used if canceling the master planning job from the **Unfinished planning processes** page did not complete within a few minutes.

## Preferred cancel option

### Cancel master planning job from the Unfinished planning processes page

1. Go to **Master planning > Inquiries and reports > Master planning > Unfinished planning processes**.
2. Select the line with the planning process that you want to cancel.
3. Select **Cancel**.

## Additional cancel options

These should only be used if canceling the master planning job from the **Unfinished planning processes** page did not complete within a few minutes.

### Delete master planning job from the **Batch jobs** page

1. Go to **System administration > Inquiries > Batch jobs**.
2. Select the line with the planning job that you want to delete.
3. Select **Delete**.

### Abort master planning job task from the **Batch jobs enhanced** page

1. Go to **System administration > Inquiries > Batch jobs**.
2. If the job ID is not shown in the list, click **Switch to enhanced form**, otherwise proceed with the next step.
3. Open the batch job. Select the **Job ID** for the batch job with tasks that you want to end.
4. In **Batch tasks**, select the tasks to end.
5. Select **Change status**, choose **Canceling** and click **OK**.
6. On the **Batch tasks** FastTab, click **Abort**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]