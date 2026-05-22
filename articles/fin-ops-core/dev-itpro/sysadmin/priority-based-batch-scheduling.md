---
title: Priority-based batch scheduling
description: Learn about the functionality for priority-based batch scheduling, including outlines on batch groups and batch jobs.
author: matapg007
ms.author: johnmichalak
ms.topic: article
ms.date: 03/13/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-10-29
ms.search.form: 
ms.dyn365.ops.version: Platform Update31
---

# Priority-based batch scheduling 

[!include [banner](../includes/banner.md)]

In Platform update 31, you can turn on the **Batch priority-based scheduling** feature in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). Priority-based scheduling decouples batch groups from the batch server and lets you define priorities for batch groups. It's no longer necessary to assign batch jobs to batch servers. Instead, relative scheduling priorities based on business requirements are used to determine the order in which tasks are run across available batch servers.

> [!IMPORTANT]
> - This feature is available with version 10.0.25.
> - This feature is enabled by default for all new instances with version 10.0.28 (PU 52).
> - This feature is enabled by default for all existing instances with version 10.0.36 (PU 60).
> - This feature is required for all instances starting with version 10.0.38 (PU 62).

You define a scheduling priority for batch groups, but you can override it for specific batch jobs. Use the scheduling priority classifications to declare relative priorities and determine the processing order of jobs and business processes. The available values for the scheduling priority are **Low**, **Normal**, **High**, **Critical**, and **Reserved capacity**. 

