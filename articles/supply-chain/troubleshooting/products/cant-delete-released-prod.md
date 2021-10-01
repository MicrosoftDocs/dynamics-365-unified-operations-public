---
title: You can't delete a released product
description: You can delete a released product and all its variants only if the released product doesn't have any related transactions.
author: SmithaNataraj
ms.date: 06/11/2021
ms.topic: troubleshooting
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-06-11
ms.dyn365.ops.version: 10.0.18
---

# You can't delete a released product

## Symptoms

You can delete a released product and all its variants only if the released product doesn't have any related transactions.

## Resolution

Follow these steps to delete a released product or product master.

1. Close all open transactions for the items.
1. Reduce the inventory to 0 (zero).
1. Perform inventory closing.
1. Delete all product variants for the product master that you want to delete.
