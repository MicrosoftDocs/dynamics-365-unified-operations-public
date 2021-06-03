---
title: Master planning is scheduling more than the available capacity
description: Master planning doesn't seem to respect capacity limitations and is scheduling more than the available capacity
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

# Master planning is scheduling more than the available capacity

## Symptoms

Master planning doesn't seem to respect capacity limitations and is scheduling more than the available capacity.

When you use operation scheduling where there is finite capacity, and where the route specifies a mix of requirements for both a resource group and individual resources, there is a small chance of overbooking because of the way that the algorithm validates for capacity conflicts. This overbooking can occur when you use helpers to run master planning. It's most likely to occur if there are many jobs that have a relatively short runtime.

## Resolution

If it's essential that no overbooking occur for operation scheduling, you can make the scheduling part of master planning single-threaded by turning on the **Accurate finite capacity for Operation Scheduling** option on the **Master planning parameters** page. This option isn't available by default. You must manually add it to the page by using personalization features. When you use this option, scheduling will run more slowly because of the lack of parallel processing.
