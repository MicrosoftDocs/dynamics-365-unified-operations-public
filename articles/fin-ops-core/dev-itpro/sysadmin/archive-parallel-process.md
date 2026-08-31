---
title: Configure parallel archive jobs in Microsoft Dynamics 365 finance and operations
description: Archive jobs in Microsoft Dynamics 365 finance and operations can run in parallel across legal entities. Discover prerequisites, concurrency limits, and how the zero-overlap scheduler works.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 07/22/2026
ms.topic: article
---

# Parallel processing for archive jobs

[!INCLUDE [banner](../includes/banner.md)]

Microsoft Dynamics 365 Finance and Operations archive jobs can now run simultaneously across legal entities. Previously, jobs ran one at a time in sequential order.

## Prerequisites

To use parallel processing for archive jobs, your environment must meet the following minimum version requirements.

### Application build version

| Platform update | Minimum build version |
|---|---|
| PU72 (10.0.48) | 7.0.7899.0 |
| PU71 (10.0.47) | 7.0.7858.24 |
| PU70 (10.0.46) | 7.0.7778.53 |
| PU69 (10.0.45) | 7.0.7690.115 |

### Finance and operations virtual entity solution

Update the finance and operations virtual entity solution from the Power Platform admin center (PPAC) to version 2.10.0.9 or later.

### How it works

The parallel processing feature is enabled by default once your environment meets the preceding version requirements. The archive job scheduler partitions jobs by legal entity. Within one scenario's scheduled job group, the scheduler schedules jobs in first-in, first-out (FIFO) order based on creation time. The scheduler always starts jobs created earlier before jobs created later.

### Default configuration

| Setting | Default value |
|---|---|
| Feature state | Enabled for all environments |
| Maximum concurrent jobs per scenario type | 3 |
| Maximum concurrent jobs across all scenario types | 5 |

For example, with default limits you can have three General ledger archive jobs and two sales orders archive jobs running at the same time (five jobs), as long as the total jobs across all scenarios doesn't exceed five.

> [!IMPORTANT]
> The concurrency job limits above are system defaults. You can't change them through the user interface or standard configuration at this time. The Microsoft team is actively evaluating approaches to support configurable job limits in a future release.

Why these limits?  Running too many archive jobs at once puts heavy workload on your database and consumes Power Platform API capacity, which can slow down or disrupt other processes in your environment. The limit of five total keeps overall system load manageable. The limit of three per scenario makes sure that one scenario, for example, General ledger archive jobs can't take up all available slots and leave other scenarios waiting. These conservative defaults work safely across all environment sizes.

### Jobs created before this feature was enabled

Only archive jobs created after parallel processing is enabled participate in parallel execution. Archive jobs that are already created and queued before the feature is enabled continue to run sequentially, one at a time in the order they were originally created.

This behavior is by design. The parallel scheduler requires each job to have a legal entity partition key assigned at creation time. Jobs created before the feature was enabled don't have this key and can't be enrolled in parallel execution retroactively.

#### What to expect when the feature is first enabled

When you enable the parallel processing feature in your environment:

- Existing queued jobs drain first. Any archive jobs that you created before the feature was enabled complete sequentially, in the order they were scheduled. This queue might take time to clear depending on how many jobs are pending, or you can cancel those jobs with scheduled status.
- New jobs run in parallel. After you create new archive jobs once the feature is enabled, those jobs are scheduled for parallel execution according to the concurrency limits described earlier.

#### Supported scenarios

Parallel processing applies to all standard archive scenarios that ship with the product. It also applies to custom archive scenarios that you or a partner build, but only when the scenario assigns a job criteria key to each job it creates. The job criteria key is a partitioning identifier, most commonly the legal entity, or `DataAreaId`, that lets the scheduler run jobs with different keys in parallel. A custom scenario that doesn't set a job criteria key still runs correctly, but its jobs run sequentially, one at a time.

For step-by-step guidance on setting the job criteria key in a custom scenario, see [Enable parallel processing with a job criteria key](archive-custom-build-scenario.md#enable-parallel-processing-with-a-job-criteria-key).

#### FAQ

- Can I increase the default concurrency limits?
Not through self-service configuration at this time. The maximum concurrent jobs per scenario (three) and the global maximum (five) are system defaults to minimize the impact to platform workload.

- Are my existing archive jobs affected?
Existing jobs that are already queued aren't parallelized. They complete sequentially as before. Only jobs created after the feature is enabled benefit from parallel execution.

- Can two jobs for the same scenario run at the same time?
Yes, up to the per-scenario limit of three. For example, two General ledger archive jobs can run simultaneously and the global limit of five isn't reached.

- Does parallel processing affect the move to history phase?
No, the move to history phase of each job runs independently and isn't affected by parallel processing. Parallel execution applies to the scheduling and execution of archive jobs. The move to history phase for each job completes as part of that job's normal lifecycle.
