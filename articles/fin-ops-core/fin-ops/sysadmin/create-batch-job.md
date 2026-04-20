---
title: Create a batch job
description: Learn about how to create batch jobs, which are groups of tasks that are submitted to an Application Object Server (AOS) instance for automatic processing.
author: matapg007
ms.author: matgupta
ms.topic: how-to
ms.date: 03/10/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: BatchJob, SysRecurrence, BatchAlerts
ms.dyn365.ops.version: Version 7.0.0
---

# Create a batch job

[!include [banner](../../../finance/includes/banner.md)]

A batch job is a group of tasks that you submit to an Application Object Server (AOS) instance for automatic processing. The batch job runs by using the security credentials of the user who created the job. Use the following procedure to create a batch job. The demo data company used to create this procedure is USMF.

## Create the batch job

1. Go to **System administration** > **Inquiries** > **Batch jobs**.
1. Select **New**.
. In the **Job description** field, enter a description of the batch job.
1. In the **Scheduled start date/time** field, enter the date and time when the batch job should run.
1. Select **Save**.

## Create a recurrence

1. On the Action Pane, select **Batch job**.
1. Select **Recurrence**. Use these options to enter a range and pattern for the recurrence.
1. Select **OK**.

> [!NOTE]
> All recurring batch jobs automatically return to the waiting state, regardless of whether they fail or succeed. This behavior ensures that recurring jobs can complete any pending work during the next run if the previous run failed. This functionality can be enabled only if the batch job's recurrence conditions are still valid. For example, the batch job must have a remaining recurrence count or a recurrence end date that hasn't passed.

## Add alerts

1. On the Action Pane, select **Batch job**.
1. Select **Alerts**. Indicate if you want alert messages sent when the batch job ends, has an error, or is canceled. Then specify if you want the alerts to be displayed as pop-up messages.
1. Select **OK**.

## Add a task to a batch job

1. On the **Batch jobs** page, select **View tasks**.
1. Select **Ctrl+N** to create a task.
1. Enter a description of the batch task.
1. In the **Company accounts** field, select the company database that the task should run in.
1. In the **Class name** field, select the process that the task should run. 
1. As appropriate, select a batch group for the task.

    You must assign client tasks to a batch group. They're automatically assigned to the default batch group (also known as the Empty batch group).

1. Select **Ctrl+S** to save the task.
1. To make the selected task dependent on another task in the job, select the **Has conditions** grid, and then follow these steps for each condition that you want to define:

    1. Select **Ctrl+N** to create a condition.
    1. Select the task ID of the parent task.
    1. Select the status that the parent task must reach before the dependent task can run.
    1. Select **Ctrl+S** to save the condition.

    If you define more than one condition, and if *all* the conditions must be met before the dependent task can run, select a condition type of **All**. If the dependent task can run after *any* of the conditions is met, select a condition type of **Any**.

1. Select how to handle task failures. To ignore the failure of a specific task, on the **General** tab, select the **Ignore task failure** option for that task. If you select this option, failure of the task doesn't cause the job to fail. You can also use the **Maximum retries** field to specify the number of times that a task should be retried before it's considered to have failed. As a best practice, don't set the **Maximum retries** field to a value that's more than **5**.

    For more information about batch retries, see [Enable batch retries](../../dev-itpro/sysadmin/retryable-batch.md).

## Batch job history

1. Under **Batch Jobs** in **Save Jobs to History**, select one of three options: **Always**, **Errors Only**, or **Never**.

    - **Always** – The history for the job is always created, regardless of the terminal status of the batch job.
    - **Errors Only** – The history for the job is created only if the job ends in the error state.
    - **Never** – No history is created for the batch job.

1. If the batch job has many batch tasks, set this field to **Errors Only** or **Never**.

> [!IMPORTANT]
> Starting with release 10.0.39, if the batch job has more than 5,000 batch tasks, the corresponding job history saves only the first 2,500 tasks. It prefers tasks with status in the following order: **Error** \> **Cancelled** \> **Finished** \> **Not Run**. This measure prevents blocking batch-related tables that large jobs might cause.

## Adjust batch job status

1. Go to **System administration** \> **Inquiries** \> **Batch jobs**.
1. Select the appropriate batch job.
1. On the Action Pane, select **Batch job** \> **Functions** \> **Change status**.
1. Select the appropriate status:

    - **Withhold** – Set the batch job as **withhold** so it's withheld from the batch job scheduler. Equivalent to *stop*.
    - **Waiting** – Set the batch job as **waiting** so it's waiting to be picked up by the batch job scheduler. Equivalent to *go*.

1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
