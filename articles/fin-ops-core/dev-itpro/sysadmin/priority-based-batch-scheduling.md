---
# required metadata

title: Priority-based batch scheduling
description: This article provides information about the functionality for priority-based batch scheduling.
author: matapg007
ms.date: 04/06/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: matgupta
ms.search.validFrom: 2019-10-29
ms.dyn365.ops.version: Platform Update31

---

# Priority-based batch scheduling 

[!include [banner](../includes/banner.md)]

In Platform update 31, you can turn on the **Batch priority-based scheduling** feature in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). Priority-based scheduling decouples batch groups from the batch server and allows you to define priorities for batch groups. It is no longer necessary to assign batch jobs to batch servers. Instead, relative scheduling priorities based on business requirements are used to determine the order in which tasks are run across available batch servers.

> [!IMPORTANT]
> - This feature is available with version 10.0.25.
> - This feature is enabled by default for all new instances with version 10.0.28 (PU 52).
> - This feature will be enabled by default for all existing instances with version 10.0.36 (PU 60).
> - This feature will be required for all instances starting with version 10.0.38 (PU 62).

A scheduling priority is defined for batch groups, but it can be overridden for specific batch jobs. The scheduling priority classifications are used to declare relative priorities, and to determine the processing order of jobs and business processes. The available values for the scheduling priority are **Low**, **Normal**, **High**, **Critical**, and **Reserved capacity**. 

