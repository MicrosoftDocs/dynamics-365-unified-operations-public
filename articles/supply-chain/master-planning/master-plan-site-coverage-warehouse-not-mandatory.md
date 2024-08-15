---
title: Master planning for site coverage, warehouse not mandatory
description: Learn how an item that has the site dimension set for coverage is planned, including outlines on conditions involved in master planning scenarios.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: kamaybac
ms.search.form: EcoResStorageDimensionGroup, ReqItemTable
ms.assetid: 316da918-67ae-43c5-baea-00ae559e29b0
---

# Master planning for site coverage, warehouse not mandatory

[!include [banner](../includes/banner.md)]

This article describes how an item that has the site dimension set for coverage is planned.

This master planning scenario involves the following conditions:

-   The site dimension is set to mandatory and must be entered on the demand transaction.
-   The warehouse dimension is not set to mandatory. The warehouse may be known, but it is not used in the master planning calculation.
-   The site dimension is set for coverage planning.
-   The warehouse dimension is not set for coverage planning. Therefore, supply and demand are aggregated by site and, perhaps, other coverage-planned dimensions also.

The following graphic illustrates how master planning proceeds. The parameters that are referred to in the graphic, and their locations, are as follows:
-   Item coverage is defined for the item. Click **Product information management &gt; Products&gt; Released products**. Select the item, and then click **Plan &gt; Item coverage**.
-   Refill relations are defined for the warehouse. Click **Inventory management &gt; Setup &gt; Inventory breakdown &gt; Warehouses**. On the **Master planning** tab, see the **Main warehouse** field group.
-   The default order type is set to Production, Purchase order or Kanban. Click **Product information management &gt; Products&gt; Released products**. Select the item, and then click **Plan &gt; Default order settings**. In the **Default order settings** form, see the **Default order type** field.

![Demand for site coverage warehouse not mandatory.](./media/multisitedemandexplosionscenarioforsitecoveragewarehousenotmandatory.jpg)



## Related information

- [Master planning and multisite functionality overview](master-plan-multisite-functionality.md)
- [Master planning for site and warehouse coverage, warehouse mandatory](master-plan-site-coverage-warehouse-mandatory.md)
- [Master planning for site coverage, mandatory warehouse](master-plan-site-warehouse-coverage-warehouse-not-mandatory.md)
- [Master planning for site coverage, warehouse not mandatory](master-plan-site-warehouse-coverage-warehouse-mandatory.md)
- [Determine the BOM version](master-plan-bom-version-determined.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]