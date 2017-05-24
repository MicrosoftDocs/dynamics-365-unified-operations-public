---
# required metadata

title: BOM calculations
description: The cost roll-up and sales price calculations are known as bill of materials (BOM) calculations, and you initiate them from the Calculations page. This topic provides information about BOM calculations.
author: YuyuScheller
manager: AnnBe
ms.date: 04/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: BOMCalcDialog, BOMCalcTable, CostingVersion, InventItemPrice, SalesQuotationTable, SalesTable, SMAServiceOrderTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 273763
ms.assetid: c6fa3348-eafa-4847-9132-e65c5f55cbf4
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yuyus
ms.dyn365.ops.intro: AX 7.0.0
ms.search.validFrom: 2016-02-28

---

# BOM calculations

[!include[banner](../includes/banner.md)]


The cost roll-up and sales price calculations are known as bill of materials (BOM) calculations, and you initiate them from the Calculations page. This topic provides information about BOM calculations.

The cost roll-up and sales price calculations are known as bill of materials (BOM) calculations, and you initiate them from the **Calculations** page. You use the **Calculations** page to perform the following tasks:

-   Calculate the cost of a manufactured item, and generate an associated item cost record within a costing version.
-   Calculate the sales price of a manufactured item, and generate an associated item sales price record within a costing version.

The way that you use the **Calculations** page varies slightly, depending on how you initiate the BOM calculations. The way that you use the **Calculations** page also depends on whether the BOM calculations involve a costing version for standard costs or planned costs, and on several policies that are defined in the costing version that is used in the BOM calculations. **Note:** A variation of the **Calculations** page is used in the context of a sales order, sales quotation, or service order line item. These calculations are known as order-specific BOM calculations. An order-specific BOM calculation doesn't generate an item cost record within a costing version. Instead, it generates a calculation record that appears on the **BOM calculation details** page. The calculation record includes a calculated cost and a calculated sales price. The **Calculations** page can be opened for a single manufactured item or for a costing version:

-   To calculate costs for a single manufactured item, you initiate BOM calculations from the **Item price** page. The **Calculations** page inherits the item identifier. The costing version, BOM version, route version, calculation quantity, calculation date, and site must be specified.
    -   By default, the BOM version and route version are set to the active versions for the item, site, date, and calculation quantity. However, you can override the default values with approved versions.
    -   By default, the calculation quantity is set to the item's standard order quantity. However, you can override the default value.
    -   The calculation date or site can be mandated by the costing version, or user-specified values can be set when the date or site isn't mandated in the costing version. A future calculation date determines how pending cost records are used. BOM calculations use a pending cost record that has the nearest from-date that is on or before the calculation date.
-   To calculate costs for all manufactured items or selected items, or to update items on a where-used basis, you initiate BOM calculations from the **Costing version setup** page or the **Costing version maintenance** page. The **Calculations** page inherits the costing version.
    -   For the calculations, it's assumed that the active BOM version and route version are used for a manufactured item (and for the related site, date, and quantity), unless a manufactured component has a specified sub-BOM or subroute.
    -   For the calculations, it's assumed that the standard order quantity is used for manufactured items. The standard order quantity provides the basis for calculating component quantities, determining the relevant BOM versions and route versions (when you use quantity-sensitive BOMs and routes), and amortizing constant costs. However, when a manufactured component has a BOM line type of **Production** or **Vendor**, or when you use a make-to-order explosion mode for the BOM calculations, this assumption doesn't apply, because quantities reflect the specified calculation quantity.
    -   The calculation date or site can be mandated by the costing version, or user-specified values can be set when the date or site isn't mandated in the costing version.

Other variations in BOM calculations reflect the costing type and restrictions of the costing version:

-   BOM calculations that use standard costs must be restricted by costing version policies, because the restrictions help guarantee that standard costing principles are used. Standard costing principles require the enforcement of restrictions about the use of standard costs for purchased items, a single-level explosion mode, and the inclusion of miscellaneous charges in unit costs.
-   BOM calculations that use planned costs don't have to follow standard costing principles. These BOM calculations can use different explosion modes, alternative sources of cost data for purchased items, and optional enforcement of restrictions within the costing version.

### BOM calculations that use standard costs

Policies within the costing version (for standard costs) can mandate enforcement of five BOM calculation policies. The **Recording restriction** option in the costing version mandates one of these policies, where miscellaneous charges must be included in the unit price. Miscellaneous charges for purchased items can be entered manually, whereas miscellaneous charges for manufactured items reflect the calculated amortization of constant costs. The **Calculation restriction** option in the costing version mandates the other four BOM calculation policies:

-   The source of cost contributions for purchased items must be based on standard costs. In other words, BOM calculations must use the item cost records within the specified costing version, or within the fallback that contains standard costs.
-   To help guarantee accurate and consistent calculation of standard costs, the explosion mode must be single-level.
-   To help guarantee consistent results when the sales price of the items is calculated, the profit setting must be mandated. The profit setting can be used, and the item sales price records can be generated, only if the costing version allows for content of sales prices.
-   The fallback principle must be mandated, and can be set to **None**, **Active** (for active cost records), or **Costing version** (for a specified costing version).

