---
# required metadata

title: Preconfigured system accounts
description: This article provides information about the system accounts that are preconfigured on your finance and operations environments.
author: jaredha
ms.date: 05/26/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: johnmichalak
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

Preconfigured system accounts are included on deployed environments so that Microsoft can manage and operate the finance and operations service and provide specific features to customers. The following table provides information about each account, including the purpose and use case for the account.  

> [!IMPORTANT] 
> Do not delete these system accounts. Deleting these accounts will cause a disruption in key functionality provided by Microsoft.

| Account | Purpose/use case |
|---|---|
| Axrunner | <p>Monitoring the health of the environment, and providing alerts as required.</p><p>**Note:** This account is deprecated for self-service environments and is no longer used.</p> |
| DataSyncFrameworkApp | Used by Microsoft Power Platform apps that are provided by Microsoft to synchronize data from finance and operations virtual tables in Dataverse, based on row version change tracking. |
| DataverseSearchApp | Used for synchronizing data from finance and operations apps to Microsoft Azure Cognitive Services through Dataverse virtual tables that have row version change tracking. This account enables global search functionality for finance and operations data on Microsoft Power Platform apps. |
| DynamicsMaintAppUser | Performing deployment and service operations in finance and operations apps. |
| FRServiceUser | The Financial Reporting service user account. The Management Reporter application uses this account for integrations with finance and operations apps. |
| MonitoringAppUser | Used as part of **Geneva Synthetics Monitoring in FnO** to help identify availability or functionality loss issues in customer environments and contribute to CRI reduction. |
| PowerPlatformApp | Connecting dual-write and virtual tables for finance and operations apps to Dataverse. |
| RetailServiceAccount | Connecting Retail services to the finance and operations environment. |
| ScaleUnitManagement | Communication with the Scale Unit Manager portal. This account is automatically added when you upgrade to version 10.0.23. |
| ScaleUnitPipeline | Maintaining and tracking communication between the scale units. This account is automatically added when you upgrade to version 10.0.19. |
| SysHealthServiceUser or Axping (depending on the deployed product version) | Monitoring the availability and health of the environment, and providing alerts as required. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

