---
title: Cancel a running batch job
description: Learn about how to cancel a batch job that is running, including overviews on aborting tasks in a batch job and enhanced batch abort features.
author: karimelazzouni
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/21/2026
ms.reviewer: johnmichalak
audience: IT Pro 
ms.search.region: Global
ms.search.validFrom: 2019-05-08
ms.search.form: 
ms.dyn365.ops.version: Platform update 27
ms.assetid: 6135bcf7-bf8f-42ae-b2c6-458f6538e6a4
ms.custom: sfi-image-nochange
---

# <a id="legacy-abort"></a>Cancel a running batch job

[!include [banner](../includes/banner.md)]

## Cancel a batch job

> [!NOTE]
> You can't cancel system jobs.

If you need to cancel a running batch job, change its status to **Canceling**. The batch job stops picking up new tasks. The status of tasks in the batch job that didn't start changes to **Didn't run**, and the status of tasks that started changes to **Canceling**. The status of a task doesn't change until the task terminates gracefully (that is, it either completes or errors out).

To cancel a running batch job, follow these steps:

1. On the **Batch job** page, on the Action Pane, select **Change status**.
1. In the **Select new status** dialog box, under **Select new status**, select **Canceling**.
1. Select **OK**.

:::image type="content" source="./media/cancelling-a-batch-job.png" alt-text="Screenshot of Changing the status of a selected batch job to Canceling.":::

The following illustration shows an example of a batch job and its tasks after the batch job is canceled.

:::image type="content" source="./media/cancelled-batchjob.png" alt-text="Screenshot of Canceled batch job and its tasks.":::

## Abort the tasks in a batch job

Sometimes, the tasks in a batch job can't terminate gracefully. Therefore, the status of the batch job remains **Canceling** while the system waits for the graceful termination. In these cases, the system administrator or batch job manager can abort all the tasks that are in **Canceling** status for a batch job. The **Abort** command forces the tasks in the batch job to immediately stop execution.

> [!IMPORTANT]
> - Aborting a running process is inherently unsafe, and therefore should be used with caution. It can cause data corruption that can, in turn, cause either orphaned or incomplete data. Use this action only to mitigate other problems that the running tasks cause.
> - This action can't stop the execution of tasks that are stuck in an unmanaged wait. Examples include tasks that are stuck because of SQL deadlocks or DIXF-related tasks. In such cases, tasks are aborted after they're no longer in an unmanaged wait.

To abort all the tasks that are in **Canceling** status for a batch job, follow these steps:

1. On the **Batch job** page, on the **Batch tasks** FastTab, select **Abort**.
1. A message box prompts you to confirm that you want to abort all running tasks for the batch job. Select **Yes**.

:::image type="content" source="./media/aborting-a-batch-job.png" alt-text="Screenshot of Aborting the tasks in a batch job.":::

### Enhanced batch abort feature

> [!IMPORTANT]
> - In release 10.0.31, a drain period was added. The appropriate batch servers won't pick up new tasks for up to 15 minutes after you use the **Enhanced batch abort** feature. This drain period gives other tasks that are in an **Executing** state on the batch servers time to complete correctly. When either no more tasks in an **Executing** state remain on those servers or 15 minutes pass, the batch servers restart.
> - This feature is enabled by default starting 10.0.38 (PU 62).
> - This feature is mandatory starting 10.0.39 (PU 63).

To use the **Enhanced batch abort** feature, enable it in the [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) workspace. After you enable this feature, the **Abort** command restarts all the batch servers that are currently running tasks of the batch job that you're trying to abort. Other tasks might also be running on those servers. The restart interrupts those tasks.

Because the servers restart, the **Enhanced batch abort** feature makes the functionality more resilient to the limitations of the **Abort** command. It also ensures that the tasks of the batch job that you're trying to cancel are truly interrupted.

To abort all the tasks that are in **Canceling** status for a batch job when the **Enhanced batch abort** feature is enabled, follow these steps:

1. On the **Batch job** page, on the **Batch tasks** FastTab, select **Abort**.
1. The **Abort batch job** dialog box lists other batch jobs that might be disrupted if you continue. To confirm that you want to continue, select **Yes**.

:::image type="content" source="./media/enhanceabort-a-batchjob.png" alt-text="Screenshot of Aborting the tasks in a batch job when the Enhanced batch abort feature is enabled.":::

If you don't want to cancel other running batch tasks on the batch servers, and you prefer the old behavior where only the tasks of the batch job are canceled instead of all running jobs, disable the **Enhanced batch abort** feature in the **Feature management** workspace. Then try to [abort a batch job](#abort-the-tasks-in-a-batch-job) again.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
