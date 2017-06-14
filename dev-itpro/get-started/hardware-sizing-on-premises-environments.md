---
# required metadata

title: Hardware sizing requirements for on-premises environments
description: This topic lists the hardware sizing requirements for an on-premises environment.
author: kfend
manager: AnnBe
ms.date: 06/14/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: Core
# ms.tgt_pltfrm: 
ms.custom: 55651
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chwolf
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 8

---

# Hardware sizing for on-premises environments
Before you begin the hardware and infrastructure sizing process for an on-premises environment, familiarize yourself with the [System requirements](./lbd-system-requirements.md) and [Setup and deployment instructions](./deployment/setup-deploy-on-premises-environments.md) to gain a solid understanding off the underlying infrastructure. 
  **Note:**Pay close attention to the system setup best practices for optimum performance. 

After you have reviewed the documentation, you can start the process of estimating your transactional and concurrent user volume and sizing your environment based on the average core throughput.

## Estimate your transactional and concurrent user volume 
All the below factors contribute to a sizing. The more detailed this information is collected the more exact the sizing of the final solution will be. There should be a bigger effort together with the customer to collect this information. A sizing without some of the below data is most probably incorrect. The absolute minimum requirement for example is the peak transaction line load per hour. 

[![Hardware sizing for on-premises environments](./media/lbd-sizing-01.png)](./media/lbd-sizing-01.png)

Seen from the left to the right the first and most important thing which needs to be defined for a correct sizing is a transaction profile or a transaction characterization. The key to a solid sizing is to always find the peak transactional volume per hour. If there is multiple peak periods then these should also be properly defined. 

After you understand what load impacts your infrastructure you need to also understand a bit more in detail how:
-	Transactions typically have certain peaks throughout the day / week. This depends a lot on the transaction type. Time and Expense entries show usually peaks more once per week whereas  Sales Order entries often either come in bulk via integration or trickle in during the day.
-	The amount of concurrent users is the second most important factor. In regards to weight compared to your sizing it is significantly less important than the transactions. You can’t size reliably based on concurrent user number so if this is the only data you have available approximate as much as possible and revisit the sizing once you have more data. Concurrent user definition:
o	Named users are not concurrent users
o	Concurrent users are always a subset of named users
o	Peak workload defines the maximum concurrency for sizing
o	Criterias for concurrent users:
	Logged on and
	Working transactions/inquiries at the time of counting and
	Not an idle session
-	The data composition is mainly about how your system will be setup and configured. How many legal entities will you have, how many items, how many BOM levels, how complex will your security setup be and so on. All of that may have small impacts on performance and can be counteracted with correct infrastructural choices.
-	Extensions can be very light weight or they can drastically change sizing up to the point that additional hardware is not able to cope with the additional load anymore. This is mainly an issue when the extensions are not coded according to best practices for performance and scalability.
-	Reporting and analytics is usually including running heavy queries against the various databases in the Dynamics 365 for Finance and Operations database system(s). Understanding and reducing the frequency when expensive reports run will help understand the impact of them.
-	3rd party solutions like ISVs can have the same impact then extensions and drive your load up significantly

## Sizing your on-premises environment
To size your on-premises environment, you need to know the average amount of transactions that can be processed. Most auxiliary systems, like Management reporter or SSRS, are less critical so this document focuses mostly on the AOS and SQL Server.
**Note:** Due to the variations you can use to make your setup highly available, we only provide very high-level guidance. In general, the compute tiers scale horizontally and should be set up in an N+1 fashion. This means that if you estimate three AOS, add a fourth. The Database tier should be set up in an **Always On** highly available setup.

## SQL Server (OLTP)

### Sizing
-	3 to 15 thousand lines per hour per core on the database server 
-	Major swing is based on: 
 o	Parameter settings  
 o	Extension levels
 o	Use of additional functionality like database log and alerts 
 o	Transaction characterization
 o	Two GB to four GB memory for each core 
 o	Auxiliary databases on the database server like Management reporter and SQL Server Reporting Services databases.
 o	Temp DB = 15% of the database size with as many files as physical processors 
 o	SAN size is based on the total concurrent transaction volume and usage

### High Availability 
We recommend that you always use SQL Server in a cluster or a mirroring setup.

## AOS (online and batch)

### Sizing 
o	Sizing by transaction volume and usage 
o	Two to six thousand lines per core 
o	8 GB to 16 GB per instance 
o	Standard box is 4 to 24 core 
o	10 to 50 users per core 
o	Batch 
o	One to four threads per core 
o	Size based on batch window characterization
o	Note that the AOS, Data Management and Batch are on the same role in service fabric. This means that you must size all three workloads as one and not as separate workloads.

### High availability 
- Verify that you have at least one to two more AOSs available than you estimate
- Verify that you have at least three to four virtual hosts available

## Management reporter
In most cases, the recommended minimum requirement of two nodes will work. Only in the case of very heavy use will you need more than two nodes.

## SQL Server reporting services
At this time, only one SQL Server Reporting Services (SSRS) node can be deployed. Verify that you have a pre-configured secondary available in you main Virtual machine would need to be replaced.

## Orchestration service
The Orchestration service manages your deployment and any communication with Lifecycle Services (LCS). When deployed as the primary service fabric service, you will need at least three VMs. These can be very light weight virtual machines with, for example, two cores each.

## Virtualization and oversubscription
Typically, there is no issue if you oversubscribe virtual hosts, if non-mission critical auxiliary services are being hosted. For example, the orchestration of services or, depending on your scenario, even Management reporter. However, mission critical services like the AOS must not be hosted on virtual hosts that are oversubscribed.


