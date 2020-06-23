---
# required metadata

title: Optimize performance with batch jobs
description: This article explains how to resolve some performance issues with Microsoft Dynamics 365 Human Resources scheduling long running batch jobs "after hours".
author: andreabichsel
manager: AnnBe
ms.date: 06/21/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

# ms.search.form: BatchJob, BatchJobEnhanced
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Core, Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-06-25
ms.dyn365.ops.version: Platform update 24
---


# Optimize  performance issues with Microsoft Dynamics 365 Human Resources scheduling long running batch jobs "after hours".

**Issue**

Microsoft Dynamics 365 Human Resources can experience performance issues if long running batch jobs are running during normal business hours.

**Resolution**

Schedule the following batch jobs during off hours. We also recommend reviewing the frequency of batch jobs that run frequently. If possible reduce the reoccurance of the batch jobs. In many cases the default frequency is sufficient system.


The following batch jobs should be validated that they are running at night/after hours.
Verify the Time zone on these reoccurring batch jobs as some of these may be running on the Pacific Time Zone.

 - Batch job history clean-up (By default this runs 1 time per month)
 - Export Staging cleanup (By default this job runs 1 time per day) 
 - Common Data Service integration missed request sync (By default runs 1 time per day) 
 - Database compression system job that needs to regularly run at off hours. (By default runs 1 time per day) 
 - Database index rebuild system job that needs to regularly run at off hours. (By default runs 1 time per day) 


1. In Human Resources, select **System administration**.

2. In the **Search** bar, and search for one of the above batch jobs.

3. Select **Run in the background** and then select **Recurrence**.

   ![Set recurrence](media/talent-batch-history-cleanup-recurrence.png)

4. Under **Define recurrence**, set the **Start date** and **Start time** to occur during off-hours or the weekend, and then select **NO END DATE**. 

   ![Define recurrence start date and time](media/talent-batch-history-cleanup-define-recurrence.png)
5. Select **OK**.

6. Change any other parameters under **Run in the background** as necessary, and then select **OK**.
