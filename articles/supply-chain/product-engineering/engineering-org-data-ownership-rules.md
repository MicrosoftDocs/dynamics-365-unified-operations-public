---
# required metadata

title: Engineering organizations and data ownership rules
description: To ensure that the master data for products is created and maintained centrally, you can use one or more engineering organizations. The engineering organization represents the organization that owns the engineering products and its engineering relevant data.
author: t-benebo
manager: tfehr
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Release 10.0.13
---

# Engineering organizations and data ownership rules

[!include [banner](../includes/banner.md)]

## Engineering organizations and operational companies

<!-- KFM Does this feature add the concept of engineering vs organizational organizations? If so, we should make this more clear and explain the role of each of these, and also describe how to configure which is which in the system.  -->


<!-- BNG I think it should be straightforward from the info below.  -->

To ensure that the master data for products is created and maintained centrally, you can use one or more *engineering organizations*. The engineering organization owns the engineering products and their engineering-relevant data. The engineering organization is always connected to a *legal entity*, which is also an organization. With this connection, the system establishes a central entry point for all engineering-relevant data for engineering products within the company. This is where engineering products are created and engineering-relevant data is maintained. From this central point, the engineering products and engineering-relevant data will be released to *operational companies*, which are the other legal entities (For more information about the release management, see [Release product structure](release-product-structure.md)). These operational companies will use the engineering data as it is designed by the engineering organization. Any logistical data will be maintained locally by each company itself.

<!-- KFM: We should describe how to create an "engineering organization" -->
You can create an engineering organization under Project Oaktree> Setup > Engineering organization. Click New, enter a name for the organization and select organization (legal entity) that it is based on. 

If you are integrating with external PLM systems you would need to create a business unit (type of organization) that would become an external organization.

## Engineering product category and engineering organizations

Engineering product categories help to ensure that engineering products are created according to your company's business rules. Engineering product categories ensure that each product behaves as required. For more information on engineering product categories, see [Engineering versions and engineering product category](engineering-versions-product-category.md).

Each engineering product category belongs to a specific engineering organization, and each category can only create products that belong to that same organization. Likewise, the right to maintain an engineering product also belongs to the organization associated with that product's engineering product category.

## Data owned by the engineering organization

Because the engineering organization owns the engineering-relevant data, they control the following:

- **Creation of engineering products**: Each engineering organization can only create new engineering products based on an engineering product category owned by that organization. In the operational companies, the local data will be maintained. <!-- KFM: What does this last sentence mean? --> <!-- BNG some data can be overwritten at a company level, so does not have to be the same as in the engineering organization -->
- **Creation of engineering versions**: When an organization creates a new engineering product, the system automatically creates an initial engineering version for that product. Only the owning engineering organization will be able to create new versions of the product.
- **Creation and maintenance of engineering attributes**: When an organization creates a new engineering product, the system automatically adds engineering attributes to the product. Only the owning engineering organization will be able to create maintain these values. For more information about engineering attributes, see [Engineering attributes and engineering attribute search](engineering-attributes-and-search.md).
- **Creation and maintenance of bill of materials connected to the engineering versions**: The owning engineering organization can directly connect a bill of materials to an engineering product version. When these bills of materials are released to other legal entities, the engineering data on the bills of materials are protected from being changed as follows:
  - The released bill of material lines can't be removed by the operational company.
  - The engineering fields on the bill of material lines are read-only to the operational company. All other fields are logistical implementation fields, which can be edited by the operational company.
  - The operational company can add bill of material lines to the same bill of materials, which lets them add local additions such as packaging materials or lubrication fluids.
  - The operational company can add a completely new, local bill of materials. This can be necessary, for example, in cases where no bill of materials is provided during the release. The operational company owns and maintains these local bills of materials. For more information about the release management, see [Release product structure](release-product-structure.md).
  - All local bills of materials and bill of materials lines are preserved when the engineering organization updates their bill of materials.

- **Creation and maintenance of routes connected to the engineering versions**: The engineering organization can directly connect a route to each engineering version. When these routes are released to other legal entities, they are protected as follows:
  - The engineering data on the routes are protected from being removed.
  - Other legal entities can add operations to the route, which enables them to add local route steps.
  - Operational companies can  add completely new routes, which can be necessary, for example, if you've chosen not to to include routes during the release. The operational companies owns and maintains these local routes. For more information about the release management, see [Release product structure](release-product-structure.md).
  - All changes made locally are preserved when updates from the engineering organization to the routes are released again.

- **Creation and maintenance of engineering documents**: The engineering organization can attach engineering documents to each engineering version.
  - When these documents are released to other legal entities, the documents are protected from being removed by the operational company. 
  - Other legal entities can add completely new documents. The operational company owns and maintains these local documents.

<!-- KFM: Sometimes we say "other legal entities" and other times we say "operational organizations". Do these mean the same thing? Might we have multiple engineering orgs and multiple operational orgs? -->
<!-- BNG operational organization does not exist, It is always operational companies or operational legal entities. operational companies is more common language -->
