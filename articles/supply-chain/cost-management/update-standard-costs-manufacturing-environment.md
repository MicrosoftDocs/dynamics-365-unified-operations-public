---
# required metadata

title: Update standard costs in a manufacturing environment
description: This article provides guidance about how to update standard costs in a manufacturing environment. 
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CostingVersion, InventStdCostConv
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 3a7c3d13-8dbc-442d-a281-ac0ebe99ec83
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Update standard costs in a manufacturing environment

[!include [banner](../includes/banner.md)]

This article provides guidance about how to update standard costs in a manufacturing environment. 

Updates can reflect new items, cost categories, or indirect cost calculation formulas. They can also reflect corrections and cost changes. The type of update affects the steps that you must complete to update standard costs, as illustrated in the following cases:

-   Enter expected standard cost changes for purchased items, and then change the status of the item cost records to **Active** on the appropriate date. However, don't recalculate the costs of manufactured items that use the purchased items.
-   Enter standard costs for a new purchased item, but don't recalculate the costs of manufactured items that have a bill of materials (BOM) version that contains the new purchased item as a component.
-   Correct or change the cost of a purchased item, or change the cost group that is assigned to a purchased item, and calculate the cost for all manufactured items that have a BOM version that contains the purchased item as a component.
-   Change the cost for a cost category, and calculate the cost for all manufactured items that have a route version that contains routing operations that use the cost category.
-   Change the cost categories that are assigned to routing operations or the cost group that is assigned to cost categories. Then calculate the cost for all manufactured items that have a route version that contains routing operations that use the cost category.
-   Change an indirect cost calculation formula, and calculate the cost for all manufactured items that are affected by the change.
-   Change or add a manufacturing site for a manufactured item, and calculate the item's manufactured cost for the site.
-   Calculate, or recalculate, the cost for a manufactured item, and recalculate the cost for all manufactured items that have a BOM version that contains the manufactured item as a component.
-   Calculate costs for a new manufactured item, based on its defined, approved, and active BOM and route information.

Each case requires careful consideration about how to update standard costs.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]