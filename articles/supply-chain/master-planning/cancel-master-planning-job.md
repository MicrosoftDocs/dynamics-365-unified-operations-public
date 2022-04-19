---
# required metadata

title: Cancel a master planning job
description: This topic explains how to cancel an active planning job that uses built-in planning functionality.
author: t-benebo
ms.date: 05/14/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqCreatePlanWorkspace, ReqProcessList
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
ms.search.validFrom: 2019-12-16
ms.dyn365.ops.version: 

---

# Cancel a master planning job

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 Supply Chain Management, there are multiple options for canceling a master planning job. For example, you may want to cancel a master planning job if it was started by mistake or is running longer than expected and you want to end it. 
The best way to cancel a planning job is from  the **Unfinished planning processes** page. Alternative options from the **Batch jobs** and **Batch jobs enhanced** pages should only be used if canceling the master planning job from the **Unfinished planning processes** page did not complete within a few minutes.

## Preferred cancel option
### Cancel master planning job from **Unfinished planning processes** page
1. Go to **Master planning > Inquiries and reports > Master planning > Unfinished planning processes**.
2. Select the line with the planning process that you want to cancel.
3. Click **Cancel**.

## Additional cancel options
These should only be used if canceling the master planning job from the **Unfinished planning processes** page did not complete within a few minutes.

### Delete master planning job from the **Batch jobs** page
1. Go to **System administration > Inquiries > Batch jobs**.
2. Select the line with the planning job that you want to delete.
3. Click **Delete**.

### Abort master planning job task from the **Batch jobs enhanced** page
1. Go to **System administration > Inquiries > Batch jobs**.
2. If the job ID is not shown in the list, click **Switch to enhanced form**, otherwise proceed with the next step.
3. Open the batch job. Click the **Job ID** for the batch job with tasks that you want to end.
4. In **Batch tasks**, select the tasks to end.
5. Click **Change status**, choose **Canceling** and click **OK**.
6. On the **Batch tasks** FastTab, click **Abort**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]