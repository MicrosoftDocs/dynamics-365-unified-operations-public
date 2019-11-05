---
# required metadata

title: Priority-based batch scheduling
description: This topic provides information about the functionality for priority-based batch scheduling.
author: peakerbl
manager: AnnBe
ms.date: 11/05/2019
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

With the release of Platform update 31, you can enable **Batch priority-based scheduling**, in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). Priority-based scheduling decouples batch groups from batch server and instead uses relative scheduling priorities to determine the sequence in which tasks are executed across available batch servers. This feature is currently available for customers on a restricted basis.

Scheduling priority is defined on batch groups with the option to be overridden on jobs, and is used to declare relative priorities of jobs and business processes. The available values for Scheduling priority are, Low, Normal, High, Critical, and Reserved capacity. The priority classification is used to determine the processing sequence when a job is scheduled to be processed. Reserved capacity represents the highest priority. Additional functionality is planned for future updates.

> [!IMPORTANT]
> This featue is only available in a restricted preview as part of Platform update 31.

Priority-based batch scheduling requires that you enable the **Batch framework contention reduction** feature in **Feature Management**.

The following procedures describe how to work with batch groups, jobs, and tasks, when **Priority based batch scheduling** is enabled.

## Batch groups
Batch groups are now only used to logically group jobs and to set the default scheduling priority. Examples of batch groups include the following:

- Jobs that belong to a specific business process.
- Jobs that share the same execution recurrence. For example every night, every week, or every month.
- Jobs that share the same priority.

### Create a batch group

1. Go to **System administration** \> **Setup** \> **Batch group**.
2. Select **New** to create a new batch group, and in the **Group** field, type a unique name for the batch group.
3. In the **Description** field, type a value.
4. In the **Scheduling priority** field, select the default scheduling priority for the batch jobs.
5. Select **Save**.

## Batch jobs
A batch job is a group of tasks that are submitted for automatic processing. Batch jobs are run by using the security credentials of the user selected as **Run by** user. Use the following procedure to create a batch job.

### Create a batch job

1. Go to **System administration** \> **Inquiries** \> **Batch jobs**.
2. Select **New**, and in the **Job description** field, type a value.
3. In the **Scheduled start date/time** field, enter a date and time.
4. In the **Run by** field, select the users whose credentials will be used when the batch job is run. For more information, see [Batch manager security role](runby.md).
5. Optional - Select **Monitoring category** to more easily identify the types of jobs during monitoring.
6. Optional - Set **Critical job** to **Yes**. For more information, see [Import users in bulk](tasks/import-bulk-users.md) or [Configure the Workflow message processing batch job as critical](../../fin-ops/organization-administration/workflow-batch-job-critical.md).
7. In the **Batch group** field, select the batch group for the job.
8. Optional- Set **Scheduling priority is overridden** to **Yes**, to enable the **Job scheduling priority** field.
9. In the **Job scheduling priority** field, select a different default priority than what is used for the batch group.
10. Optional - In the **Active period** field, select a time range for when the batch job can be run. For more information see [Active batch periods](activeperiod.md).
11. Select **Save**.

### Add a task to a batch job

1. On the **Batch job** form, in the **Batch tasks** section, select **New**.
2. In the **Task description** field, type a value.
3. In the **Company accounts** field, select the company in which the task will run.
4. In the **Class name** field, select the applicable process to be run, and then select **Save**.
5. Expand the **Batch task detail** section to add additional settings for the batch task or to add constraints.
6. On the **General** tab, set **Ignore task failure** to **Yes**, if the failure of the task should not cause the job to fail.
7. In the **Maximum retries** field, specify the number of times that a task should be retried before it is considered to have failed.
8. Set the **Private** field to **Yes**, if the task should only be run by the user who created the job. This is only applicable for client tasks.
9. On the **Constraints tab**, select **New** to define a constraint between tasks.
10. In the **Task ID** field, select the preceding task.
11. In the **Expected status** field, select the status that the preceding task must reach before the current task can run.
12. Select **Save**.

> [!NOTE]
> If you enter more than one condition, and if all conditions must be met before the dependent task can run, select a condition type of **All**. Select a condition type of **Any** if the dependent task can run after any of the conditions have been met.
