---
# required metadata

title: Batch server overview | Microsoft Docs
description: This article describes batch processing and batch servers, and how to plan for their use.
author: maertenm
manager: AnnBe
ms.date: 2016-02-29 19:19:28
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: annbe
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 57201
ms.assetid: a16693b5-1192-414f-bdbe-ff12b49b43ae
ms.region: Global
# ms.industry: 
ms.author: maertenm

---

# Batch server overview

This article describes batch processing and batch servers, and how to plan for their use.

The batch framework provides an asynchronous, server-based batch processing environment that can process tasks across multiple instances of Application Object Server (AOS). You should become familiar with the following aspects of the batch framework:

-   A **batch job** is a process that is used to achieve a specific goal. A batch job consists of one or more batch tasks.
-   A **batch task** is an activity that is run by a batch job. You can add batch tasks that have multiple types of dependencies to a batch job. You can also configure AOS instances to run multiple threads, each of which runs a task. All batch tasks that are waiting to be run can be run by any available AOS instance that is configured as a batch server. To improve throughput and reduce overall execution time, you can define a batch job as many tasks and then use a batch server to run the tasks against all available AOS instances.
-   A **batch group** is an attribute of a batch task. A batch group lets the administrator determine or specify which AOS instance runs the task. When you create a new task, it's put in the default batch group. All batch servers are configured to process the default batch group and the waiting tasks from any job. Additionally, you can create a named batch group, and then set an affinity between that batch group and specific AOS instances. After you create this affinity, only the specified AOS instances will process tasks from the named batch group, and those AOS instances will process tasks from the named batch group only. You can also add the default batch group to the configured servers, if that batch group is required.

## Batch server topology planning
The capacity of a batch server is based on the maximum number of threads that can run concurrently on the AOS instance. Each thread runs one batch task. You can add complex dependencies between or among tasks. You can run these tasks in serial steps or parallel steps, depending on the business logic and requirements. All tasks that don't have any dependencies are considered parallel tasks. AOS instances that are configured as batch servers periodically check for tasks that are waiting to be processed. The batch server assigns each parallel task to a thread and starts to process the thread. You can run multiple threads across multiple AOS instances. Each AOS instance automatically runs multiple threads, depending on that capacity that is defined in the configuration settings. Therefore, parallel tasks from a job can be run on multiple threads across multiple AOS instances. A batch server checks for available threads one time per minute. Therefore, you might have to wait for a minute before you see that a waiting task is picked up for processing by an available thread.

## Batch server management planning
All batch servers can be managed from a single location. One typical use of batch servers is to load balance jobs across multiple time zones and servers. You can define the period when an AOS instance acts as a batch server. You can also set the number of threads that the batch server will process during that period. The applicable times for the period are based on the user's time zone, not the time zone of the location of the AOS instance. The period is based on a scheduled start time and a scheduled end time. Because batch servers are also active AOS instances that service requests from Microsoft Dynamics 365 for Operations clients and other associated components, you must carefully determine when an AOS instance should be available to process batches. For example, a batch server is set to process only two batch threads from 8:00 AM to 6:00 PM in the time zone where it's located. However, from 6:00 PM to 7:30 AM, the server can be set to process 20 threads.

## Walkthroughs
The following walkthroughs describe how tasks are processed, and how batch groups can be used to associate batch jobs with batch servers.

### Batch processing of dependent tasks

For this example, you've created a job that is called JOB 1. As the following diagram shows, the job has seven tasks: TASK 1, TASK 2, TASK 3, TASK 4, TASK 5, TASK 6, and TASK 7. ![A job that has dependent tasks](./media/batch_framework_programmability.gif) The tasks have the following dependencies:

-   TASK 1 is the first task.
-   TASK 2 runs when TASK 1 is completed (regardless of the success or failure of TASK 1).
-   TASK 3 runs when TASK 2 is successful.
-   TASK 4 runs when TASK 2 is successful.
-   TASK 5 runs when TASK 2 fails.
-   TASK 6 runs when TASK 3 fails.
-   TASK 7 runs when both TASK 3 and TASK 4 are successful.

Two batch servers, Batch1 and Batch2, are configured. Each server has a capacity of one thread. Imagine that Batch1 checks for waiting tasks, assigns TASK 1 to its thread, and starts to run TASK 1. Although Batch2 and its single thread are also available, TASK 2 continues to wait until TASK 1 is completed. As soon as TASK 1 is completed, TASK 2 is ready to be run. This time, imagine that Batch2 checks for waiting tasks, assigns TASK 2 to its thread, and starts to run TASK 2. If TASK 2 is successful, TASK 3 and TASK 4 are ready to be run. This time, imagine that Batch2 checks for waiting tasks, assigns TASK 3 to its thread, and starts to run TASK 3. Batch1 also checks for waiting tasks, assigns TASK 4 to its thread, and starts to run TASK 4. If TASK 3 and TASK 4 are successful, one of the batch servers runs TASK 7. If TASK 2 fails, one of the batch servers runs TASK 5. If TASK 3 fails, one of the available batch servers runs TASK 6. **Note:** For this walkthrough, we are using Batch1 and Batch2 to explain the concept. Any batch server that has available threads will start to run a waiting task. You must create a batch group to determine or specify which batch job runs on which server.

### Batch processing that uses batch groups

This example shows how batch jobs can be processed on specific batch servers. You have three batch servers: AOS1, AOS2, and AOS3. By default, all the batch servers process tasks from all batch jobs, depending on the number of available threads. You create a named batch group, BG1, and configure it to run on AOS2 and AOS3. Therefore, tasks from jobs in BG1 will run only on AOS2 or AOS3, depending on the number available threads. AOS1 won't process tasks from jobs in BG1. Likewise, AOS2 and AOS3 will process tasks from BG1 only. You can configure AOS2 and AOS3 to process tasks from other batch groups. These batch groups include the default batch group.

