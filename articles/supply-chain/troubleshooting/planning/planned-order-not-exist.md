---
title: The system can't find a planned order when operating on multiple orders
description: You get a 'Planned order does not exist' error When operating on multiple planned orders where at least two orders belong to the same item ID
author: t-benebo
ms.date: 12/07/2021
ms.topic: troubleshooting
ms.search.form: 
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-12-07
ms.dyn365.ops.version: 10.0.24
---

# The system can't find a planned order when operating on multiple orders

## Symptoms

You get a "Planned order does not exist" error when attempting to perform an operation on multiple planned orders at the same time where at least two orders belong to the same item ID (for example, on firm or change order type).

## Cause

When the system firms or changes the type of an order, it must reconsider existing planned orders for the item  to make sure the planned supply matches the demand and existing supply. As a part of this process, the system recreates planned orders for the item and therefore the second planned order that the system was expecting to process no longer exists.

## Workaround

Approve the orders before processing them because then they won't be deleted when the system processes the first order for the item.
