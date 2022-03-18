---
title: You can't consolidate multiple product receipts into a single purchase order
description: You can't consolidate multiple product receipts into a single purchase order if the different product receipt lines have different accounting dates.
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

# You can't consolidate multiple product receipts into a single purchase order

## Symptoms

You can't consolidate multiple product receipts into a single purchase order if the different product receipt lines have different accounting dates.

## Resolution

In earlier versions of Dynamics 365 Supply Chain Management, consolidation was allowed in this situation. However, the practice is prone to error. The accounting date on the purchase order lines that are created should not differ from the accounting date on the product receipt lines that those purchase order lines were created from. (The accounting date on the purchase order lines matches the accounting date on the purchase order header.) Therefore, the consolidation of multiple product receipts into a single purchase orders is no longer allowed.

The accounting date is used, for example, for budget reservations and encumbrance. Therefore, it should be kept during the transition from product receipt to purchase order.
