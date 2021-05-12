---
title: Planned purchase order is created when a purchase exists within negative days
description: If the coverage code is Min/max, Planning Optimization creates a planned purchase order when a purchase exists within negative days.
author: ChristianRytt
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ReqTransPo,MpsIntegrationParameters
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: ilebedev
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Planned purchase order is created when a purchase exists within negative days

KB number: 4614298

## Symptoms

If the coverage code is *Min/max*, Planning Optimization creates a planned purchase order when a purchase exists within negative days.

## Resolution

Planning Optimization doesn't support negative days. However, it always ensures that planned orders won't be scheduled within the lead time relative to the current date. For example, the purchase lead time is 10 days, and a purchase order is expected to arrive eight days from today. In this case, the purchase order will be used as supply for demand that is five days from today.

Therefore, we recommend that you adjust your lead times to cover all (or almost all) of your scenarios.
