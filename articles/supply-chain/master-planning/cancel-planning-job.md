---
# required metadata

title: Master planning home page
description: Master planning allows companies to determine and balance the future need for raw materials and capacity to meet company goals. 
author: ShylaThompson
manager: AnnBe
ms.date: 12/03/2018
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
ms.author: roxanad
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Cancel planning job

It is possible to cancel an active planning job that uses Planning Optimization.

How to cancel a planning run:

1. Go to **Master planning \&gt; Setup \&gt; Plans**
2. Select the relevant plan for the planning run
3. Click **History**
4. Select the planning job that you want to cancel
5. Click **Cancel -** Note that only active jobs can be canceled
6. The **Status** of the job will show **Canceling,** until Planning Optimization service confirms that the job is canceled
7. When the job is canceled **Status** change to **Cancelled**

**Note:** You need to refresh the page information (Finance and Operations refresh icon) for status changes to be displayed.
