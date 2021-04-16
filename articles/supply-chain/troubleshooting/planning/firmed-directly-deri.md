---
title: Directly derived firmed orders are processed by an in-review workflow
description: Directly derived firmed orders are processed by a workflow with a status of "In-review"
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

KB Number: 4612450

## Issue description

Directly derived firmed orders are processed by a workflow with a status of *In-review*.

## Resolution
<!-- KFM: This is not clear. Please revise. Is it the workflow or the order that has an in-review status? -->
This is the expected behavior. Firmed derived orders (subcontract purchase orders) are assigned an *In-review* status when change tracking is enabled.
