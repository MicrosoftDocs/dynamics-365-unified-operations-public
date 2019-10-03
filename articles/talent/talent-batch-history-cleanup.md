---
# required metadata

title: Optimize performance with auto cleanup tasks
description: This topic explains how to resolve some performance issues with Microsoft Dynamics 365 Talent by cleaning up the batch job history.
author: andreabichsel
manager: AnnBe
ms.date: 09/23/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Core, Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2019-09-23
ms.dyn365.ops.version: Platform update 24
---


# Optimize performance with auto cleanup tasks

[!include [banner](../includes/banner.md)]

**Issue**

Microsoft Dynamics 365 Talent can experience performance issues if the batch job history grows too large.

**Cause**

Batch jobs that run frequently can lead to unsustainable growth of the batch job history. This can cause performance issues. 

**Resolution**

Schedule an automatic task to clean up your batch job history. We recommend setting up the task to run weekly, but you might need to run the cleanup more or less frequently, depending on your environment. The following procedure contains our recommended settings, but you can change these according to your needs.

1. In Talent, select **System administration**.

2. In the **Search** bar, enter **Batch job history clean-up**.

   ![Search for batch job history cleanup](media/talent-batch-history-cleanup-search-bar.png)

3. In **History limit (days)**, enter **30**.

   ![Set history limit to 30](media/talent-batch-history-cleanup-history-limit.png)

4. Select **Run in the background** and then select **Recurrence**.

   ![Set recurrence](media/talent-batch-history-cleanup-recurrence.png)

5. Under **Define recurrence**, set the **Start date** and **Start time** to occur during off-hours or the weekend, and then select **NO END DATE**. 

   ![Define recurrence start date and time](media/talent-batch-history-cleanup-define-recurrence.png)

6. Under **RECURRENCE PATTERN**, select **Days** and set **REPEAT AFTER SPECIFIED INTERVAL** to **7**.

   ![Set cleanup to repeat weekly](media/talent-batch-history-cleanup-recurrence-pattern.png)

7. Select **OK**.

8. Change any other parameters under **Run in the background** as necessary, and then select **OK**.

