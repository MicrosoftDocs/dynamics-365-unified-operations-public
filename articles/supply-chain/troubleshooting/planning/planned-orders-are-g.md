---
title: Planned orders are generated for phantom products after running master planning
description: Planned orders are generated for phantom products after running master planning
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

KB Number: 4614729

## Issue description

Planned orders are generated for phantom products after running master planning.

## Resolution

The **Phantom** setting on released products determines what the default line type on the bill of material (BOM) should be. When **Phantom** is set to *Yes*, the system will still create planned orders for the item, but the planned order will have **Directly derived requirement** set to *Yes*. This means that the planned production order can't be firmed on its own, it will always be included automatically when the parent production order is firmed, and the BOM lines of the planned phantom order will be included in the BOM of the parent production order.  
