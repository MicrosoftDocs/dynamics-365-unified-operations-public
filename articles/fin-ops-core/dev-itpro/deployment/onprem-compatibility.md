---
title: Microsoft Dynamics 365 Finance + Operations (on-premises), Microsoft Dynamics 365 Finance, and Microsoft Dynamics 365 Supply Chain Management supported software
description: Learn about which software component versions are compatible with Microsoft Dynamics 365 Finance + Operations (on-premises),  Microsoft Dynamics 365 Finance, and Microsoft Dynamics 365 Supply Chain Management non-managed environments.
author: faix
ms.author: osfaixat
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 09/15/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-06-30
ms.dyn365.ops.version: Platform update 44 
ms.service: dynamics-365-op
---

# Microsoft Dynamics 365 Finance + Operations (on-premises), Microsoft Dynamics 365 Finance, and Microsoft Dynamics 365 Supply Chain Management supported software

[!include [banner](../includes/banner.md)]

This article explains which versions of dependent software are compatible with different versions of Microsoft Dynamics 365 Finance + Operations (on-premises). These software requirements (where applicable) are relevant to all non-Microsoft managed environments, including development boxes, cloud-hosted environments, and similar setups.

## All non-Microsoft managed environments

### Microsoft Windows Server

Both Microsoft Windows Server Standard and Microsoft Windows Server Datacenter are supported.

| Version                       | Supported since  | End of life   |
|-------------------------------|------------------|---------------|
| Microsoft Windows Server 2022 | 10.0.38          | Not available |
| Microsoft Windows Server 2019 | 10.0.17          | 10.0.41       |
| Microsoft Windows Server 2016 | Original release | 10.0.26       |

> [!NOTE]
> Only en-US operating system installations are supported.

### Microsoft SQL Server

#### Software
Both Microsoft SQL Server Standard Edition and Enterprise Edition are supported.

This section covers the following SQL Server components:

- Database Engine
- SQL Server Reporting Services (SSRS)
- SQL Server Integration Services (SSIS)

| Version                          | Supported since  | End of life   |
|----------------------------------|------------------|---------------|
| Microsoft SQL Server 2022 (CU12) | 10.0.39          | Not available |
| Microsoft SQL Server 2019        | 10.0.21          | 10.0.44       |
| Microsoft SQL Server 2016 SP2    | 10.0.9           | 10.0.28       |

> [!IMPORTANT]
> Using multiple versions of Microsoft SQL Server throughout a single environment is not supported.

#### Database Collation

Finance + Operations (on-premises) supports a limited set of collations. The following table lists the supported collations.

> [!IMPORTANT]
> The Orchestrator database used by the local agent must use the `SQL_Latin1_General_CP1_CI_AS` collation.

| Name                                            | Supported since  | Notes         |
|-------------------------------------------------|------------------|---------------|
| Chinese_Simplified_Pinyin_160_CI_AS_SC_UTF8     | 10.0.40          | Supported only on SQL Server 2022 CU12 and later |
| SQL_Latin1_General_CP1_CI_AS                    | Original release |               |

#### High Availability 

You should always utilize SQL Server in either a cluster or mirroring setup for production environments. 

> [!IMPORTANT]
> Database failover is only supported in an active or passive configuration. Read-only replicas aren't supported.

### Minimum Microsoft .NET Framework runtime

The requirements for the .NET Framework are specified on a per-node basis. For specific features and versions, see [Set up and deploy on-premises environments](./setup-deploy-on-premises-latest.md#prerequisites).

| Minimum version                        | Required since |
|----------------------------------------|----------------|
| Microsoft .NET Framework version 4.8.0 | 10.0.42        |
| Microsoft .NET Framework version 4.7.2 | 10.0.11        |

### Minimum Visual C++ Redistributable runtime

The requirements for the Visual C++ Redistributable are specified on a per-node basis. For specific features and versions, see [Set up and deploy on-premises environments](./setup-deploy-on-premises-latest.md#prerequisites).

>[!NOTE]
>The Visual C++ Redistributable 2015-2022 is a unified package that replaces the older Visual C++ Redistributable 2015-2019 and Visual C++ Redistributable 2017 packages.

| Minimum version                                                 | Required since   | Not required after |
|-----------------------------------------------------------------|------------------|--------------------|
| Microsoft Visual C++ Redistributable 2015-2022 (v14.44.35208.0) | 10.0.45          |                    |
| Microsoft Visual C++ Redistributable 2015-2022 (v14.34.31945.0) | 10.0.36          | 10.0.44            |
| Microsoft Visual C++ Redistributable 2015-2022 (v14.32.31326.0) | 10.0.31          | 10.0.35            |
| Microsoft Visual C++ Redistributable 2015-2019 (v14.25.28508.3) | 10.0.17          | 10.0.30            |
| Microsoft Visual C++ Redistributable 2017                       | 10.0.0           | 10.0.16            |
| Microsoft Visual C++ Redistributable 2013                       | Original release |                    |


## On-premises environments only

### Active Directory Federation Services (AD FS)

Active Directory Federation Services (AD FS) is a server role that can be installed on a machine running Windows Server. 

| Version                                                     | Supported since  | End of life   |
|-------------------------------------------------------------|------------------|---------------|
| Active Directory Federation Services on Windows Server 2022 | 10.0.38          | Not available |
| Active Directory Federation Services on Windows Server 2019 | 10.0.17          | Not available |
| Active Directory Federation Services on Windows Server 2016 | Original release | 10.0.26       |

> [!IMPORTANT]
> - AD FS on Windows Server 2016 only supports authentication through the Microsoft Entra Authentication Library (ADAL).
> - In order to uptake the upcoming migration to the Microsoft Authentication Library, you need to deploy your AD FS on Windows Server 2019 
> (MSAL). For more information, see [Migrate applications to the Microsoft Authentication Library (MSAL)](/azure/active-directory/develop/msal-migration).
> - After July 1, 2022, any customers still using AD FS on Windows Server 2016 will no longer be able to use the Office add-ins. This is irrespective of the Microsoft Dynamics 365 Finance + Operations (on-premises) version that they are running.

## Minimum Azure Service Fabric runtime

Your Service Fabric cluster should always be on a supported version according to the official documentation, [Service Fabric supported versions](/azure/service-fabric/service-fabric-versions).

| Minimum version             | Required since |
|-----------------------------|----------------|
| Service Fabric runtime 10.0 | 10.0.41        |
| Service Fabric runtime 8.2  | 10.0.30        |
| Service Fabric runtime 8.0  | 10.0.24        |

## Microsoft Office Server

Office Server is an optional component. For more information, see [Configure document preview](../../fin-ops/organization-administration/configure-document-management.md#for-a-microsoft-dynamics-365-finance--operations-on-premises-environment).

| Version                      | Supported since | End of life   |
|------------------------------|-----------------|---------------|
| Microsoft Office Server 2017 | 10.0.0          | Not available |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
