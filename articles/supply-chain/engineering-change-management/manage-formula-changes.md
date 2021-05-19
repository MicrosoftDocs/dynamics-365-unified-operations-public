---
title: Manage changes in formulas and their ingredients
description: This topic describes how to do formula management and manage changes to process manufacturing master data
author: t-benebo
ms.date: MM/DD/YYYY
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: YYYY-MM-DD
ms.dyn365.ops.version: 10.0.18
---

# Manage changes in formulas and their ingredients

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

If you are using the process manufacturing capabilities of Supply Chain Management, then you can also use the related formula management capabilities to manage changes on:

- **Formula and planning items**: Manage changes to ingredients in formulas and their co-products and by-products.
- **Co-products and by-products**: Edit quantities and other information of the co-products and by-products in a formula.
- **Catchweight items**: Manage changes in catchweight items.

## Turn on this feature in your system

To use this capability, you must complete the following tasks:

1. Enable the Engineering change management feature and its configuration key as described in [Engineering change management overview](product-engineering-overview.md). As mentioned in that topic, be sure to also enable the **Change management for process manufacturing** license key, which is nested below the main **Engineering Change Management** license key.
1. Turn on the *Manage changes to formulas and their ingredients* feature in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Feature naming conventions

Within the Supply Chain Management user interface and documentation, change management functionality is typically referred to as *engineering change management* and the manageable products are typically referred to as *engineering products*. Although this terminology isn't usually associated with managing formulas for process manufacturing, you should think of engineering change management simply as change management and think of engineering products as versioned products.

## Work with formula change management features

The following list summarizes how engineering change management features apply to formula management, and provides links for more information. Because formula change management leverages engineering change management features, you should learn how engineering change management works so that you can use it to manage your formulas and their ingredients.

- **Centralized product data management**: Set up an organization that, through a managed release process, ensures that accurate and relevant product data is available to users across the enterprise. For more information, see [Engineering companies and data ownership rules](engineering-org-data-ownership-rules.md).
- **Product versioning**: Track changes to products through product versions, and control the product throughout all stages of the supply chain. This way you're able to keep track of the changes in your formulations. For more information, see [Engineering versions and engineering product categories](engineering-versions-product-category.md).
- **Product lifecycle management**: Manage the visibility of product data across the organization and control the availability of product versions at each stage of the supply chain. You have detailed control over when a product version can be used in certain business processes, and can create your own lifecycle states to fit your business needs. For more information, see [Product lifecycle states and transactions](product-lifecycle-state-transactions.md).
- **Formula change management**: Users throughout your organization can request changes to formulas. Use change orders to assess and document the impact of proposed changes. Add workflows to manage the change process and the release of new versions of the product and its formula. For more information, see [Manage changes to engineering products](engineering-change-management.md)
- **Readiness control**: Ensure all necessary product data is fully populated before the product is released by using system checks and user guidance (questionnaires and checklists). For more information, see [Product readiness](product-readiness.md)
- **Enhanced product release functionality**: Release fully defined product versions and its formula from an organization (legal entity) to other legal entities and even decide whether the product information needs to be reviewed or edited before release. For more information, see [Release product structures](release-product-structure.md)

Note that most of the topics linked to in the previous list provide examples based on bills of materials (BOM). However, formulas work similarly. Some of the concepts useful to know when managing formulas and BOMs with change management (or only formula change management) are the following:

- Production type is specified on the engineering category details. So you can choose if the item is BOM, formula, or planning item
- Whether the product is a catch weight item is also specified in the engineering category details.
- Co- and by-products are not engineering products, meaning they are not versioned. If you need to change them, just create a new product. This is to ease maintenance.
- You can manage end items that are BOMs and that have child formula items. The functionality will work for both cases (only discrete engineering items and also formula items) as well as the combinations of both of them together. <!-- KFM: I'm not sure what we are trying to say for this point. -->
