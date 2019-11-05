---
# required metadata

title: Priority based batch scheduling
description: This topic provides an overview of batch processing.
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

# Priority based batch scheduling 

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

With the release of Platform update 31, it is possible to enable **Batch priority-based scheduling**, in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). Priority based scheduling decouples batch groups from batch server and instead uses relative scheduling priorities to determine the sequence in which tasks are executed across available batch servers. This feature is currently available for customers on a restricted basis.

**Scheduling priority** is defined on batch groups and can optionally be overridden on jobs. It is used to declare relative priorities of jobs/business processes. The available values for Scheduling Priority are: Low, Normal, High, Critical, and Reserved Capacity. The priority classification is used to determine the processing sequence when a job is scheduled to be processed. **Reserved capacity** represents the highest priority and additional functionality is planned for future updates.

> [!IMPORTANT]
> This featue is only available in restricted preview as part of Platform update 31.

**Priority based batch scheduling** requires that also the **Batch framework contention reduction** feature is enabled in **Feature Management**.

The following procedures describes the how to work with Batch groups, jobs and tasks, when the **Priority based batch scheduling** is enabled.

## Batch groups
Batch groups are now only used to logically group jobs and to set the default Scheduling priority. Examples of batch groups include the following:

- Jobs that belong to a specific business process
- Jobs that share the same execution recurrence—for example every night, every week, or every month
- Jobs that share the same priority

Use the following procedure to create a batch group.

### Create a batch group

1. Go to **System administration \> Setup \> Batch group**.
2. Click **New** to create a new batch group.
3. In the **Group** field, type a name for the batch group that is unique.
4. In the **Description** field, type a value.
5. In the **Scheduling priority** field, select the default scheduling priority for the batch jobs.
6. Click **Save**.

## Batch jobs
A batch job is a group of tasks that are submitted for automatic processing. Batch jobs are run by using the security credentials of the user selected as **Run by** user. Use the following procedure to create a batch job.

### Create a batch job

1. Go to **Navigation pane \> Modules \> System administration \> Inquiries \> Batch jobs**.
2. Click **New**.
3. In the **Job description** field, type a value.
4. In the **Scheduled start date/time** field, enter a date and time.
5. In the **Run by** field, select the users whose credentials will be used during execution. For more information, see [Batch manager security role](runby.md).
6. Optionally select **Monitoring category**, that can be used to easier identify types of jobs during monitoring.
7. Optionally set **Critical job** field to Yes. For more information, see [Import users in bulk](tasks/import-bulk-users.md) or [Configure the Workflow message processing batch job as critical](../../fin-ops/organization-administration/workflow-batch-job-critical.md).
8. In the **Batch group** field, select the batch group for the job.
9. Optionally set **Scheduling priority is overridden** to Yes, to enable the **Job scheduling priority** field.
10. In the **Job scheduling priority** field, select a different default priority than used for the Batch Group.
11. In the **Active period** field, optionally select a time range for when the batch job can be executed. For more information see [Active batch periods](activeperiod.md).
12. Click **Save**.

### Add a task to a batch job

1. In the **Batch job** form, go to the **Batch tasks** section and click New.
2. In the **Task description** field, type a value.
3. In the **Company accounts** field, select the company in which the task will run.
4. In the **Class name** field, select the applicable process to be executed.
5. Click **Save**.
6. Expand the **Batch task detail** section to add additional settings for the batch task or to add constraints:
7. Go to the **General** tab to add additional settings for the task.
8. Set **Ignore task failure** to Yes, if the failure of the task should not cause the job to fail.
9. In the **Maximum retries** field to specify the number of times that a task should be retried before it is considered to have failed.
10. Set the **Private** field to Yes, if the task should only be run by the user who created the job. Only applicable for client tasks.
11. Go to the **Constraints tab** and click **New** to define constraint between tasks.
12. In the **Task ID** field, select the preceding task.
13. In the **Expected status** field, select the status that the preceding task must reach before the current task can run.
14. Click **Save**.

> [!NOTE]
> If you enter more than one condition, and if all conditions must be met before the dependent task can run, select a condition type of **All**. Select a condition type of **Any** if the dependent task can run after any of the conditions has been met.
