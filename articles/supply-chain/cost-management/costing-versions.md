---
# required metadata

title: Costing versions overview
description: This article provides information about costing versions, how to maintain them, and the types of data that you can include in them. The primary purpose of a costing version is to contain cost records about items, cost categories, and calculation formulas for indirect costs.
author: JennySong-SH
ms.date: 05/16/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BOMCalcDialog, BOMCalcTable, CostingVersion
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: ["54532", "intro-internal"]
ms.assetid: cd239da5-f434-4d1b-8196-5414c888d76d
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Costing versions overview

[!include [banner](../includes/banner.md)]

This article provides information about costing versions, how to maintain them, and the types of data that you can include in them. The primary purpose of a costing version is to contain cost records about items, cost categories, and calculation formulas for indirect costs.

A costing version can serve one or more purposes, depending on the data that the costing version contains. The primary purpose of a costing version is to contain cost records about items, cost categories, and calculation formulas for indirect costs. A costing version can contain a set of standard cost records or a set of planned cost records that are based on the costing type that is assigned to the costing version.

Learn more at [Glossary of terms in Dynamics 365 business processes](/dynamics365/guidance/business-processes/glossary#costing-methodology) and [Define product and service costing overview](/dynamics365/guidance/business-processes/product-service-define-cost-overview).  

## Costing versions for standard or planned costs
### Standard costs

A costing version can support a standard cost inventory model for items, where the costing version contains a set of standard cost records about items and manufacturing processes. Cost data about manufacturing processes is expressed in terms of the cost categories for routing operations and the calculation formulas for manufacturing overheads.

### Planned costs

A costing version can contain a set of planned cost records about items and manufacturing processes. A costing version that contains planned costs is often used to support cost calculation simulations, such as simulations of the effect that cost changes to purchased materials or manufacturing processes has on the calculated costs of manufactured items. The item cost records for planned costs can also be used to support an actual cost inventory model by providing the initial values for item costs. These values include the calculation of planned costs for manufactured items.

## Entering costs
Data maintenance for cost records in a costing version involves entering costs for purchased items and for items that are transferred between sites. Additional data maintenance for manufacturers involves entering costs for cost categories that are associated with routing operations, entering calculation formulas for the indirect costs that reflect manufacturing overhead, and calculating costs for manufactured items. 

The item cost data in a costing version consists of one or more cost records for each item. When an item cost record is first entered, it has **Pending** status and an intended effective date. When you activate the item cost record, the status is updated to **Active**, and the effective date is updated to the activation date. Different item cost records can reflect different sites, effective dates, or statuses. When you calculate costs for manufactured items for a future date, the bill of materials (BOM) calculation uses cost records that have the relevant effective date, regardless of whether the status is **Pending** or **Active**. An item's current active cost record is used to estimate production order costs and to value inventory transactions under a standard costing inventory model. The maintenance of cost records for cost categories and indirect cost calculation formulas resembles the maintenance of item cost records. 

Two blocking policies for a costing version determine whether pending costs can be maintained and whether the pending cost can be activated. Use the blocking policies to permit data maintenance, and then use them to prevent data maintenance for cost records in a costing version. 

A costing version can also contain data about item sales prices or purchase prices for BOM calculation purposes.

## Item sales prices for BOM calculations
The main reason for including data about sales prices is to retain a manufactured item’s calculated sales price. The calculated sales price can then be analyzed to determine how components, routing operations, and overhead contribute to the cost and sales price. 

A secondary reason for including data about sales prices is to define the sales price records for component items. These records can then be used to calculate the sales price of manufactured items. You first define the sales price model that is embedded in a BOM calculation group, and assign the BOM calculation group to purchased items. Then, when you perform BOM calculations that use planned costs, you select the cost price model of the BOM calculation group. 

Otherwise, the sales price records for items are used only as reference information, regardless of whether the records are manually entered or calculated. By activating an item’s sales price record, you can update the item’s base sales price. However, the base sales price isn't site-specific and can be manually overridden. The item’s base sales price is used as a default sales price on sales orders and sales quotations.

## Item purchase prices for BOM calculations
The main reason for enabling purchase price data is to define purchase price records for component items, so that these records can be used to calculate the costs of manufactured items. The item purchase price records must be manually entered. 

To enable purchase price content, you first define a BOM calculation group that contains a cost price model for the item’s purchase price, and assign the BOM calculation group to purchased items. You then use a cost price model for the BOM calculation group when you perform BOM calculations that use planned costs to calculate the sales price of manufactured items. 

The purchase price records for items are also used as reference information. By changing the status of an item’s purchase price record from **Pending** to **Active**, you can update the item’s base purchase price. However, the base purchase price isn't site-specific and can be manually overridden. The item's base purchase price is used as a default purchase price on purchase orders.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]