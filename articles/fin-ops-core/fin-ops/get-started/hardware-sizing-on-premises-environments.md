---
title: Hardware sizing requirements for on-premises environments
description: This article lists the hardware sizing requirements for an on-premises environment.
author: sericks007
ms.date: 06/02/2021
ms.topic: article
ms.prod: dynamics-365
ms.technology: 
audience: Application User, Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 8
ms.assetid: 
ms.service: 
search.app:
  - financeandoperationsonprem-docs
---

# Hardware sizing requirements for on-premises environments

[!include [banner](../includes/banner.md)]

Before you begin the hardware and infrastructure sizing process for an on-premises environment, familiarize yourself with the [System requirements for cloud deployments](system-requirements.md) and [Setup and deployment instructions](../../dev-itpro/deployment/setup-deploy-on-premises-environments.md) to gain a solid understanding off the underlying infrastructure.

> [!NOTE]
> Pay close attention to the system setup best practices for optimum performance.

After you have reviewed the documentation, you can start the process of estimating your transactional and concurrent user volume and sizing your environment based on the average core throughput.

## Factors that affect sizing

All the factors shown in the following illustration contribute to sizing. The more detailed information that is collected, the more precisely you can determine sizing. Hardware sizing, without supporting data, is likely to be inaccurate. The absolute minimum requirement for necessary data is the peak transaction line load per hour.

[![Hardware sizing for on-premises environments.](./media/lbd-sizing-01.png)](./media/lbd-sizing-01.png)

Viewed from left to right, the first and most important factor needed to accurately estimate sizing is a transaction profile or a transaction characterization. It's important to always find the peak transactional volume per hour. If there are multiple peak periods, then these periods need to be accurately defined.

As you understand the load that impacts your infrastructure, you also need to understand more detail about these factors:

- **Transactions** – Typically transactions have certain peaks throughout the day/week. This mostly depends on the transaction type. Time and expense entries usually show peaks once per week, whereas Sales order entries often come in bulk via integration or trickle in during the day.
- **Number of concurrent users** – The number of concurrent users is the second most important sizing factor. You cannot reliably get sizing estimates based on the number of concurrent users, so if this is the only data you have available, estimate an approximate number, and then revisit this when you have more data. An accurate concurrent user definition means that:

    - Named users are not concurrent users.
    - Concurrent users are always a subset of named users. 
    - Peak workload defines the maximum concurrency for sizing.

    Criteria for concurrent users is that the user meets all the following criteria:

    - Logged on.
    - Working transactions/inquiries at the time of counting.
    - Not an idle session.

- **Data composition** – This is mostly about how your system will be set up and configured. For example, how many legal entities you will have, how many items, how many BOM levels, and how complex your security setup will be. Each of those factors may have a small impact on performance, so these factors can be offset by using smart choices when it comes to infrastructure.
- **Extensions** – Customizations can be simple or complex. The number of customizations and the nature of complexity and usage has a varied impact on the size of the infrastructure needed. For complex customizations, it's advised to conduct performance evaluations to ensure that they are not only tested for efficiency but also help understand the infrastructure needs. This is even more critical when the extensions are not coded according to best practices for performance and scalability.
- **Reporting and analytics** – These factors typically include running heavy queries against the various databases in the system. Understanding and reducing the frequency when expensive reports run will help you understand the impact of them.
- **Third-party solutions** – These solutions, like ISVs, have the same implications and recommendations as extensions.

## Sizing your environment

To understand your sizing requirements, you need to know the peak volume of transactions that you need to process. Most auxiliary systems, like Management Reporter or SSRS, are less mission critical. As a result, this document focuses mostly on AOS and SQL Server.

> [!NOTE]
> In general, the compute tiers scale out and should be set up in an N+1 fashion, meaning if you estimate three AOS, add a fourth AOS. The database tier should be set up in an Always On highly-available setup.

## SQL Server (OLTP)

### Sizing

- 3K to 15K transaction lines per hour per core on DB server.
- Typical AOS-to-SQL core ratio 3:1 for the primary SQL Server. Additional cores are required based on the chosen high availability configuration.

    - Processing database-heavy operations may regress this to 2:1.

- The following factors influence variations:

    - Parameter settings in use.
    - Levels of extensions.
    - Usage of additional functionality, such as database log and alerts. Extreme database logging will further reduce throughput per hour per core below 3K lines.
    - Complexity of data composition – A simple chart of accounts versus a detailed fine-grained chart of accounts has implications on throughput (as an example).
    - Transaction characterization.
    - 2 GB to 16 GB memory for each core.
    - Auxiliary databases on DB server such as Management reporter and SSRS databases.
    - Temp DB = 15% of DB size, with as many files as physical processors.
    - SAN size and throughput based on total concurrent transaction volume/usage.

### High availability

We recommend always utilizing SQL Server in either a cluster or mirroring setup. The second SQL node should have the same number of cores as the primary node.

### Active Directory Federation Services (AD FS)

For AD FS sizing, see the [AD FS Server Capacity documentation](/windows-server/identity/ad-fs/design/planning-for-ad-fs-server-capacity).

A [sizing spreadsheet](https://adfsdocs.blob.core.windows.net/adfs/ADFSCapacity2016.xlsx) is available for planning the number of instances in your deployment.

## AOS (Online and batch)

### Sizing

- Sizing by transaction volume/usage

    - 2K to 6K lines per core
    - 16 GB per instance
    - Standard box – 4 to 24 cores
    - 10 to 15 Enterprise users per core
    - 15 to 25 Activity users per core
    - 25 to 50 Team members per core

- Batch

    - 1 to 4 batch threads per core
    - Size based on batch window characterization

- Note that the AOS, Data Management, and Batch are on the same role in the Service Fabric. You need to size for these three workloads combined, and not separate these like in Microsoft Dynamics AX 2012.
- The same variability factors for SQL Server apply here.

### High availability

- Ensure that you have at least 1 to 2 more AOS available than you estimate.
- Ensure that you have at least 3 to 4 virtual hosts available.

## Management reporter

In most cases, unless used extensively, the recommended minimum requirements using two nodes should work well. Only in cases where there is heavy use will you need more than two nodes. Please scale as needed.

## SQL Server Reporting Services

For the general availability release, only one SSRS node can be deployed. Monitor your SSRS node while testing and increase the number of cores available for SSRS on a need basis. Make sure that you have a preconfigured secondary node available on a virtual host that is different than the SSRS VM. This is important if there is an issue with the virtual machine that hosts SSRS or the virtual host. If this the case, they would need to be replaced.

Starting with version 10.0.17, it is possible to configure additional SSRS nodes to achieve high availability. For more information, see [Configure high availability for SQL Server Reporting Services (SSRS) nodes](../../dev-itpro/deployment/onprem-ssrsha.md).

## Environment Orchestrator

The Orchestrator service is the service that manages your deployment and the related communication with LCS. This service is deployed as the primary Service Fabric service and requires at least three VMs. This service is co-located with the Service Fabric orchestration services. This and should be sized to the peak load of the cluster. For more information, see [Plan and prepare your Service Fabric Standalone cluster deployment](/azure/service-fabric/service-fabric-cluster-standalone-deployment-preparation).

## Virtualization and oversubscription

Mission critical services like the AOS should be hosted on Virtual hosts that have dedicated resources – cores, memory, and disk.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
