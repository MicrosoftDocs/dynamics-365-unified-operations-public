---
# required metadata

title: System requirements for on-premises environments
description: This topic lists the system requirements for an on-premises environment.
author: kfend
manager: AnnBe
ms.date: 06/013/2017
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

# System requirements for on-premises environments

[!include[banner](../includes/banner.md)]

Before you install Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (on-premises), verify that the system that you're working with meets or exceeds the minimum network, hardware, and software requirements. 

## Network requirements 
Finance and Operations can work on networks that use Internet Protocol Version 4 (IPv4) or Internet Protocol Version 6 (IPv6). Consider the network environment when you plan the system, and use the following guidelines. 

### Network response time 
The following table lists the minimum network requirements for the connection between the web browser and Application Object Server (AOS), and for the connection between AOS and the database in an on-premises system. 

| Value     | Web browser to AOS | AOS to database | AOS to LCS |
|-----------|--------------------|-----------------|------------|
| Bandwidth | 50 KBps            | 100 Mbps        |            |
| Latency   | 250–300 ms         | < 1 ms          |            |

- Finance and Operations (on-premises) is designed for networks that have a latency of 250–300 milliseconds (ms) or less. This latency is the latency from a browser client to the data center that hosts Finance and Operations. 
- Bandwidth requirements for Finance and Operations (on-premises) depend on your scenario. Typical scenarios require a bandwidth of more than 50 kilobytes per second (KBps). However, for scenarios that have high payload requirements, such as workspaces or scenarios that involve extensive customization, more bandwidth is recommended. 

In general, Finance and Operations is optimized for the Internet. The number of round trips from a browser client to the data center is very small, and the whole payload is compressed. 

> [!WARNING]
> Don’t calculate bandwidth requirements from a client location by multiplying the number of users by the minimum bandwidth requirements. The concurrent usage of a given location is very difficult to calculate. If you're concerned about bandwidth requirements, use a preview version of Finance and Operations. 

### LAN environments 
In local area network (LAN) environments, Microsoft Remote Desktop in Microsoft Windows Server isn't required in order to connect to Finance and Operations (on-premises). However, it might be required for servicing operations on the environment. 

### WAN environments 
In wide area network (WAN) environments, Remote Desktop in Windows Server isn't required in order to connect to Finance and Operations (on-premises). However, it might be required for servicing operations. 

### Internet connectivity requirements 
Finance and Operations (on-premises) doesn't require Internet connectivity to work. However, some features aren't available in offline mode. 

<table>
<tbody>
<tr>
<td><strong>Browser client</strong></td>
<td>An intranet scenario without Internet connectivity is a design point for the on-premises deployment option. Some features that require cloud services won't be available, such as Help and task guide libraries in LCS.</td>
</tr>
<tr>
<td><strong>Server</strong></td>
<td>The AOS or Service Fabric tier must be able to communicate with LCS. The on-premises client doesn't have to be connected to the cloud.</td>
</tr>
<tr>
<td><strong>Telemetry</strong></td>
<td>Telemetry data might be lost if there are interruptions in connectivity. Interruptions in connectivity to LCS don't affect the on-premises application functionality.</td>
</tr>
<tr>
<td><strong>LCS</strong></td>
<td>Connectivity to LCS is required for deployment, code deployment, and servicing operations.</td>
</tr>
</tbody>
</table>

## Telemetry data transfer to the cloud 
Most telemetry is stored locally and can be accessed by using Event Viewer in Microsoft Windows. A small subset of telemetry events is transferred to our telemetry pipeline. 

## Domain requirements 
Consider the following domain requirements when you install Finance and Operations:

- Computers that run base for Finance and Operations (on-premises) components must belong to an Active Directory Domain. Active Directory Domain Services (AD DS) must be configured in native mode.

    > [!NOTE]
    > Retail system requirements aren't currently supported. Therefore, Finance and Operations (on-premises) doesn't include Retail. 

- Computers that run base Finance and Operations (on-premises) components must have access to other computers in AD DS. These computers can be in the same domain or in another trusted domain. 
- The domain controller must run in Microsoft Windows Server 2016. 

## Hardware requirements 
This section describes the hardware that is required in order to run Finance and Operations (on-premises). 

Based on the system configuration, and the applications and features that you decide to use, the actual requirements might vary. Here are some of the factors that affect the choice of appropriate hardware for Finance and Operations: 

- The number of transactions per hour
- The number of concurrent users
- The number of remote connections
- The number of locations

For more information about the factors that you should consider, see “How to size an on-premises installation.”

## Minimum infrastructure requirements 
Finance and Operations (on-premises) uses Microsoft Azure Service Fabric to host the AOS, Batch, Data management, Management reporter, and Orchestrator services. Microsoft SQL Server Reporting Services (SSRS) isn't hosted in the Service Fabric cluster.

Microsoft SQL Server must be set up in a high-availability hadron setup that has at least two nodes.

The following figure shows the minimum number of virtual machines (VMs) that is allowed.

[![System requirements and VMs](./media/lbd-system-requirements-01.png)](./media/lbd-system-requirements-01.png)

