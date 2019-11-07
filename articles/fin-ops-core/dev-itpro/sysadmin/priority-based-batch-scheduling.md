---
# required metadata

title: Priority-based batch scheduling
description: This topic provides information about the functionality for priority-based batch scheduling.
author: peakerbl
manager: AnnBe
ms.date: 11/07/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 62333
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: hasaid
ms.search.validFrom: 2019-10-29
ms.dyn365.ops.version: Platform Update31

---

# Priority-based batch scheduling 

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

In Platform update 31, you can turn on the **Batch priority-based scheduling** feature in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). Priority-based scheduling decouples batch groups from the batch server. Instead, relative scheduling priorities are used to determine the order that tasks are run in across available batch servers.

> [!IMPORTANT]
> This feature is available only in a restricted preview as part of Platform update 31.

A scheduling priority is defined for batch groups, but it can be overridden for specific batch jobs. The scheduling priority classifications are used to declare relative priorities and to determine the processing order of jobs and business processes. The available values for the scheduling priority are **Low**, **Normal**, **High**, **Critical**, and **Reserved capacity**. **Reserved capacity** represents the highest priority.

Additional functionality is planned for future updates.

Priority-based batch scheduling requires that you turn on the **Batch framework contention reduction** feature in Feature management.

The following procedures explain how to work with batch groups, jobs, and tasks, when the **Priority based batch scheduling** feature is turned on.

## Batch groups

Batch groups are now used only to logically group jobs and to set the default scheduling priority. Here are some examples of batch groups:

- Jobs that belong to a specific business process
- Jobs that have the same execution recurrence (for example every night, every week, or every month)
- Jobs that have the same priority

### Create a batch group

1. Go to **System administration** \> **Setup** \> **Batch group**.
2. Select **New** to create a batch group.
3. In the **Group** field, enter a unique name for the batch group.
4. In the **Description** field, enter a value.
5. In the **Scheduling priority** field, select the default scheduling priority for the batch jobs in the batch group.
6. Select **Save**.

## Batch jobs

A batch job is a group of tasks that are submitted for automatic processing. Batch jobs are run by using the security credentials of the user who is selected in **Run by** field. Use the following procedure to create a batch job.

### Create a batch job

1. Go to **System administration** \> **Inquiries** \> **Batch jobs**.
2. Select **New** to create a batch job.
3. In the **Job description** field, enter a value.
4. In the **Scheduled start date/time** field, enter a date and time.
5. In the **Run by** field, select the users whose security credentials will be used when the batch job is run. For more information, see [Batch manager security role](runby.md).
6. Optional: In the **Monitoring category** field, select a value to make it easier to identify the types of jobs during monitoring.
7. Optional: Set the **Critical job** option to **Yes**. For more information, see [Import users in bulk](tasks/import-bulk-users.md) or [Configure the Workflow message processing batch job as critical](../../fin-ops/organization-administration/workflow-batch-job-critical.md).
8. In the **Batch group** field, select the batch group for the job.
9. Optional: Set the **Scheduling priority is overridden** option to **Yes**, to make the **Job scheduling priority** field available.
10. Optional: In the **Job scheduling priority** field, select a default priority that differs from the default priority that is defined for the batch group.
11. Optional: In the **Active period** field, select the time range when the batch job can be run. For more information, see [Active batch periods](activeperiod.md).
12. Select **Save**.

### Add a task to a batch job

1. On the **Batch job** page, in the **Batch tasks** section, select **New**.
2. In the **Task description** field, enter a value.
3. In the **Company accounts** field, select the company that the task will be run in.
4. In the **Class name** field, select the process to run.
5. Select **Save**.
6. Expand the **Batch task detail** FastTab to add more settings for the batch task, or to add constraints.
7. On the **General** tab, set the **Ignore task failure** option to **Yes** to specify that failure of the task should not cause the job to fail.
8. In the **Maximum retries** field, specify the number of times that a task should be retried before it's considered to have failed.
9. Set the **Private** option to **Yes** if the task should be run only by the user who created the job. This option is applicable only to client tasks.
10. On the **Constraints** tab, select **New** if the execution of the selected task should be dependent on the status of a preceding task for the job.
11. In the **Task ID** field, select the preceding task.
12. In the **Expected status** field, select the status that the preceding task must reach before the current task can run.
13. Select **Save**.

> [!NOTE]
> If you enter more than one condition/constraint, and if all conditions must be met before the dependent task can run, select **All** as the condition type. If the dependent task can run after any of the conditions has been met, select **Any** as the condition type.
