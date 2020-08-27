---
# required metadata

title: Product engineering overview
description: The product engineering solution helps you plan and manage product versioning, lifecycle management, and engineering change management.
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

# Product engineering overview

<!-- KFM: should we call it "Engineering change management" or "Product engineering"? -->

[!include [banner](../includes/banner.md)]

## Feature summary

Today’s manufacturers require strong product data management, version control and engineering change management to succeed in a world of constantly shrinking product lifecycles, increased quality and reliability requirements, as well as an increased focus on product safety.

Engineering change management brings structure and discipline to the product data management process and enables products to be defined, released and revised in a controlled manner supported by workflows. Through product versions and engineering change management, it is possible to document, assess the impact of, and apply engineering changes throughout the entire lifecycle of a product.

Engineering change management helps you plan and manage product versioning, lifecycle management, and engineering change management. Its main features are:

- Product versioning
- Enhanced product release functionality that enables you to maintain product master data in one legal entity (the engineering company), and publish the fully configured released product to other legal entities
- Rules for validating that necessary information is populated before a product version is activated (readiness checks)
- Fine-grained control of when a released product may be used in certain business processes (improved product lifecycle management)
- Engineering change requests with workflow support
- Engineering change orders with workflow support

## Turn on the project engineering solution for your system

To enable it, turn on the configuration key **Engineering Change Management**.

<!-- KFM: We would normally provide a longer description of how to this, something like:

    1. Place your system into maintenance mode as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
    2. Go to **System administration \> Setup \> License configuration**.
    3. Expand the **XXXX** section.
    4. Select the **XXXXXX** check box.
    5. Turn off maintenance mode as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).

Can we do that here? Do we also need to do anything in feature management? The private preview version of this document probably needs to describe how to enable the flight too.

 -->
