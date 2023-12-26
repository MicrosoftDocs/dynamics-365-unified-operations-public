---
title: Costing sheets
description: Setting up the costing sheet involves two objectives. As the first objective, you define the format for displaying cost of goods sold information about a manufactured item or production order. The formatted display is termed a costing sheet. As the second objective, you define the basis for calculating indirect costs. The costing sheet setup builds on the cost group feature for displaying information and for the indirect cost calculation formulas. The two objectives of costing sheet setup are described in this article. 
author: JennySong-SH
ms.date: 11/18/2021
ms.topic: article
ms.search.form: CostSheetDesigner, CostSheetCalculationFactor
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Costing sheets

[!include [banner](../includes/banner.md)]

Setting up the costing sheet involves two objectives. As the first objective, you define the format for displaying cost of goods sold information about a manufactured item or production order. The formatted display is termed a costing sheet. As the second objective, you define the basis for calculating indirect costs. The costing sheet setup builds on the cost group feature for displaying information and for the indirect cost calculation formulas. The two objectives of costing sheet setup are described in this article. 

The following table lists the out-of-box security roles that can access costing sheets, including the level of access granted to each role by the default settings.

| Role | Access
|---|---|
| Accounting manager | Edit |
| Inventory accountant clerk | View |
| Inventory accountant | View |

A costing sheet is the formatted display of information about the cost of goods that are sold for a manufactured item or a production order. When you set up a costing sheet, you define the format for the information and also define the basis for calculating indirect costs. The costing sheet setup builds on the cost group features for displaying information and for the formulas that are used to calculated indirect cost. Here is more information about the two objectives of costing sheet setup:

- **Define the format for the costing sheet.** The user-defined format for a costing sheet identifies the segmentation of costs that contain a manufactured item’s cost of goods sold. For example, the information about an item’s cost of goods sold can be segmented into material, labor, and overhead, based on cost groups. These cost groups are assigned to items, cost categories for routing operations, and indirect cost calculation formulas. The format for the costing sheet typically requires intermediate totals when multiple cost groups have been defined. For example, multiple cost groups that are related to material can be aggregated. The definition of a costing sheet format is optional, but a costing sheet format must be defined if indirect costs will be calculated.
- **Define the basis for calculating indirect costs.** Indirect costs reflect manufacturing overhead that is associated with the production of a manufactured item. An indirect cost calculation formula can be expressed as either a surcharge or a rate. A surcharge represents a percentage of value, whereas a rate represents an amount per hour for a routing operation. A cost group defines the basis for the calculation formula, such as a 100-percent surcharge for a labor cost group or a USD 50.00 hourly rate for a machine cost group. If you want to define a calculation formula and its cost group basis, the costing sheet setup requires that you identify the cost group that represents the overhead, and select whether a surcharge or rate approach is used.

Each calculation formula must be entered as a cost record. The cost record consists of a specified costing version, a surcharge percentage or a rate amount, the cost group basis, a status, and an effective date. When a cost record is first entered, it has **Pending** status and an effective date. When you activate the cost record, the status is updated to so that the record is the current active record, and the effective date is updated to the activation date. The cost record can also specify a site for a site-specific calculation formula. Alternatively, you can leave the **Site** field blank to indicate that the calculation formula is a company-wide formula. The cost record can optionally consist of a specified item or item group when the calculation formula has been marked as a per-item formula. 

The current active cost records for indirect cost calculation formulas are used to estimate production order costs. They are also used to calculate actual costs that are related to actual consumption of time and material. Pending cost records are used in bill of materials (BOM) calculations for a future date. 

Two blocking policies for a costing version determine whether pending costs can be maintained, and whether the pending cost can be started. Use the blocking policies to permit data maintenance, and then to prevent data maintenance for the cost data in a costing version. 

After you define the costing sheet format and calculations for indirect costs, you must perform a separate step to validate and save the information. The costing sheet represents a company-wide format for consistently displaying information about the costs of goods sold. 

The costing sheet is displayed as part of the **Calculate item cost** page. The costing sheet can be displayed for a manufactured item’s calculated cost record on the **Item price** page or for an order-specific calculation record on the **BOM calculation results** page. It can also be displayed as part of the **Price calculation** page for a production order.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
