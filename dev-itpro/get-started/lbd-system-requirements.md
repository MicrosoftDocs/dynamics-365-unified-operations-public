---
# required metadata

title: System requirements for On-premises environments
description: This topic lists the system requirements for an On-premises environment.
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

# System requirements for On-premises environments

[!include[banner](../includes/banner.md)]

Before you install Microsoft Dynamics 365 for Finance and Operations Enterprise Edition on-premises, make sure that the system that you are working with meets or exceeds the minimum network, hardware, and software requirements. 

## Network requirements 
Microsoft Dynamics 365 for Operations can operate on networks that use Internet Protocol Version 4 (IPv4) or Internet Protocol Version 6 (IPv6). Consider the network environment when you plan the system, and use the following guidelines. 

### Network response time 
The following table lists the minimum network requirements for the connection between the Web Browser and the Application Object Server (AOS) and the connection between the AOS and the database in a Microsoft Dynamics 365 for Finance and Operations on-premises system. 

| Value         | Web browser to AOS | AOS to database | AOS to Lifecycle Services |
|---------------|--------------------|-----------------|---------------------------|
| Bandwidth (b) | 50 KBps            | 199 Mbps        |                           |
| Latency       | 250-300 ms         | < 1 ms          |                           |

- Microsoft Dynamics 365 for Finance and Operations on-premises is designed for networks with latency of 250-300 milliseconds (ms) or less. This is the latency from a browser client to the data center that hosts Dynamics 365 for Operations. 

- Bandwidth requirements for Microsoft Dynamics 365 for Finance and Operations on-premises depend on your scenario. Most typical scenarios require a bandwidth of more than 50 kilobytes per second (KBps). However, for scenarios that have high payload requirements, such as workspaces or scenarios that involve extensive customization, more bandwidth is recommended. 
In general, Dynamics 365 for Operations is optimized for the Internet. The number of round trips from a browser client to the data center is very small, and the whole payload is compressed. 

**Warning:** Don’t compute bandwidth requirements from a client location by multiplying the number of users by the minimum bandwidth requirements. The concurrent usage of a given location is very difficult to calculate. For customers who are concerned about bandwidth requirements, use a preview version of Dynamics 365 for Operations. 

### Local area network (LAN) environments 
No Windows Server Remote Desktop requirement to connect to Microsoft Dynamics 365 for Finance and Operations on-premises but it may be required for servicing operations on the environment. 

### Wide area network (WAN) environments 
No Windows Server Remote Desktop requirement to connect to Microsoft Dynamics 365 for Finance and Operations on-premises but it may be required for servicing operations. 

### Internet connectivity requirements 
Microsoft Dynamics 365 for Finance and Operations on-premises does not need internet connectivity to operate yet certain features are not available in the offline mode. 

| Browser client           | INTRANET scenario without INTERNET connectivity is a design point for the on Premise deployment option. Some features that require cloud services will not be available (Help, Task Guides Libraries in LCS) |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Server                   | The AOS or Service Fabric tier must be able to communicate with LCS. The AX modern client does not need to be connected to the cloud.                                                                        |
| Telemetry                | Telemetry data may be lost if there are interruptions in connectivity. Interruptions in connectivity to LCS do not affect the on Premise application functionality.                                          |
| Lifecycle Services (LCS) | Connectivity to LCS is required for deployment, code deployment and servicing operations.                                                                                                                    |

## Telemetry data transfer to the cloud 
Most telemetry is stored locally and can be accessed via the Windows Event Viewer. A small subset of telemetry events is transferred into our telemetry pipeline. 
Please find more data on how to troubleshoot in the Microsoft Dynamics 365 for Finance and Operations on-premises specific documentation items. 

## Domain requirements 
Consider the following domain requirements when you install Microsoft Dynamics 365 for Operations: 
· Computers that run base Microsoft Dynamics 365 for Finance and Operations on-premises components must belong to an Active Directory domain, and Active Directory must be configured in native mode. 
**Note:** Retail system requirements are not determined at this point. Microsoft Dynamics 365 for Finance and Operations on-premises does not include retail. 
· Computers that run base Microsoft Dynamics 365 for Finance and Operations on-premises components must have access to other computers in Active Directory. These computers may be either in the same domain or in another trusted domain. 
· The domain controller must run in Windows Server 2016 

## Hardware requirements 

This section of the document describes the hardware that is required to run Microsoft Dynamics 365 for Finance and Operations on-premises. 
Actual requirements vary, based on the system configuration and based on the applications and features that you decide to use. The following are some of the many factors that affect the choice of appropriate hardware for a Microsoft Dynamics 365 for Operation: 

· The number of transactions per hour.
· The number of concurrent users. 
· The number of remote connections. 
· The number of locations. 
· For more information about the factors to consider please refer to the how to the published “How to size and on premise installation” content. 

## Minimum Infrastructure requirements 
Microsoft Dynamics 365 for Finance and Operations on-premises utilizes service fabric to host the AOS, Batch, Data management, Management reporter and Orchestrator services. SSRS is not hosted in the service fabric cluster. 
Independent of that SQL Server must be setup in a high availability hadron setup with at least 2 nodes. 

