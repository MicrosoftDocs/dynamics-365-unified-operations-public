---
# required metadata

title: Master planning and multisite functionality | Microsoft Docs
description: Master planning takes the settings of the site and warehouse inventory dimensions into account. 
author: YuyuScheller
manager: AnnBe
ms.date: 2015-09-10 08:44:29
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: InventLocation, InventSite
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 2434
ms.assetid: b210796b-7891-49db-9234-d2adf7145e57
ms.region: Global
ms.industry: Manufacturing
ms.author: roxanad

---

# Master planning and multisite functionality

Master planning takes the settings of the site and warehouse inventory dimensions into account. 

The site dimension is mandatory, and you can set the warehouse dimension to be mandatory.

When a dimension is mandatory, a dimension value must be entered on all inventory transactions. Therefore, during master planning, the site and the warehouse for the initial demand are known. The site dimension is also consistent so that during the explosion of lower-level demand, the site value does not change.

When the warehouse is not set to mandatory, it may not be known from the initial demand. The planning engine must determine which warehouse to use based on the settings that are defined for the item, individual warehouses, and the details of the order line.

The following wiki articles describe how the planning engine works, when different settings are defined, to determine the warehouse to use.

[Master planning - site and warehouse coverage, warehouse mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-and-warehouse-coverage-warehouse-mandatory)

[Master planning - site coverage, warehouse mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-coverage-warehouse-mandatory)

[Master planning - site and warehouse coverage, warehouse not mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-and-warehouse-coverage-warehouse-not-mandatory)

[Master planning - site coverage, warehouse not mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-coverage-warehouse-not-mandatory)

[Master planning - How the BOM version is determined](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-how-the-bom-version-is-determined)

