---
# required metadata

title: Bills of materials and formulas
description: This article provides information about bills of materials (BOMs) and formulas, which are a central part of the definition of products and product variants. BOMs and formulas specify the required materials or ingredients for a specific product. Formulas also specify the co-products and by-products that are received in a specific production context. 
author: cvocph
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: BOMConsistOf, BOMDesigner, BOMTable, EcoResProductProcessManufacturingWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: yuyus
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 19331
ms.assetid: c19b437a-2de2-4728-9477-2bcb0c2b1f5e
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: conradv
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Bills of materials and formulas

[!include[banner](../includes/banner.md)]


This article provides information about bills of materials (BOMs) and formulas, which are a central part of the definition of products and product variants. BOMs and formulas specify the required materials or ingredients for a specific product. Formulas also specify the co-products and by-products that are received in a specific production context. 

Bills of materials
------------------

A bill of materials (BOM) defines the components that are required in order to produce a product. The components can be raw materials, semifinished products, or ingredients. In some cases, services can be referenced in a BOM. However, BOMs typically describe the *material resources* that are required.  

When it's combined with a route or production flow that describes the operations and resources that are required in order to build a product, the BOM forms the foundation for calculating the estimated cost of the product.  

A BOM is an individual entity that is described by the following information:

-   BOM ID
-   BOM name
-   The BOM lines that describe the components and ingredients
-   The BOM versions, which define the product and period that the BOM can be used for

A single BOM describes a single level that is identified by a unique ID. Components might have their own BOMs that are referenced by BOM versions. You can display and edit the complete hierarchy of BOMs for a specific product in the BOM designer.

### Formulas, co-products, and by-products

A formula is a subtype of BOM that is typically used for process manufacturing. In addition to components and ingredients, a formula describes co-products and by-products. In the actual version, the definition of co-products and by-products for the formula requires the formula version. A formula is typically defined for one specific finished product (a formula or planning item) that is defined in the formula version.

### BOMs in the product lifecycle

In the product lifecycle, many types of BOM might be created for various reasons:

-   **Sketching/Draft BOM** – This BOM gives a draft estimation of required materials in an early design phase and helps you do a rough estimate of cost and estimated product attributes. This BOM isn't usually used in enterprise resource planning (ERP).
-   **Engineering BOM** – This BOM is typically used when you design products that are based on existing product portfolios. Engineering BOMs are structured to simplify the design process and group complex products into engineering modules. For simple products, it might be possible to engineering BOMs for the actual production process. However, for other products, the engineering BOM must be converted to an actual production BOM. Engineering BOMS are typically represented by phantoms in the BOM hierarchy. Although engineering BOMs can be used for the planning and execution of manufacturing operations, this approach can lead to inefficiencies, especially in repetitive operations where many orders are created.
-   **Planning BOM** – This BOM is used to do planning for material requirements. The demand of components and ingredients is calculated based on the demand of the finished products. Like costing BOMs, planning BOMs might represent a specific mix of material that is used in a period.
-   **Production BOM** – This is the actual BOM that is used for a specific production. A production BOM must take into account the actual resources that are used to produce the product. When a production order, batch order, or kanban is created, the multiple levels of BOMs that are represented by phantoms are collapsed into one level and distributed over the operations for the order.
-   **Costing BOM** – This BOM is used to calculated the estimated cost of a product. For example, you can use a costing BOM when standard cost is used or the estimated planned cost of a given product is calculated. Costing BOMs can refer to a specific mix of materials and resources that is expected to be used. Therefore, you can use the costing BOM to create a representative estimated cost for a period and help avoid variances over time.

The types of BOM that are actually used in an implementation depend on the implementation, and also on the business scenarios and requirements. In simple implementations, a planning BOM, production BOM, and costing BOM can be modeled as one BOM. In environments that have frequent engineering changes and multiple alternative routes, a larger set of BOM types will probably be required.

