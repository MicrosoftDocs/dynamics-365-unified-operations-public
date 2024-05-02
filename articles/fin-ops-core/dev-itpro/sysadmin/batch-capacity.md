---
title: Batch capacity
description: Learn about the batch capacity, including overviews on batch auto scaling and how to increase batch capacities.
author: cwithfourplus
ms.author: johnmichalak
ms.topic: article
ms.date: 03/07/2024
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2024-03-07
ms.dyn365.ops.version: Platform Update50
---

# Batch capacity 

[!include [banner](../includes/banner.md)]

Batch capacity refers to the maximum number of batch tasks that can be processed at a time. It depends on both the number of batch servers and the number of batch threads available for processing these tasks.

To calculate the batch capacity, multiply the number of batch servers by the number of batch threads per server:

*Batch capacity* = *Number of batch servers* &times; *Number of batch threads per server*

The total batch capacity for the environment is determined based on user licenses. We establish the minimum and maximum number of batch servers required to serve this batch capacity.

To view batch capacity, use **System Administration** \> **Setup** \> **Server configuration** and look for available batch servers.

## Batch auto scaling 

Auto scaling is a new feature that automatically adjusts your batch servers according to resource usage thresholds. It provides elasticity to your environment, allowing it to adapt to varying workloads dynamically. This process is entirely automated and relies on predefined signals based on CPU and memory usage of batch servers.

Auto scaling becomes beneficial when the workload on an environment fluctuates over time. We continuously monitor the reported load and periodically evaluate triggers to determine if scaling is necessary.

The lower load threshold signifies the point at which the service scales in. If the average load falls below this threshold, the service scales in.

Conversely, the upper load threshold indicates when the service scales out. If the average load exceeds this threshold, the service scales out.

> [!NOTE]
> - For batch auto scaling to work, your environment should have [batch priority-based scheduling](priority-based-batch-scheduling.md) enabled, and your PU should be 10.0.26 (PU 50) or higher.
> - After batch auto scaling is activated for the environment, the platform periodically adjusts the thread count for each server as per batch capacity. Any manual alterations to the thread count are disregarded and overridden by the platform's automated processes.

For example, where your environment comprises six batch servers, each with eight threads, totaling 48 batch threads. 

If your environment encounters elevated CPU and memory usage on batch servers, the platform might introduce another batch server while decreasing the thread count per server to seven. This action ensures that even with seven batch servers, the total thread count remains consistent at 49, closely aligning with the initial count of 48.

Conversely, when batch server CPU and memory utilization are low, platform might opt to remove two servers while increasing the thread count per server to 12, maintaining a total of 48 threads.

This approach ensures that the total active threads for your environment remain constant while optimizing the number of batch servers, thus ensuring appropriate allocation of infrastructure resources. 

## How to increase batch capacity

To increase the batch capacity in a production environment, you must acquire more user licenses and update subscription estimates in Microsoft Dynamics Lifecycle Services. For updated user licenses, we automatically increase the batch capacity by adjusting the thread count per existing server. The platform adds more batch servers after the existing batch servers reach their threshold limits for CPU and memory utilization.

To increase the batch capacity in a sandbox environment, you need a Tier-4 or Tier-5 sandbox. This action isn't possible in Tier-2 or Tier-3 sandboxes.

For more information about capacity planning, see [Environment planning](../organization-administration/environment-planning.md).
