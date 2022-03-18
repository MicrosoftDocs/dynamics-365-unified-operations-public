---
title: BOM explosion behaves differently for firmed and estimated production orders
description: Bill of materials explosion behaves differently for firmed production orders and for estimated production orders for manually created work
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

# BOM explosion behaves differently for firmed and estimated production orders

## Symptoms

When a production order is firmed, the items aren't exploded when you explode the bill of materials (BOM). However, when you manually create a work order and then estimate the production order, the items are exploded.

### Resolution

The explosion that occurs when the production order is firmed will point to the planned order, but it doesn't appear that the planned order is currently firmed in this case. However, if the production order has been estimated, the explosion is triggered from the released production order where no planned order exists.
