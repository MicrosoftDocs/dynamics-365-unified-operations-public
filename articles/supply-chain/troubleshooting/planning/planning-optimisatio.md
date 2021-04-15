---
title: Planned purchase order created when a purchase exists within negative days
description: Planning Optimization creates a planned purchase order when a purchase exists within negative days if the coverage code is min/max
author: SmithaNataraj
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

# Planned purchase order created when a purchase exists within negative days

KB Number: 4614298

## Issue description

Planning Optimization creates a planned purchase order when a purchase exists within negative days if the coverage code is min/max.

## Resolution

This is the expected behavior. Planning Optimization doesn't support negative days. However, Planning Optimization always ensures that planned orders won't be scheduled within the lead time relative to the current date. For example, if the purchase lead time is 10 days and there is a purchase order that is expected to arrive 8 days from now, then it will be used as supply for the demand that is, for example, 5 days from now. Therefore, we recommend that you adjust your lead times to cover all (or nearly all) of your scenarios.
