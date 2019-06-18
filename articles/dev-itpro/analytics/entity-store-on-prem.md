---
# required metadata

title: PowerBI.com integration with on-premises environments
description: This topic provides information about how to enable Entity Store for on-premises deployments.
author: MilindaV
manager: AnnBe
ms.date: 06/17/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: EntityStoreOnPrem
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 27661
ms.assetid: 861cfa94-c6f3-4c84-89ac-22c78bf6b7a4
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2019-06-17
ms.dyn365.ops.version: AX 7.0.0

---

# PowerBI.com integration with on-premises environments

[!include [banner](../includes/banner.md)]

Cloud version on Dynamics 365 for Finance and Operations (F&O) provides several features that enable deeper integration with PowerBI. Some of these capabilities are not yet implemented on Dynamics 365 for Finance and Operations on-premises deployments. With the availability of Entity store in on-premises deployments, customers can leverage PowerBI.com for reporting and analytics with F&O data. 
This document outlines the Analytics capabilities available in on-premises deployments with Platform update 26 and later.

| Feature/capability                                                     | Cloud     | On-premises (Platform update 26 or later)                                                         |
|------------------------------------------------------------------------|-----------|---------------------------------------------------------------------------------------------------|
| Analytical workspaces                                                  | Available | **Not yet implemented** <br> Customers can use the reports built on Entity store with PowerBI.com.                                                                               |
| Pin reports, tiles, and dashboards from PowerBI.com into the client    | Available | **Not yet implemented**                                                                               |
| Author and distribute PowerBI reports with Finance and Operations data | Available | **Available** <br> Customers can modify ready-made reports and create new reports by using Entity store on-premises. |
| Extract Finance and Operations data into data warehouses               | Available | **Available**                                                                                        |

## Enable Entity Store on-premises 
This topic supplements the topic, [Set up and deploy on-premises environments](../deployment/setup-deploy-on-premises-pu12.md). The section numbers in this topic, correspond to the sections in that topic.

## [3. Plan your users and service accounts](../deployment/setup-deploy-on-premises-pu12.md#plan-your-users-and-service-accounts)

| User account               | Type     | Purpose                                                                                                                                              | User name       |
|----------------------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| AOS SQL AXDW DB Admin user | SQL user | Finance and Operations uses this user to populate the AXDW database. The user is optional and must be created only if you want Entity Store support. | axdwadmin       |
| AOS SQL AXDW FB Admin user | SQL user | Finance and Operations uses this user to populate the AXDW database. The user is optional and must be created only if you want Entity Store support. | axdwruntimeuser |
