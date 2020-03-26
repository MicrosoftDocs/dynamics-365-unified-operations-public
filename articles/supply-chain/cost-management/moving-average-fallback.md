---
# required metadata

title: Moving average, fallback cost sequence
description: 
author: AndersGirke
manager: AnnBe
ms.date: 03/25/2020
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
ms.author: aevengir
ms.search.validFrom: 2020-03-25
ms.dyn365.ops.version: Release 10.0.11
---

# Moving average fallback cost sequence

One way that you can calculate the cost of your inventory is by using a _Moving average_. Each inventory item can have up to three cost values associated with it, which are:

- **Last issue:** The last issue cost assigned prior to inventory going negative
- **Active cost:** The latest cost activated in a costing version
- **Item price:** The cost specified for the released product

The system uses a _fallback cost sequence_ to establish the order of preference for which of those values to use in the moving average calculation. If the preferred cost value isn&#39;t available, the system will use the next-preferred value, and so on.

In previous versions of Supply Chain Management, the system used a fixed fallback cost sequence (_Last issue – Active cost – Item price_). As of version 10.0.11, this is still the default, but you can also enable a feature that lets you choose from among three available fallback cost sequences. This ability can be especially useful for organizations that use negative inventory values on a regular basis.

To enable the fallback cost sequence selector, you (or an administrator) must use [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable the feature called _Moving average fallback cost sequence_.

To select the fallback cost sequence for moving average calculations:

1. Go to the  **Parameters**  page and open the  **Inventory accounting**  tab.
2. In the  **Moving Average**  section, set the  **Fallback cost sequence**  to one of the following:
    - **Last issue – Active cost – Item price** - This is the default sequence, which is the same one used when the _Moving average fallback cost sequence_ feature isn&#39;t enabled.
    - **Active cost – Last issue**
    - **Active cost – Item price** - This setting can help mitigate performance issues that can occur in organizations that use business processes where inventory regularly goes negative while at the same time having a high transaction volume.

![Inventory accounting parameters](media/inventory-accounting-parameters.png "Inventory accounting parameters")