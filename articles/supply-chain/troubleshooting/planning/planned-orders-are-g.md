---
title: Master planning generates planned orders for phantom products
description: Planned orders are generated for phantom products after master planning is run.
author: ChristianRytt
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ReqTransPo
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: anderso
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Master planning generates planned orders for phantom products

KB number: 4614729

## Symptoms

Planned orders are generated for phantom products after master planning is run.

## Resolution

The setting of the **Phantom** option for released products determines the default line type on the bill of material (BOM). When the **Phantom** option is set to *Yes*, the system will still create planned orders for the item, but the **Directly derived requirement** option for each planned order will be set to *Yes*. Therefore, the planned production order can't be firmed on its own. Instead, it will always be automatically included when the parent production order is firmed. Additionally, the BOM lines of the planned phantom order will be included in the BOM of the parent production order.
