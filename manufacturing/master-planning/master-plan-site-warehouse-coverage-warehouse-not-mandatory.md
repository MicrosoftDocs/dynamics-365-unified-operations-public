---
# required metadata

title: Master planning for site and warehouse coverage, warehouse not mandatory | Microsoft Docs
description: This topic describes how an item that has site and warehouse as coverage dimensions is planned. The warehouse dimension is not mandatory.
author: YuyuScheller
manager: AnnBe
ms.date: 2015-09-10 08:49:16
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
ms.custom: 2514
ms.assetid: 20a08838-8db0-4481-8327-01f98464a78c
ms.region: Global
ms.industry: Manufacturing
ms.author: roxanad

---

# Master planning for site and warehouse coverage, warehouse not mandatory

This topic describes how an item that has site and warehouse as coverage dimensions is planned. The warehouse dimension is not mandatory.

This master planning scenario involves the following conditions:

-   The site dimension is set to mandatory and must be entered on the demand transaction. This setting can't be modified.
-   The warehouse dimension is not set to mandatory. The warehouse may be known, but it is not used in the master planning calculation.
-   The site and warehouse dimensions are set for coverage planning. Other dimensions may be set for coverage planning also. However, they are not affected by the multisite functionality.

The following graphic illustrates how master planning proceeds. The parameters that are referred to in the graphic, and their locations, are as follows:
-   The warehouse is set to Manual. Click **Inventory management &gt; Setup &gt; Inventory breakdown &gt; Warehouses**. On the **Master planning** FastTab, see the **Manual** field.
-   Item coverage is defined for the item. Click **Product information management &gt; Products&gt; Released products**. Select the item, and then, on the Action pane, on the **Plan** tab, click **Item coverage**.
-   Refill relations are defined for the warehouse. Click **Inventory management &gt; Setup &gt; Inventory breakdown &gt; Warehouses**. On the **Master planning** FastTab, see the **Main warehouse** field group.
-   The default order type is set to Production, Purchase order, or Kanban. Click **Product information management &gt; Products&gt; Released products**. Select the item, and then, on the Action pane, on the **Plan** tab, click **Default order settings**. In the **Default order settings** form, see the **Default order type**.

![Demand for site and warehouse, warehouse not](./media/multisitedemandexplosionscenarioforsiteandwarehousecoveragewarehousenotmandatory.jpg)

 
-



See also
--------

[Master planning and multisite functionality](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-and-multisite-functionality)

[Master planning - site and warehouse coverage, warehouse mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-and-warehouse-coverage-warehouse-mandatory)

[Master planning - site coverage, warehouse mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-coverage-warehouse-mandatory)

[Master planning - site coverage, warehouse not mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-coverage-warehouse-not-mandatory)

[Master planning - How the BOM version is determined](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-how-the-bom-version-is-determined)

