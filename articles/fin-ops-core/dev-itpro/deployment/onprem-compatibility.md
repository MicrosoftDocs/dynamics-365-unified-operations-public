---
# required metadata

title: Microsoft Dynamics 365 for Finance and Operations (onpremises) supported software
description: This topic explains which software component versions are compatible with Microsoft Dynamics 365 for Finance and Operations (onpremises).
author: faix
ms.date: 06/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
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

---

# Microsoft Dynamics 365 for Finance and Operations (onpremises) supported software

[!include [banner](../includes/banner.md)]

This topic explains which versions of dependent software are compatible with different versions of Microsoft Dynamics 365 for Finance and Operations (onpremises).

## Microsoft Windows Server

| Version                       | Supported since    | End of support     |
|-------------------------------|--------------------|--------------------|
| Microsoft Windows Server 2019 | platform update 41 | N/A                |
| Microsoft Windows Server 2016 | original release   | platform update 50 |

## Microsoft SQL Server

This covers the following components:
 - Database Engine
 - SQL Server Reporting Services
 - SQL Server Integration Services

| Version                       | Supported since    | End of support     |
|-------------------------------|--------------------|--------------------|
| Microsoft SQL Server 2016 SP2 | platform update 33 | N/A                |
| Microsoft SQL Server 2016 SP1 | original release   | platform update 38 |

## Minimum Service Fabric runtime

Your Service Fabric cluster should always be on a supported version according to the official documentation: [Service Fabric supported versions](/azure/service-fabric/service-fabric-versions)

| Minimum Version            | Required since       |
|----------------------------|----------------------|
| Service Fabric runtime 7.2 | platform update 41   |
| Service Fabric runtime 7.1 | platform update 38   |

## Microsoft Office Server

This is an optional component. For more information see [Configure document preview](../../fin-ops/organization-administration/configure-document-management#for-a-microsoft-dynamics-365-finance--operations-on-premises-environment)

| Version                      | Supported since    | End of support |
|------------------------------|--------------------|----------------|
| Microsoft Office Server 2017 | platform update 12 | N/A            |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]