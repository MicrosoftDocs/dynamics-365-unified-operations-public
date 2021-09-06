---
title: Planned orders take a long time to update
description: When updating the requirement quantity and/or delivery date on a planned order, it typically takes at least 30 seconds per order to save the update
author: ChristianRytt
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# Planned orders take a long time to update

## Symptoms

When updating the requirement quantity and/or delivery date on a planned order, it typically takes at least 30 seconds per order to save the update.

## Resolution

This is a known issue with the built-in master planning engine. It is caused by the underlying auto explosion through the BOM structure during edits. This issue is addressed in Planning Optimization, where a planner can update and approve the relevant orders and, when desired, trigger a planning run to update planned orders for the underlying BOM structure.

One way to improve performance with the built-in master planning engine is to do the following steps:

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Select a plan.
1. Expand the **Time fence in days** FastTab.
1. Set **Explosion** to *Yes*, and set the field below this setting to 0 (zero).

> [!NOTE]
> This will limit the period for explosions performed for this master plan to a single day.
