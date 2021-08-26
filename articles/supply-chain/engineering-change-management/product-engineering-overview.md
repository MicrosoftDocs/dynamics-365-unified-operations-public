---
# required metadata

title: Engineering change management overview
description: This topic provides an overview of engineering change management, which helps you plan and manage product versioning, and manage product lifecycles and engineering changes.
author: t-benebo
ms.date: 08/26/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: Release 10.0.21
---

# Engineering change management overview

[!include [banner](../includes/banner.md)]

## Feature summary

Today's manufacturers require strong product data management, version control, and engineering change management to succeed in a world of constantly shrinking product lifecycles, increased quality and reliability requirements, and an increased focus on product safety.

Engineering change management brings structure and discipline to the product data management process, and enables products to be defined, released, and revised in a controlled manner that is supported by workflows. Through product versions and engineering change management, you can document, assess the impact of, and apply engineering changes throughout the whole lifecycle of a product.

Engineering change management helps you plan and manage product versioning, and manage product lifecycles and engineering changes. Here is a list of its main features:

- Product versioning
- Enhanced product release functionality that lets you maintain product master data in one legal entity (the engineering company) and publish the fully configured released product to other legal entities
- Rules for validating that required information is entered before a product version is activated (readiness checks)
- Improved product lifecycle management through fine-grained control over when a released product can be used in specific business processes
- Engineering change requests that are supported by workflows
- Engineering change orders that are supported by workflows

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4HE6B]

The preceding video ([Change management capabilities in Dynamics 365 Supply Chain Management](https://youtu.be/N313FqvRuBc)) is included in the [Finance and Operations playlist](https://www.youtube.com/playlist?list=PLcakwueIHoT_SYfIaPGoOhloFoCXiUSyW) available on YouTube.

## Turn on the engineering change management features for your system

Before you can use engineering change management, you must enable both the *Engineering Change Management* feature and its configuration key. If you also want to track the version dimension of products in transactions (optional), then you must also enable the *Product version dimension* feature and its configuration key. Once those are set up as needed, you will also be able to turn on additional optional features for engineering change management.

### Turn on the basic engineering change management features

First, turn on the features by following these steps.

1. Go to the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.
1. Check for updates.
1. Turn on the feature that is named *Engineering Change Management*.
1. If you want to use it, also turn on the feature that is named *Product dimension version*.

### Turn on the required configuration keys

Next, turn on the configuration keys by following these steps.

1. Put your system into maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Go to **System administration \> Setup \> License configuration**.
1. Expand the **Trade** node.
1. Enable the configuration key for the main feature by selecting the **Engineering Change Management** checkbox.
1. Expand the **Engineering Change Management** node, and select or clear the following checkboxes as required (depending on the features that you want to use):

    - **Attribute search** – Select this checkbox to enable the [attribute search feature](engineering-attributes-and-search.md). We recommend enabling this feature, but you can clear this checkbox if you won't use it.
    - **Change management for process manufacturing** – Select this checkbox if you want to use Engineering change management features to manage changes in formulas for process manufacturing. If you don't have to manage formulas, you can clear this checkbox. For more information, see [Manage changes in formulas and their ingredients](manage-formula-changes.md).

1. If you also want to use the version dimension, then select the **Product dimension - Version** checkbox. (This checkbox is further down the list, not nested under the **Engineering Change Management** node.)
1. Turn off maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).

> [!IMPORTANT]
> Starting in April 2022, the license keys for both **Engineering Change Management** and **Product dimension - Version** will be enabled by default for all new installations, but you will still be able to disable them if needed.

### Turn on additional engineering change management features

Once you have turned on the basic engineering change management features and enabled their configuration keys, several additional and optional engineering change management features will be added to feature management, each of which is listed under the *Engineering change management* module. The following table names and describes each optional feature and provides links for more information.

| Feature&nbsp;name in feature&nbsp;management | Description |
|---|---|
| Enable change management on existing products | Enables you to convert existing products to engineering products so you can start to manage them using engineering change management.<br><br>For more information, see [Enable change management on existing products](change-management-existing-products.md) |
| Engineering notifications for production | When a product is changed in engineering, it may be important to notify production of those changes so they can take appropriate actions, such as component substitution, BOM replacement, or route replacement. With this feature, you'll be able to notify production of the changes being made in products that are being produced.<br><br>For more information, see [Manage changes to engineering products](engineering-change-management.md). |
| Improved attribute inheritance for Engineering Change Management | Provides a simpler way to manage attributes for finished goods or intermediate items. With this feature, it will be easier to identify all the attributes that belong to an item and you will be able to choose which should be propagated from that item to its parent item. This is useful, for example, when one of the components of a finished good is fragile, toxic or flammable because then you'll be able to easily identify and propagate the fragile, toxic, or flammable attribute to the finished good.<br><br>For more information, see [Engineering attributes and engineering attribute search](engineering-attributes-and-search.md). |
| Product readiness checks | Enables you to set up readiness checks for standard (non-engineering) products. Use product readiness checks to ensure each product is fully defined and all required policies are configured before the product is made available and used in transactions. If you disable this feature after using it for a while, all existing readiness checks for standard products will be deleted. For more information, see [Product readiness](product-readiness.md). |
| Manage changes to formulas and their ingredients | Enables you to track changes to formula ingredients, co-products, and by-products.<br><br>For more information, see [Manage changes in formulas and their ingredients](manage-formula-changes.md). |
| Variant generation for engineering products | Enables you to generate variants for engineering products based on available dimension values.<br><br>For more information, see [Generate variants for engineering products](engineering-variants.md) |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
