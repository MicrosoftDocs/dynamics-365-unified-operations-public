---
# required metadata

title: Master planning for site coverage, warehouse not mandatory | Microsoft Docs
description: This topic describes how an item that has the site dimension set for coverage is planned.
author: YuyuScheller
manager: AnnBe
ms.date: 2015-09-10 08:46:21
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: EcoResStorageDimensionGroup, ReqItemTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: YuyuScheller
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 2474
ms.assetid: a745e0b3-d3cf-41c4-97a0-7ac70160e397
ms.region: Global
ms.industry: Manufacturing
ms.author: roxanad

---

# Master planning for site coverage, warehouse not mandatory

This topic describes how an item that has the site dimension set for coverage is planned.

This master planning scenario involves the following conditions:

-   The site dimension is set to mandatory and must be entered on the demand transaction.
-   The warehouse dimension is not set to mandatory. The warehouse may be known, but it is not used in the master planning calculation.
-   The site dimension is set for coverage planning.
-   The warehouse dimension is not set for coverage planning. Therefore, supply and demand are aggregated by site and, perhaps, other coverage-planned dimensions also.

The following graphic illustrates how master planning proceeds. The parameters that are referred to in the graphic, and their locations, are as follows:
-   Item coverage is defined for the item. Click **Product information management &gt; Products&gt; Released products**. Select the item, and then click **Plan &gt; Item coverage**.
-   Refill relations are defined for the warehouse. Click **Inventory management &gt; Setup &gt; Inventory breakdown &gt; Warehouses**. On the **Master planning** tab, see the **Main warehouse** field group.
-   The default order type is set to Production, Purchase order or Kanban. Click **Product information management &gt; Products&gt; Released products**. Select the item, and then click **Plan &gt; Default order settings**. In the **Default order settings** form, see the **Default order type** field.

![Demand for site coverage warehouse not mandatory](./media/multisitedemandexplosionscenarioforsitecoveragewarehousenotmandatory.jpg)



See also
--------

[Master planning and multisite functionality](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-and-multisite-functionality)

[Master planning - site coverage, warehouse mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-coverage-warehouse-mandatory)

[Master planning - site and warehouse coverage, warehouse not mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-and-warehouse-coverage-warehouse-not-mandatory)

[Master planning - site and warehouse coverage, warehouse mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-and-warehouse-coverage-warehouse-mandatory)

[Master planning - how the BOM version is determined](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-how-the-bom-version-is-determined)

