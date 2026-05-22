---
title: Batch capacity
description: Learn about the batch capacity, including overviews on batch auto scaling and how to increase batch capacities.
author: cwithfourplus
ms.author: johnmichalak
ms.topic: article
ms.date: 03/13/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2024-03-07
ms.dyn365.ops.version: Platform Update50
---

# Batch capacity

[!include [banner](../includes/banner.md)]

Batch capacity refers to the maximum number of batch tasks that the system can process at one time. It depends on both the number of batch servers and the number of batch threads available for processing these tasks.

To calculate the batch capacity, multiply the number of batch servers by the number of batch threads per server:

*Batch capacity* = *Number of batch servers* &times; *Number of batch threads per server*

User licenses determine the total batch capacity for the environment. The system uses this batch capacity to establish the minimum and maximum number of batch servers required.

To view batch capacity, use **System Administration** > **Setup** > **Server configuration** and look for available batch servers.

## Batch auto scaling

Auto scaling is a new feature that automatically adjusts your batch servers according to resource usage thresholds. It provides elasticity to your environment, so it can adapt to varying workloads dynamically. This process is entirely automated and relies on predefined signals based on CPU and memory usage of batch servers.

Auto scaling is beneficial when the workload on an environment fluctuates over time. The system continuously monitors the reported load and periodically evaluates triggers to determine if scaling is necessary.

The lower load threshold signifies the point at which the service scales in. If the average load falls below this threshold, the service scales in.

Conversely, the upper load threshold indicates when the service scales out. If the average load exceeds this threshold, the service scales out.

> [!NOTE]
>
> - For batch auto scaling to work, you need to enable [batch priority-based scheduling](priority-based-batch-scheduling.md) in your environment, and your PU needs to be 10.0.26 (PU 50) or higher.
> - After you activate batch auto scaling for the environment, the platform periodically adjusts the thread count for each server as per batch capacity. The platform disregards and overrides any manual alterations to the thread count.

In PBS-enabled environments, autoscaling now ensures a constant total thread count across all batch servers, regardless of scale-up or scale-down events.

For example, your environment starts with six batch servers, each configured with eight threads, totaling 48 threads. As the environment scales, if autoscaling increases the number of servers to eight, the system automatically adjusts each server to use six threads, keeping the total at 48 (8 × 6 = 48). Similarly, if the environment scales down to four servers, each one is assigned 12 threads to maintain the same total (4 × 12 = 48).

In both cases, the overall thread capacity stays consistent - only the distribution changes.

This approach ensures that batch processing capacity remains consistent, even when CPU or memory usage alone wouldn't trigger autoscale.

> [!NOTE]
>
> - The thread count per server doesn't exceed 16, in line with platform safeguards to prevent resource saturation. By default, the thread count is set to 8. When you enable autoscaling, you can no longer manually configure the thread count, as the platform automatically manages it.

## How to increase batch capacity

To increase the batch capacity in a production environment, acquire more user licenses and update subscription estimates in Microsoft Dynamics Lifecycle Services. For updated user licenses, the system automatically increases the batch capacity by adjusting the thread count per existing server. The platform adds more batch servers after the existing batch servers reach their threshold limits for CPU and memory utilization.

To increase the batch capacity in a sandbox environment, you need a Tier-4 or Tier-5 sandbox. You can't perform this action in Tier-2 or Tier-3 sandboxes.

For more information about capacity planning, see [Environment planning](../organization-administration/environment-planning.md).
