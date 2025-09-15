---
title: Engineering change management overview
description: Access an overview of engineering change management, which helps you plan and manage product versioning, and manage product lifecycles and engineering changes.
author: sgmsft
ms.author: shwgarg
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: overview
ms.date: 03/18/2025
ms.custom: 
  - bap-template
---

# Engineering change management overview

[!include [banner](../includes/banner.md)]

## Feature summary

Today's manufacturers require strong product data management, version control, and engineering change management to succeed in a world of constantly shrinking product lifecycles, increased quality and reliability requirements, and an increased focus on product safety.

Engineering change management brings structure and discipline to the product data management process, and enables products to be defined, released, and revised in a controlled manner that is supported by workflows. Through product versions and engineering change management, you can document, assess the impact of, and apply engineering changes throughout the whole lifecycle of a product.

Engineering change management helps you plan and manage product versioning, and manage product lifecycles and engineering changes. Here's a list of its main features:

- Product versioning
- Enhanced product release functionality that lets you maintain product master data in one legal entity (the engineering company) and publish the fully configured released product to other legal entities
- Rules for validating that required information is entered before a product version is activated (readiness checks)
- Improved product lifecycle management through fine-grained control over when a released product can be used in specific business processes
- Engineering change requests that are supported by workflows
- Engineering change orders that are supported by workflows

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=5580ff02-3710-47ca-a022-7f9a8ea9c3c3]

The preceding video ([Change management capabilities in Dynamics 365 Supply Chain Management](https://youtu.be/N313FqvRuBc)) is included in the [finance and operations playlist](https://www.youtube.com/playlist?list=PLcakwueIHoT_SYfIaPGoOhloFoCXiUSyW) available on YouTube.

## Number sequence requirements

To use engineering change management, both the BOM number sequence and the formula number sequence (if you're using formulas) must be set to *Automatic* on the **Number sequences** page.

## Turn the required configuration keys on or off

As of Supply Chain Management version 10.0.36, all **Engineering Change Management** keys are turned on by default, but the **Product dimension - Version** key will only be turned on by default for new systems (not for older systems that are upgraded to version 10.0.36 or later). If you need to turn any of these keys on or off, follow these steps.

1. Put your system into maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Go to **System administration \> Setup \> License configuration**.
1. Expand the **Trade** node.
1. Enable or disable the configuration key for the main feature using the **Engineering Change Management** checkbox.
1. Expand the **Engineering Change Management** node, and select or clear the following checkboxes as required (depending on the features that you want to use):

    - **Attribute search** – Select this checkbox to enable the [attribute search feature](engineering-attributes-and-search.md). We recommend enabling this feature, but you can clear this checkbox if you won't use it.
    - **Change management for process manufacturing** – Select this checkbox if you want to use Engineering change management features to manage changes in formulas for process manufacturing. If you don't have to manage formulas, you can clear this checkbox. Learn more in [Manage changes in formulas and their ingredients](manage-formula-changes.md).

1. If you also want to use the [version dimension](../pim/product-dimensions.md#version-dim), then select the **Product dimension - Version** checkbox. (This checkbox is further down the list, not nested under the **Engineering Change Management** node.) You can clear this check box if you don't need this feature.

    > [!WARNING]
    > When you turn on the **Product dimension - Version** key for an existing system, some functionality could become broken or stop working as expected if you've installed other solutions that add customizations to the inventory dimensions. For the version dimension to be fully functional, you might have to update those solutions so that they include the version dimension in their references to the inventory dimensions. See [The version product dimension](../pim/product-dimensions.md#version-dim) for details.

1. Turn off maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. The database must be synchronized to ensure that the configuration keys are properly updated to reflect your changes. If you changed any of the key settings, do one of the following steps, depending on which type of environment you're working on:
    - **For Tier 1 (development) environments**: Open your project in Microsoft Visual Studio and then select **Dynamics 365 \> Synchronize database \> Synchronize**.
    - **For Tier 2 (and higher) environments**: The database syncs automatically after you put the environment in and out of maintenance mode, so you can skip this step.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
