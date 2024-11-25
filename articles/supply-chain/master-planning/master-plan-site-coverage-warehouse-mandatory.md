---
title: Master planning for site coverage, mandatory warehouse
description: Learn how an item that has the site as coverage dimension is planned, including outlines on conditions involved in master planning scenarios.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: kamaybac
ms.search.form: EcoResStorageDimensionGroup, ReqItemTable
ms.assetid: aa135030-f98c-48bf-902c-e52f680dc247
---

# Master planning for site coverage, mandatory warehouse

[!include [banner](../includes/banner.md)]

This article describes how an item that has the site as coverage dimension is planned. Warehouse is a mandatory dimension.

This master planning scenario involves the following conditions:

-   The site dimension is set to mandatory and must be entered on the demand transaction. This setting can't be modified.
-   The warehouse dimension is set to mandatory and must be entered on the demand transaction.
-   The site dimension is set for coverage planning. Other dimensions may be set for coverage planning also. However, they are not affected by the multisite functionality.
-   The warehouse dimension is not set for coverage planning. Therefore, supply and demand are aggregated by site and, perhaps, other coverage-planned dimensions also.

The following graphic illustrates how master planning proceeds. The parameters that are referred to in the graphic, and their locations, are as follows:
-   Item coverage is defined for the item. Click **Product information management &gt; Products&gt; Released products**. Select the item, and then click **Plan &gt; Item coverage**.
-   Refill relations are defined for the warehouse. Click **Inventory management &gt; Setup &gt; Inventory breakdown &gt; Warehouses**. On the **Master planning** tab, see the **Main warehouse** field group.
-   The default order type is set to Production, Purchase order, or Kanban. Click **Product information management &gt; Products&gt; Released products**. Select the item, and then click **Plan &gt; Default order settings**. In the **Default order settings** form, see the **Default order type**.

![Demand for site coverage warehouse mandatory.](./media/multisitedemandexplosionscenarioforsitecoveragewarehousemandatory.jpg)



## Related information

- [Master planning and multisite functionality overview](master-plan-multisite-functionality.md)
- [Master planning for site and warehouse coverage, warehouse mandatory](master-plan-site-warehouse-coverage-warehouse-mandatory.md)
- [Master planning for site coverage, mandatory warehouse](master-plan-site-coverage-warehouse-mandatory.md)
- [Master planning for site and warehouse coverage, warehouse not mandatory](master-plan-site-warehouse-coverage-warehouse-not-mandatory.md)
- [Determine the BOM version](master-plan-bom-version-determined.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]