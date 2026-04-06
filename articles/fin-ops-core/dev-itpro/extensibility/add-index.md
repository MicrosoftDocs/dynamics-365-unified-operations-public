---
title: Add indexes to tables through extension
description: Learn how to add an index to a table through extension so that you can store additional data for access to data based on the new fields.
author: ivanv-microsoft
ms.author: ivanv
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-06-01
ms.dyn365.ops.version: Platform update 4
---

# Add indexes to tables through extension

[!include [banner](../includes/banner.md)]

Often, you extend tables so that you can store extra data for later use but also quickly access data that's based on the new fields. Therefore, it's often beneficial to have a dedicated index that speeds up the database search. You can add a new index to an existing table through extension. To add an index to an existing table, extend the selected table, and then create an index just as you would create an index on a new table. You can add both new and existing fields so that they're part of the new index.

In the following illustration, an `InventTable` extension is used to define an index for a new field on the `InventTable` table.

:::image type="content" source="media/AddIndex.jpg" alt-text="Screenshot of a new index defined on the InventTable extension.":::

> [!WARNING]
> Don't use this approach to create unique indexes. This change is an intrusive change that might break the solutions of other independent software vendors (ISVs) if those solutions are deployed in the same environment. This capability will be removed in future platform releases.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
