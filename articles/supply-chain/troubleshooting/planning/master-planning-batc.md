---
title: Can't filter master planning items by their related coverage group values
description: Can't filter master planning items by their related coverage group values
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

# Can't filter master planning items by their related coverage group values

KB Number: 4612572

## Symptoms

You would like to filter the items to be included in a master planning batch job according to values of related records from the item coverage table (for example, to filter items by their **Vendor** and/or **Coverage group**). The batch job filter setup allows you to create a join from the **Items** table to the **Item coverage** table, and then to specify field values from the item coverage table in your query. However, when you do so, the system still creates planned orders for the entire item coverage, not just for the items that match the values you specified from the item coverage table.

## Resolution

The batch job filter is only able to filter on items. Although you are able to add a join to the **Item coverage** table, filter settings that you make against that table will not affect the query output because at runtime, the system runs planning for all the coverage groups and all the variations those filtered items have. Any coverage groups that are included in the items filter won't affect the planning output after a given item is already included in the run.
