---
# required metadata

title: Analytic reports are not being updated
description: 
author: Darinkramer
manager: AnnBe
ms.date: 11/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2018-11-02
ms.dyn365.ops.version: Talent

---

# Analytic reports are not being updated

[!include [banner](includes/banner.md)]

**Issue:**

The customer's data changes Dont show up on the **Analytics** tabs of any of their workspaces.

**Cause:**

By default, PowerBI reports are refreshed every 4 hours as the “deploy measurement” batch job is scheduled.

**Resolution:**

This may just be timing, the steps below list the process to initiate the batch job and update the analytics workspaces.

1.  Navigate to the batch jobs page at **System administration \> Links \> Batch jobs \> Batch jobs**, or use **Search** and enter “Batch Jobs”.

1.  Find the **Deploy measurement** job in the list.

1.  Select the **Edit** button on the top of the page and set the scheduled start date/time to a value that will refresh the analytics closer to the current time.

![](media/batch-jobs.png)