**Normal** is the default value and is applied to all existing batch groups when the feature is turned on. **Reserved capacity** represents the highest priority. In Platform update 32 and later versions, you can use it to dedicate reserved capacity for jobs. For more information, see the [Set the batch reserved capacity level](priority-based-batch-scheduling.md#set-the-batch-reserved-capacity-level) section later in this article.

For example, there are 100 batch tasks for processing. Forty tasks will be served from the reserved queue, 30 from the critical queue, 15 from the high queue, ten from the normal queue, and five from the low queue. It isn't the priority-based order of execution that will be selected for processing, but the weight of the batch tasks from each priority.

| Priority | Weight |
|----------|--------|
| Low | 5% |
| Normal | 10% |
| High | 15% |
| Critical | 30% |
| Reserved capacity | 40% + Dedicated X threads |

> [!NOTE]
> Because the schedule priority is set to **Normal** for all existing batch groups when the feature is turned on, it's important that you plan and update the scheduling priority for each batch group so that it represents the relative priorities according to business requirements for the related batch jobs and their related business processes.

Platform update 32 includes upgrade support for existing batch jobs. For more information, see the [Automatic batch group migration for batch jobs](priority-based-batch-scheduling.md#automatic-batch-group-migration-for-batch-jobs) section later in this article.

Advantages of priority-based batch scheduling include:

- Priorities are introduced up to the batch job level.
- It serves as a prerequisite for near-zero downtime servicing.
- It doesn't tie a batch job to a particular server.

The following steps explain how to work with batch groups, jobs, and tasks, when the **Priority-based batch scheduling** feature is turned on.

1. **Identify** – Identify the priorities of the existing batch jobs.
2. **Enable** – Enable priority-based scheduling in Feature management. By default, all existing batch jobs in will be given the **Normal** priority.
3. **Update** – Selectively update the priorities for jobs that are not **Normal** priority (such as **Reserved capacity**, **Critical**, **High**, and **Low**).
4. **Apply** – Apply **Reserved capacity** if there is a need to dedicate capacity for some jobs beyond the priority.

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
4. In the **Class name** field, select the process to run. Classes appear in the list only if the **CanGoBatchJournal** property is turned on.
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

14. If the batch task supports input parameters, select **Parameters**, and then set task-specific parameters.
15. Select **OK**, and then select **Save**.

## Set the batch reserved capacity level

1. Go to **System administration** \> **Setup** \> **System parameters**.
2. On the **Batch global settings** tab, in the **Batch reserved capacity level** field, select the reserved capacity level to use for batch jobs that have **Reserved capacity** priority:

    - **No reserved capacity** – This value is the default value.
    - **Low reserved capacity** – Ten percent of the cumulative batch threads are reserved.
    - **Medium reserved capacity** – Fifteen percent of the cumulative batch threads are reserved.
    - **High reserved capacity** – Twenty-five percent of the cumulative batch threads are reserved.

    For example, there are ten Batch AOS instances, each of which is configured with 12 threads. Therefore, the cumulative number of batch threads is 120. If you configure the batch-reserved capacity level as high reserved capacity, 25 percent of the cumulative threads (that is, 30 threads) will be dedicated to processing batch tasks from the reserved queue. These 30 threads will be allocated among three AOS instances. Therefore, three of the ten AOS instances will be dedicated to processing the reserved queue. If there are no batch tasks to process under reserved capacity, those three AOS instances will be idle.

    > [!NOTE]
    > Sample values are for the purpose of illustration only. The actual reserved capacity depends on the configuration of the batch server and the number of available batch threads at any given point. Don't configure the dedicated X threads unless there is a use case where there is a constant number of batch tasks to run under the reserved category.

3. Select **Save**.

> [!NOTE]
> Any reserved capacity is exclusive to batch jobs that have **Reserved capacity** priority. The reserved capacity won't be made available for batch jobs that have other priorities, even if there is idle reserved capacity.

A new internal system batch job, **System job to clean up expired batch heartbeat records**, cleans up the new BatchHeartbeatTable table. This batch job has the class name **SysCleanupBatchHeartbeatTable**. BatchHeartbeatTable is an internal monitoring table that is used to determine, configure, and distribute reserved capacity threads among online nodes.

## Best practices
- We recommend that you adjust the priority so that all batch jobs don't have the same priority. For example, don't set the priority for all batch jobs to **High** or **Critical**. The following table provides the distribution that you should consider when configuring batch priorities.

    | Priority	| Possible distribution percentage of batch jobs, excluding **Reserved capacity** |
    |----------|--------|
    | Low | 10% to 50%
    | Normal |	15% to 35%
    | High	| 15% to 35%
    | Critical | 	10% to 30%

- Batch jobs should be scheduled in such a way that there is always a mix of jobs with different priorities around the clock. For example, don't schedule all batch jobs with the **Normal** priority in the morning, **High** in the afternoon, **Critical** in the evening, and **Low** at night.
- The reserved queue, when used with **Reserved capacity** priority, will give the experience as having dedicated resources for batch job. If not required, then do not allocate batch jobs to the **Reserved capacity** priority.
- Priorities are not used to stack rank tasks against each other. Instead, priorities determine the probability with which a task will be picked for execution.
- We recommend that you keep the number of threads the same across the servers to eliminate performance degradation.
- We recommend implementing the BatchRetryable interface to batch tasks to prevent issues from SQL Server transient errors. For more information, see [Retry the batch job task when transient SQL Server errors occur](retryable-batch.md#retry-the-batch-job-task-when-transient-sql-server-errors-occur).
- Batch tasks should be idempotent in nature. Regardless of how many times you execute them, you should achieve the same result, and tasks should be set up with a retry count greater than zero. This allows the system to recover from any kind of transient errors that may occur during job execution. For more information, see [Retry the batch job task when transient SQL Server errors occur](retryable-batch.md#retry-the-batch-job-task-when-transient-sql-server-errors-occur).
- If there are larger workloads, we recommend breaking them down into smaller workloads or tasks so that they execute and complete in ten minutes or less.
- SQL Server transactions in batch tasks should be as small as possible in duration so that it doesn't cause SQL Server blocking that may impact performance of other batch jobs and user activity.
- We recommend having more than one batch group to take advantage of priority-based batch scheduling, and use different priorities at a batch-group level.
- When debugging batches in UAT by connecting to a development machine, you will have to disable the rest of the batch server by running the following script to ensure that all the batches are running on the development machine. 

    ```
    UPDATE ssc
    SET ssc.enablebatch = 0
    FROM dbo.sysserverconfig ssc
    WHERE ssc.serverid = '<servername Tier2 batch server>'   
    ```

## Automatic batch group migration for batch jobs

After the feature is turned on, batch group information on the task is duplicated on the job that will be used. The batch group assignment on a job is based on the batch group that is most used for the tasks for the job.

A new system batch job, **System job to seed batch group associations to batch jobs**, manages the migration. This batch job has the class name **SysMigrateBatchGroupsForPriorityBasedScheduling**.

The batch job is run every day at 1:00 AM, even if the **Batch priority-based scheduling** feature is turned off. It migrates the delta of applicable batch jobs since the last execution.

The batch job is also run when the feature is turned on, to migrate any batch jobs since the last execution. The user who turned on the feature will receive a notification that includes a reference to the ID of the migration batch job.

We recommend that you review the automatic batch group assignment after the feature is turned on and the migration is completed. To facilitate this review, the **Batch group** field for tasks is read-only. To support backward compatibility, the value of this field will be propagated from the job when new batch tasks are added.

As a best practice, we recommend that you do not assign a high or critical priority to all batch jobs.

## Batch concurrency

In Platform update 58, you can turn on the **(Preview) Batch concurrency control** feature in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). This feature lets you set a limit on the number of tasks that can run concurrently in a specific batch job. Therefore, it helps you prioritize your batch jobs and optimize the use of your resources. For example, by limiting the number of tasks for a low-priority batch job, you can avoid overloading the system and affecting the performance of other, higher-priority batch jobs.

> [!IMPORTANT]
> - This feature is available with version 10.0.34 (PU 58).
> - This feature is enabled by default for all new instances with version 10.0.39 (PU 63).

### Prerequisites

As a prerequisite, the **Batch Priority Based Scheduling** feature must be enabled in the environment.

### Why do you need batch concurrency control?

Batch jobs are a common way to perform background tasks, such as data processing, reporting, or integration. However, if too many batch tasks are running at the same time, they can cause performance issues or resource contention. For example, you have one batch job that runs every hour and processes a large amount of data, but you have another batch job that runs every 15 minutes and has high priority. Without batch concurrency control, you can't ensure that the high-priority batch job will get enough resources to run smoothly and in a timely manner.

> [!NOTE]
> - This feature is available as of version 10.0.34.
> - If concurrency control isn't required, the **Max concurrency** field on the **Batch group** page should be set to **0** (zero).
> - The feature isn't recommended for batch jobs that have more than 5,000 concurrent, ready-to-run tasks, because it might degrade performance of batch scheduling.
> - If the **Max concurrency** value exceeds the total number of batch threads that are available in the environment, the feature will be ineffective.
> - The **Max concurrency** value applies to each batch job in the group. It isn't the cumulative value for the batch group.

### How do you use batch concurrency control?

To use batch concurrency control, you must turn on the **(Preview) Batch concurrency control** feature in Feature management. Then go to **Batch groups**, and select a batch group that you want to apply the concurrency limit to. The **Batch group** page has a new field that's named **Max concurrency**. You can enter a positive integer that represents the maximum number of tasks that can run at the same time for each batch job in the selected batch group. This setting applies to all the batch jobs that belong to the batch group.

For example, if you set the **Max concurrency** value to **10** for a batch group, only 10 tasks from a batch job in that batch group can run concurrently. If more than 10 tasks for the job are waiting to run, they're queued until some of the running tasks are completed.

The **Max concurrency** value doesn't affect the number of tasks that can run across different batch groups. It applies only to the tasks in the same batch group. If concurrency control isn't required, it should be set to **0** (zero), which is the default value.

If you want to completely pause all batch jobs in the batch group, set the **Max concurrency** field to **-1**. Any tasks that the system picked before you set the value to **-1** will continue to run.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
