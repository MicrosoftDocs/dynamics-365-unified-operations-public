---
# required metadata

title: Cancel a master planning job
description: This topic explains how to cancel an active planning job that uses the built in planning functionality.
author: ChristianRytt
manager: AnnBe
ms.date: 12/16/2019
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

In Microsoft Dynamics 365 Supply Chain Management, there are multiple options to cancel a master planning job. 
This can be useful in case a master planning job was started by mistake or is running longer than expected and needs to be ended.

## Cancel master planning job from **Unfinished planning processes** form
1. Navigate to **Unfinished planning processes**: **Master planning** > **Inquiries and reports** > **Master planning** > **Unfinished planning processes**
2. Select the line with the planning process to cancel
3. Click **Cancel**

## Delete master planning job from **Batch jobs** form
1. Navigate to **Batch jobs**: **System administration** > **Inquiries** > **Batch jobs**
2. Select the line with the planning job to delete
3. Click **Delete**

## Abort master planning job task from **Batch jobs enhanced form**
1. Navigate to **Batch jobs**: **System administration** > **Inquiries** > **Batch jobs**
2. If **Job ID** is not shown in the list, click **Switch to enhanced form**, else proceed with the next step
3. Open the **Batch job**: Click on the **Job ID** of the **Batch job** with tasks to abort
4. In **Batch tasks** select the tasks to abort
5. In the **Batch tasks** fast tab click **Abort**
