---
# required metadata

title: Master planning for site and warehouse coverage, warehouse mandatory | Microsoft Docs
description: This topic describes how an item that has site and warehouse as coverage dimensions is planned. The warehouse dimension is mandatory.
author: YuyuScheller
manager: AnnBe
ms.date: 2015-09-10 08:53:02
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
ms.custom: 2554
ms.assetid: 7a8230a4-93e0-4166-9448-81ec2e5d8031
ms.region: Global
ms.industry: Manufacturing
ms.author: roxanad

---

# Master planning for site and warehouse coverage, warehouse mandatory

This topic describes how an item that has site and warehouse as coverage dimensions is planned. The warehouse dimension is mandatory.

This master planning scenario involves the following conditions:

-   The site dimension is set to mandatory and must be entered on the demand transaction.
-   The warehouse dimension is set to mandatory and must be entered on the demand transaction.
-   The site and warehouse dimensions are set for coverage planning. Other dimensions may be set for coverage planning also. However, they are not affected by the multisite functionality.

The following graphic illustrates how master planning proceeds. The parameters that are referred to in the graphic, and their locations, are as follows:
-   The warehouse is set to **Manual**. Click **Inventory management &gt; Setup &gt; Inventory breakdown &gt; Warehouses**. On the **Master planning** FastTab, see the **Manual** field.
-   Item coverage is defined for the item. Click **Product information management &gt; Products&gt; Released products**. Select the item, and then, on the Action pane, on the **Plan** tab, click **Item coverage**.
-   Refill relations are defined for the warehouse. Click **Inventory management &gt; Setup &gt; Inventory breakdown &gt; Warehouses**. On the **Master planning** FastTab, see the **Main warehouse** field group.
-   The default order type is set to Production, Purchase order, or Kanban. Click **Product information management &gt; Products&gt; Released products**. Select the item, and then, on the Action pane, on the **Plan** tab, click **Default order settings**. In the **Default order settings** form, see the **Default order type**.

![Demand site and warehouse coverage, wh mandatory](./media/multisitedemandexplosionscenarioforsiteandwarehousecoveragewarehousemandatory.jpg)



See also
--------

[Master planning and multisite functionality](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-and-multisite-functionality)

[Master planning - site coverage, warehouse mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-coverage-warehouse-mandatory)

[Master planning - site coverage, warehouse not mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-coverage-warehouse-not-mandatory)

[Master planning - site and warehouse coverage, warehouse not mandatory](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-site-and-warehouse-coverage-warehouse-not-mandatory)

[Master planning - How the BOM version is determined](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/master-planning/master-planning-how-the-bom-version-is-determined)

