---
# required metadata

title: Optimize performance by scheduling batch jobs after hours
description: This article explains how to resolve performance issues with Microsoft Dynamics 365 Human Resources by scheduling long-running batch jobs after hours.
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
ms.search.validFrom: 2020-06-23
ms.dyn365.ops.version: Platform update 24
---


# Optimize performance by scheduling batch jobs after hours

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



## Issue

Microsoft Dynamics 365 Human Resources can experience performance issues if long-running batch jobs run during typical business hours.

## Resolution

Schedule the following batch jobs during off hours. We also recommend reviewing the frequency of batch jobs that run frequently. If possible, reduce the recurrence of the batch job. In many cases, the default frequency is sufficient.

The following batch jobs should run at night or after hours. Check the time zone for these recurring batch jobs. Some batch jobs might use Pacific Standard Time (PST).

| Batch job | Default occurrence |
| --- | --- |
| Batch job history cleanup | One time per month |
| Export staging cleanup | One time per day |
| Common Data Service integration missed request sync | One time per day |
| Database compression system job that needs to run regularly during off hours | One time per day |
| Database index rebuild system job that needs to run regularly during off hours | One time per day |

1. In Human Resources, select **System administration**.

1. In the **Search** bar, search for one of the preceding batch jobs.

1. Select **Run in the background**, and then select **Recurrence**.

   :::image type="content" source="media/talent-batch-history-cleanup-recurrence.png" alt-text="Screenshot of setting the recurrence for a batch job.":::

1. Under **Define recurrence**, set the **Start date** and **Start time** to occur during off hours or the weekend. Select **No end date**. 

   :::image type="content" source="media/talent-batch-history-cleanup-define-recurrence.png" alt-text="Screenshot of defining the recurrence start date and time.":::

1. Select **OK**.

1. If needed, change any other parameters under **Run in the background**, and then select **OK**.

## Additional resources

[Optimize performance with auto cleanup tasks](hr-admin-troubleshooting-batch-history.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
