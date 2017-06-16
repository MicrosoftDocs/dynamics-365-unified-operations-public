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

  **Note:** Pay close attention to the system setup best practices for optimum performance. 

After you have reviewed the documentation, you can start the process of estimating your transactional and concurrent user volume and sizing your environment based on the average core throughput.

## Factors that affect sizing
All the factors shown in the following illustration contribute to sizing. The
more detailed information that is collected, the more precisely you can
determine sizing for the final solution. The effort to collect this information
is very important. Hardware sizing, without some of this data, is likely to be
inaccurate. The absolute minimum requirement, for example, is the peak
transaction line load per hour.

[![Hardware sizing for on-premises environments](./media/lbd-sizing-01.png)](./media/lbd-sizing-01.png)

Viewed from left to right, the first and most important factor needed to
accurately estimate sizing information is a transaction profile or a transaction
characterization. It’s important to always find the peak transactional volume
per hour. If there are multiple peak periods, then these periods need to be
accurately defined.

As you understand the load that impacts your infrastructure, you also need to
understand more detail about these factors:

**Transactions** - Typically transactions have certain peaks throughout the
day/week. This mostly depends on the transaction type. Time and expense entries
usually show peaks once per week, whereas Sales order entries often come in bulk
via integration or trickle in during the day.

**Number of concurrent users** – The number of concurrent users is the second
most important sizing factor. You cannot reliably get sizing estimates based on
the number of concurrent users, so if this is the only data you have available,
estimate an approximate number, and then revisit this when you have more data.
An accurate concurrent user definition means that:

- Named users are not concurrent users.
- Concurrent users are always a subset of named users.
- Peak workload defines the maximum concurrency for sizing.
- Criteria for concurrent users is that the user meets all the following criteria:
  - Logged on.
  - Working transactions/inquiries at the time of counting.
  - Not an idle session.

**Data composition** – This is mostly about how your system will be set up and
configured. For example, how many legal entities you will have, how many items,
how many BOM levels, and how complex your security setup will be. Each of those
factors may a have small impact on performance, so these factors can be offset
by using smart choices when it comes to infrastructure.

**Extensions** – Customizations can be simple or complex. The number of
customizations and the nature of complexity and usage has a varied impact on the
size of the infrastructure needed. For complex customizations, it’s advised to
conduct performance evaluations to ensure that they are not only tested for
efficiency but also help understand the infrastructure needs. This is even more
critical when the extensions are not coded according to best practices for
performance and scalability.

**Reporting and analytics** – These factors typically include running heavy
queries against the various databases in the Finance and Operations database
systems. Understanding and reducing the frequency when expensive reports run
will help you understand the impact of them.

**Third-party solutions** – These solutions, like ISVs, have the same
implications and recommendations as extensions.

## Sizing your Finance and Operations environment
To understand your sizing requirements, you need to know the average amount of
transactions that you can process. Most auxiliary systems, like Management
Reporter or SSRS, are less mission critical. As a result, this document focuses
mostly on AOS and SQL Server.

**Note:** Due to the many variations that you can use to make your setup highly
available, we provide only very high-level guidance. In general, the compute
tiers scale horizontally and should be set up in an N+1 fashion, meaning if you
estimate three AOS, add a fourth AOS. The database tier should be set up in an
Always On highly-available setup.

## SQL Server (OLTP)

### Sizing
-	3 to 15 thousand lines per hour per core on the database server 
- The following factors influence variations:
  - Parameter settings in use.
  - Levels of extensions.
  - Usage of additional functionality, such as database log and alerts.
  - Transaction characterization.
  - 2 GB to 4 GB memory for each core.
  - Auxiliary databases on DB server such as Management reporter and SSRS databases.
  - Temp DB = 15% of DB size, with as many files as physical processors.
  - SAN size based on total concurrent transaction volume/usage.

### High availability 
We recommend always utilizing SQL Server in either a cluster or mirroring setup.

### Active Directory Federation Services (AD FS)
For AD FS sizing, see the [AD FS Server Capacity
documentation](https://docs.microsoft.com/en-us/windows-server/identity/ad-fs/design/planning-for-ad-fs-server-capacity).

A [sizing spreadsheet](http://adfsdocs.blob.core.windows.net/adfs/ADFSCapacity2016.xlsx)
is available for planning the number of instances in your deployment.

AOS (Online and batch)
----------------------

### Sizing

- Sizing by transaction volume/usage
  - 2K to 6K lines per core
  - 8 GB to 16 GB per instance
  - Standard box – 4 to 24 cores
  - 10 to 50 users per core
- Batch
   - 1 to 4 batch threads per core
   - Size based on batch window characterization
- Note that the AOS, Data Management, and Batch are on the same role in the
Service Fabric. You need to size for these three workloads combined, and not
separate these like in Microsoft Dynamics AX 2012.

### High availability
- Ensure that you have at least 1 to 2 more AOS available than you estimate.
- Ensure that you have at least 3 to 4 virtual hosts available.

## Management reporter
In most cases, unless used extensively, the recommended minimum requirements
using two nodes should work well. Only in cases where there is heavy use will
you need more than two nodes.

## SQL Server Reporting Services
For the general availability release, only one SSRS node can be deployed. Make
sure that you have a preconfigured secondary node available on a virtual host
that is different than the SSRS VM. This is important in case there is an issue
with the virtual machine which hosts SSRS or the virtual host. If this the case,
they would need to be replaced.

## Environment Orchestrator
The Orchestrator service is the service that manages your deployment and the
related communication with LCS. As we deploy this as the primary Service Fabric
service, you will need at least three VMs. These can be very lightweight,
virtual machines with approximately 2 cores each.

## Virtualization and oversubscription
Generally, it’s okay to oversubscribe virtual hosts that host non-mission
critical auxiliary services such as the Orchestrator service, or depending on
your scenario, even Management reporter. Mission critical services like the AOS
should be hosted on Virtual hosts that are not oversubscribed.

