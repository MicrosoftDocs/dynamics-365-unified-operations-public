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

| Account | Purpose/use case of the account|
|---|---|
| Axrunner | Used to monitor the health of the environment and provide alerts when necessary.<br><br>**Note**: This account is deprecated with self-service environments and is no longer used. |
| FRServiceUser | The Financial Reporting service user account, which is used by the Management Reporter application for integrations with Finance and Operations apps. |
| PowerPlatformS2S | Used to connect dual-write and virtual tables for Finance and Operations apps to Microsoft Dataverse.|
| RetailServiceAccount | Used for Retail services to connect to the Finance and Operations environment. |
| ScaleUnitManagement | Used for communication with the Scale Unit Manager portal. This account is automatically added when upgrading to 10.0.23. |
| ScaleUnitPipeline | Used to maintain and keep track of communication between the scale units. This account is automatically added when upgrading to 10.0.19. |
| SysHealthServiceUser or Axping (depending on the deployed product version) | Used to monitor the availability and health of the environment and provide alerts when necessary. |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
