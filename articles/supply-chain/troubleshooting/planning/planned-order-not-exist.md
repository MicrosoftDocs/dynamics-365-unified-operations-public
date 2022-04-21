---
title: The system can't find a planned order during operations on multiple orders
description: A "Planned order does not exist" error occurs when you perform operations on multiple planned orders, and at least two orders belong to the same item ID.
author: t-benebo
ms.date: 12/07/2021
ms.topic: troubleshooting
ms.search.form: ReqTransPo_ReqTransPoMarkChangeType
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-12-07
ms.dyn365.ops.version: 10.0.24
---

# The system can't find a planned order during operations on multiple orders

Error code: SYS24774

## Symptoms

You receive the following error message when you try to perform an operation on multiple planned orders at the same time, and at least two of the orders belong to the same item ID. For example, the error might occur when the orders are firmed or their order type is changed.

> Planned order %1 does not exist.

## Cause

When the system firms or changes the type of an order, it must reconsider existing planned orders for the item, to make sure that the planned supply matches the demand and existing supply. As part of this process, the system re-creates planned orders for the item. Therefore, the second planned order that the system expects to process no longer exists.

## Workaround

Approve the orders before you process them. In this way, the orders won't be deleted when the system processes the first order for the item.
