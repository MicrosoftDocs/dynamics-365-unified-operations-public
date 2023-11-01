---
# required metadata

title: Engineering change management overview (contains video)
description: This article provides an overview of engineering change management, which helps you plan and manage product versioning, and manage product lifecycles and engineering changes.
author: t-benebo
ms.date: 08/09/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 

ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: 10.0.21
---

# Engineering change management overview

[!include [banner](../includes/banner.md)]

## Feature summary

Today's manufacturers require strong product data management, version control, and engineering change management to succeed in a world of constantly shrinking product lifecycles, increased quality and reliability requirements, and an increased focus on product safety.

Engineering change management brings structure and discipline to the product data management process, and enables products to be defined, released, and revised in a controlled manner that is supported by workflows. Through product versions and engineering change management, you can document, assess the impact of, and apply engineering changes throughout the whole lifecycle of a product.

Engineering change management helps you plan and manage product versioning, and manage product lifecycles and engineering changes. Here is a list of its main features:

- Product versioning
- Enhanced product release functionality that lets you maintain product master data in one legal entity (the engineering company) and publish the fully configured released product to other legal entities
- Rules for validating that required information is entered before a product version is activated (readiness checks)
- Improved product lifecycle management through fine-grained control over when a released product can be used in specific business processes
- Engineering change requests that are supported by workflows
- Engineering change orders that are supported by workflows

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4HE6B]

