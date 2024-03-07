---
# required metadata

title: Batch Capacity
description: This article provides information about the Batch Capacity.
author: cwithfourplus
ms.date: 03/07/2024
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
ms.search.validFrom: 2024-03-07
ms.dyn365.ops.version: Platform Update50

---

# Batch Capacity 

[!include [banner](../includes/banner.md)]

Batch Capacity refers to the maximum number of batch tasks that can be processed at a time. It depends on both the number of batch servers and the number of batch threads available for processing these tasks.

To calculate the Batch Capacity, multiply the number of batch servers by the number of batch threads per server:

**Batch Capacity = Number of batch servers * Number of batch threads per server**

The total Batch Capacity for the environment is determined based on user licenses. Additionally, we establish the minimum and maximum number of Batch Servers required to serve this Batch Capacity.

To view Batch Capacity, use **System Administration > Setup > Server configuration** and look for available Batch Servers.

## Batch Auto Scaling 

Auto scaling is a new feature that automatically adjusts your Batch servers according to resource usage thresholds. It provides elasticity to your environment, allowing it to adapt to varying workloads dynamically. This process is entirely automated and relies on predefined signals based on CPU and memory usage of Batch Servers.

Auto scaling becomes beneficial when the workload on an environment fluctuates over time. We continuously monitor the reported load and periodically evaluate triggers to determine if scaling is necessary.

The lower load threshold signifies the point at which the service scales in. If the average load falls below this threshold, the service scales in.

Conversely, the upper load threshold indicates when the service scales out. If the average load exceeds this threshold, the service scales out.

> [!NOTE]
> - For Batch Auto Scaling to work, your environment should be have [Batch Priority based scheduling](priority-based-batch-scheduling.md) enabled and your PU should be 10.0.26 (PU 50) or higher.
> - Once Batch Auto Scaling is activated for the environment, the platform will periodically adjust the thread count for each server as per Batch Capacity. Any manual alterations to the thread count will be disregarded and overridden by the platform's automated processes.


For instance where your environment comprises 6 Batch Servers, each with 8 threads, totaling 48 batch threads. 

If your environment encounters elevated CPU/Memory usage on Batch Servers, platform may introduce an additional Batch server while decreasing the thread count per server to 7. This action ensures that even with 7 batch servers, the total thread count remains consistent at 49, closely aligning with the initial count of 48.

Conversely, when Batch Server CPU/Memory utilization is low, platform may opt to remove 2 servers while increasing the thread count per server to 12, maintaining a total of 48 threads.

This approach ensures that the total active threads for your environment remain constant while optimizing the number of Batch Servers, thus ensuring appropriate allocation of infrastructure resources. 

## How to increase Batch Capacity

To increase the Batch Capacity, you need to acquire more user licenses. With updated user licenses, we automatically augment the Batch Capacity by adjusting the thread count per existing server. Additionally, the platform adds more Batch Servers once the existing Batch Servers reach their threshold limits of CPU/Memory.