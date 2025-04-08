---
title: Master planning for site and warehouse coverage, warehouse not mandatory
description: Learn how an item that has site and warehouse as coverage dimensions is planned. The warehouse dimension is not mandatory.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: kamaybac
ms.search.form: EcoResStorageDimensionGroup, ReqItemTable
ms.assetid: 92d47bdd-df68-4f60-ac9a-96aa08236c26
---

# Master planning for site and warehouse coverage, warehouse not mandatory

[!include [banner](../includes/banner.md)]

This article describes how an item that has site and warehouse as coverage dimensions is planned. The warehouse dimension is not mandatory.

This master planning scenario involves the following conditions:

-   The site dimension is set to mandatory and must be entered on the demand transaction. This setting can't be modified.
-   The warehouse dimension is not set to mandatory. The warehouse may be known, but it is not used in the master planning calculation.
-   The site and warehouse dimensions are set for coverage planning. Other dimensions may be set for coverage planning also. However, they are not affected by the multisite functionality.

The following graphic illustrates how master planning proceeds. The parameters that are referred to in the graphic, and their locations, are as follows:
-   The warehouse is set to Manual. Click **Inventory management &gt; Setup &gt; Inventory breakdown &gt; Warehouses**. On the **Master planning** FastTab, see the **Manual** field.
-   Item coverage is defined for the item. Click **Product information management &gt; Products&gt; Released products**. Select the item, and then, on the Action Pane, on the **Plan** tab, click **Item coverage**.
-   Refill relations are defined for the warehouse. Click **Inventory management &gt; Setup &gt; Inventory breakdown &gt; Warehouses**. On the **Master planning** FastTab, see the **Main warehouse** field group.
-   The default order type is set to Production, Purchase order, or Kanban. Click **Product information management &gt; Products&gt; Released products**. Select the item, and then, on the Action Pane, on the **Plan** tab, click **Default order settings**. In the **Default order settings** form, see the **Default order type**.

![Demand for site and warehouse, warehouse not.](./media/multisitedemandexplosionscenarioforsiteandwarehousecoveragewarehousenotmandatory.jpg)



## Related information

- [Master planning and multisite functionality overview](master-plan-multisite-functionality.md)
- [Master planning for site coverage, mandatory warehouse](master-plan-site-warehouse-coverage-warehouse-mandatory.md)
- [Master planning for site and warehouse coverage, warehouse mandatory](master-plan-site-coverage-warehouse-mandatory.md)
- [Master planning for site and warehouse coverage, warehouse not mandatory](master-plan-site-coverage-warehouse-not-mandatory.md)
- [Determine the BOM version](master-plan-bom-version-determined.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]