---
# required metadata

title: Information used in BOM calculations with standard costs
description: Bills of material (BOM) calculations use data from several sources to calculate the standard costs of a manufactured item. The sources include information about items, bills routings, indirect cost calculation formulas, and the costing version.
author: JennySong-SH
ms.date: 10/25/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BOMCalcDialog, BOMCalcGroup, BOMCalcTable, ProdParmBOMCalc
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: ca17e6dd-b16a-4bbc-8682-b16345ab9906
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Information used in BOM calculations with standard costs

[!include [banner](../includes/banner.md)]

Bills of material (BOM) calculations use data from several sources to calculate the standard costs of a manufactured item. The sources include information about items, bills routings, indirect cost calculation formulas, and the costing version.

The purchased item information that is used in a standard cost BOM calculation includes the following:
-   Cost − A purchased item’s costs are maintained as site-specific cost records in a costing version for standard costs. Each cost record has an effective date, and the BOM calculation date determines which cost record will be used. For example, a BOM calculation with a future calculation date might use a cost record with a pending status and a future effective date.
-   Cost group − The cost group that is assigned to a purchased item provides the basis for cost segmentation in the calculated costs of a manufactured item.
-   Warning conditions that are embedded in the item’s BOM calculation group enable the BOM calculation to identify potential problems. This can be when the purchased item has a zero cost, a zero quantity in a BOM, or an out-of-date cost record. The applicable warning conditions can be overridden when initiating a BOM calculation.

The manufactured item information that is used in a standard cost BOM calculation includes the following:
-   Standard order quantity for inventory − The item’s standard order quantity for inventory, acts as the default accounting lot size for amortizing constant costs in a BOM calculation. The accounting lot size will also reflect the order quantity multiple if it is specified.
-   Warning conditions that are embedded in the item’s BOM calculation group enable the BOM calculation to identify potential problems. One example could be that the manufactured item does not have a BOM or route. The applicable warning conditions can be overridden when initiating a BOM calculation.

The bill of material information that is used in a standard cost BOM calculation includes the following:
-   BOM version − The BOM version that is assigned to the manufactured item has effective from and to dates, and a status for approved and active. The bill version can be company-wide or site-specific, and it can optionally reflect quantity breakpoints.
-   BOM line item quantity − A component typically has a variable quantity required, but it can be a constant. The component quantity is typically expressed for producing one parent item, but it may be expressed per 100 or per 1000 to handle decimal precision issues. The component quantity can also be calculated based on measurements.
-   BOM line item scrap − A component can have a variable or constant quantity for planned scrap.
-   BOM line item valid dates − A component can have valid from and to dates.
-   BOM line item type of production − The costing lot size for amortizing constant costs will reflect the BOM calculation quantity and a make-to-order explosion mode, because the BOM calculation assumes that the manufactured component will be produced to the exact quantity instead of its standard order quantity.
-   Sub-BOM for a manufactured component − A manufactured component can optionally have a specified BOM version, which would be used instead of the item’s current active BOM version in a BOM calculation.
-   Sub-route for a manufactured component − A manufactured component can optionally have a specified route version, which would be used instead of the item’s current active route version in a BOM calculation.
-   Operation number and the impact of operation scrap percentages − The operation number links a component to a specific operation, and operations can have a scrap percentage. The linkage enables BOM calculations to account for scrap percentages and cumulative scrap percentages across multiple operations on the component’s required quantity.
-   Ignore BOM line item in cost calculations − A component can be ignored for BOM calculation purposes.

The operations resource information that is used in a standard cost BOM calculation includes:
-   Hourly costs − The hourly costs that are associated with an operations resource are expressed as cost categories that are assigned to set up time and run time. These cost categories should be identified for resource groups and operations resources. The hourly costs that are associated with a cost category can be site-specific or company-wide.
-   Per unit costs − Some manufacturing environments assign operations resource costs per unit of output, which would be expressed as a different cost category for quantity. For example, the quantity-related costs can reflect piece rates for labor, or a paint manufacturer may assign operations resource costs per gallon of output.
-   Overriding operations resource information on routing operations − The resource information about cost categories will be inherited by operations, where it can be overridden. BOM calculations will use the cost category information that is specified on the routing operations.
-   Cost group for a cost category − The cost group that is assigned to a cost category provides cost segmentation in the calculated costs of a manufactured item. For example, different cost groups might be used to segment the calculated costs that are associated with machines and labor or with setup and run time.

The route information that is used in a standard cost BOM calculation includes:
-   Route version − The route version that is assigned to the manufactured item has effective from and to dates, and a status for approved and active. The route version must be site-specific, and it can optionally reflect quantity breakpoints.
-   Routing operation time − The time can be specified for runtime and setup time. The hourly time is typically expressed for producing one parent item, but it may be expressed per 100 or per 1000 to handle decimal precision issues.
-   Routing operation time for secondary resources − A secondary resource has the same operation number as the primary resource, and the same routing operation time. For example, an operation might require a machine as the primary resource and labor and tools as secondary resources.
-   Routing operation scrap percentage − BOM calculations will account for scrap percentages and cumulative scrap percentages across multiple operations. This applies to the required time for routing operations and the required quantity for components that are linked to operation numbers.
-   Cost categories for a routing operation − Operations resource information about cost categories will be inherited by operations, where it can be overridden. BOM calculations will use the cost category information that is specified on the routing operations.

The manufacturing overhead information that is used in a standard cost BOM calculation includes:
-   Surcharge − A surcharge calculation formula reflects a percentage of value, such as 100 percent, that is tied to a specific cost group, such as labor.
-   Rate − A rate calculation formula reflects an amount per unit, such as USD 10.00 per hour, that is tied to a specific cost group, such as labor.
-   Time-based versus material-based overhead − The manufacturing overhead can be tied to routing operations or material components.

The costing version information that is used in a standard cost BOM calculation includes:
-   Costing type − The costing version must contain standard costs. Several restrictions apply to BOM calculations that use standard costs. For example, these restrictions specify that miscellaneous charges must be included in unit costs and that the BOM calculation explosion mode must be single level.
-   Mandated fallback principle − The costing version can mandate the use of a fallback principle, such as using a specified costing version or the active cost records. The mandated fallback principle typically applies to a costing version that represents the incremental updates in a two-version approach for cost updates.
-   Blocking flag for pending costs − A blocking flag can prevent BOM calculations of the pending cost for manufactured items.
-   Specified from-date − The specified from-date will act as the default calculation date for all BOM calculations that involve the costing version.
-   Specified site − A specified site will limit BOM calculations to the single site.
-   Content of the costing version must include costs − The content must include costs. It can optionally include sales prices in order to calculate suggested sales prices for manufactured items.

Several sources of information can be specified when initiating a BOM calculation. This includes the site, the calculation date, and the costing version.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]