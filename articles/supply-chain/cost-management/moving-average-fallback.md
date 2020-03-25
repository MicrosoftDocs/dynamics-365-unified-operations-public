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

One way that you can evaluate your inventory is by using a _Moving average_. For organizations that need to support negative physical inventory values, the moving average method can implement the fallback cost sequence of _Last issue – Active cost – Item price_ to determine the cost.

This feature helps to mitigate performance issues can occur in organizations that use business processes where inventory regularly goes negative while at the same time having a high transaction volume. If this applies to you, then using a fallback cost sequence of _Active cost – item price_ may help solve the issue.

To set up moving average calculations:

1. Go to the **Parameters** page and open the **Inventory accounting** tab.
1. In the **Moving average** section, set the **Fallback cost sequence** to one of the following:
    - **Last issue – Active cost – Item price** (Default value when enabling the feature)
    - **Active cost – Last issue**
    - **Active cost – item price**

![Inventory accounting parameters](media/inventory-accounting-parameters.png "Inventory accounting parameters")