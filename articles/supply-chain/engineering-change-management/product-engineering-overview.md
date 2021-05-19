---
# required metadata

title: Engineering change management overview
description: This topic provides an overview of engineering change management, which helps you plan and manage product versioning, and manage product lifecycles and engineering changes.
author: t-benebo
ms.date: 11/11/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2020-09-28
ms.dyn365.ops.version: Release 10.0.15
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

## Turn on the engineering change management and version dimension features for your system

Before you can use engineering change management, you must enable both the *Engineering Change Management* feature and its configuration key. If you also want to track the version dimension of products in transactions (optional), then you must also enable the *Product version dimension* feature and its configuration key.

First, turn on the features by following these steps.

1. Go to the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.
1. Check for updates.
1. Turn on the feature that is named *Engineering Change Management*.
1. If you want to use it, then also turn on the feature that is named *Product dimension version*.

Next, turn on the configuration keys by following these steps.

1. Put your system into maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Go to **System administration \> Setup \> License configuration**.
1. Expand the **Trade** node.
1. Enable the configuration key for the main feature by selecting the **Engineering Change Management** check box.
1. Expand the **Engineering Change Management** node and select or clear the following checkboxes as needed (depending on which features you want to use):
    - **Attribute search** – Select this check box to enable the [attribute search feature](engineering-attributes-and-search.md). We recommend enabling this feature, but you can clear this check box if you won't use it.
    - **Change management for process manufacturing** – Select this check box if you would like to use Engineering change management features to manage changes in formulas for process manufacturing. If you don't need to manage formulas, then you can clear this check box. For more information, see [Manage changes in formulas and their ingredients](manage-formula-changes.md).
1. If you also want to use the version dimension, then select the **Product dimension - Version** check box. (This check box is further down the list, not nested under the **Engineering Change Management** node.)
1. Turn off maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).

> [!IMPORTANT]
> Starting in April 2022, the license keys for both **Engineering Change Management** and **Product dimension - Version** will be enabled by default for all new installations, but you will still be able to disable them if needed.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
