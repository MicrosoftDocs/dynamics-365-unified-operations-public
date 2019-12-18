---
# required metadata

title: Cancel a master planning job
description: This topic explains how to cancel an active planning job that uses built-in planning functionality.
author: ChristianRytt
manager: AnnBe
ms.date: 12/18/2019
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
ms.search.validFrom: 2019-12-16
ms.dyn365.ops.version: 

---

# Cancel a master planning job

In Microsoft Dynamics 365 Supply Chain Management, there are multiple options for canceling a master planning job. You my want to cancel a master planning job if it was started by mistake or is running longer than expected and needs to be ended.

## Cancel master planning job from **Unfinished planning processes** page
1. Go to **Master planning** > **Inquiries and reports** > **Master planning** > **Unfinished planning processes**.
2. Select the line with the planning process to cancel.
3. Click **Cancel**.

## Delete master planning job from **Batch jobs** page
1. Go to **System administration** > **Inquiries** > **Batch jobs**.
2. Select the line with the planning job to delete.
3. Click **Delete**.

## Abort master planning job task from **Batch jobs enhanced form**
1. Go to **System administration** > **Inquiries** > **Batch jobs**.
2. If the job ID is not shown in the list, click **Switch to enhanced form**, otherwise proceed with the next step.
3. Open the batch job. Click the **Job ID** for the batch job with tasks to end.
4. In **Batch tasks**, select the tasks to end.
5. on the **Batch tasks** FastTab, click **Abort**.
