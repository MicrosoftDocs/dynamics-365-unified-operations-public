---
# required metadata

title: Optimize performance with auto cleanup tasks
description: This article explains how to improve performance in Microsoft Dynamics 365 Human Resources by cleaning up the batch job history.
author: twheeloc
ms.date: 05/14/2026
ms.topic: how-to
# optional metadata

# ms.search.form: BatchJob, BatchJobEnhanced
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Platform update 24
---


# Optimize performance with auto cleanup tasks

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

**Issue**

Microsoft Dynamics 365 Human Resources can experience performance problems if the batch job history grows too large.

**Cause**

Batch jobs that run frequently can cause unsustainable growth of the batch job history. This growth can lead to performance problems.

**Resolution**

Schedule an automatic task to clean up your batch job history. Set up the task to run weekly, but you might need to run the cleanup more or less frequently, depending on your environment. The following procedure contains the recommended settings, but you can change these settings according to your needs.

1. In Human Resources, select **System administration**.

1. In the **Search** bar, enter **Batch job history clean-up**.

   :::image type="content" source="media/talent-batch-history-cleanup-search-bar.png" alt-text="Screenshot of searching for batch job history cleanup in the Search bar.":::

1. In **History limit (days)**, enter **30**.

   :::image type="content" source="media/talent-batch-history-cleanup-history-limit.png" alt-text="Screenshot of setting the history limit to 30 days.":::

1. Select **Run in the background** and then select **Recurrence**.

   :::image type="content" source="media/talent-batch-history-cleanup-recurrence.png" alt-text="Screenshot of selecting Run in the background and Recurrence options.":::

1. Under **Define recurrence**, set the **Start date** and **Start time** to occur during off-hours or the weekend, and then select **NO END DATE**.

   :::image type="content" source="media/talent-batch-history-cleanup-define-recurrence.png" alt-text="Screenshot of defining the recurrence start date and start time with no end date.":::

1. Under **RECURRENCE PATTERN**, select **Days** and set **REPEAT AFTER SPECIFIED INTERVAL** to **7**.

   :::image type="content" source="media/talent-batch-history-cleanup-recurrence-pattern.png" alt-text="Screenshot of setting the recurrence pattern to repeat every seven days.":::

1. Select **OK**.

1. Change any other parameters under **Run in the background** as necessary, and then select **OK**.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
