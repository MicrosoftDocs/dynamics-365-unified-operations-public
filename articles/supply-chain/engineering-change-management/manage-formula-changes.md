---
title: Manage changes in formulas and their ingredients
description: Learn how to do formula management and manage changes to process manufacturing master data, including an outline on toggling this feature.
author: sgmsft
ms.author: shwgarg
ms.topic: article
ms.date: 05/19/2021
ms.reviewer: kamaybac
ms.search.form:
---

# Manage changes in formulas and their ingredients

[!include [banner](../includes/banner.md)]

If you're using the process manufacturing capabilities of Microsoft Dynamics 365 Supply Chain Management, you can also use the related formula management capabilities to manage the following changes:

- **Formula and planning items:** Manage changes to ingredients in formulas and their co-products and by-products.
- **Co-products and by-products:** Edit quantities and other information of the co-products and by-products in a formula.
- **Catchweight items:** Manage changes to catch-weight items.

## Turn this feature on or off

The functionality described in this article requires that both the *Engineering Change Management* and *Manage changes to formulas and their ingredients* features be turned on for your system. For details about how to turn these features on or off, see [Engineering change management overview](product-engineering-overview.md).

## Feature naming conventions

In the Supply Chain Management user interface (UI) and documentation, change management functionality is typically referred to as *engineering change management*, and the manageable products are typically referred to as *engineering products*. Although this terminology isn't usually associated with the management of formulas for process manufacturing, you should think of engineering change management as simply change management, and you should think of engineering products as versioned products.

## Work with formula change management features

The following list summarizes how engineering change management features apply to formula management. It also provides links to more information. Because formula change management takes advantage of engineering change management features, you should learn how engineering change management works in general, so that you can use it to manage your formulas and their ingredients.

- **Centralized product data management** – Set up an organization that, through a managed release process, ensures that accurate and relevant product data is available to users across the enterprise. Learn more in [Engineering companies and data ownership rules](engineering-org-data-ownership-rules.md).
- **Product versioning** – Track changes to products through product versions, and control the product throughout all stages of the supply chain. In this way, you can track the changes in your formulations. Learn more in [Engineering versions and engineering product categories](engineering-versions-product-category.md).
- **Product lifecycle management** – Manage the visibility of product data across the organization, and control the availability of product versions at each stage of the supply chain. You have detailed control over when a product version can be used in specific business processes, and you can create your own lifecycle states to fit your business needs. Learn more in [Product lifecycle states and transactions](product-lifecycle-state-transactions.md).
- **Formula change management** – Users throughout your organization can request changes to formulas. Use change orders to assess and document the impact of proposed changes. Add workflows to manage the change process and the release of new versions of the product and its formula. Learn more in [Manage changes to engineering products](engineering-change-management.md).
- **Readiness control** – Use system checks and user guidance (questionnaires and checklists) to ensure that all required product data is fully entered before the product is released. Learn more in [Product readiness](product-readiness.md).
- **Enhanced product release functionality** – Release fully defined versions of a product and its formula from an organization (legal entity) to other legal entities. You can even decide whether the product information must be reviewed or edited before release. Learn more in [Release product structures](release-product-structure.md).

Note that most of the articles that are linked to in the previous list provide examples that are based on bills of materials (BOMs). However, formulas work in a similar way. Here are some additional concepts that are useful to know when you use change management (or only formula change management) to manage formulas and BOMs:

- For each [product engineering category](engineering-versions-product-category.md), you can specify the production type (BOM, formula, or planning item). You can also specify whether catch-weight support is required for products that use that category.
- Co-products and by-products aren't engineering products. Therefore, they aren't versioned. If you must change them, just create a new product. This approach makes maintenance easier.
- You can manage end items that are BOMs and that have child formula items. The functionality will work for any combination of BOMs that contain formulas and/or formulas that contain BOMs.
