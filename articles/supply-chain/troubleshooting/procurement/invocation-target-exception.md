---
title: An exception occurs during vendor invoice posting
description: An "Exception has been thrown by the target of an invocation" exception occurs during vendor invoice posting.
author: kamaybac
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: PurchTable, PurchTablePart
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# An exception occurs during vendor invoice posting


## Symptoms

You receive the following exception when posting a vendor invoice:

> Exception has been thrown by the target of an invocation

## Cause

This issue can occur because of inconsistency in purchase order distributions.

## Resolution

To unblock this issue and reset the purchase order to a *Draft* state, go to **Procurement and sourcing \> Periodic tasks \> Clean up \> Purchase order distribution reset**. For more information, see the following blog post: [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).
