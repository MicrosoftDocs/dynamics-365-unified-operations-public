---
# required metadata

title: Cost objects
description: This article provides information about costs objects, and explains how costs and quantities are accumulated. A cost object is an entity that costs and quantities are accumulated for. A cost object entity can be either a product or product variants, such as variants for style and color.  
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventCostOnhandItem
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: ec776b98-813a-490d-848f-468452d98fac
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Cost objects

[!include [banner](../includes/banner.md)]

This article provides information about costs objects, and explains how costs and quantities are accumulated. A cost object is an entity that costs and quantities are accumulated for. A cost object entity can be either a product or product variants, such as variants for style and color.  

## Cost objects

The **Cost objects** page lists all cost objects that are registered on a product. The cost objects are defined by data from the following sources:

-   Product
-   Product dimension group
-   Storage dimension group
-   Tracking dimension group

**Note:** A cost object represents a cost element of the **Direct material** type only. A cost object and an inventory object differ in the way that a cost object is defined by the inventory dimensions that are selected for financial inventory. For example, an item has the following configuration:

-   **Site:** Physical inventory = Yes, Financial inventory = Yes
-   **Warehouse:** Physical inventory = Yes, Financial inventory = No
-   **Batch No.:** Physical inventory = Yes, Financial inventory = No

The following table shows what is a cost object and what is an inventory object.

| Object type      | Item number | Site | Warehouse | Batch No. |
|------------------|-------------|------|-----------|-----------|
| Cost object      | x           | x    |           |           |
| Inventory object | x           | x    |  x        | x         |

## Accumulation of costs and quantities
-   The value in the **Value** fieldis a sum of the following values:
    -   Physical cost amount
    -   Financial cost amount
    -   Adjustments
-   The value in the **Quantity** field is a sum of the following values:
    -   Received
    -   Deducted
    -   Posted quantity
-   The **Average unit cost** field is a calculated field. The value is calculated by dividing the **Value** value by the **Quantity** value.

**Note:** The **Include physical value **parameter has no effect on the preceding calculations.

## Additional resources

[Product dimension group](/dynamicsax-2012/appuser-itpro/about-product-dimensions)

[Storage dimension group](/dynamicsax-2012//storage-dimension-groups-form)

[Tracking dimension group](/dynamicsax-2012//tracking-dimension-groups-form)

[What's new or changed](../../fin-ops-core/fin-ops/get-started/whats-new-changed.md)

[Cost entries](cost-entries.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]