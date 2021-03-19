---
# required metadata

title: Reset stuck batch jobs
description: This topic explains how to resolve resolve issues with batch jobs that are stuck.
author: andreabichsel
manager: tfehr
ms.date: 03/19/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: BatchJob, BatchJobEnhanced
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2021-03-19
ms.dyn365.ops.version: Platform update 42
---


# Reset stuck batch jobs

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

## Issue

Microsoft Dynamics 365 Human Resources can experience issues with batch jobs that are stuck in either an "Executing" or "Cancelling" state, and do not complete execution.

## Resolution

When a batch job is stuck in an "Executing" or "Cancelling" state, you can reset the status of the job by forcing the cancellation of the job. Once the batch canceled, you can reset the batch by setting it to a "Waiting" status.

1. In the **System administration** workspace, select the **Links** page, and select **Batch jobs**.

2. On the **Batch job** list page, select the job that needs to be reset. 

3. On the action ribbon, select the **Force cancel** action, and confirm the action.

   > [!NOTE]
   > The **Force cancel** action is only available when the selected batch job has a status of either "Executing" or "Cancelling".

4. On the action ribbon, select **Change status**.

5. On the **Select new status** page, select **Waiting**, and select **OK**.

   ![Select a new batch job status](./media/hr-admin-reset-batch-status.png)

When the batch job status has been set to "Waiting", it will be picked up again for execution in the next scheduled batch run.

## Additional resources

[Optimize performance by scheduling batch jobs after hours](hr-admin-troubleshooting-batch-jobs.md)
[Optimize performance with auto cleanup tasks](hr-admin-troubleshooting-batch-history.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
