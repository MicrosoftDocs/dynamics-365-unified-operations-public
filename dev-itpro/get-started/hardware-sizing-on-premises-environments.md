---
# required metadata

title: Hardware sizing requirements for on-premises environments
description: This topic lists the hardware sizing requirements for an on-premises environment.
author: kfend
manager: AnnBe
ms.date: 06/13/2017
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
Doing hardware and infrastructure sizing for Dynamics 365 for Finance and Operations on-premises can be in three distinct steps: 

1. First familiarize yourself with the system requirements and setup instructions to get a good overview and understanding off the underlying infrastructure: 

- [System requirements](./lbd-system-requirements.md)

- [Set up and deploy on-premises environments](./deployment/setup-deploy-on-premises-environments.md)
  **Note:**Please spend special attention to the appendix of the setup documentation on best practices to setup your system for optimum performance. 

2. Estimate your transactional and concurrent user volume.
3. Size based on average core throughput

## Estimate your transactional and concurrent user volume 

All the below factors contribute to a sizing. The more detailed this information is collected the more exact the sizing of the final solution will be. There should be a bigger effort together with the customer to collect this information. A sizing without some of the below data is most probably incorrect. The absolute minimum requirement for example is the peak transaction line load per hour. 

GRAPHIC

Seen from the left to the right the first and most important thing which needs to be defined for a correct sizing is a transaction profile or a transaction characterization. The key to a solid sizing is to always find the peak transactional volume per hour. If there is multiple peak periods then these should also be properly defined. 
Once you understand what load impacts your infrastructure you need to also understand a bit more in detail how:
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
Sizing your Dynamics 365 for Finance and Operations environment
To size you need to know the average amount of transactions you can process. Most auxiliary systems like Management Reporter or SSRS are less mission critical so this document focuses mostly on the AOS and SQL Server.
Note: Due to the many variations you can use to make your setup highly available we only give very high level guidance. In general the compute tiers scale horizontally and should be setup in an N+1 fashion meaning if you estimate three AOS, add a fourth. The Database tier should usually be setup in an Always On highly available setup.
SQL Server (OLTP)
Sizing
-	3K to 15K Lines Per Hour Per Core on DB Server 
-	Major Swing is based on: 
o	Parameter Settings in use 
o	Levels of Extensions
o	Usage of additional functionality like database log and alerts etc. 
o	Transaction characterization
o	2 GB to 4 GB Memory for Each Core 
o	Auxiliary databases on DB server like Management reporter, SQL Server Reporting services databases and such.
o	Temp DB = 15% of DB Size with as many files as physical processors 
o	SAN Size based on total concurrent transaction volume/usage
High Availability 
We recommend utilizing SQL Server always on either in a cluster or mirroring setup.
AOS (Online and Batch)
Sizing 
o	Sizing by Transaction Volume/Usage 
o	2K to 6K Lines per Core 
o	8 GB to 16 GB per Instance 
o	Standard Box – 4 to 24 Core 
o	10 to 50 Users Per Core 
o	Batch 
o	1 to 4 Threads Per Core 
o	Size Based on Batch Window Characterization
o	Note that the AOS, Data Management and Batch are on the same role in service fabric. So you need to size for all these three workloads combined and not separate like in Microsoft Dynamics AX 2012.
High Availability 
o	Ensure that you have at least 1-2 more AOS available than you estimate. 
o	Ensure that you have at least 3 – 4 virtual hosts available
Management reporter
In most cases unless used extensively the 2 nodes recommended in the minimum requirements should work well. Only in case of very heavy use you will need more than two nodes.
SQL Server reporting services
For the initial general availability release only one SSRS node can be deployed. Please make sure that you have a pre-configured secondary available in you main Virtual machine would need to be replaced.
Orchestration service
The Orchestration service it the service which manages your deployment and the regarding communication with LCS. As we deploy this as the primary service fabric service you will need at least three VMs. These can be very light weight virtual machines with e.g. 2 cores each.
Virtualization and oversubscription
As a general rule of thumb it is usually ok to oversubscribe virtual hosts which host non mission critical auxiliary services like the orchestration service or depending on your scenario even Management reporter. Mission critical services like the AOS should be hosted on Virtual Hosts which are not oversubscribed.


