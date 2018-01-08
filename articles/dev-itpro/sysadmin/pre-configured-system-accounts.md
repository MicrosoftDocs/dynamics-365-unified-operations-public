---
# required metadata

title: Pre-configured system accounts
description: This topic provides information about the system accounts that are pre-configured on your Dynamics 365 for Finance and Operations, Enterprise edition environments.
author: manalidongre
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
ms.reviewer: kfend
ms.search.scope: 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2017-11-01
ms.dyn365.ops.version: Platform update 13

---

# Pre-configured system accounts

[!include[banner](../includes/banner.md)]

Pre-configured system accounts are included on deployed environments so that Microsoft can manage and operate the Dynamics 365 for Finance and Operations, Enterprise edition service and provide specific features to customers. The following table provides information about each account, including the purpose and use case for the account.  

> [!IMPORTANT] 
> Do not delete these system accounts. Deleting these accounts will cause a disruption in key functionality provided by Microsoft.

| Account detail                                                             | Purpose/use case of the account                                                                                                                           |
|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Axrunner                                                                   | This account is used to monitor the health of the environment and provide alerts when necessary.                                                          |
| FRServiceUser                                                              | This is the Financial Reporting service user account, which is used by the Management Reporter application for integrations with Dynamics 365 for Unified Operations. |
| RetailServiceAccount                                                       | This account is used for Retail services to connect to the Dynamics 365 for Unified Operations environment.                                                   |
| SysHealthServiceUser or Axping (depending on the deployed product version) | This account is used to monitor the availability and health of the environment and provide alerts when necessary.                                       |