Please see below diagram for the minimum amount of virtual machines: 
[![System requirements and virtual machines](./media/lbd-system-requirements-01.png)](./media/lbd-system-requirements-01.png)

### Processor and RAM requirements 
The following table lists the number of processors and amount of RAM that are required for server computers. 
**Note:** If other Microsoft software is installed on the same computer, the system must also comply with the hardware requirements for that software.
**Note:** We recommend that you limit other server applications on the same computer as the AOS, to 1 GB of RAM.

| Topology              | Role                                                          | Instances | Cores | Memory(GB) |
|-----------------------|---------------------------------------------------------------|-----------|-------|------------|
| Production            |                                                               |           |       |            |
|                       | AOS (Web Client, Data Management, Batch)                      | 3         | 8     | 24         |
|                       | Management Reporter                                           | 2         | 4     | 16         |
|                       | SQL Server Reporting Services                                 | 1         | 4     | 16         |
|                       | Orchestrator                                                  | 3         | 2     | 8          |
|                       |                                                               |           |       |            |
| Sandbox               |                                                               |           |       |            |
|                       | AOS (Web Client, Data Management, Batch)                      | 2         | 8     | 24         |
|                       | Management Reporter                                           | 1         | 4     | 16         |
|                       | SQL Server Reporting Services                                 | 1         | 4     | 16         |
|                       | Orchestrator                                                  | 3         | 2     | 8          |
|                       |                                                               |           |       |            |
| Shared infrastructure |                                                               |           |       |            |
|                       | SQL Server                                                    | 2         | 8     | 32         |
|                       | File Server / Storage area network / Highly available storage |           |       |            |
|                       | Active directory                                              | 3         | 4     | 16         |

### Storage
- AOS: Microsoft Dynamics 365 for Finance and Operations is utilizing Azure blob storage to store certain data like metadata, traces, documents etc. The on Premise version will use a SMB 3.0 share, for this either Storage spaces direct or a Storage area network will be required. https://technet.microsoft.com/en-us/windows-server-docs/storage/storage-spaces/storage-spaces-direct-overview
- SQL: Viable options are: 
  •	A highly available SSD setup
  •	A storage area network
  •	Direct attached storage
- IOPS: The storage for both data management and SQL Server should have at least 2000 IOPS.

### Virtual Host requirements
There are many different ways on how to setup virtual hosts and SQL Server. As a general rule of thumb the more physical hardware is utilized the more performance the less physical hardware the easier the maintenance. In all cases if virtualization is used there should no VM Snapshots being taken.

For setting up the virtual hosts to host the Microsoft Dynamics 365 for Finance and Operations on-premises environment make sure to have at least 3 virtual hosts which have enough cores to the infrastructure you sized. There are many advanced configurations possible where e.g. the SQL Server is residing on physical hardware whereas everything else is virtualized. If SQL Server gets virtualized at least the disk subsystem should be a fast storage area network or equal. In all cases make sure that your basic virtual host setup is highly available and redundant.

## Software requirements for all server computers 
 The following software must be present on a computer before any Microsoft Dynamics 365 for Operations components can be installed:
 
•	Microsoft .NET Framework
•	Service Fabric
 
More information on Service Fabric: 
https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-cluster-creation-for-windows-server#download-the-service-fabric-standalone-package
 
### Supported server operating systems
The following table lists the server operating systems that are supported for Microsoft Dynamics 365 for Operations components. 

| Operating system                           | Note                                                                                               |
|--------------------------------------------|----------------------------------------------------------------------------------------------------|
| Windows Server 2016 Datacenter or Standard | These requirements are for both the database and the server hosting the Application Object Server. |

### Software requirements for database servers
Regardless of the version of SQL Server you use, the following requirements apply: 
•	Only 64-bit versions of SQL Server are supported. 
•	In a production environment, we recommend that you install the latest cumulative update for the version of SQL Server that you are using.  
•	Microsoft Dynamics 365 for Operations supports Unicode collations that are case-insensitive, accent-sensitive, kanasensitive, and width-insensitive. The collation must match the Microsoft Windows locale of the computers that are running instances of the AOS. If you are setting up a new installation, we recommend that you select a Windows collation instead of a SQL Server collation. For more information about how to select a collation for a SQL Server database, see the SQL Server documentation (http://go.microsoft.com/fwlink/?linkid=119526). 
 
The following table lists the supported versions of SQL Server for the Microsoft Dynamics AX databases. For the minimum hardware requirements for SQL Server, see http://www.microsoft.com/sql/default.mspx.

| Requirement                                                     | Notes                                                                                                                                                                    |
|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Microsoft SQL Server 2016, Standard Edition, Enterprise Edition | For SQL Server 2016 hardware requirements, see Hardware and Software Requirements for Installing SQL Server 2016: https://msdn.microsoft.com/en-us/library/ms143506.aspx |

## Software requirements for client computers
Any computer which can host a web browser. Tested browsers are Microsoft Internet Explorer, Edge and Google Chrome
 
## Hardware and software requirements for Retail components 
Microsoft Dynamics 365 for Finance and Operations on-premises does not include the retail components.
 
## 64-bit operating system support
All components must run on a 64 bit operating system besides the client which is a standard web browser or an app created by the Microsoft Dynamics 365 for Finance and Operations on-premises export function.

