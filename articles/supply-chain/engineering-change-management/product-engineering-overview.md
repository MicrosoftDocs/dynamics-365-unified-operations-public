---
# required metadata

title: Engineering change management overview
description: This topic provides an overview of engineering change management, which helps you plan and manage product versioning, and manage product lifecycles and engineering changes.
author: t-benebo
manager: tfehr
ms.date: 09/28/2020
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

## Turn on engineering change management for your system

First, turn on engineering change management by following these steps.

1. Go to [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
1. Check for updates.
1. Turn on the feature that is named **(Preview) Engineering Change Management**.

Next, turn on the **Engineering Change Management** configuration key by following these steps.

1. Put your system into maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
1. Go to **System administration \> Setup \> License configuration**.
1. Expand the **Trade** node, and select the **Engineering Change Management** check box.
1. Turn off maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
