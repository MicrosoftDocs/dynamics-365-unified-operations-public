---
title: Inventory tag counting
description: Learn about tag counting, which you use to compare the actual contents of a warehouse with the on-hand inventory.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form: InventJournalCount, InventJournalCountTag
ms.topic: how-to
ms.date: 11/19/2024
ms.custom: 
  - bap-template
---

# Inventory tag counting

[!include [banner](../includes/banner.md)]

This article provides information about tag counting, which you use to compare the actual contents of a warehouse with the on-hand inventory.

By creating lines on the **Tag counting** page, you place a tag number on each inventory item, such as a number from 1 to 500. During the count, you enter the item number and the quantity on a corresponding tag. This tag can then be used as the basis for input in the tag counting journal.

After you post the tag counting journal, a new counting journal is created on the **Counting** page. The new journal is based on the tag counting journal lines that you created.

To tag-count items by a specific inventory dimension, select the dimension on the **Display dimension** page that is displayed when you create the tag counting journal. For example, to count items in a specific warehouse, select the **Warehouse** check box. If **Lock items during count** on the **General** tab of the **Inventory and warehouse management parameters** page is set to *Yes*, items can't be physically updated during counting. However, items in tag counting journals aren't locked during counting. Inventory transactions aren't created until the tag counting lines are posted and transferred to a counting journal. If tags are entered randomly, and you want to identify missing tags, select the **Tag** column header to sort the lines by tag.

## Related information

[Cycle counting](../warehousing/cycle-counting.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