The preceding video ([Change management capabilities in Dynamics 365 Supply Chain Management](https://youtu.be/N313FqvRuBc)) is included in the [finance and operations playlist](https://www.youtube.com/playlist?list=PLcakwueIHoT_SYfIaPGoOhloFoCXiUSyW) available on YouTube.

## Number sequence requirements

To use engineering change management, both the BOM number sequence and the formula number sequence (if you are using formulas) must be set to *Automatic* on the **Number sequences** page.

## Turn on the engineering change management features for your system

Before you can use engineering change management, you must enable both the *Engineering Change Management* feature and its configuration keys. If you also want to track the version dimension of products in transactions (optional), you must also enable both the *Product version dimension* feature and its configuration key. After those prerequisites are set up as required, you will be able to turn on additional optional features for engineering change management.

As of Supply Chain Management version 10.0.36, both the *Engineering Change Management* and *Product dimension version* features are mandatory and can't be turned off. The engineering change management license keys are also turned on by default in version 10.0.36 and later, but you can turn them off if you don't use the feature. The product version dimension key is turned on by default for new systems, but it remains turned off by default for systems that have been upgraded from versions earlier than 10.0.36.

### Turn the basic engineering change management features on or off

To turn the basic engineering change management features on or off, follow these steps. As of Supply Chain Management version 10.0.25, the *Engineering Change Management* feature is turned on by default. As of Supply Chain Management version 10.0.36, both the *Engineering Change Management* and *Product dimension version* features are mandatory and can't be turned off.

1. Go to the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.
1. Check for updates.
1. Turn the feature named *Engineering Change Management* on or off, as needed.
1. If you want to track the [version dimension](../pim/product-dimensions.md#version-dim) of products in transactions (optional), turn on the feature that is named *Product dimension version*.

### Turn the required configuration keys on or off

Next, turn on the configuration keys by following these steps. As of Supply Chain Management version 10.0.36, all **Engineering Change Management** keys are turned on by default, but the **Product dimension - Version** key will only be turned on by default for new systems (not for older systems that are upgraded to version 10.0.36 or later).

1. Put your system into maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Go to **System administration \> Setup \> License configuration**.
1. Expand the **Trade** node.
1. Enable or disable the configuration key for the main feature using the **Engineering Change Management** checkbox.
1. Expand the **Engineering Change Management** node, and select or clear the following checkboxes as required (depending on the features that you want to use):

    - **Attribute search** – Select this checkbox to enable the [attribute search feature](engineering-attributes-and-search.md). We recommend enabling this feature, but you can clear this checkbox if you won't use it.
    - **Change management for process manufacturing** – Select this checkbox if you want to use Engineering change management features to manage changes in formulas for process manufacturing. If you don't have to manage formulas, you can clear this checkbox. For more information, see [Manage changes in formulas and their ingredients](manage-formula-changes.md).

1. If you also want to use the [version dimension](../pim/product-dimensions.md#version-dim), then select the **Product dimension - Version** checkbox. (This checkbox is further down the list, not nested under the **Engineering Change Management** node.) You can clear this check box if you don't need this feature.

    > [!WARNING]
    > When you turn on the **Product dimension - Version** key for an existing system, some functionality could become broken or stop working as expected if you've installed other solutions that add customizations to the inventory dimensions. For the version dimension to be fully functional, you might have to update those solutions so that they include the version dimension in their references to the inventory dimensions. See [The version product dimension](../pim/product-dimensions.md#version-dim) for details.

1. Turn off maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. The database must be synchronized to ensure that the configuration keys are properly updated to reflect your changes. If you changed any of the key settings, do one of the following steps, depending on which type of environment you are working on:
    - **For Tier 1 (development) environments**: Open your project in Microsoft Visual Studio and then select **Dynamics 365 \> Synchronize database \> Synchronize**.
    - **For Tier 2 (and higher) environments**: The database syncs automatically after you put the environment in and out of maintenance mode, so you can skip this step.

### Turn on additional engineering change management features

After you turn on the basic engineering change management features and enable their configuration keys, several additional and optional engineering change management features are added to [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). Each of those features is listed under the **Engineering change management** module. The following table describes each optional feature and provides links for more information.

| Feature name in feature management | Description | Feature state |
|---|---|---|
| Enable change management on existing products | <p>This feature lets you convert existing products to engineering products so that you can start to manage them by using engineering change management.</p><p>For more information, see [Enable change management on existing products](change-management-existing-products.md).</p> | On by default as of version 10.0.25. <br><br>Mandatory as of version 10.0.32. |
| Engineering notifications for production | <p>When a product is changed in engineering, it might be important to notify production about those changes. In that way, production workers can take appropriate action, such as component substitution, bill of materials (BOM) replacement, or route replacement. This feature lets you notify production about changes to products that are being produced.</p><p>For more information, see [Manage changes to engineering products](engineering-change-management.md).</p> |  On by default as of version 10.0.25. <br><br>Mandatory as of version 10.0.32. |
| Improved attribute inheritance for Engineering Change Management | <p>This feature simplifies the management of attributes for finished goods or intermediate items. When this feature is turned on, it's easier to identify all the attributes that belong to an item, and you can select the attributes that should be propagated from that item to its parent item. This feature is useful when, for example, one component of a finished good is fragile, toxic, or flammable, because you can easily identify the fragile, toxic, or flammable attribute and propagate it to the finished good.</p><p>For more information, see [Engineering attributes and engineering attribute search](engineering-attributes-and-search.md).</p> |  On by default as of version 10.0.25. <br><br>Mandatory as of version 10.0.32. |
| Product readiness checks | <p>This feature lets you set up readiness checks for standard (non-engineering) products. Use product readiness checks to ensure that each product is fully defined and all the required policies are configured before the product is made available and used in transactions. If you disable this feature after you've used it for a while, all existing readiness checks for standard products will be deleted.</p><p>For more information, see [Product readiness](product-readiness.md).</p> |  On by default as of version 10.0.25. <br><br>Mandatory as of version 10.0.32. |
| Manage changes to formulas and their ingredients | <p>This feature lets you track changes to formula ingredients, co-products, and by-products.</p><p>For more information, see [Manage changes in formulas and their ingredients](manage-formula-changes.md).</p> |  On by default as of version 10.0.25.<br><br>Mandatory as of version 10.0.36. |
| Variant generation for engineering products | <p>This feature lets you generate variants for engineering products, based on available dimension values.</p><p>For more information, see [Generate variants for engineering products](engineering-variants.md).</p> |  On by default as of version 10.0.25.<br><br>Mandatory as of version 10.0.32. |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

