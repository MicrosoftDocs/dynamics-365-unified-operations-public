---
title: You can't filter master planning items by their related coverage group values
description: You can't filter master planning items by their related coverage group values.
author: ChristianRytt
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ReqTransPo
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: ilebedev
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# You can't filter master planning items by their related coverage group values

KB number: 4612572

## Symptoms

You want to filter the items that will be included in a master planning batch job, based on the values of related records from the item coverage table. (For example, you want to filter items by their **Vendor** and/or **Coverage group** value). The filter setup for the batch job lets you create a join from the **Items** table to the **Item coverage** table, and then specify field values from the item coverage table in your query. However, after you complete this setup, the system still creates planned orders for the whole item coverage, not just for the items that match the specified field values from the item coverage table.

## Resolution

The batch job filter can filter only on items. Although you can add a join to the **Item coverage** table, filter settings that you make against that table won't affect the query output. At runtime, the system runs planning for all the coverage groups and all the variations that the filtered items have. After an item is already included in the run, any coverage groups that are included in the item filter a won't affect the planning output.
