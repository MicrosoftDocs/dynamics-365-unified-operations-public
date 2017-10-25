---
# required metadata

title: Inventory tag counting
description: This article provides information about tag counting, which you use to compare the actual contents of a warehouse with the on-hand inventory.
author: MarkusFogelberg
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventJournalCount, InventJournalCountTag
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: YuyuScheller
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail
# ms.tgt_pltfrm:
ms.custom: 11594
ms.assetid: 03772d0e-5c37-454c-ab85-82bc8b60a76d
ms.search.region: Global
# ms.search.industry:
ms.author: mafoge
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Inventory tag counting

[!include[banner](../includes/banner.md)]

[!include[retail name](../includes/retail-name.md)]


This article provides information about tag counting, which you use to compare the actual contents of a warehouse with the on-hand inventory.

By creating lines on the **Tag counting** page, you place a tag number on each inventory item, such as a number from 1 to 500. During the count, you enter the item number and the quantity on a corresponding tag. This tag can then be used as the basis for input in the tag counting journal. After you post the tag counting journal, a new counting journal is created on the **Counting** page. The new journal is based on the tag counting journal lines that you created. To tag-count items by a specific inventory dimension, select the dimension on the **Display dimension** page that is displayed when you create the tag counting journal. For example, to count items in a specific warehouse, select the **Warehouse** check box. If the **Lock items during count** slider on the **Inventory and warehouse management parameters** page is selected, items can't be physically updated during counting. However, items in tag counting journals aren't locked during counting. Inventory transactions aren't created until the tag counting lines are posted and transferred to a counting journal. If tags are entered randomly, and you want to identify missing tags, click the **Tag** column header to sort the lines by tag.

See also
--------

[Cycle counting](../warehousing/cycle-counting.md)
