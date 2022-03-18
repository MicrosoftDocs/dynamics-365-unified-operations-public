---
title: Planned orders are generated for in-stock with production orders
description: Planned orders are generated even though you have items in stock and production orders already exist for them
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


# Planned orders are generated for in-stock with production orders

## Symptoms

Planned orders are generated even though you have items in stock and production orders already exist for them.

## Resolution

You might be able to fix this issue by increasing the **Positive days** value for the relevant groups on the **Coverage group** page. This change will cause the system to determine whether on-hand inventory can be used for the demand. Then a new planned order won't be generated for the items that are in stock.