### BOM calculations that use planned costs

Policies within the costing version (for planned costs) can optionally mandate enforcement of five BOM calculation policies. Alternatively, the policies can just provide default values. The **Recording restriction** option in the costing version determines whether the BOM calculation policy about miscellaneous charges will be mandated or act as a default value. Miscellaneous charges can optionally be included in the unit price. The **Calculation restriction** option in the costing version determines whether the other four BOM calculation policies will be mandated or act as default values:

-   The source of cost contributions for a purchased item can be the item cost records within a costing version. Alternatively, the source can be defined by the BOM calculation group that is assigned to the item. For example, the BOM calculation group can define purchase price trade agreements as the source of cost contribution data.
-   The explosion mode can be single-level, multilevel, or make-to-order, or it can be based on the BOM line item. The explosion mode for the BOM line type replicates the cost calculation logic for production order estimates.
-   The profit setting can be mandated, or it can be a default value. The profit setting can be used, and the item sales price records can be generated, only if the costing version allows for content of sales prices.
-   The fallback principle can be mandated, or it can be a default value. The fallback principle can be set to **None**, **Active** (for active cost records), or **Costing version** (for a specified costing version).

BOM calculations generate warning messages and other types of messages. Several BOM calculation policies determine the types of messages. The warning conditions are defined in the BOM calculation group that is assigned to items. However, you can override these warning conditions when you initiate a BOM calculation. When the fallback principle is used, it's often helpful if the fallback is shown as an information message. When you're trying to update calculated costs for items that have missing cost records, it's also helpful if the information message identifies items that weren't updated.

## BOM calculations that use the fallback principle
The following situations illustrate two uses of the fallback principle:

-   **Two-version approach to standard cost updates** - A costing version can contain the incremental changes to standard costs, such as pending cost records that represent new items or cost changes. In this situation, the fallback principle can identify the use of the active standard costs that are contained in other costing versions.
-   **Simulation of the effect of cost changes by using planned costs** - A costing version for planned costs can contain incremental changes for simulation purposes. This costing version will include pending cost records that represent the simulated cost changes to items, cost categories, and calculation formulas for indirect cost. In this situation, the fallback principle can identify the use of the active standard costs that are contained in other costing versions.

## BOM calculation of a suggested sales price
When you use a cost-plus-markup approach, the calculated sales price for an item reflects the set of profit-setting percentages that is specified for the BOM calculation, and the costs that are associated with the item's component items, routing operations, and applicable manufacturing overheads. The markup reflects profit-setting percentages that are assigned to cost groups, and the cost groups that are assigned to items, cost categories for routing operations, and the indirect cost calculation formulas for manufacturing overheads. The sets of profit-setting percentages are labeled **Standard**, **Profit 1**, **Profit 2**, and **Profit 3**. Within the Profit 1 set, for example, a profit-setting percentage of 50 percent can be defined for a cost group that is assigned to purchased material, and a profit-setting percentage of 80 percent can be defined for a cost group that is assigned to cost categories for routing operations. The context of the BOM calculation determines how the results of a calculated sales price are handled:

-   **BOM calculation for an item and specified costing version** - The BOM calculation generates a pending sales price record within the costing version. This sales price record provides the starting point for viewing the calculation details (for example, on the **Calculate item cost** page). The sales price record acts mainly as reference information and isn't used as the basis for a sales price on sales orders.
-   **Order-specific BOM calculation** - A variation of the **BOM calculatio**n page is used in the context of a sales order, sales quotation, or service order line item. An order-specific BOM calculation doesn't generate a record in the within a costing version. Instead, it generates a calculation record that appears on the **BOM calculation results** page. This calculation record provides the starting point for viewing the calculation details (for example, on the **Calculate item cost** page). Information about a selected calculation record can be transferred to the originating line item. For example, the calculated sales price can be transferred to a sales order line item.

## Orderspecific BOM calculations
An order-specific BOM calculation represents a variation of a BOM calculation for a manufactured item. The order-specific BOM calculation is performed in the context of a sales order, sales quotation, or service order line item. An order-specific BOM calculation generates a calculation record that appears on the **BOM calculation results** page. The calculation record includes a calculated weight, a calculated cost that is based on active cost records, and a calculated sales price. The calculation record that each order-specific BOM calculation for an item generates on the **BOM calculation results** page is uniquely identified by a calculation number. The results of a calculation record can be optionally transferred to the originating line item. An order-specific BOM calculation differs from a BOM calculation for a manufactured item in two ways:

-   An order-specific BOM calculation doesn't generate an item cost record within a costing version. Therefore, the BOM calculation policies aren't applied when an item cost record is created, or when a cost record is overwritten.
-   An order-specific BOM calculation always uses the active cost records for components, cost categories, and indirect cost calculation formulas.





