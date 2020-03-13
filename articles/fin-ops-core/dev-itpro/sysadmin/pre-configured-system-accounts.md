---
# required metadata

title: Preconfigured system accounts
description: This topic provides information about the system accounts that are pre-configured on your Finance and Operations environments.
author: laneswenka
manager: AnnBe
ms.date: 11/07/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2017-11-01
ms.dyn365.ops.version: Platform update 13

---

# Preconfigured system accounts

[!include [banner](../includes/banner.md)]

Pre-configured system accounts are included on deployed environments so that Microsoft can manage and operate the Finance and Operations service and provide specific features to customers. The following table provides information about each account, including the purpose and use case for the account.  

> [!IMPORTANT] 
> Do not delete these system accounts. Deleting these accounts will cause a disruption in key functionality provided by Microsoft.

|                               Account detail                               |                                                                    Purpose/use case of the account                                                                    |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                  Axrunner                                  |                                   This account is used to monitor the health of the environment and provide alerts when necessary.                                    |
|                               FRServiceUser                                | This is the Financial Reporting service user account, which is used by the Management Reporter application for integrations with Finance and Operations. |
|                            RetailServiceAccount                            |                              This account is used for Retail services to connect to the Finance and Operations environment.                              |
| SysHealthServiceUser or Axping (depending on the deployed product version) |                           This account is used to monitor the availability and health of the environment and provide alerts when necessary.                           |

