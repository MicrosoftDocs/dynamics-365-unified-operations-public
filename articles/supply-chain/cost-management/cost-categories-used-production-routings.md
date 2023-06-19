---
# required metadata

title: Cost categories used in production routing
description: This article provides information about cost categories that apply to manufacturing environments that use routing.
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ProjCategory, RouteCostCategoryPrice
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: a3fdc76c-0a27-4723-b1c7-4322f707d89e
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Cost categories used in production routing

[!include [banner](../includes/banner.md)]

This article provides information about cost categories that apply to manufacturing environments that use routing.

Cost categories apply to manufacturing environments that use routing. They are assigned to operations resources and routing operations to define hourly costs and to segment cost contributions in a manufactured item’s calculated costs. The cost groups that are assigned to cost categories classify manufacturing cost contributions, based on the operation resources and the type of activity, such as setup time and run time. The specificity of cost group assignments enables manufacturing overhead to be calculated based on routing information. 

**Note:** In manufacturing environments, cost categories are known by several other names, such as labor rate codes or machine rate codes. 

Each cost category has associated cost records and an assigned cost group. Different cost categories are required for different production purposes.

-   Assign different hourly costs, depending on the operations resource. For example, the costs can differ for various types of labor skills, machines, or manufacturing cells.
-   Assign different hourly costs for the setup time or run time that is associated with a routing operation.
-   Assign operations resource costs based on the output quantity instead of hourly costs, such as the piece rates for paying labor.
-   Provide cost group segmentation of cost contributions to a manufactured item’s calculated cost. For example, you can segment of labor and machine costs.
-   Provide the cost group basis for overhead calculation formulas, such as formulas for labor-related and machine-related overhead, or overhead that is related to setup and run time.

A cost category can be assigned to the setup time, the process time, and the quantity for a routing operation. When, for example, costs or cost group segmentation differs between the setup time and the process time, different cost categories should be defined and assigned to the setup time and the process time. The selective use of cost categories for setup time, process time, and quantity is determined by the route group that is assigned to an operation. The assignment of cost categories to time and quantity can be mandated by company-wide policies that are defined on the **Production control parameters** page. 

Each cost category has associated costs that are based on the definition of cost records in a costing version. Use the **Cost category price** page to define the cost records for a specified costing version and site. When the cost record for a cost category is first entered, it has a status of **Pending** and an intended effective date. When you activate the cost record, the status is updated to **Current active**, and the effective date is updated to the activation date. Different cost records might reflect different sites, effective dates, or statuses. Bills of materials (BOM) calculations for a future or historical date use cost records that have the relevant effective date. The current active cost record will be used to estimate production order costs and to value reported time against a production order. 

The cost record for a cost category can be site-specific or company-wide. To make a cost record site-specific, assign a site to it. Otherwise, a blank value indicates that the cost record applies to all sites in the company. Because costs can differ between sites, for example, the cost records must be defined as site-specific. 

A routing operation generally inherits the cost categories that are assigned to the operations resource or master operation. When a production order is created, the routing operations in the production route reflect the selected route version. You can override the cost categories that are assigned to the operations in the production route. 

Some types of production work can apply to project time estimates and reporting. In this case, a cost category is required for production and project purposes. You must define additional project-related information when a cost category is flagged for use in projects.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]