---
# required metadata

title: Microsoft Dynamics 365 Finance + Operations (on-premises) supported software
description: This article explains which software component versions are compatible with Microsoft Dynamics 365 Finance + Operations (on-premises).
author: faix
ms.date: 9/21/2022
ms.topic: article
ms.prod: dynamics-365 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this article to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2021-06-30 
ms.dyn365.ops.version: Platform update 44 
search.app:
  - financeandoperationsonprem-docs
---

# Microsoft Dynamics 365 Finance + Operations (on-premises) supported software

[!include [banner](../includes/banner.md)]

This article explains which versions of dependent software are compatible with different versions of Microsoft Dynamics 365 Finance + Operations (on-premises).

## Microsoft Windows Server

Both Microsoft Windows Server Standard and Microsoft Windows Server Datacenter are supported.

| Version                       | Supported since  | End of life   |
|-------------------------------|------------------|---------------|
| Microsoft Windows Server 2019 | 10.0.17          | Not available |
| Microsoft Windows Server 2016 | Original release | 10.0.26       |

> [!NOTE]
> Only en-US operating system installations are supported.

## Microsoft SQL Server

Both Microsoft SQL Server Standard Edition and Enterprise Edition are supported.

This section covers the following SQL Server components:

- Database Engine
- SQL Server Reporting Services (SSRS)
- SQL Server Integration Services (SSIS)

| Version                       | Supported since  | End of life   |
|-------------------------------|------------------|---------------|
| Microsoft SQL Server 2019     | 10.0.21          | Not available |
| Microsoft SQL Server 2016 SP2 | 10.0.9           | 10.0.28       |
| Microsoft SQL Server 2016 SP1 | Original release | 10.0.14       |

> [!IMPORTANT]
> Using multiple versions of Microsoft SQL Server throughout a single environment is not supported.

## Active Directory Federation Services (AD FS)

Active Directory Federation Services (AD FS) is a server role that can be installed on a machine running Windows Server. 

| Version                                                     | Supported since  | End of life   |
|-------------------------------------------------------------|------------------|---------------|
| Active Directory Federation Services on Windows Server 2019 | 10.0.17          | Not available |
| Active Directory Federation Services on Windows Server 2016 | Original release | 10.0.26       |

> [!IMPORTANT]
> - AD FS on Windows Server 2016 only supports authentication through the Azure Active Directory Authentication Library (ADAL).
> - In order to uptake the upcoming migration to the Microsoft Authentication Library, you need to deploy your AD FS on Windows Server 2019 
> (MSAL). For more information, see [Migrate applications to the Microsoft Authentication Library (MSAL)](/azure/active-directory/develop/msal-migration).
> - After July 1, 2022, any customers still using AD FS on Windows Server 2016 will no longer be able to use the Office add-ins. This is irrespective of the Microsoft Dynamics 365 Finance + Operations (on-premises) version that they are running.

## Minimum Azure Service Fabric runtime

Your Service Fabric cluster should always be on a supported version according to the official documentation, [Service Fabric supported versions](/azure/service-fabric/service-fabric-versions).

| Minimum version            | Required since |
|----------------------------|----------------|
| Service Fabric runtime 8.2 | 10.0.30        |
| Service Fabric runtime 8.0 | 10.0.24        |
| Service Fabric runtime 7.2 | 10.0.17        |
| Service Fabric runtime 7.1 | 10.0.14        |

## Minimum Microsoft .NET Framework runtime

The requirements for .NET Framework are specified on a per node basis. For specific features and versions, see [Set up and deploy on-premises environments (Platform update 41 and later)](./setup-deploy-on-premises-pu41.md#prerequisites).

| Minimum version                        | Required since |
|----------------------------------------|----------------|
| Microsoft .NET Framework version 4.7.2 | 10.0.11        |

## Microsoft Office Server

Office Server is an optional component. For more information, see [Configure document preview](../../fin-ops/organization-administration/configure-document-management.md#for-a-microsoft-dynamics-365-finance--operations-on-premises-environment).

| Version                      | Supported since | End of life   |
|------------------------------|-----------------|---------------|
| Microsoft Office Server 2017 | 10.0.0          | Not available |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
