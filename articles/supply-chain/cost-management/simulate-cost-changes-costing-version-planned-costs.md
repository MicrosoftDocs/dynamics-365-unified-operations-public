---
# required metadata

title: Simulate cost changes by using a costing version for planned costs
description: This article explains how you can simulate the effects of cost changes on a manufactured item’s calculated costs by using a separate costing version for planned costs.
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CostingVersion
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 1e41953f-cdb9-4598-b776-46e49383a773
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Simulate cost changes by using a costing version for planned costs

[!include [banner](../includes/banner.md)]

This article explains how you can simulate the effects of cost changes on a manufactured item’s calculated costs by using a separate costing version for planned costs.

You can simulate the effects of cost changes on the calculated costs of a manufactured item by using a separate costing version for planned costs. Use this separate costing version to enter pending cost records that reflect incremental cost changes, and to calculate the cost impact on manufactured items. Because the Active costs fallback principle will be used in the bill of materials (BOM) calculations, only the incremental cost changes must be entered.

## Guidelines for defining the simulation costing version
Use the following guidelines when you define the costing version for simulations:

-   Assign a costing type of **Planned costs**.
-   Assign a meaningful identifier for the costing version, such as **Simulation**.
-   Make sure that the content includes cost records.
-   Allow the entry of cost records. Don't block the entry of pending costs.
-   Allow the entry of cost records for all sites. If you specify a site, you will limit the entry of cost records to that site.
-   Prevent the activation of pending costs. Only pending costs must be entered for cost records in the simulation costing version.
-   Don't enter a "from" date. A calculation date will be entered for each BOM calculation that uses the simulation costing version.
-   Specify a fallback principle of **Current active**. The fallback principle enables incremental cost changes to be entered for simulation purposes but uses the current active costs as the source for all other cost records. We assume that all current active costs exist for all other cost records.
-   Specify a cost price model of **Version cost price**, but don't restrict calculations. For example, the simulations can also use the **BOM calculation group** cost price model to indicate the source of cost contribution data for purchased items.
-   Specify an explosion mode of **Multilevel**, but don't restrict calculations. The simulations can use other explosion modes.

## Costing versions
The following scenarios illustrate how the simulation costing version is used to simulate the impact of cost changes. Before you enter a simulated cost change, delete the pending cost records in the simulation costing version, so that you have a clean starting point. Use the **Item price** page to view and delete the pending cost records that are related to item prices and cost category prices.

-   Simulate the cost change for a purchased item. For example, the cost change might reflect an expected increase or decrease in the cost of critical purchased materials. To define the different cost for a purchased item, use the **Item price** page to enter a pending cost record in the simulation costing version.
-   Simulate the cost change for a cost category. For example, the cost change might reflect an expected increase or decrease in labor rates, or in the hourly rates for operations resources. To define the different cost for a cost category, use the **Cost category price** page to enter a pending cost record in the simulation costing version.
-   Simulate the cost change in an indirect cost calculation formula. For example, the cost change might reflect an expected increase or decrease in manufacturing overhead. To define the change in an indirect cost calculation formula, use the **Costing sheet setup** page to enter a pending cost record in the simulation of costing version, and to validate and save the change.

After you enter the simulated cost changes, calculate the costs for manufactured items that are affected by the cost changes. Use the **Calculation** page for the simulation costing version, and identify the selected manufactured items that will be affected by the cost changes. The BOM calculations apply to all manufactured items unless you select specific items. Alternatively, you can use the BOM calculation option for where-used updates. View the item cost records in the simulation costing version to analyze how the simulated cost changes affected the costs of the selected manufactured items. Use the **Item price** page and the **Calculate item cost** page to view and analyze the costs.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]