---
title: Manage changes in formulas and their ingredients
description: This topic describes how to do formula management and manage changes to process manufacturing master data.
author: t-benebo
ms.date: 05/19/2021
ms.topic: article
# ms.search.form:[Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-05-19
ms.dyn365.ops.version: 10.0.20
---

# Manage changes in formulas and their ingredients

[!include [banner](../includes/banner.md)]

If you're using the process manufacturing capabilities of Microsoft Dynamics 365 Supply Chain Management, you can also use the related formula management capabilities to manage the following changes:

- **Formula and planning items:** Manage changes to ingredients in formulas and their co-products and by-products.
- **Co-products and by-products:** Edit quantities and other information of the co-products and by-products in a formula.
- **Catchweight items:** Manage changes to catch-weight items.

## Turn on this feature in your system

To use this capability, you must complete the following tasks:

1. Enable the *Engineering change management* feature and its configuration key, as described in [Engineering change management overview](product-engineering-overview.md). As is mentioned in that topic, make sure that you also enable the **Change management for process manufacturing** license key, which is nested below the main **Engineering Change Management** license key.
1. Turn on the *Manage changes to formulas and their ingredients* feature in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Feature naming conventions

In the Supply Chain Management user interface (UI) and documentation, change management functionality is typically referred to as *engineering change management*, and the manageable products are typically referred to as *engineering products*. Although this terminology isn't usually associated with the management of formulas for process manufacturing, you should think of engineering change management as simply change management, and you should think of engineering products as versioned products.

## Work with formula change management features

The following list summarizes how engineering change management features apply to formula management. It also provides links to more information. Because formula change management takes advantage of engineering change management features, you should learn how engineering change management works in general, so that you can use it to manage your formulas and their ingredients.

- **Centralized product data management** – Set up an organization that, through a managed release process, ensures that accurate and relevant product data is available to users across the enterprise. For more information, see [Engineering companies and data ownership rules](engineering-org-data-ownership-rules.md).
- **Product versioning** – Track changes to products through product versions, and control the product throughout all stages of the supply chain. In this way, you can track the changes in your formulations. For more information, see [Engineering versions and engineering product categories](engineering-versions-product-category.md).
- **Product lifecycle management** – Manage the visibility of product data across the organization, and control the availability of product versions at each stage of the supply chain. You have detailed control over when a product version can be used in specific business processes, and you can create your own lifecycle states to fit your business needs. For more information, see [Product lifecycle states and transactions](product-lifecycle-state-transactions.md).
- **Formula change management** – Users throughout your organization can request changes to formulas. Use change orders to assess and document the impact of proposed changes. Add workflows to manage the change process and the release of new versions of the product and its formula. For more information, see [Manage changes to engineering products](engineering-change-management.md).
- **Readiness control** – Use system checks and user guidance (questionnaires and checklists) to ensure that all required product data is fully entered before the product is released. For more information, see [Product readiness](product-readiness.md).
- **Enhanced product release functionality** – Release fully defined versions of a product and its formula from an organization (legal entity) to other legal entities. You can even decide whether the product information must be reviewed or edited before release. For more information, see [Release product structures](release-product-structure.md).

Note that most of the topics that are linked to in the previous list provide examples that are based on bills of materials (BOMs). However, formulas work in a similar way. Here are some additional concepts that are useful to know when you use change management (or only formula change management) to manage formulas and BOMs:

- For each [product engineering category](engineering-versions-product-category.md), you can specify the production type (BOM, formula, or planning item). You can also specify whether catch-weight support is required for products that use that category.
- Co-products and by-products aren't engineering products. Therefore, they aren't versioned. If you must change them, just create a new product. This approach makes maintenance easier.
- You can manage end items that are BOMs and that have child formula items. The functionality will work for any combination of BOMs that contain formulas and/or formulas that contain BOMs.
