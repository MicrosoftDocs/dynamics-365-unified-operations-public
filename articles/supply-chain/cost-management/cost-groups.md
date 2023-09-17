---
# required metadata

title: Cost groups
description: Cost groups provide the basis for segmenting and analyzing cost contributions in a manufactured item’s calculated cost, such as the cost contributions for material, labor, and overhead. Cost group segmentation has several synonyms within manufacturing environments, such as cost breakdown, cost decomposition, or cost classification. 
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BOMCostGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 1855f744-f73f-4fa8-8290-a7ee126d368b
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Cost groups

[!include [banner](../includes/banner.md)]

Cost groups provide the basis for segmenting and analyzing cost contributions in a manufactured item’s calculated cost, such as the cost contributions for material, labor, and overhead. Cost group segmentation has several synonyms within manufacturing environments, such as cost breakdown, cost decomposition, or cost classification. 

Cost group segmentation has several synonyms within manufacturing environments, such as cost breakdown, cost decomposition, or cost classification. Cost group segmentation can serve several purposes. Here are some examples:

-   It can segment costs for different types of material, such as ingredients and packaging material for a canned goods product, based on the cost groups that are assigned to items.
-   It can segment costs for different types of operations resources, such as different types of labor or machines, based on the cost groups that are assigned to cost categories that are related to operations resources and routing operations.
-   It can segment costs for setup time and run time in routing operations, based on the cost groups that are assigned to cost categories that are related to the routing operations.
-   It can segment costs for different types of overhead, such as labor-related and machine-related overhead, based on cost groups that are assigned to indirect costs in the costing sheet setup.
-   It can act as the basis for calculating various types of manufacturing overhead in the costing sheet setup. This overhead can include different types of overhead that are related to routing information about operations resources, or information about setup time and run time. Manufacturing overhead can also be related to cost contributions of component material, reflecting a lean manufacturing philosophy that eliminates the need for routing information.

Cost group segmentation applies to a manufactured item’s calculated cost, regardless of whether that cost was based on standard costs or planned costs. The **Summary** page displays this segmentation by cost group, by level, or by both cost group and level. 

The ability to retain cost group segmentation across multiple levels in a product structure is known as *splitting*. Splitting applies only to manufactured items that use a standard cost inventory model. If splitting isn't used, the cost of a manufactured component is treated as a material cost contribution. The inventory parameter for cost breakdown by subledger indicates that cost group segmentation will be retained across multiple levels in standard cost calculations. By contrast, if a policy has no levels, cost group segmentation applies only to a single-level calculation. For example, the **Cost rollup by cost group** page displays the cost group segmentation across multiple levels for standard cost items. 

Cost group segmentation can also apply to variances for a standard cost item. A second inventory parameter defines whether variances are identified by cost group or just summarized. 

A cost group can be assigned a cost group type and a behavior for supplemental segmentation purposes.

-   **Cost group type** − Each cost group must be assigned a cost group type to indicate that the cost group applies to direct material, direct manufacturing, or direct outsourcing, or to designate it as indirect or undefined. A cost group that is designated as direct material can be assigned to items. A direct manufacturing cost group can be assigned to cost categories. A direct outsourcing cost group can be assigned to a product type of service, so that you can classify costs that are associated with the service purchase to subcontracting activities. An indirect cost group can be assigned to indirect costs for surcharges or rates. A cost group that is designated as undefined can be assigned to items, cost categories, or indirect costs. The assignment of a cost group type serves several purposes. First, it constrains the ability to assign a cost group and to view a list of applicable cost groups. Second, it provides supplemental segmentation for reporting purposes. Third, it can be used to assign ledger accounts for variances.
-   **Behavior** − Each cost group can optionally be assigned a behavior to indicate that the cost group applies to fixed costs or variable costs. A cost group that has a null value for behavior is treated as a variable cost. The assignment of a behavior serves only a reporting purpose. For example, costs can be displayed with segmentation of fixed and variable costs on the costing sheet and on the **Cost rollup by cost group** page. If you assign a profit setting percentage to each cost group, the bill of materials (BOM) calculation provides a suggested sales price, based on a cost-plus-markup approach.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]