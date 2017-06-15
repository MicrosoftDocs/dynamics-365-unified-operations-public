---
# required metadata

title: Dynamics 365 for Finance and Operations, Enterprise edition on-premises overview 
description: Dynamics 365 for Finance and Operations, Enterprise edition now supports running business processes in customer data centers with the on-premises or Local Business Data (LBD) deployment option. 
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
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.2.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 60373
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: arifk
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform Update 8

---# Dynamics 365 for Finance and Operations, Enterprise edition on-premises overview 

Dynamics 365 for Finance and Operations, Enterprise edition now supports running business processes in customer data centers with the on-premises or Local Business Data (LBD) deployment option. With this deployment option, application servers and the Microsoft SQL Server database will run in the customer's data center or the data center of the customer's partner. Customers and partners will manage the application lifecycle through Lifecycle Service (LCS) in the Microsoft Cloud. LCS features, such as business process modeling, software deployment and patching, and monitoring and diagnostics, are available for on-premises deployments. 

**Note:** The terms *Local Business Data (LBD)* and *on-premises* are interchangeable in this topic.

## Architecture 

The LBD deployment option uses Microsoft Dynamics 365 Finance and Operations cloud components that are deployed on-premises using Windows Server Service Fabric standalone clusters. Service Fabric is Microsoft’s next-generation middleware platform for building and managing enterprise-class high-scale applications. Service Fabric standalone clusters can be deployed on any computer that is running Windows Server. 

LBD deployment defines two types of Service Fabric standalone clusters: clusters for production environments and clusters for sandbox environments. The following services or node types are deployed into these clusters: 

- **Application Object Servers** - Provide the ability to run the Finance and Operations application functionality in client, batch, and import/export scenarios. 
- **Management Reporter** - Provides financial reporting functionality. 
- **SQL Server Reporting Services** - Provides document reporting functionality. 
- **Local Business Data Environment Orchestrator** - Enables the removal of environment management from Lifecycle Services.

**Note:** Retail Server is not supported in LBD deployments at this time. 

[![Service fabric standalone cluster](./media/lbd-overview-01.png)](./media/lbd-overview-01.png)

Application lifecycle management scenarios for LBD deployments use Lifecycle Services like the cloud service. Customers can use proven tools and methodologies to manage their on-premises deployments. 

[![Application lifecycle management for Local Business Data deployments](./media/lbd-overview-02.png)](./media/lbd-overview-02.png)

## Data storage 
The LBD deployment option stores core customer data on-premises. LBD deployments depend on cloud services to manage the application lifecycle and support scenarios.  These services enable initial onboarding, initiation and tracking of support incidents, and service updates and upgrades. Data supplied to supporting services is stored at rest in the United States. The following table provides more information. 

| Supporting services                   | Data at rest in the United States                                                                                                                                                                                                                                                            |
|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Microsoft Dynamics Lifecycle Services | Project content and files are stored within a project. This includes application configuration data, code, metadata, and data assets that comprise the application, and business process models. Also included is anonymized user activity logs and information that is collected during the onboarding process. |
| Microsoft Office signup portal        | Customer information that is collected during the onboarding process.                                                                                                                                                                                                                                 |
| Microsoft Azure Active Directory      | Authentication for Dynamics Lifecycle Services and Visual Studio Team Services.                                                                                                                                                                                                               |
Additional services or components can be configured to extend the LBD deployment as needed, however configuration choices may cause core customer data to be transferred outside of the customer’s data center. For example, configuring data management features that are used to integrate external services with an LBD deployment may result in the transfer of core customer data outside the on-premises deployment.   

