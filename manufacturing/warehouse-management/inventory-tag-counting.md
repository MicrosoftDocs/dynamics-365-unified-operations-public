---
# required metadata

title: Inventory tag counting | Microsoft Docs
description: This article provides information about tag counting, which you use to compare the actual contents of a warehouse with the on-hand inventory. 
author: YuyuScheller
manager: AnnBe
ms.date: 2015-10-30 12:54:09
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: InventJournalCount, InventJournalCountTag
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 2084
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 11594
ms.assetid: ed1e26a9-8ad9-4a17-96e0-282c86ba5717
ms.region: Global
# ms.industry: 
ms.author: mafoge

---

# Inventory tag counting

This article provides information about tag counting, which you use to compare the actual contents of a warehouse with the on-hand inventory. 

By creating lines on the **Tag counting** page, you place a tag number on each inventory item, such as a number from 1 to 500. During the count, you enter the item number and the quantity on a corresponding tag. This tag can then be used as the basis for input in the tag counting journal. After you post the tag counting journal, a new counting journal is created on the **Counting** page. The new journal is based on the tag counting journal lines that you created. To tag-count items by a specific inventory dimension, select the dimension on the **Display dimension** page that is displayed when you create the tag counting journal. For example, to count items in a specific warehouse, select the **Warehouse** check box. If the **Lock items during count** slider on the **Inventory and warehouse management parameters** page is selected, items can't be physically updated during counting. However, items in tag counting journals aren't locked during counting. Inventory transactions aren't created until the tag counting lines are posted and transferred to a counting journal. If tags are entered randomly, and you want to identify missing tags, click the **Tag** column header to sort the lines by tag.

See also
--------

[Cycle counting](https://docs.microsoft.com/en-us/dynamics365/operations/manufacturing/warehouse-management/cycle-counting)