**Normal** is the default value and is applied to all existing batch groups when you turn on the feature. **Reserved capacity** represents the highest priority. In Platform update 32 and later versions, you can use it to dedicate reserved capacity for jobs. For more information, see the [Set the batch reserved capacity level](priority-based-batch-scheduling.md#set-the-batch-reserved-capacity-level) section later in this article.

For example, suppose there are 100 batch tasks for processing. Forty tasks come from the reserved queue, 30 from the critical queue, 15 from the high queue, 10 from the normal queue, and five from the low queue. The system doesn't select the priority-based order of execution for processing. Instead, it uses the weight of the batch tasks from each priority.

| Priority | Weight |
|----------|--------|
| Low | 5% |
| Normal | 10% |
| High | 15% |
| Critical | 30% |
| Reserved capacity | 40% + Dedicated X threads |

> [!NOTE]
> Because the schedule priority is set to **Normal** for all existing batch groups when you turn on the feature, plan and update the scheduling priority for each batch group so that it represents the relative priorities according to business requirements for the related batch jobs and their related business processes.

Platform update 32 includes upgrade support for existing batch jobs. For more information, see the [Automatic batch group migration for batch jobs](priority-based-batch-scheduling.md#automatic-batch-group-migration-for-batch-jobs) section later in this article.

Advantages of priority-based batch scheduling include:

- It introduces priorities up to the batch job level.
- It serves as a prerequisite for near-zero downtime servicing.
- It doesn't tie a batch job to a particular server.

The following steps explain how to work with batch groups, jobs, and tasks when you turn on the **Priority-based batch scheduling** feature.

1. **Identify** – Identify the priorities of the existing batch jobs.
1. **Enable** – Enable priority-based scheduling in Feature management. By default, all existing batch jobs have the **Normal** priority.
1. **Update** – Selectively update the priorities for jobs that aren't **Normal** priority (such as **Reserved capacity**, **Critical**, **High**, and **Low**).
1. **Apply** – Apply **Reserved capacity** if you need to dedicate capacity for some jobs beyond the priority.

## Batch groups

Use batch groups to logically group jobs and set the default scheduling priority. Here are some examples of batch groups:

- Jobs that belong to a specific business process
- Jobs that have the same execution recurrence, such as every night, every week, or every month
- Jobs that have the same priority

### Create a batch group

1. Go to **System administration** > **Setup** > **Batch group**.
1. Select **New** to create a batch group.
1. In the **Group** field, enter a unique name for the batch group.
1. In the **Description** field, enter a value.
1. In the **Scheduling priority** field, select the default scheduling priority for the batch jobs in the batch group.
1. Select **Save**.

## Batch jobs

A batch job is a group of tasks that you submit for automatic processing. The batch job runs by using the security credentials of the user you select in the **Run by** field. Use the following procedure to create a batch job.

### Create a batch job

1. Go to **System administration** > **Inquiries** > **Batch jobs**.
1. Select **New** to create a batch job.
1. In the **Job description** field, enter a value.
1. In the **Scheduled start date/time** field, enter a date and time.
1. In the **Run by** field, select the users whose security credentials are used when the batch job runs. For more information, see [Batch manager security role](runby.md).
1. (Optional) In the **Monitoring category** field, select a value to make it easier to identify the types of jobs during monitoring.
1. (Optional) Set the **Critical job** option to **Yes**. For more information, see [Import users in bulk](../../fin-ops/sysadmin/import-bulk-users.md) or [Configure the Workflow message processing batch job as critical](../../fin-ops/organization-administration/workflow-batch-job-critical.md).
1. In the **Batch group** field, select the batch group for the job.
1. (Optional) Set the **Scheduling priority is overridden** option to **Yes**, to make the **Job scheduling priority** field available.
1. (Optional) In the **Job scheduling priority** field, select a default priority that differs from the default priority that's defined for the batch group.
1. (Optional) In the **Active period** field, select the time range when the batch job can run. For more information, see [Active batch periods](activeperiod.md).
1. Select **Save**.

### Add a task to a batch job

1. On the **Batch job** page, in the **Batch tasks** section, select **New**.
1. In the **Task description** field, enter a value.
1. In the **Company accounts** field, select the company that the task runs in.
1. In the **Class name** field, select the process to run. Classes appear in the list only if the **CanGoBatchJournal** property is turned on.
1. Select **Save**.
1. Expand the **Batch task detail** FastTab to add more settings for the batch task, or to add constraints.
1. On the **General** tab, set the **Ignore task failure** option to **Yes** to specify that failure of the task shouldn't cause the job to fail.
1. In the **Maximum retries** field, specify the number of times that a task should be retried before it's considered to have failed.
1. Set the **Private** option to **Yes** if the task should run only by the user who created the job. This option applies only to client tasks.
1. On the **Constraints** tab, select **New** if the execution of the selected task should be dependent on the status of a preceding task for the job.
1. In the **Task ID** field, select the preceding task.
1. In the **Expected status** field, select the status that the preceding task must reach before the current task can run.
1. Select **Save**.

    > [!NOTE]
    > If you enter more than one condition or constraint, and if all conditions must be met before the dependent task can run, select **All** as the condition type. If the dependent task can run after any of the conditions is met, select **Any** as the condition type.

1. If the batch task supports input parameters, select **Parameters**, and then set task-specific parameters.
1. Select **OK**, and then select **Save**.

## Set the batch reserved capacity level

1. Go to **System administration** > **Setup** > **System parameters**.
1. On the **Batch global settings** tab, in the **Batch reserved capacity level** field, select the reserved capacity level to use for batch jobs that have **Reserved capacity** priority:

    - **No reserved capacity** – This value is the default value.
    - **Low reserved capacity** – 10 percent of the cumulative batch threads are reserved.
    - **Medium reserved capacity** – 15 percent of the cumulative batch threads are reserved.
    - **High reserved capacity** – 25 percent of the cumulative batch threads are reserved.

    For example, there are 10 Batch Application Object Server (AOS) instances, each of which is configured with 12 threads. Therefore, the cumulative number of batch threads is 120. If you configure the batch-reserved capacity level as high reserved capacity, 25 percent of the cumulative threads (that is, 30 threads) are dedicated to processing batch tasks from the reserved queue. These 30 threads are allocated among three AOS instances. Therefore, three of the 10 AOS instances are dedicated to processing the reserved queue. If there are no batch tasks to process under reserved capacity, those three AOS instances are idle.

    > [!NOTE]
    > Sample values are for illustration only. The actual reserved capacity depends on the configuration of the batch server and the number of available batch threads at any given point. Don't configure the dedicated X threads unless there's a use case where there's a constant number of batch tasks to run under the reserved category.

1. Select **Save**.

> [!NOTE]
> Any reserved capacity is exclusive to batch jobs that have **Reserved capacity** priority. The reserved capacity isn't available for batch jobs that have other priorities, even if there's idle reserved capacity.

A new internal system batch job, **System job to clean up expired batch heartbeat records**, cleans up the new BatchHeartbeatTable table. This batch job has the class name **SysCleanupBatchHeartbeatTable**. BatchHeartbeatTable is an internal monitoring table that's used to determine, configure, and distribute reserved capacity threads among online nodes.

## Best practices

- Adjust the priority so that all batch jobs don't have the same priority. For example, don't set the priority for all batch jobs to **High** or **Critical**. Consider the following distribution when configuring batch priorities.

    | Priority | Possible distribution percentage of batch jobs, excluding Reserved capacity |
    |----------|--------|
    | Low | 10% to 50% |
    | Normal | 15% to 35% |
    | High | 15% to 35% |
    | Critical | 10% to 30% |

- Schedule batch jobs so that there's always a mix of jobs with different priorities around the clock. For example, don't schedule all batch jobs with the **Normal** priority in the morning, jobs with the **High** priority in the afternoon, jobs with the **Critical** priority in the evening, and jobs with the **Low** priority at night.
- When you use the reserved queue with **Reserved capacity** priority, it gives the experience as having dedicated resources for batch job. If you don't require this behavior, don't allocate batch jobs to the **Reserved capacity** priority.
- Priorities don't stack rank tasks against each other. Instead, priorities determine the probability by which a task is picked for execution.
- Keep the number of threads the same across the servers to eliminate performance degradation.
- Implement the **BatchRetryable** interface for batch tasks to prevent problems from SQL Server transient errors. For more information, see [Retry for SQL transient connection errors](retryable-batch.md#retry-for-sql-transient-connection-errors).
- Batch tasks should be idempotent. Regardless of how many times you run them, you achieve the same result. Set up tasks with a retry count that's more than 0 (zero). This setting enables the system to recover from any kind of transient errors that might occur during job execution. For more information, see [Retry for SQL transient connection errors](retryable-batch.md#retry-for-sql-transient-connection-errors).
- For larger workloads, break them down into smaller workloads or tasks, so that they run and complete in 10 minutes or less.
- Keep SQL Server transactions in batch tasks as small as possible in duration so they don't cause SQL Server blocking that might impact performance of other batch jobs and user activity.
- Use more than one batch group to take advantage of priority-based batch scheduling, and use different priorities at a batch-group level.
- When you debug batches in user acceptance testing (UAT) by connecting to a development machine, disable the rest of the batch server by running the following script. By using this script, you ensure that all the batches run on the development machine. 

    ```
    UPDATE ssc
    SET ssc.enablebatch = 0
    FROM dbo.sysserverconfig ssc
    WHERE ssc.serverid = '<servername Tier2 batch server>'   
    ```

## Automatic batch group migration for batch jobs

When you turn on this feature, the system duplicates batch group information from the task to the job. The system assigns a batch group to a job based on the batch group that most tasks in the job use.

A new system batch job, **System job to seed batch group associations to batch jobs**, manages the migration. This batch job uses the class name **SysMigrateBatchGroupsForPriorityBasedScheduling**.

The system runs the batch job every day at 1:00 AM, even if the **Batch priority-based scheduling** feature is turned off. The batch job migrates the delta of applicable batch jobs since the last execution.

The system also runs the batch job when you turn on the feature, to migrate any batch jobs since the last execution. The system notifies you with a reference to the ID of the migration batch job.

Review the automatic batch group assignment after you turn on the feature and the migration finishes. To facilitate this review, the **Batch group** field for tasks is read-only. To support backward compatibility, the system propagates the value of this field from the job when you add new batch tasks.

Don't assign a high or critical priority to all batch jobs.

## Batch concurrency

In Platform update 58, you can turn on the **Batch concurrency control** feature in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). This feature lets you set a limit on the number of tasks that can run concurrently in a specific batch job. Therefore, it helps you prioritize your batch jobs and optimize the use of your resources. For example, by limiting the number of tasks for a low-priority batch job, you can avoid overloading the system and affecting the performance of other, higher-priority batch jobs.

> [!IMPORTANT]
> - This feature is available with version 10.0.34 (PU 58) as **(Preview) Batch concurrency control** .
> - This feature is generally available starting with 10.0.38 (PU 62).
> - This feature is enabled by default with version 10.0.39 (PU 63).
> - This feature is mandatory starting with version 10.0.41 (PU 65).

### Prerequisites

As a prerequisite, enable the **Batch Priority Based Scheduling** feature in the environment.

### Why do you need batch concurrency control?

Batch jobs commonly perform background tasks like data processing, reporting, or integration. However, if too many batch tasks run at the same time, they can cause performance problems or resource contention. For example, one of your batch jobs runs every hour and processes a large amount of data. Another batch job runs every 15 minutes and has high priority. Without batch concurrency control, you can't ensure that the high-priority batch job gets enough resources to run smoothly and on time.

> [!NOTE]
> - If you don't need concurrency control, set the **Max concurrency** field on the **Batch group** page to **0** (zero).
> - Don't use this feature for batch jobs that have more than 5,000 concurrent, ready-to-run tasks because it might degrade performance of batch scheduling.
> - If the **Max concurrency** value exceeds the total number of batch threads that are available in the environment, the feature is ineffective.
> - The **Max concurrency** value applies to each batch job in the group. It isn't the cumulative value for the batch group.

### How do you use batch concurrency control?

To use batch concurrency control, turn on the **(Preview) Batch concurrency control** feature in Feature management. Then go to **Batch groups**, and select a batch group that you want to apply the concurrency limit to. The **Batch group** page has a new field named **Max concurrency**. Enter a positive integer that represents the maximum number of tasks that can run at the same time for each batch job in the selected batch group. This setting applies to all the batch jobs that belong to the batch group.

For example, if you set the **Max concurrency** value to **10** for a batch group, only 10 tasks from a batch job in that batch group can run concurrently. If more than 10 tasks for the job are waiting to run, they're queued until some of the running tasks complete.

The **Max concurrency** value doesn't affect the number of tasks that can run across different batch groups. It applies only to the tasks in the same batch group. If you don't need concurrency control, set it to **0** (zero), which is the default value.

If you want to completely pause all batch jobs in the batch group, set the **Max concurrency** field to **-1**. Any tasks that the system picked before you set the value to **-1** continue to run.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