### Approval of BOMs and formulas

Each BOM and formula can be separately approved or unapproved. Typically, approval of a BOM or formula occurs when the first relevant BOM version is approved. However, in some business scenarios, these approvals might be different steps in the process and might involve different process owners.  

Note that, if a BOM is unapproved, all related BOM versions are also unapproved.

## BOM and formula versions
To relate a specific BOM or formula to a product variant that can be produced, you must create a BOM version or formula version. The validity of BOM versions and formula versions can be constrained by period, quantity, site, specific product dimensions, and other criteria. Formula versions have additional important attributes, such as yield, co-product and by-product definitions, and the cost distribution instructions for the formula.

### Approval of BOM and formula versions

Before a BOM version can be used in the planning or manufacturing process, it must be approved. When a BOM version is approved, the related BOM can also be approved, depending on the user's selection and authentication rights. Note that a BOM version can be approved only if the related BOM itself is approved.

### Activation of the default BOM or formula version

To set a specific BOM or formula as the default BOM version or formula version that will be used by master planning or used to create of production orders, you must activate the version. When a version is activated, the uniqueness of the version for the given constraints (for example, period, site, or quantity) is verified. You receive an error message if the version that you're trying to activate conflicts with a version that is already active. You must then either inactivate the conflicting version or modify the version constraints (usually the period) to prevent an ambiguous activation.

### Product change with case management

The product change case for approval and activation of new or changed BOMs and BOM versions provides an easy way to see an overview of the BOM version constraints. You can also approve and activate all BOMs and formulas that are related to a specific change for one activation date.

### Alternative BOM versions

Sometimes, the active BOM version or formula version should not be used in forecasts, sales, or a parent product. In this case, you can select a specific approved BOM as part of the requirement (forecast line, sales line, or BOM line) if an approved BOM version or formula version exists for the alternative BOM or formula.  

When planned orders, production orders, or kanbans are created, the planner or shop floor supervisor can use any approved BOM version that is valid on the requested planned production date to plan for or produce a specific product. The BOM version that is used doesn't have to be activated as the default BOM version.

## BOM and formula lines
A BOM line is created for each material, service, or ingredient. The line defines the planned consumption of the specified product variant and also defines the various attributes that are related to the planned consumption.  

BOM lines can have the following line types: **Item**, **Phantom**, **Pegged supply**, **Vendor**.

### Item

Select the **Item** line type for materials or services that are directly consumed, and that don't require further explosion or pegged supply.

### Phantom

Select the **Phantom** line type when you want to explode any lower-level BOM items that are contained on the BOM line. In Master scheduling, in planned cost calculation, or on estimation of a production order that uses BOM lines of the **Phantom** type, the parent BOM line that refers to a product variant that has a phantom BOM is replaced by the component items that are listed as BOM lines in that BOM, as determined by the applicable active BOM version of that product variant. If the product variant has an applicable active route, the operations of that route are merged into the parent route.  

Note that phantoms are typically used to simplify the engineering process. Extensive use of phantom BOMs in many levels has an effect on performance, especially in highly repetitive manufacturing scenarios. To improve performance, you should avoid deep hierarchies of phantoms. Instead, use pre-exploded production BOMs and routes.

### Pegged supply

Select the **Pegged supply** line type when you want to create a subproduction, a BOM line event kanban, or a direct purchase order for any product variant that the BOM line references. The subproduction, event kanban, or purchase order is created when you estimate the production order. The required item quantities are automatically reserved for the consuming production order.

### Vendor

Select the **Vendor** line type if the production process uses a subcontractor, and you want a subproduction or purchase order to be created automatically for the subcontractor.  

**Note about subcontracted operations in a BOM:** The service or work that is performed by the subcontractor must be created as service item that is tracked in inventory. You must attach the service item to the parent item as a BOM line. The route must contain an operation that is assigned to the subcontractor's operations resource.



