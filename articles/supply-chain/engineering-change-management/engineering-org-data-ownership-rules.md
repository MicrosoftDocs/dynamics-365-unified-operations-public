---
# required metadata

title: Engineering companies and data ownership rules
description: This topic explains how you can use one or more engineering companies to ensure that the master data for products is centrally created and maintained. An engineering company represents the company that owns the engineering products and its engineering-relevant data.
author: t-benebo
ms.date: 09/28/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EngChgEngineeringOrganization
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: 10.0.15
---

# Engineering companies and data ownership rules

[!include [banner](../includes/banner.md)]

## Engineering companies and operational companies

To ensure that the master data for products is centrally created and maintained, you can use one or more *engineering companies*. An engineering company owns the engineering products and their engineering-relevant data. It's always connected to (based on) an existing *legal entity*, which is also a company. Through this connection, the system establishes a central entry point for all engineering-relevant data for engineering products in the engineering company. In this central entry point, engineering products are created, and engineering-relevant data is maintained. From it, the engineering products and engineering-relevant data will be released to *operational companies*, which are other legal entities. (For more information about the release management, see [Release product structures](release-product-structure.md).) These operational companies will use the engineering data as it has been designed by the engineering company. Any logistical data is locally maintained by each engineering company and operational company.

To create an engineering company, go to **Engineering change management \> Setup \> Engineering organizations**. Select **New**, enter a name for the engineering company, and select the existing company (legal entity) that it's based on.

If you're integrating with external product lifecycle management (PLM) systems, you must create a business unit (type of company) that will become an external company.

## Engineering product categories and engineering companies

*Engineering product categories* help ensure that engineering products are created according to your company's business rules and behave as required. For more information about engineering product categories, see [Engineering versions and engineering product categories](engineering-versions-product-category.md).

Each engineering product category belongs to a specific engineering company and can create only products that belong to that company. Likewise, the right to maintain an engineering product also belongs to the company that is associated with that product's engineering product category.

## Data that is owned by the engineering company

Because the engineering company owns the engineering-relevant data, it controls the following processes:

- **Creation of engineering products:** Each engineering company can only create new engineering products that are based on an engineering product category that it owns. In some cases, operational companies maintain their own local data that is related to those products.
- **Creation of engineering versions:** When a company creates a new engineering product, the system automatically creates an initial engineering version for it. Only the owning engineering company will be able to create new versions of that product.
- **Creation and maintenance of engineering attributes:** When a company creates a new engineering product, the system automatically adds engineering attributes to it. Only the owning engineering company will be able to create and maintain the values for those attributes. For more information about engineering attributes, see [Engineering attributes and engineering attribute search](engineering-attributes-and-search.md).
- **Creation and maintenance of bills of materials (BOMs) that are connected to the engineering versions:** The owning engineering company can directly connect a BOM to an engineering product version. When these BOMs are released to other legal entities, changes to the engineering data on the BOMs are limited in the following ways:

    - The operational company can't remove released BOM lines.
    - The engineering fields on the BOM lines are read-only for the operational company. All other fields are logistical implementation fields and can be edited by the operational company.
    - The operational company can add BOM lines to the same BOM. In this way, it can add local additions, such as packaging materials or lubrication fluids.
    - The operational company can add a completely new, local BOM. This change might be required in cases where, for example, no BOM is provided during the release. The operational company owns and maintains these local BOMs. For more information about release management, see [Release product structures](release-product-structure.md).
    - All local BOMs and BOM lines are preserved when the engineering company updates its BOM.

- **Creation and maintenance of routes that are connected to the engineering versions:** The engineering company can directly connect a route to each engineering version. When these routes are released to other legal entities, changes to the data on the routes are limited in the following ways:

    - The other legal entities can't remove the engineering data on the routes.
    - The other legal entities can add operations to the route. In this way, they can add local route steps.
    - Operational companies can add completely new, local routes. This change might be required if, for example, you haven't included routes during the release. The operational companies own and maintain these local routes. For more information about release management, see [Release product structures](release-product-structure.md).
    - All changes that are made locally are preserved when updates from the engineering company are released again to the routes.

- **Creation and maintenance of engineering documents:** The engineering company can attach engineering documents to each engineering version.

    - When these documents are released to other legal entities, the documents are protected from being removed by the operational company.
    - Other legal entities can add completely new, local documents. The operational company owns and maintains these local documents.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]