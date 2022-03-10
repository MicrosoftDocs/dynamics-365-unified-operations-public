---
# required metadata

title: Preconfigured system accounts
description: This topic provides information about the system accounts that are pre-configured on your Finance and Operations environments.
author: jaredha
ms.date: 03/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2017-11-01
ms.dyn365.ops.version: Platform update 13

---

# Preconfigured system accounts

[!include [banner](../includes/banner.md)]

Pre-configured system accounts are included on deployed environments so that Microsoft can manage and operate the Finance and Operations service and provide specific features to customers. The following table provides information about each account, including the purpose and use case for the account.  

> [!IMPORTANT] 
> Do not delete these system accounts. Deleting these accounts will cause a disruption in key functionality provided by Microsoft.

| Account | Purpose/use case |
|---|---|
| Axrunner | <p>Monitoring the health of the environment, and providing alerts as required.</p><p>**Note:** This account is deprecated for self-service environments and is no longer used.</p> |
| FRServiceUser | The Financial Reporting service user account. The Management Reporter application uses this account for integrations with Finance and Operations apps. |
| PowerPlatformS2S | Connecting dual-write and virtual tables for Finance and Operations apps to Microsoft Dataverse.|
| RetailServiceAccount | Connecting Retail services to the Finance and Operations environment. |
| ScaleUnitManagement | Communication with the Scale Unit Manager portal. This account is automatically added when you upgrade to version 10.0.23. |
| ScaleUnitPipeline | Maintaining and tracking communication between the scale units. This account is automatically added when you upgrade to version 10.0.19. |
| SysHealthServiceUser or Axping (depending on the deployed product version) | Monitoring the availability and health of the environment, and providing alerts as required. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
