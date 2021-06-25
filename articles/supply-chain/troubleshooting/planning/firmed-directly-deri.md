---
title: Directly derived firmed orders are processed by an in-review workflow
description: Directly derived firmed orders are processed by a workflow that has a status of In-review.
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

# Directly derived firmed orders are processed by an in-review workflow

KB number: 4612450

## Symptoms

Directly derived firmed orders are processed by a workflow that has a status of *In-review*.

## Resolution

When change tracking is enabled, a status of *In-review* is assigned to firmed derived orders (subcontract purchase orders). Therefore, if a purchase order is derived (a subcontract purchase order), it's only submitted to a workflow. If a purchase order is a firmed planned purchase order, it's automatically approved to ensure that the planning engine doesn't create new planned orders while the purchase order is still in *Draft* status.
