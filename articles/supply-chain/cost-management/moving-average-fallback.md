---
# required metadata

title: Moving average, fallback cost sequence
description: 
author: AndersGirke
manager: AnnBe
ms.date: 03/10/2020
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
ms.search.validFrom: 2020-03-10
ms.dyn365.ops.version: Release 10.0.11
---

# Moving average, fallback cost sequence

In Microsoft Dynamics 365 Supply Chain Management, you can evaluate inventory by method **Moving average**. Organizations may have business scenarios where physical negative Inventory is required for a short period of time. **Moving average** supports this by applying a default sequence **&quot;Last issue – Active cost – Item price&quot;** used to determine the cost.

A new feature **Moving average, fallback cost sequence** is introduced in **Inventory accounting- parameters** allowing users to select between 3 pre-determined fallback sequences.

- **Last issue – Active cost – Item price** (Default value when enabling the feature)
- **Active cost – Last issue**
- **Active cost – item price**

This feature is introduced to mitigate performance issues observed in Organizations that have business processes where inventory regularly goes negative and at the same time have a high transaction volume. Customers matching this profile will benefit selecting a fallback sequence **Active cost – item price.**
