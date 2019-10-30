---
# required metadata

title: Cancel a planning job
description: This topic explains how to cancel an active planning job that uses Planning Optimization.
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

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/preview-banner.md)]

# Cancel a planning job

In Dynamics 365 Supply Chain, it's possible to cancel an active planning job that uses Planning Optimization. To cancel the active planning job, follow the steps below.

> [!NOTE]
> Only active jobs can be canceled.

1. Go to **Master planning > Setup > Plans**.
2. Select the appropriate plan for the planning run.
3. Click **History**.
4. Select the planning job that you want to cancel.
5. Click **Cancel**. 
6. The job status will be "Canceling" until the Planning Optimization service confirms that the job is canceled.
7. When the job is canceled, the status changes to "Canceled".

> [!NOTE]
> You need to refresh the page using the refresh icon to see changes to the status.