### Processor and RAM requirements 
The following table lists the number of processors and the amount of random-access memory (RAM) that are required for server computers. 

> [!NOTE]
> If other Microsoft software is installed on the same computer, the system must also comply with the hardware requirements for that software. We recommend that you limit other server applications on the same computer as AOS to 1 gigabyte (GB) of RAM.

| Topology              | Role                                                      | Instances | Cores | Memory (GB) |
|-----------------------|-----------------------------------------------------------|-----------|-------|-------------|
| Production            | AOS (Web Client, Data Management, Batch)                  | 3         | 8     | 24          |
|                       | Management Reporter                                       | 2         | 4     | 16          |
|                       | SQL Server Reporting Services                             | 1         | 4     | 16          |
|                       | Orchestrator                                              | 3         | 2     | 8           |
| Sandbox               | AOS (Web Client, Data Management, Batch)                  | 2         | 8     | 24          |
|                       | Management Reporter                                       | 1         | 4     | 16          |
|                       | SQL Server Reporting Services                             | 1         | 4     | 16          |
|                       | Orchestrator                                              | 3         | 2     | 8           |
| Shared infrastructure | SQL Server                                                | 2         | 8     | 32          |
|                       | File Server/Storage area network/Highly available storage |           |       |             |
|                       | Active Directory                                          | 3         | 4     | 16          |

### Storage
- **AOS** – Finance and Operations uses Azure blob storage to store data. This data includes metadata, traces, and documents. The on-premises version will use a Server Message Block (SMB) 3.0 share for this data. For more information, see [Storage Spaces Direct in Windows Server 2016](https://technet.microsoft.com/en-us/windows-server-docs/storage/storage-spaces/storage-spaces-direct-overview). 
- **SQL** – Here are the viable options:

    - A highly available solid-state drive (SSD) setup
    - A storage area network (SAN)
    - Direct-attached storage (DAS)

- **IOPS** – The storage for both Data management and SQL Server should have at least 2,000 input/output operations per second (IOPS).

### Virtual host requirements
There are many ways to set up virtual hosts and SQL Server. In general, the more physical hardware is used, the better the performance. However, the less physical hardware, the easier the maintenance. In all cases, if virtualization is used, no VM snapshots should be taken.

When you set up the virtual hosts for a Finance and Operations (on-premises) environment, verify that you have at least three virtual hosts. Each virtual host should have enough cores for the infrastructure that you sized. Multiple advanced configurations are possible, where the SQL Server resides on physical hardware but everything else is virtualized. If SQL Server is virtualized, at a minimum, the disk subsystem should be a fast SAN or the equivalent. In all cases, make sure that the basic setup of the virtual host is highly available and redundant.

## Software requirements for all server computers 
 The following software must be present on a computer before any Finance and Operations components can be installed:
 
- The Microsoft .NET Framework
- Service Fabric
 
For more information, see [Create a standalone cluster running in Windows Server](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-cluster-creation-for-windows-server#download-the-service-fabric-standalone-package).
 
### Supported server operating systems
The following table lists the server operating systems that are supported for Finance and Operations components. 

| Operating system                                     | Notes                                                                  |
|------------------------------------------------------|------------------------------------------------------------------------|
| Microsoft Windows Server 2016 Datacenter or Standard | These requirements are for the database and the server that hosts AOS. |

### Software requirements for database servers
Regardless of the version of SQL Server that you use, the following requirements apply:

- Only 64-bit versions of SQL Server are supported. 
- In a production environment, we recommend that you install the latest cumulative update (CU) for the version of SQL Server that you're using.  
- Finance and Operations supports Unicode collations that are case-insensitive, accent-sensitive, kana-sensitive, and width-insensitive. The collation must match the Windows locale of the computers that are running AOS instances. If you're setting up a new installation, we recommend that you select a Windows collation instead of a SQL Server collation. For more information about how to select a collation for a SQL Server database, see the [SQL Server documentation](http://go.microsoft.com/fwlink/?linkid=119526). 
 
The following table lists the SQL Server versions that are supported for the Finance and Operations databases. For more information, see the minimum hardware requirements for [SQL Server](http://www.microsoft.com/sql/default.mspx).

| Requirement                                                      | Notes                                   |
|------------------------------------------------------------------|-----------------------------------------|
| Microsoft SQL Server 2016 Standard Edition or Enterprise Edition | For the hardware requirements for SQL Server 2016, see [Hardware and Software Requirements for Installing SQL Server 2016](https://msdn.microsoft.com/en-us/library/ms143506.aspx). |

## Software requirements for client computers
Any computer that can host a web browser can be used as a client computer. Tested browsers are Internet Explorer, Microsoft Edge, and Google Chrome.

## Software requirements for Active Directory
Use ADFS 3.0.
 
## Hardware and software requirements for Retail components 
Finance and Operations (on-premises) doesn't include the Retail components.
 
## Support for 64-bit operating systems
The client and any apps that are created by the Finance and Operations (on-premises) export function are run in a standard web browser. All other components must run on a 64-bit operating system.
